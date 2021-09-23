# 如何在TeX里得到总页数
整体思路很简单粗暴，就是在文档的最后添加一个label。然后在需要的地方pageref一下。。。。
然而这个东西被做成了一个lastpage的宏包。相信这个宏包的作者应该会处理好细节的。

```
\usepackage{lastpage}
\pageref{LastPage} % 在任何你需要总页数的地方。
```