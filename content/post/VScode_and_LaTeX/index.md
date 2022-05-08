---
title: 如何优雅地使用Visual Studio Code（VScode）编写LaTeX
subtitle: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”（WYSIWYG，What
  You See Is What You Get），选择合适且舒适的编辑器能让你的写作事半功倍。
date: 2022-05-08T12:57:27.315Z
summary: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”（WYSIWYG，What
  You See Is What You Get），选择合适且舒适的编辑器能让你的写作事半功倍。
draft: false
featured: false
authors:
  - admin
lastmod: 2022-4-25T00:00:00Z
tags:
  - LaTeX
  - VScode
categories:
  - 软件学习
projects: []
---
## **前言**

* TeX是由Donald E.Knuth开发的、以排版文字和数学公式为目的的一个计算机软件。LaTeX是建立在TeX上的一套宏集。TeX家族非常庞大且复杂，感兴趣可以参考[这里](https://www.overleaf.com/learn/latex/Articles/The_TeX_family_tree%3A_LaTeX%2C_pdfTeX%2C_XeTeX%2C_LuaTeX_and_ConTeXt)。
* 大多数时候，可以利用特定的LaTeX编辑器编写LaTeX程序，例如TeXworks、WinEdt以及TexStudio等，这类编辑器功能齐全，通常集编辑和预览于一身。然而，这类编辑器的界面往往显示效果不佳，这也是该文的写作缘由。
* 本文只关注编辑器，关于TeX的发行版一般可以选择TexLive（通用）、MikTeX（Windows）以及MacTeX（MacOS）等，TexLive功能比较齐全，如果空间允许建议安装。此外CTex是专门面向中文的发行版，已经许久没有维护了，体验不佳，建议非必要不要安装。
* 本文只关注本地编辑器，这里有许多非常优秀且好用的线上LaTeX编辑器，例如[OverLeaf](https://www.overleaf.com/)、[Slager](https://www.slager.cn/#/home)以及[JaxEdit](http://jaxedit.com/note/)等。
* 关于[TexLive](https://www.latex-project.org/)以及[VScode](https://code.visualstudio.com/)的安装，本文在此不再赘述。

- - -

## **为什么选择VScode**

当前流行的文本编辑器很多，例如Sublime Text、Atom以及Notepad++等，关于LaTeX不同编辑器的比较在维基百科上有详细的说明：

> {{< hl >}}[http://en.wikipedia.org/wiki/Comparison_of_TeX_editors](http://en.wikipedia.org/wiki/Comparison_of_TeX_editors){{< /hl >}}

选择VScode有以下三点原因：

* 轻量级且速度快，并且VScode还可以提供只有IDE才提供的终端功能。
* 免费且开源，这两点非常具有吸引力，况且VScode有大名鼎鼎的微软支持。
* 高扩展性，插件几乎可以无所不能，高移植性，可在各大平台运行，甚至可以在网页运行你的[VScode](https://github.com/coder/code-server)，以及完善的文档和庞大的社区，帮助你随时学习。

**总结即是：VScode is all you need！**
{style="color: green"}

- - -

## VScode配置LaTeX

关于VScode配置LaTeX的相关文档可以参考VScode插件LaTeX Workshop:

> {{< hl >}}https://github.com/James-Yu/LaTeX-Workshop/wiki{{< /hl >}}

本文将主要配置步骤总结如下：

1. **在VScode中安装插件LaTeX Workshop**： 如果一切顺利，打开tex文件，点击VScode左侧TEX里面的Bulid LaTeX project便可以进行编译查看。 
2. **外置的PDF阅读器**： 如上所说，可以使用VScode内置的PDF阅读器，但个人建议使用[Sumatra PDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer)作为外置的PDF阅读器，该PDF十分轻巧，适合简单的阅读和查看。
3. **VScode设置**：进入VScode按{{< hl >}}Ctrl+Shift+P{{< /hl >}}搜索settings，打开Open Settings （JSON）即settings.json文件，将其修改如下：

```
// 外置PDF阅读器
"latex-workshop.view.pdf.viewer": "external",
"latex-workshop.view.pdf.external.viewer.command": "D:/SumatraPDF/SumatraPDF.exe", // 注意修改自己电脑中PDF的路径
"latex-workshop.view.pdf.external.viewer.args": [
        "%PDF%"
    ],
 
// 设置正向和反向搜索
"latex-workshop.view.pdf.external.synctex.command": "D:/SumatraPDF/SumatraPDF.exe", // 注意修改自己电脑中PDF的路径
"latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        // 注意修改自己电脑中VScode以及PDF的路径
        "\"D:\\VScode\\Microsoft VS Code\\Code.exe\" \"D:\\VScode\\Microsoft VS Code\\resources\\app\\out\\cli.js\" --ms-enable-electron-run-as-node -r -g \"%f:%l\"",
        "%PDF%"
    ],
  
// 防止保存即自动编译
"latex-workshop.latex.autoBuild.run": "never",

// 鼠标右键tex文件可显示特有的功能
"latex-workshop.showContextMenu": true,

// 去掉错误和警告信息提醒，这些可以在VScode终端获取
"latex-workshop.message.error.show"  : false,
"latex-workshop.message.warning.show": false,

// 能够获取宏包中命令，从而开启自动补全功能
"latex-workshop.intellisense.package.enabled": true,
```

与此同时，在Sumatra PDF的高级选项中，修改其txt文件，在最后增加：

```
// 注意修改自己电脑中VScode的路径
InverseSearchCmdLine = "D:\VScode\Microsoft VS Code\Code.exe" "D:\VScode\Microsoft VS Code\resources\app\out\cli.js" --ms-enable-electron-run-as-node -r -g "%f:%l"
EnableTeXEnhancements = true
```

至此，有关VScode配置LaTeX的主要步骤结束。为了有更好地体验，通常会增加以下配置：

```
// 根据个人习惯将列数控制在90以内
"editor.rulers": [
        90
    ],
"editor.wordWrap": "wordWrapColumn",
"editor.wordWrapColumn": 90,

// 右键选择Format Document或者Shift+Alt+F可以自动调整tex文件格式
"[latex]": {
    "editor.defaultFormatter": "James-Yu.latex-workshop"
    },
```

- - -

## Tips

1. 在VScode的tex源文件中输入@会有意想不到的效果，更多特性可参考[这里](https://github.com/James-Yu/LaTeX-Workshop)。

2. VScode的主题我个人比较喜欢[Github Theme](https://marketplace.visualstudio.com/items?itemName=GitHub.github-vscode-theme)、[Eva Theme](https://marketplace.visualstudio.com/items?itemName=fisheva.eva-theme)、[One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)以及[Atom One Light/Dark Theme](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onelight)。

3. LaTeX在线公式编辑推荐[LaTeX公式编辑器](https://www.latexlive.com/home)，在线表格编辑推荐[Tables Generator](https://www.tablesgenerator.com/latex_tables)。

4. LaTeX简单学习推荐[它](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)。

- - -