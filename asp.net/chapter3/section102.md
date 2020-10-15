# Xamarin refit API

## 设置请求 Headers

### 1. 静态 headers

```csharp
[Headers("User-Agent: Awesome Octocat App")]
[Get("/users/{user}")]
Task<User> GetUser(string user);
```

静态 headers 可以添加到每一个请求中

```csharp
[Headers("User-Agent: Awesome Octocat App")]
public interface IGitHubApi
{
    [Get("/users/{user}")]
    Task<User> GetUser(string user);
    
    [Post("/users/new")]
    Task CreateUser([Body] User user);
}
```

移除静态 headers 

```csharp
[Headers("X-Emoji: :rocket:")]
public interface IGitHubApi
{
    [Get("/users/list")]
    [Headers("X-Emoji")] // 移除 X-Emoji header
    Task<List> GetUsers();
    
    [Get("/users/{user}")]
    [Headers("X-Emoji:")] // 重新定义 X-Emoji header 的值为空
    Task<User> GetUser(string user);
    
    [Post("/users/new")]
    Task CreateUser([Body] User user, [Header("X-Emoji")] string emoji);
}
```

重新定义 headers

```csharp
[Headers("X-Emoji: :rocket:")]
public interface IGitHubApi
{
    [Get("/users/list")]
    Task<List> GetUsers();  // X-Emoji: :rocket:
    
    [Get("/users/{user}")]
    [Headers("X-Emoji: :smile_cat:")]
    Task<User> GetUser(string user);  // X-Emoji: :smile_cat:
    
    [Post("/users/new")]
    [Headers("X-Emoji: :metal:")]
    Task CreateUser([Body] User user, [Header("X-Emoji")] string emoji);  // X-Emoji: :trollface:
}
```

重新定义只适用于具有相同名称的 headers，以下代码将导致包含所有 headers

```csharp
[Headers("Header-A: 1")]
public interface ISomeApi
{
    [Headers("Header-B: 2")]
    [Post("/post")]
    Task PostTheThing([Header("Header-C")] int c);  // Header-A: 1  // Header-B: 2  // Header-C: 3
}
```

### 2. 动态 headers

#### 2.1 headers设置在参数里

```csharp
[Get("/users/{user}")]
Task<User> GetUser(string user, [Header("Authorization")] string authorization);
// Authorization: OAUTH-TOKEN
```

```csharp
[Get("/users/{user}")]
Task<User> GetUser(string user, [Authorize("Bearer")] string authorization);
// Authorization: Bearer OAUTH-TOKEN
```

#### 2.2 添加方法`AuthenticatedHttpClientHandler`继承`HttpClientHandler`

```csharp
public class AuthenticatedHttpClientHandler : HttpClientHandler
    {
        private readonly string token;

        public AuthenticatedHttpClientHandler(string getToken)
        {
            if (getToken == null) throw new ArgumentNullException(nameof(getToken));
            this.token = getToken;
        }

        protected override async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken cancellationToken)
        {
            // See if the request has an authorize header
            var auth = request.Headers.Authorization;
            if (auth != null)
            {
                var token = this.token;
                request.Headers.Authorization = new AuthenticationHeaderValue(auth.Scheme, token);
            }

            return await base.SendAsync(request, cancellationToken).ConfigureAwait(false);
        }
    }
```

接口

```csharp
[Headers("Authorization: Bearer")]
public interface IGitHubApi
{
    [Get("/users/list")]
    [Headers("X-Emoji")] // 移除 X-Emoji header
    Task<List> GetUsers();
    
    [Get("/users/{user}")]
    Task<User> GetUser(string user);
    
    [Post("/users/new")]
    Task CreateUser([Body] User user);
}
```

调用

```csharp
string token = "OAUTH-TOKEN";
var api = RestService.For<IMemberPortalServices>(new HttpClient(new AuthenticatedHttpClientHandler(token)) { BaseAddress = new Uri("http://my.service.uri/app") });
var location = await api.GetLocationOfRebelBase();
// Authorization: Bearer OAUTH-TOKEN
```

