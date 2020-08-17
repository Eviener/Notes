---
description: XML DOM 定义了所有 XML 元素的对象和属性，以及访问它们的方法（接口）。
---

# XML DOM 基础知识

## 一、简介

HTML DOM 和 XML DOM 都是DOM的不同部分

### 1. DOM  -用于任何结构化文档的标准模型

DOM 是 **W3C**（World Wide Web Consortium）**标准**。

DOM 定义了访问诸如 XML 和 HTML 文档的标准：

DOM 是**W3C 文档对象模型**（全称 Document Object Model）。是一个使程序和脚本 有能力 动态地访问和更新文档的内容、结构以及样式的**平台**和语言中立的**接口**。

 DOM 定义了所有文档元素的**对象和属性**，以及访问它们的**方法**（接口）。

### 2. XML DOM  -用于 XML 文档的标准模型

* 用于 XML 的标准对象模型
* 用于 XML 的标准编程接口
* 中立于平台和语言
* W3C 标准

 XML DOM 定义了所有 XML 元素的**对象和属性**，以及访问它们的**方法**（接口）。

 换句话说：**XML DOM 是用于获取、更改、添加或删除 XML 元素的标准。**XML DOM 包含了遍历 XML 树，访问、插入及删除节点的方法（函数）。

### 3. HTML DOM  -用于 HTML 文档的标准模型

 HTML DOM 定义了所有 HTML 元素的**对象和属性**，以及访问它们的**方法**（接口）。

## 二、什么是 DOM

xml文件：

```markup
<?xml version="1.0" encoding="utf-8"?>
<customer id="12" status="archived">
	<firstname>Joe</firstname>
	<lastname>Bloggs</lastname>
</customer>
```

起始部分是声明，紧接着是根元素`customer`。  
`customer`元素有两个属性\(`id`和`status`\)，每个属性都有其对应值\(`"12"`和`"archived"`\)。  
`customer`节点下有两个子元素`firstname`和`lastname`，每个子元素都含有简单的文本内容（`"Joe"`和`"Bloggs"`）。

XML文档的每个部分（**声明、元素、属性、值和文本内容**）都可以用类表示。如果使用集合属性来存储子内容，我们就可以用一棵对象树来完整的表示整个文档。这称为文档对象模型\(Document Object Model\)，或DOM。

## 三、节点

XML 文档中的每个成分都是一个**节点**。

XML DOM 节点的规定：

* 整个文档是一个文档节点
* 每个 XML 元素是一个元素节点
* 包含在 XML 元素中的文本是文本节点
* 每一个 XML 属性是一个属性节点
* 注释是注释节点

**文本总是存储在文本节点中**。

例：**`<year>2005</year>`**，元素节点 `<year>`，拥有一个值为 `2005` 的文本节点。

## 四、节点树

 XML DOM 把 XML 文档视为一种树结构。这种树结构被称为**节点树**。

可通过节点树访问所有节点。可以修改或删除它们的内容，也可以创建新的元素。

### 父节点、子节点和同级节点

* 在节点树中，顶端的节点称为根节点
* 根节点之外的每个节点都有一个父节点
* 节点可以有任何数量的子节点

