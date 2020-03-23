- [基础](#basic)
  * [使用通配符的技巧](#useLIKE)
  * [正则表达式](#reg)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

<a name="basic"></a>
# 基础
<a name="useLIKE"></a>
## 使用通配符的技巧
* 把通配符置于搜索模式的开始处，搜索起来是最慢的
<a name="reg"></a>
## 正则表达式
* 区分大小写: REGEXP BINARY
* OR匹配：[123] = 1 | 2 | 3
* 匹配任意一个字符： '.000' 可以匹配 '1000', '2000', etc
* NOT匹配：[^123] = 匹配除这些字符以外的任何东西
* 匹配范围：[1 - 9]：匹配1-9任意一个数字，[a-z]：匹配a到z任意一个字母
* 转义：
  * "\\." 匹配 字符串中包含"."；
  * 多数正则表达式实现使用单个反斜杠转义特殊字符。MYSQL要求两个反斜杠（MUYSQL自己解释一个，正则表达式库解释另一个）
