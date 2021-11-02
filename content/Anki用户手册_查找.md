# 查找

[TOC]

## 简单搜索

​				

当你在搜索框中输入文本时，Anki 会查找出匹配的笔记并显示出笔记所生成的卡片。Anki查找笔记中所有字段的内容，但不搜索标签（可看看后面搜索标签的部分）。

<details> <summary>查看官方英文文档</summary>
    When you type some text into the search box, Anki finds matching notes and displays their cards. Anki searches in all fields of the notes, but does not search for tags (see later in this section for how to search for tags). 
    </details> 

举例说明：

| 查找内容           | 解释                                                     | 官方英文解释                                                 |
| ------------------ | -------------------------------------------------------- | ------------------------------------------------------------ |
| dog                | 匹配像 "doggy" and "underdog"                            | search for "dog" - will match words like "doggy" and "underdog" too. |
| dog cat            | 查找**同时**包括 "dog" 和 "cat" 的笔记                   | finds notes that have both "dog" and "cat" on them, such as "raining cats and dogs". |
| dog or cat         | 查找有 "dog" 或 "cat"  的笔记                            | finds notes with either "dog" or "cat".                      |
| dog (cat or mouse) | 查找dog and cat 或 dog and mouse的笔记                   | finds notes with dog and cat, or dog and mouse.              |
| -cat               | 查找不含 "cat" 的笔记                                    | finds notes without the word "cat".                          |
| -cat -mouse        | 查找同时不含 "cat" 和 "mouse" 的笔记                     | finds notes with neither "cat" nor "mouse".                  |
| -(cat or mouse)    | 同上                                                     | same as the above.                                           |
| "a dog"            | 查找含有a dog笔记，如匹配atta dog，但不匹配dog a 和 adog | finds notes with the exact sequence of characters "a dog" on them, such as "atta dog", but not "dog a" or "adog". |
| -"a dog"           | 查找不含a dog的笔记                                      | finds notes without the exact phrase "a dog"                 |
| d_g                | 查找**d+任意一个字符+g**的笔记，如 dog, dig, dug 等      | finds notes with d, <a letter>, g, like dog, dig, dug, and so on. |
| d*g                | 查找**d+0个及以上字符+g** , 如 dg, dog, dung 等          | finds notes with d, <zero or more letters>, g, like dg, dog, dung, etc. |
| w:dog              | 查找单词dog的笔记，不匹配像 "doggy" or "underdog".       | search for "dog" on a word boundary - will match "dog", but not "doggy" or "underdog". Requires Anki 2.1.24+ or AnkiMobile 2.1.61+. |
| w:dog*             | 匹配 dog and doggy 但不匹配 underdog                     | will match "dog" and "doggy", but not "underdog".            |
| w:*dog             | 匹配 dog and underdog 但不匹配 doggy                     | will match "dog" and "underdog", but not "doggy".            |



从上面的例子中需要注意的事情

* 搜索词之间用<kbd>backspace</kbd>分开

* 当有多个搜索词时，Anki会从笔记中匹配所有的搜索词，搜索词之间会加上 'and' 。在 Anki 2.1.24+ and AnkiMobile 2.0.60+ 如你所愿 ("dog and cat" 等同 "dog cat") 。但是旧版本中and会作为一个查找的单词。
* 匹配多个搜索词中任意一个，你可以使用 "or" 。
* 你可以使用 "-" 去排除某搜索词。
* 你可以使用圆括号来放置多个搜索词，如： dog (cat or mouse) 。这个将 OR 和 AND 组合起来搜索，例子中的圆括号，它匹配 'dog cat' 或 'dog mouse' ，如果没有圆括号，则匹配 'dog and cat' 或 'mouse' 。
* Anki只能在排序字段（自定义字段里设置）中搜索格式化文本（加粗，倾斜，颜色等）。例如：如果在你某个字段内容里面有个 "**exa**mple" （注意exa有加粗），当搜索词是 "example" ，在字段不是排序字段时，它将无法匹配到 "**exa**mple" 。如果搜索词在字段里没有格式化，或者没有部分格式化，Anki是可以在任何字段搜索到的。
* 标准的搜索对拉丁字符a-z，A-Z不区分大小写。其他字符，如斯拉夫字母则区分大小写，不过你可以通过搜索时大小写都写上或者正则表达式来达到忽略大小写。



## 在指定字段中搜索其内容

Anki 可以匹配在指定字段中的文本。字段的匹配默认情况下是精确匹配。

