---
description: 2020-06-12 新学笔记
---

# 常用命令

## Param 设置参数

* **string** 类型参数：`[string]$Context`
* **int** 类型参数：`[int]$Context`
* **Array** 数组：`[string[]]$Schemas`

**`throw`** 设置参数必填

```csharp
Param(
[string[]]$Tables=$(throw "表名称不能为空,多个表用英文逗号隔开"),
[string]$SaveTo=$(throw "表对应生成的模型代码保存路径不能为空"),
[string[]]$Schemas,
[string]$Context
)
```

**注意：**参数必须写在代码的最前面

## echo 打印、输出

```csharp
echo "正在检查默认项目设置......"
```

## write-warning 打印、输出警告

```csharp
write-warning "设置成功，当前数据库操作上下文为：$Context";
```

## pwd 当前路径

返回当前路径，是个对象

```csharp
//用个变量存储当前路径
$servicePath=pwd;
//获取当前路径
$install=$servicePath.Path;
```

## pushd 修改路径

```csharp
pushd c:\windows\system32;
```

## Windows服务进程

```csharp
//定义参数
Param(
[string]$Name=$(throw "系统服务名称不能为空"),
[string]$Description=$(throw "请用简单一句描述一下你的服务"),
)

//生成Windows服务进程，并设置服务启动状态为自动启动
sc.exe create $Name binPath=$install start=auto;

//设置服务描述
sc.exe description $Name $Description;

//开始启动Windows服务
sc.exe start $Name;

//查看服务运行情况
sc.exe query $Name;

//删除服务
sc.exe delete $Name;
```

更多Windows**服务进程**相关知识可[查看官方文档](https://docs.microsoft.com/zh-cn/powershell/scripting/samples/managing-services?view=powershell-7)。

