---
title: 如何优雅地使用Visual Studio Code（VScode）编写LaTeX
subtitle: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”（What
  You See Is What You Get），因此选择合适且舒适的编辑器能让写作事半功倍。
date: 2022-05-08T07:01:51.966Z
summary: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”（What
  You See Is What You Get），因此选择合适且舒适的编辑器能让写作事半功倍。
draft: false
featured: false
authors:
  - admin
lastmod: 2022-4-25T00:00:00Z
tags:
  - $\LaTeX$
  - VScode
categories:
  - 软件学习
projects: []
---
## **前言**

* TeX是由Donald E.Knuth开发的、以排版文字和数学公式为目的的一个计算机软件。  


* 大多数时候，为了简单我们编写LaTeX是利用其专门的编辑器，例如TeXworks、WinEdt以及TexStudio等，往往这一类的编辑器功能齐全，集编辑和预览于一身。但同时这类编辑器往往界面效果不佳，作为一个颜值党，这是我不能接受的。


* 本文只关注编辑器，关于TeX的环境或发行版一般可以选择Texlive或者MikTex，Texlive相对较大，功能比较齐全，如果空间允许建议安装。此外CTex是专门面向中文的发行版，已经许久没有维护了，体验不佳，建议非必要不要安装。

---

## **为什么选择VScode**
流行的文本编辑器很多，例如Sublime Text、Atom以及Notepad++等，关于LaTeX不同编辑器的比较在维基百科上进行了相关比较：

{{< hl >}}> [http://en.wikipedia.org/wiki/Comparison_of_TeX_editor](http://en.wikipedia.org/wiki/Comparison_of_TeX_editors){{< /hl >}}

{{hl}}选择VScode有以下三点主要原因：
* 
*
*
---