| 查找内容      | 解释                                                         | 官方英文解释                                                 |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| front:dog     | 在字段名为Front中查找含有 "dog" 笔记，含有 "a dog" 的文本则不匹配。 | find notes with a Front field of exactly "dog". A field that says "a dog" will not match. |
| front:\*dog\* | 在字段名为Front中查找'dog' 的笔记。                          | find notes with Front field containing dog somewhere         |
| front:        | 在字段名为Front中查找为空的笔记。                            | find notes that have an empty Front field                    |
| front:_*      | 在字段名为Front中查找不为空的笔记。                          | find notes that have a non-empty Front field                 |
| front:*       | 在字段名为Front中查找空和不为空的笔记。                      | find notes that have a Front field, empty or not             |
| fr*:text      | 在字段名以  "fr" 开头中查找text的笔记。要求Anki 2.1.24+ or AnkiMobile 2.1.60+。 | find notes in a field starting with "fr". Requires Anki 2.1.24+ or AnkiMobile 2.1.60+. |

## 标签，牌组，卡片模板，笔记类型

| 查找内容                    | 解释                                                         | 官方英文解释                                                 |
| --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| tag:animal                  | 查找 "animal" 标签的笔记                                     | find notes with the tag "animal"                             |
| tag:none                    | 查找没有标签的笔记                                           | find notes with no tags                                      |
| tag:ani*                    | 查找以ani开头的标签的笔记                                    | find notes with tags starting with ani                       |
| deck:french                 | 查找 French 的牌组，子牌组，如French::Vocab                  | find cards in a French deck, or subdecks like French::Vocab  |
| deck:french -deck:french::* | 查找French 的牌组，但不含子牌组                              | find cards in French, but not subdecks                       |
| deck:"french vocab"         | 查找 "french vocab" ，注意查找内容有空格需加双引号。         | searching when a deck has a space                            |
| "deck:french vocab"         | 同上                                                         | also ok                                                      |
| deck:filtered               | 筛选的牌组                                                   | filtered decks only                                          |
| -deck:filtered              | 不是筛选的牌组                                               | normal decks only                                            |
| card:forward                | 查找 "Forward" 的卡片模板。                                  | search for Forward cards                                     |
| card:2                      | 查找第2个卡片模板，如笔记中的第2个完形填空所对应的模板，翻转卡片中的第2个等。 | search for cards by template number - eg, to find the second cloze deletion for a note, you’d use |
| note:basic                  | 查找笔记类型是 "Basic" 的卡片。                              | search for cards with a Basic note type                      |

## 忽略重音，组合字符

要求 Anki 2.1.24+ 或 AnkiMobile 2.0.60+ 以上

你可以使用  `nc:` 来移除组合字符。举例如下：

| 查找内容 | 解释                                     | 官方英文解释                                         |
| -------- | ---------------------------------------- | ---------------------------------------------------- |
| nc:uber  | 匹配含有 "uber", "über", "Über" 等的笔记 | matches notes with "uber", "über", "Über" and so on. |
| nc:は    | 匹配  "は", "ば", and "ぱ"               | matches "は", "ば", and "ぱ"                         |



## 正则表达式

Anki 2.1.24+ and AnkiMobile 2.0.60+ 支持使用正则表达式来搜索笔记中的内容。一个标准和强大的搜索文本的方式。

使用 re: 来开始正则搜索。Anki将会按照下面原始输入来处理，所有记住下面所列的规则。

举例说明：

> "re:(some|another).*thing"

查找含有  "some" or "another"  + 0至多个字符 + "thing" 的笔记。

> re:\d{3}

查找有3个数字的笔记。

正则搜索同样可以指定在某一字段中搜索其内容，请注意和一般在指定字段中搜索其内容不同，正则表达式不需要精确匹配，也是说是模糊匹配，不区分大小写。

> front:re:[a-c]1

匹配在 "Front" 字段中  a1, B1 or c1 。

> front:re:^[a-c]1$

像上面一样，但是如果前面和后面有任何字符则不匹配。^ 表示行首，$ 表示行尾。

需要注意：

* 默认情况下搜索是不区分大小写的，如果要区分大小写可以使用  (?-i) 。
* 一些文本比如空格、换行在 HTML 里有不同。你可以使用 HTML 编辑器来查看 HTML 文本。
* 对于Anki正则支持的具体情况，可以查看正则文档：
  https://docs.rs/regex/1.3.9/regex/#syntax



## 卡片的状态

| 查找内容     | 解释                         | 官方英文解释                                                 |
| ------------ | ---------------------------- | ------------------------------------------------------------ |
| is:due       | 复习卡片和学习中卡片等待学习 | review cards and learning cards waiting to be studied        |
| is:new       | 新卡片                       | new cards                                                    |
| is:learn     | 学习中的卡片                 | cards in learning                                            |
| is:review    | 到期或没到期的复习卡片       | reviews (both due and not due) and lapsed cards              |
| is:suspended | 暂停的卡片                   | cards that have been manually suspended                      |
| is:buried    | 隐藏的卡片                   | cards that have been buried, either [automatically](https://docs.ankiweb.net/studying.html#siblings-and-burying) or manually |





## 卡片的属性



## 近期的事件



### 添加



### 编辑



### 回答



### 第一次回答



## 匹配特殊字符



### 原始输入



## 卡片ID







