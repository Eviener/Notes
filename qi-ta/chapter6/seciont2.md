# gitbook 命令行

## 1、常用命令

### 1.安装 gitbook

```text
npm install gitbook-cli -g
```

### 2.查看版本\(检验是否安装成功\)

```text
gitbook -V
```

### 3.初始化gitbook

首先进入你要写书的目录，输入如下命令：

```text
gitbook init
```

初始化 GitBook 目录，则会创建 `README.md` 和 `SUMMARY.md`两个 `markdown`格式的文件

* README.md - 项目的介绍
* SUMMARY.md - GitBook 的目录结构

### 4.定义目录结构

先在`SUMMARY.md`文件定义目录结构，然后在根目录下执行命令：

```text
gitbook init
```

将会自动生成目录结构对应的文件夹和 markdown 文件

### 5.启动服务，浏览书籍

```text
gitbook serve--open
```

### 6.**打包**

```text
gitbook build
```

### 7.更新 gitbook

```text
npm update gitbook-cli -g
```

### 8.卸载 gitbook

```text
npm uninstall gitbook-cli -g
```

