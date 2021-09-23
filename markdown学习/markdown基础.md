# Markdown 基本要素

## 各级标题
> # 这是一级标题
> ## 二级标题
> ### 三级标题
> #### 四级标题
> ##### 五级标题
> ###### 六级标题

## 标题id
> # 这个标题拥有1个id {#my_id}
MPE拓展特性

## 强调
*斜体*  
**粗体** 
*组**合符**号*  
~~删除文字~~

## 列表
- Item 1 
- Item 2
  - Item 2a
  - item 2b

## 有序列表
1. Item 1
1. Item 2
2. Item 3
   1. Item 3a
   2. Item 3b

## 添加图片
![desktop](https://i.loli.net/2020/02/25/SfXi8mREukVOoUT.png)
强烈建议使用`html`代码添加图片，能调居中大小什么的，方便多了
```html
<div align=center>
    <img src="https://i.loli.net/2020/02/25/SfXi8mREukVOoUT.png" width="20%">
</div> 
```
<div align=center>
    <img src="https://i.loli.net/2020/02/25/SfXi8mREukVOoUT.png" width="20%">
</div> 

## 链接
http://github.com 
[GitHub](http://github.com)

## 引用
As xxx say:
> We're living the future so
> the present is our past.

## 分割线
---
***
___

## 行内代码
`<addr>`

## 代码块
```
print hello
```

### 语法高亮
```python
print hello
```

```applescript
tell application "Safari"
    make new document
end tell
```

### 代码块class（MPE扩展特性）
给代码设置`class`，类似属性。
```javascript {.class1 .class}
funtion add(x,y) {
    return x + y
}
```

### 代码行数（class的一种）

```javascript {.line-numbers}
funtion add(x,y) {
    return x + y
}
```

### 高亮代码行数
添加`highlight`属性的来高亮代码行数
```applescript {.line-numbers}
property the_urls : {¬
	"https://www.liaoxuefeng.com/wiki/896043488029600/900375748016320", ¬
	"https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git"}

tell application "Safari"
	if the_urls = {} then
		-- If you don't want to open a new window for an empty list, replace the
		-- following line with just "return"
		set {first_url, rest_urls} to {"", {}}
	else
		-- `item 1 of ...` gets the first item of a list, `rest of ...` gets
		-- everything after the first item of a list.  We treat the two
		-- differently because the first item must be placed in a new window, but
		-- everything else must be placed in a new tab.
		set {first_url, rest_urls} to {item 1 of the_urls, rest of the_urls}
	end if
	
	make new document at end of documents with properties {URL:first_url}
	tell window 1
		repeat with the_url in rest_urls
			make new tab at end of tabs with properties {URL:the_url}
		end repeat
	end tell
end tell
```

## 任务列表
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> support
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

## 扩展语法
### 表格
需要在插件设置中打开`enableExtendedTableSyntax`选项来使其工作。
colspan `>` or `empty cell`:
| a   | b   |
| --- | --- |
| >   | 1   |
| 2   |     |

rowspan `^`:
| a   | b   |
| --- | --- |
| 1   | 2   |
| ^   | 4   |

## Emoji & Font-Awesome
只适用于`markdown-it parser`而不适用于`pandoc parser`。
:smile:
:fa-car:

## 上标
30^th^

## 下标
H~2~O

## 脚注
Content [^1]
[^1]: Hi! This is a footnote

## 缩略
_[HTML]: Hyper Text Markup Language
_[W3C]: World wide Web Consortium
The HTML specification
is maintained by the W3C.

## 标记
==marked==

## CriticMarkup

Lorem ipsum dolor{++ sit++} amet…
Lorem{-- ipsum--} dolor sit amet…
Lorem {~~hipsum~>ipsum~~} dolor sit amet…
Lorem ipsum dolor sit amet.{>>This is a comment<<}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. {==Vestibulum at orci magna. Phasellus augue justo, sodales eu pulvinar ac, vulputate eget nulla.==}{>>confusing<<} Mauris massa sem, tempor sed cursus et, semper tincidunt lacus.