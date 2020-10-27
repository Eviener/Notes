---
description: 开发中经常会遇到的问题及解决方案
---

# .NET Core 常见问题

## 1、api 接口参数首字母大写

## 2、api路由

```csharp
[HttpGet]
[Route("~/api/IDCard/CreateTempIDCardPdfPreview/{coverageId}/{name}.pdf")]
public FileStreamResult CreateTempIDCardPdfPreview([Required] int coverageId)
{
    return null;
}
```



