---
description: Node 对象代表文档树中的一个单独的节点。
---

# XML DOM Node对象

 这里的节点可以是：元素节点、属性节点、文本节点等所有的节点类型。

## 一、Node 对象属性

| 属性 | 描述 |
| :--- | :--- |
| [baseURI](https://www.runoob.com/dom/prop-node-baseuri.html) | 返回节点的绝对基准 URI。 |
| [childNodes](https://www.runoob.com/dom/dom-prop-node-childnodes.html) | 返回节点的子节点的节点列表。 |
| [firstChild](https://www.runoob.com/dom/dom-prop-node-firstchild.html) | 返回节点的第一个子节点。 |
| [lastChild](https://www.runoob.com/dom/dom-prop-node-lastchild.html) | 返回节点的最后一个子节点。 |
| [localName](https://www.runoob.com/dom/prop-node-localname.html) | 返回节点名称的本地部分。 |
| [namespaceURI](https://www.runoob.com/dom/dom-prop-node-namespaceuri.html) | 返回节点的命名空间 URI。 |
| [nextSibling](https://www.runoob.com/dom/dom-prop-node-nextsibling.html) | 返回元素之后紧接的节点。 |
| [nodeName](https://www.runoob.com/dom/dom-prop-node-nodename.html) | 返回节点的名称，根据其类型。 |
| [nodeType](https://www.runoob.com/dom/dom-prop-node-nodetype.html) | 返回节点的类型。 |
| [nodeValue](https://www.runoob.com/dom/dom-prop-node-nodevalue.html) | 设置或返回节点的值，根据其类型。 |
| [ownerDocument](https://www.runoob.com/dom/dom-prop-node-ownerdocument.html) | 返回节点的根元素（document 对象）。 |
| [parentNode](https://www.runoob.com/dom/dom-prop-node-parentnode.html) | 返回节点的父节点。 |
| [prefix](https://www.runoob.com/dom/prop-node-prefix.html) | 设置或返回节点的命名空间前缀。 |
| [previousSibling](https://www.runoob.com/dom/dom-prop-node-previoussibling.html) | 返回元素之前紧接的节点。 |
| [textContent](https://www.runoob.com/dom/dom-prop-node-textcontent.html) | 设置或返回节点及其后代的文本内容。 |

注意：Text 节点中可能不包含子节点，所以把子节点添加到文本节点中可能会导致一个 DOM 错误。

## 二、Node 对象方法

| 方法 | 描述 |
| :--- | :--- |
| [appendChild\(\)](https://www.runoob.com/dom/dom-met-node-appendchild.html) | 把新的子节点添加到节点的子节点列表末尾。 |
| [cloneNode\(\)](https://www.runoob.com/dom/dom-met-node-clonenode.html) | 克隆节点。 |
| [compareDocumentPosition\(\)](https://www.runoob.com/dom/dom-met-node-comparedocumentposition.html) | 比较两个节点的文档位置。 |
| getFeature\(feature,version\) | 返回 DOM 对象，此对象可执行带有指定特性和版本的专门的 API。 |
| getUserData\(key\) | 返回与节点上键关联的对象。此对象必须首先通过使用相同的键调用 setUserData 来设置到此节点。 |
| [hasAttributes\(\)](https://www.runoob.com/dom/dom-met-node-hasattributes.html) | 如果节点拥有属性，则返回 ture，否则返回 false。 |
| [hasChildNodes\(\)](https://www.runoob.com/dom/dom-met-node-haschildnodes.html) | 如果节点拥有子节点，则返回 true，否则返回 false。 |
| [insertBefore\(\)](https://www.runoob.com/dom/dom-met-node-insertbefore.html) | 在已有的子节点之前插入一个新的子节点。 |
| isDefaultNamespace\(URI\) | 返回指定的 namespaceURI 是否默认。 |
| [isEqualNode\(\)](https://www.runoob.com/dom/dom-met-node-isequalnode.html) | 检查两个节点是否相等。 |
| [isSameNode\(\)](https://www.runoob.com/dom/dom-met-node-issamenode.html) | 检查两个节点是否为同一节点。 |
| isSupported\(feature,version\) | 返回指定的特性是否在此节点上得到支持。 |
| [lookupNamespaceURI\(\)](https://www.runoob.com/dom/met-node-lookupnamespaceuri.html) | 返回匹配指定前缀的命名空间 URI。 |
| [lookupPrefix\(\)](https://www.runoob.com/dom/met-node-lookupprefix.html) | 返回匹配指定命名空间 URI 的前缀。 |
| normalize\(\) | 把节点（包括属性）下的所有文本节点放置到一个"标准"的格式中，其中只有结构（比如元素、注释、处理指令、CDATA 区段以及实体引用）来分隔 Text 节点，例如，既没有相邻的 Text 节点，也没有空的 Text 节点。 |
| [removeChild\(\)](https://www.runoob.com/dom/dom-met-node-removechild.html) | 删除子节点。 |
| [replaceChild\(\)](https://www.runoob.com/dom/dom-met-node-replacechild.html) | 替换子节点。 |
| setUserData\(key,data,handler\) | 把对象关联到节点上的键。 |

