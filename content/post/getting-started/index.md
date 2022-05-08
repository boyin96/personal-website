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

* TeX是由Donald E.Knuth开发的、以排版文字和数学公式为目的的一个计算机软件。LaTeX是以TeX为基础的格式，是建立在TeX上的一套宏集。  


* 大多数时候，编写LaTeX是利用其专门的编辑器，例如TeXworks、WinEdt以及TexStudio等，这一类的编辑器功能齐全，集编辑和预览于一身。但这类编辑器的界面往往效果不佳，这是我不能接受的。


* 本文只关注编辑器，关于TeX的环境或发行版一般可以选择TexLive（通用）、MikTeX（Windows）以及MacTeX（MacOS）等，TexLive相对较大，功能比较齐全，如果空间允许建议安装。此外CTex是专门面向中文的发行版，已经许久没有维护了，体验不佳，建议非必要不要安装。

* 关于[TexLive](https://www.latex-project.org/)以及[VScode](https://code.visualstudio.com/)的安装，本文在此不再赘述。

---

## **为什么选择VScode**
流行的文本编辑器很多，例如Sublime Text、Atom以及Notepad++等，关于LaTeX不同编辑器的比较在维基百科上进行了相关比较：

> http://en.wikipedia.org/wiki/Comparison_of_TeX_editors

选择VScode有以下三点主要原因：

* 轻量级且速度快，并且VScode可以提供只有IDE才能有的例如终端等功能。

* 免费且开源，这两点应该是非常具有吸引力的，况且VScode的背后可是“宇宙无敌”的微软。

* 高扩展性，插件几乎可以无所不能，高移植性，可在各大平台运行，甚至可以在网页运行你的[VScode](https://github.com/coder/code-server)，以及完善的文档和社区，帮助你随时学习。

**总结即是：VScode is all you need！**
{style="color: green"}

---

## VScode配置LaTeX
关于VScode配置LaTeX的相关文档可以参考VScode插件LaTeX Workshop:
> https://github.com/James-Yu/LaTeX-Workshop/wiki

本文将主要配置步骤总结如下：
1. **在VScode中安装插件LaTeX Workshop**： 如果一切顺利，打开tex文件，点击VScode左侧TEX里面的Bulid LaTeX project便可以进行编译查看。 

2. **配置额外的PDF阅读器**： 如上所说，可以使用VScode内置的PDF阅读器，但个人建议使用[Sumatra PDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer)作为额外的PDF阅读器，该PDF十分轻巧，适合简单的阅读和查看。

3. **VScode设置**：进入VScode按Ctrl+Shift+P搜索settings，打开Open Settings （JSON）即settings.json文件，将其修改如下：


---

## Tips

VScode的主题

---