---
title: 如何优雅地使用Visual Studio Code（VScode）编写LaTeX
subtitle: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”，选择合适且舒适的编辑器能让你的写作事半功倍。
date: 2022-05-10T07:22:53.436Z
summary: 作为世界上最强大的排版系统，LaTeX是每一名科研工作者必备技能之一，尤其对于理工科而言，其重要性不言而喻。LaTeX并非“所见即所得”，选择合适且舒适的编辑器能让你的写作事半功倍。
draft: false
featured: false
authors:
  - admin
lastmod: 2022-4-25T00:00:00Z
tags:
  - LaTeX
  - VScode
commentable: true
categories:
  - 软件学习
projects: []
---
{{< toc >}}

## **前言**

* TeX是由Donald E.Knuth开发的、以排版文字和数学公式为目的的一个计算机软件。LaTeX是建立在TeX上的一套宏集。TeX家族庞大且复杂，感兴趣可以参考[这里](https://www.overleaf.com/learn/latex/Articles/The_TeX_family_tree%3A_LaTeX%2C_pdfTeX%2C_XeTeX%2C_LuaTeX_and_ConTeXt)。
* 大多数时候，可以利用特定的LaTeX编辑器编写LaTeX程序，例如[**TeXworks**](https://tug.org/texworks/)、[**WinEdt**](https://www.winedt.com/)以及[**TexStudio**](https://www.texstudio.org/)等，这类编辑器功能齐全，通常集编辑和预览于一身。然而，这类编辑器的界面往往显示效果不佳，这也是该文的写作缘由。
* 本文只关注编辑器，关于TeX的发行版一般可以选择[**TexLive**](https://www.latex-project.org/)（通用）、[**MikTeX**](https://miktex.org/)（Windows）以及[**MacTeX**](https://www.tug.org/mactex/)（MacOS）等，TexLive功能比较齐全，如果空间允许建议安装。此外CTex是专门面向中文的发行版，已经许久没有维护了，体验不佳，建议非必要不要安装。
* 本文只关注本地编辑器，这里有许多非常优秀且好用的线上LaTeX编辑器，例如[**OverLeaf**](https://www.overleaf.com/)、[**Slager**](https://www.slager.cn/#/home)以及[**JaxEdit**](http://jaxedit.com/note/)等。
* 关于TexLive以及[**VScode**](https://code.visualstudio.com/)的安装，本文在此不再赘述。

- - -

## **为什么选择VScode**

当前流行的文本编辑器很多，例如Sublime Text、Atom以及Notepad++等，关于LaTeX不同编辑器的比较在维基百科上有详细的说明：

> [http://en.wikipedia.org/wiki/Comparison_of_TeX_editors](http://en.wikipedia.org/wiki/Comparison_of_TeX_editors)

选择VScode有以下三点原因：

* 轻量级且速度快，并且VScode还可以提供只有IDE才提供的终端功能。
  
* 免费且开源，这两点非常具有吸引力，况且VScode有大名鼎鼎的微软支持。
  
* 高扩展性，插件几乎可以无所不能，高移植性，可在各大平台运行，甚至可以在网页运行你的[**VScode**](https://github.com/coder/code-server)，以及完善的文档和庞大的社区，帮助你随时学习。

当然以上都是软件本身的优质特性，实际上在使用以后，强大的搜索能力、代码补全能力以及优美的高亮显示等性能，都会让你爱不释手！

**总结即是：VScode is all you need！**
{style="color: green"}

- - -

## **VScode配置LaTeX**

关于VScode配置LaTeX的相关文档可以参考VScode插件LaTeX Workshop:

> [https://github.com/James-Yu/LaTeX-Workshop/wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki)

本文将主要配置步骤总结如下：

1. **在VScode中安装插件LaTeX Workshop**： 如果一切顺利，打开tex源文件，点击VScode左侧TEX里面的`Build LaTeX project`便可以进行编译，并利用VScode内置PDF进行查看。
  
2. **外置的PDF阅读器**： 如上所说，可以使用VScode内置的PDF阅读器，但个人建议使用[**Sumatra PDF**](https://www.sumatrapdfreader.org/download-free-pdf-viewer)作为外置的PDF阅读器，该PDF十分轻巧，适合简单的阅读和查看。

3. **VScode设置**：进入VScode按`Ctrl+Shift+P`搜索settings，打开Open Settings（JSON），即settings.json文件，将其修改如下：

```json
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

```json
// 注意修改自己电脑中VScode的路径
InverseSearchCmdLine = "D:\VScode\Microsoft VS Code\Code.exe" "D:\VScode\Microsoft VS Code\resources\app\out\cli.js" --ms-enable-electron-run-as-node -r -g "%f:%l"
EnableTeXEnhancements = true
```

至此，有关VScode配置LaTeX的主要步骤结束。为了有更好地体验，可增加以下配置：

```json
// VScode自动换行
"editor.wordWrap": "on",

// 右键选择Format Document或者Shift+Alt+F可以自动调整tex文件格式
"[latex]": {
    "editor.defaultFormatter": "James-Yu.latex-workshop"
    },
```

- - -

## **VScode推荐插件**

* **filesize** - 便捷显示文件大小

* **WakaTime** - 记录你的编程时间

* **Material Icon Theme** - 更好看的文件图标

* **Code Spell Checker** - 检查拼写

- - -

## **VScode常用快捷键**

* `Ctrl+Shift+P`：打开VScode命令窗

* `Ctrl+Alt+B`：编译当前TeX文件

* `Ctrl+Alt+V`：查看PDF文件

* `Ctrl+Alt+J`：定位到PDF指定位置

* `Shift+Alt+F`：格式化TeX文件

* `Ctrl+/`：增加/取消当前注释

- - -

## **LaTeX好用功能**

1. 利用[**Pandoc**](https://pandoc.org/)可以直接将tex源码转化为Word，非常方便，当然它还可以转化为其它更多的格式。

2. 利用[**LaTeXdiff**](https://www.overleaf.com/learn/latex/Articles/Using_Latexdiff_For_Marking_Changes_To_Tex_Documents)可以比较两个tex文件的差异并生成diff.tex，再利用TexLive编译该diff.tex即可生成PDF文件，非常方便。

- - -

## **一些提示**

1. 在VScode的tex源文件中输入`@`以及将鼠标停留在LaTeX数学环境之间都会有意想不到的效果，更多特性可以参考[这里](https://github.com/James-Yu/LaTeX-Workshop)。

2. VScode的主题个人比较喜欢[**Brackets Light Pro**](https://marketplace.visualstudio.com/items?itemName=fehey.brackets-light-pro)、[**Github Theme**](https://marketplace.visualstudio.com/items?itemName=GitHub.github-vscode-theme)、[**Eva Theme**](https://marketplace.visualstudio.com/items?itemName=fisheva.eva-theme)、[**One Dark Pro**](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)、[**Atom One Light Theme**](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onelight)以及[**Atom One Dark Theme**](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-theme-onedark)。

3. LaTeX在线公式编辑推荐[LaTeX公式编辑器](https://www.latexlive.com/home)，在线表格编辑推荐[Tables Generator](https://www.tablesgenerator.com/latex_tables)。

4. LaTeX简单学习推荐[它](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)。

5. [CTAN](https://www.ctan.org/)：一个TeX最全面的归档网络。

6. [Mathpix](https://mathpix.com/)：一款非常便捷的公式转化软件，可以通过截图等方式直接获取公式LaTeX源码或其他格式。

- - -

## **参考**

1. [Visual Studio Code (vscode) 配置LaTeX](https://zhuanlan.zhihu.com/p/166523064)

2. [使用VSCode编写LaTeX](https://zhuanlan.zhihu.com/p/38178015)

3. [VS Code + LaTeX](https://zhuanlan.zhihu.com/p/108095566)

4. [有哪些好的 LaTeX 编辑器](https://www.zhihu.com/question/19954023/answer/23121933)

5. [TeX 家族](https://zhuanlan.zhihu.com/p/248669482)

6. [How to use Latexdiff with TexLive?](https://tex.stackexchange.com/questions/376483/how-to-use-latexdiff-with-texlive)

7. [Windows下Pandoc转换LaTeX成Word最全指令](https://blog.csdn.net/qq_27464321/article/details/88853270)

---
