---
title: "Obsidian Setup for Math Note Taking"
author: "Leon Han"
date: 2023-09-17T21:21:23-07:00
description: "The Ultimate Solution for Math Note Taking"
draft: false
---
## Introduction
### The Stone Age
I started writing $\LaTeX$ documents since the first semester of my undergraduate program. As a $\LaTeX$ novice, I first installed the default [MacTeX](https://tug.org/mactex/) 2018 distribution and finished all my lab reports using the [TeXShop](https://pages.uoregon.edu/koch/texshop/obtaining.html) software that comes with MacTeX.

I have to say, the journey of learning all syntax from scratch was fascinating (for those who are interested in typesetting real $\LaTeX$ documents, [LaTeX-Tutorial](https://latex-tutorial.com)  has some really good examples). I still remember the days when I was formatting tables, placing the captions, drawing optical diagrams and electrical circuits, etc. all by typing lines of codes. They look clean, neat and beautiful, which forced me to keep on producing high-quality documents purely to satisfy my eyes.
![A Circuit Drawn by CircuiTikZ](/images/ISP_PD_diagram.png)
```latex
\begin{circuitikz}
\draw (0,0) node[op amp] (opamp) {}
  (opamp.-) to [R,l_=$R_1$,*-] ($(opamp.-)-(2,0)$) to ($(opamp.-)-(2,0.65)$) node[ground] {}
  (opamp.out) -- ($(opamp.out)+(0,1.7)$) to[leD*] ($(opamp.-)+(0,1.2)$) -| (opamp.-)
  (opamp.out) to[short,*-] ($(opamp.out)+(-0.1,0)$)
  (opamp.+) to[short,-o] ($(opamp.+)+(-0.5,0)$) node [left] {$v_\text{in}$} node [ocirc] {} 
  ;
\end{circuitikz}
```
At that time, I wasn't doing any real hardcore math note taking. To speed up typing equations, I started to create "snippets" via the `\newcommand` preamble that interprets abbreviated input.
```latex
\newcommand{\NA}{N_{\mathrm A}}
\newcommand{\md}{{\mathrm d}}
\newcommand{\imd}{{\,\mathrm d}}
\newcommand{\me}{{\mathrm e}}
\newcommand{\mi}{{\mathrm i}}
\newcommand{\eps}{\varepsilon}
\renewcommand{\phi}{\varphi}
\newcommand{\const}{{\mathrm{const}}}
\newcommand{\rmM}{{\mathrm M}}
\newcommand{\FM}{{F_{\mathrm M}}}
\newcommand{\fM}{{f_{\mathrm M}}}
\newcommand{\vect}[1]{\boldsymbol{#1}}
\newcommand{\kB}{{k_\mathrm{B}}}
\newcommand{\kBT}{{k_\mathrm{B}T}}
```
This looks awkward from a modern point of view, but that really was how I tried to avoid typing too many characters. I wasn't aware of the caveats until a year after.
### Polishing Cold Weapons
As COVID hit Beijing early 2020, I had my first remote semester in my life. What made the quarantine life even worse was that I took both Quantum Mechanics and Intro to Mathematical Physics (solving some basic partial differential equations). With the necessity of taking and sharing note, I suddenly realized that my replacement in preamble won't render correctly if somebody else pasted my version of equations to their own documents!

I then convinced myself that for general purposes, the $\TeX$ equation itself shouldn't be altered via custom abbreviations. Instead, there should be some way that can automatically expand the characters. I then came over the [article](https://castel.dev/post/lecture-notes-1/) from [Gilles Castel's Blog](https://castel.dev), which reshaped my mind totally. Whatever learning curve would be, the speed that I could eventually achieve looked promising, so I dived in.

I became intermediately experienced in Vim, and I learned touch typing. I immersed myself into note taking everyday, and built up a lot of notes. The craziest thing during that semester was, I typed my Quantum Mechanics midterm by hand! It was so smooth to type any equation like this:
$$
\lim_{\varepsilon \to 0^{+}} \int_{-\varepsilon}^{\varepsilon}\psi\rq\rq\left(x\right)\,\mathrm{d}x=-\frac{2mV_0}{\hbar^2}\lim_{\varepsilon \to 0^{+}} \int_{-\varepsilon}^{\varepsilon} \psi\left(x\right)\delta\left(x\right)\\,\mathrm{d}x,
$$
and this:
$$
\begin{align*} u(x,t) &= \frac{Aa}{ES\omega} \frac{\sin \frac{\omega}{a}x}{\cos \frac{\omega}{a}l}\sin \omega t + \frac{Aa}{ESl\omega \cos \frac{\omega}{a}l}\left[ \frac{(-)^{m}a}{2\omega}\cos \frac{\omega}{a}l - l \right] \sin \frac{\omega}{a}x\sin \omega t \\\\
&+ \frac{4A\omega}{\pi ESa}\sum_{n=0,n\neq m} \frac{(-)^{n}}{2n+1} \frac{1}{\left( \frac{\omega}{a} \right)^{2}-\left( \frac{2n+1}{2l}\pi \right)^{2}}\sin \frac{2n+1}{2l}\pi x\sin \frac{2n+1}{2l}a\pi t \\\\
&= \frac{(-)^{m}Aa^{2}}{2ESl\omega^{2}}\sin \frac{\omega}{a}x\sin \omega t. \end{align*}
$$
I also used [Mathpix Snips](https://mathpix.com/snip) (it was free at that time) for copying some nicely formatted equation images. 

However, despite the fact that I finished my undergraduate thesis using the combination of [VimTeX](https://github.com/lervag/vimtex) and [UltiSnips](https://github.com/SirVer/ultisnips), I still found an annoying point: $\LaTeX$ requires compiling the document again for any original file change. Although VimTeX makes it a lot easier and faster, the compilation still needs time. This time issue underlies the problem of correcting any error during typing. What might be counter-intuitive is, as I become more experienced, I start to feel more frustrated when I typed something wrong and/or mis-trigger some snippet. Looking reminiscently, it's reasonable because an experienced typer tends to type more characters before recompile the document to see the effect. The separation of `.tex` file and the rendered document also makes $\LaTeX$ documents less like a note, not to say having to use `\item` and `\begin{}` for a simple bullet or enumerated list.

In the meantime I also tried [Notion](https://www.notion.so). I will say it definitely has some really tempting features, such as nice UI and formatting, native cloud storage, database, etc., but after some extensive period of (free student) use, I found myself not really accustomed to the workflow management concept from which the software is designed. Vim and $\LaTeX$ snippet support are also in complete in Notion, the former being really useful to focus our hands on keyboard. 
### Embracing Pistol
Here comes the problem. Is there any software that can handle:
1. Markdown syntax and formatting
2. Vim and rich editor navigation support
3. $\TeX$ real-time rendering
4. Text expansion triggers that resembles UltiSnips
5. File based, making it easy to automate

I didn't believe this editor exists, and was planning to make my own. 

Then came [Obsidian](https://obsidian.md) and [Obsidian LaTeX Suite](https://github.com/artisticat1/obsidian-latex-suite#cheatsheet). 

This is, by far, the ultimate and perfect setup of mathematical note taking. Literally the best, no competitors.

From stone to metal, now we have firearms.
## The Actual Setup

### Installation and Cloud Sync
The first step is, obviously, download the software from the [Obsidian](https://obsidian.md) website. After the installation, you will have to **create a new vault**. Obsidian can function perfectly without internet connection, but it is always better if you have same data on multiple devices. Obsidian is totally free for personal use, and it provides a cloud syncing service that cost $8-10 a month. However, this cloud service is **totally optional** and you will not lose any feature without that. You just need some configurations before creating the vault. Most of the time (if you are not an iOS user), use any cloud services from Microsoft, Google, Amazon, etc. you like, the vault created under the cloud directory will behave just as like a cloud folder. 

For iOS users, things get just a little bit more complicated:
* iCloud: If you want system-level sync integration, install the iOS Obsidian before you do anything on your personal computer. Under iOS Obsidian, create a new vault. Then select to open that vault folder in desktop Obsidian.
![Creating a Vault under iOS](/images/create_ios_vault_shade_pad.png|360)
	* If you are using iOS and/or iPadOS device with any other desktop operating system, such as iOS + iPadOS + Linux or iOS + Windows, you might need to install iCloud on either Windows or Linux PC. Mac users can just open the folder after creating it under iOS.
* OneDrive, DropBox, AWS etc.: there is a [Remotely Save](https://github.com/remotely-save/remotely-save) plugin for Obsidian, which have not been tested by me.
* Other methods are being discussed at this [Reddit Post](https://www.reddit.com/r/ObsidianMD/comments/y4o76p/struggling_to_get_obsidian_ios_to_point_to_vault/), or you can just pay for the syncing service.
### Plugins and Settings
To install LaTeX Suite, follow the [steps](https://help.obsidian.md/Extending+Obsidian/Community+plugins) below:
1. Open **Settings** in Obsidian.
2. Select **Turn on community plugins** (make sure restricted mode is off).
3. Select **Browse** to explore available community plugins.
4. Search for **LaTeX Suite**, and **Install**.
![Installing LaTeX Suite](/images/community_plugin.png)
5. There is also a plugin called [Extended MathJax](https://github.com/wei2912/obsidian-latex), which allows the user to alter preambles. As for now, I created the file `preamble.sty` and included `\newcommand{\bm}{\boldsymbol}` in the file to let `\bm` command render correctly if someone is transferring from [KaTeX](https://katex.org).

Once you installed LaTeX Suite, you can configure the snippets within the plugin. The plugin comes with a set of [default snippets](https://github.com/artisticat1/obsidian-latex-suite/blob/main/src/default_snippets.ts), which is loosely based on [Gilles Castell's](https://castel.dev/post/lecture-notes-1/#other-snippets). However, it is encouraged that you modify them on your own. To do so, open Settings, and scroll down until you find the settings of LaTeX Suite. You can see the snippets as a collection of typescript text.

The [syntax](https://github.com/artisticat1/obsidian-latex-suite#snippets) of the snippets are pretty straightforward, but it is always better to check on it before making any modifications. You can also get a sense of how it works by taking look at the GIFs in the plugin `README.md`.

The following are my version 1.0 modification of the default snippets. 
```typescript
[    
    // Math mode
    {trigger: "mk", replacement: "$$0$", options: "tA"},
    {trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},
    {trigger: "beg", replacement: "\\begin{$0}\n$1\n\\end{$0}", options: "mA"},


    // Dashes
    // {trigger: "--", replacement: "–", options: "tA"},
    // {trigger: "–-", replacement: "—", options: "tA"},
    // {trigger: "—-", replacement: "---", options: "tA"},


    // Greek letters
    // {trigger: "@a", replacement: "\\alpha", options: "mA"},
    // {trigger: "@A", replacement: "\\alpha", options: "mA"},
    // {trigger: "@b", replacement: "\\beta", options: "mA"},
    // {trigger: "@B", replacement: "\\beta", options: "mA"},
    // {trigger: "@c", replacement: "\\chi", options: "mA"},
    // {trigger: "@C", replacement: "\\chi", options: "mA"},
    // {trigger: "@g", replacement: "\\gamma", options: "mA"},
    // {trigger: "@G", replacement: "\\Gamma", options: "mA"},
    // {trigger: "@d", replacement: "\\delta", options: "mA"},
    // {trigger: "@D", replacement: "\\Delta", options: "mA"},
    // {trigger: "@e", replacement: "\\epsilon", options: "mA"},
    // {trigger: "@E", replacement: "\\epsilon", options: "mA"},
    // {trigger: ":e", replacement: "\\varepsilon", options: "mA"},
    // {trigger: ":E", replacement: "\\varepsilon", options: "mA"},
    // {trigger: "@z", replacement: "\\zeta", options: "mA"},
    // {trigger: "@Z", replacement: "\\zeta", options: "mA"},
    // {trigger: "@t", replacement: "\\theta", options: "mA"},
    // {trigger: "@T", replacement: "\\Theta", options: "mA"},
    // {trigger: "@k", replacement: "\\kappa", options: "mA"},
    // {trigger: "@K", replacement: "\\kappa", options: "mA"},
    // {trigger: "@l", replacement: "\\lambda", options: "mA"},
    // {trigger: "@L", replacement: "\\Lambda", options: "mA"},
    // {trigger: "@m", replacement: "\\mu", options: "mA"},
    // {trigger: "@M", replacement: "\\mu", options: "mA"},
    // {trigger: "@r", replacement: "\\rho", options: "mA"},
    // {trigger: "@R", replacement: "\\rho", options: "mA"},
    // {trigger: "@s", replacement: "\\sigma", options: "mA"},
    // {trigger: "@S", replacement: "\\Sigma", options: "mA"},
    // {trigger: "ome", replacement: "\\omega", options: "mA"},
    // {trigger: "@o", replacement: "\\omega", options: "mA"},
    // {trigger: "@O", replacement: "\\Omega", options: "mA"},
    {trigger: "([^\\\\])(${GREEK}|${SYMBOL})", replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before greek letters and symbols"},


    // Insert space after greek letters and symbols, etc
    {trigger: "\\\\(${GREEK}|${SYMBOL}|${SHORT_SYMBOL})([A-Za-z])", replacement: "\\[[0]] [[1]]", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) sr", replacement: "\\[[0]]^{2}", options: "rmA"},
    // {trigger: "\\\\(${GREEK}|${SYMBOL}) cb", replacement: "\\[[0]]^{3}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) td", replacement: "\\[[0]]^{$0}$1", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) hat", replacement: "\\hat{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) dot", replacement: "\\dot{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) bar", replacement: "\\bar{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) vec", replacement: "\\vec{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) tilde", replacement: "\\tilde{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}|${SYMBOL}) und", replacement: "\\underline{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK}),\\.", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},
    {trigger: "\\\\(${GREEK})\\.,", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},


    // Operations
    {trigger: "te", replacement: "\\text{$0}", options: "m"},
    {trigger: "text", replacement: "\\text{$0}", options: "mA"},
    {trigger: "bf", replacement: "\\mathbf{$0}", options: "mA"},
    {trigger: "sr", replacement: "^{2}", options: "mA"},
    // {trigger: "cb", replacement: "^{3}", options: "mA"},
    {trigger: "td", replacement: "^{$0}$1", options: "mA"},
    {trigger: "_", replacement: "_{$0}$1", options: "mA"},
    {trigger: "sts", replacement: "_\\text{$0}", options: "rmA"},
    {trigger: "sq", replacement: "\\sqrt{ $0 }$1", options: "mA"},
    {trigger: "//", replacement: "\\frac{$0}{$1}$2", options: "mA"},
    {trigger: "ee", replacement: "\\mathrm{e}^{ $0 }$1", options: "m"},
    {trigger: "rm", replacement: "\\mathrm{$0}$1", options: "mA"},
    {trigger: "conj", replacement: "^{*}", options: "mA"},
    {trigger: "trace", replacement: "\\mathrm{Tr}", options: "mA"},
    {trigger: "trans", replacement: "^\\mathrm{T}", options: "mA"},
    {trigger: "det", replacement: "\\det", options: "mA"},
    {trigger: "Re", replacement: "\\mathrm{Re}", options: "mA"},
    {trigger: "Im", replacement: "\\mathrm{Im}", options: "mA"},

    {trigger: "([a-zA-Z]),\\.", replacement: "\\boldsymbol{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])\\.,", replacement: "\\boldsymbol{[[0]]}", options: "rmA"},
    {trigger: "([A-Za-z])(\\d)", replacement: "[[0]]_{[[1]]}", options: "rmA", description: "Auto letter subscript", priority: -1},
    {trigger: "([A-Za-z])_(\\d\\d)", replacement: "[[0]]_{[[1]]}", options: "rmA"},
    {trigger: "\\hat{([A-Za-z])}(\\d)", replacement: "hat{[[0]]}_{[[1]]}", options: "rmA"},
    {trigger: "\\\\boldsymbol{([A-Za-z])}(\\d)", replacement: "\\boldsymbol{[[0]]}_{[[1]]}", options: "rmA"},
    {trigger: "\\\\vec{([A-Za-z])}(\\d)", replacement: "\\vec{[[0]]}_{[[1]]}", options: "rmA"},
    {trigger: "([a-zA-Z])bar", replacement: "\\bar{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])hat", replacement: "\\hat{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])ddot", replacement: "\\ddot{[[0]]}", options: "rmA", priority: 3},
    {trigger: "([a-zA-Z])dot", replacement: "\\dot{[[0]]}", options: "rmA", priority: 1},
    {trigger: "([a-zA-Z])vec", replacement: "\\vec{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])tilde", replacement: "\\tilde{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])und", replacement: "\\underline{[[0]]}", options: "rmA"},
    {trigger: "bar", replacement: "\\bar{$0}$1", options: "mA"},
    {trigger: "hat", replacement: "\\hat{$0}$1", options: "mA"},
    {trigger: "dot", replacement: "\\dot{$0}$1", options: "mA"},
    {trigger: "ddot", replacement: "\\ddot{$0}$1", options: "mA", priority: 2},
    {trigger: "vec", replacement: "\\vec{$0}$1", options: "mA"},
    {trigger: "tilde", replacement: "\\tilde{$0}$1", options: "mA"},
    {trigger: "und", replacement: "\\underline{$0}$1", options: "mA"},
    {trigger: "over", replacement: "\\overline{$0}$1", options: "m"},

    {trigger: "([^\\\\])(arcsin|arccos|arctan|arccot|arccsc|arcsec|sin|cos|tan|cot|csc)", replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "\\\\(arcsin|arccos|arctan|arccot|arccsc|arcsec|sin|cos|tan|cot|csc)([A-Za-gi-z])", replacement: "\\[[0]] [[1]]", options: "rmA"}, // Insert space after trig funcs. Skips letter "h" to allow sinh, cosh, etc.
    {trigger: "\\\\(arcsinh|arccosh|arctanh|arccoth|arcsch|arcsech|sinh|cosh|tanh|coth|csch)([A-Za-z])", replacement: "\\[[0]] [[1]]", options: "rmA"}, // Insert space after trig funcs
    {trigger: "\\\\(neq|geq|leq|gg|ll|sim)([0-9]+)", replacement: "\\[[0]] [[1]]", options: "rmA"}, // Insert space after inequality symbols


    // Visual operations
    {trigger: "U", replacement: "\\underbrace{ ${VISUAL} }_{ $0 }", options: "mA"},
    {trigger: "B", replacement: "\\underset{ $0 }{ ${VISUAL} }", options: "mA"},
    {trigger: "C", replacement: "\\cancel{ ${VISUAL} }", options: "mA"},
    {trigger: "K", replacement: "\\cancelto{ $0 }{ ${VISUAL} }", options: "mA"},
    {trigger: "S", replacement: "\\sqrt{ ${VISUAL} }", options: "mA"},



    // Symbols
    {trigger: "ooo", replacement: "\\infty", options: "mA"},
    {trigger: "sum", replacement: "\\sum", options: "mA"},
    {trigger: "prod", replacement: "\\prod", options: "mA"},
    {trigger: "lim", replacement: "\\lim_{ ${0:n} \\to ${1:\\infty} } $2", options: "mA"},
    {trigger: "([^\\\\])pm", replacement: "[[0]]\\pm", options: "rm"},
    {trigger: "([^\\\\])mp", replacement: "[[0]]\\mp", options: "rm"},
    {trigger: "+-", replacement: "\\pm", options: "mA"},
    {trigger: "-+", replacement: "\\mp", options: "mA"},
    {trigger: "...", replacement: "\\dots", options: "mA"},
    {trigger: "<->", replacement: "\\leftrightarrow ", options: "mA"},
    {trigger: "->", replacement: "\\to", options: "mA"},
    {trigger: "!>", replacement: "\\mapsto", options: "mA"},
    {trigger: "invs", replacement: "^{-1}", options: "mA"},
    {trigger: "\\\\\\", replacement: "\\setminus", options: "mA"},
    {trigger: "||", replacement: "\\mid", options: "mA"},
    {trigger: "and", replacement: "\\cap", options: "mA"},
    {trigger: "orr", replacement: "\\cup", options: "mA"},
    {trigger: "inn", replacement: "\\in", options: "mA"},
    {trigger: "\\subset eq", replacement: "\\subseteq", options: "mA"},
    {trigger: "set", replacement: "\\{ $0 \\}$1", options: "mA"},
    {trigger: "=>", replacement: "\\implies", options: "mA"},
    {trigger: "=<", replacement: "\\impliedby", options: "mA"},
    {trigger: "iff", replacement: "\\iff", options: "mA"},
    {trigger: "e\\xi sts", replacement: "\\exists", options: "mA", priority: 1},
    {trigger: "===", replacement: "\\equiv", options: "mA"},
    {trigger: "Sq", replacement: "\\square", options: "mA"},
    {trigger: "!=", replacement: "\\neq", options: "mA"},
    {trigger: ">=", replacement: "\\geq", options: "mA"},
    {trigger: "<=", replacement: "\\leq", options: "mA"},
    {trigger: ">>", replacement: "\\gg", options: "mA"},
    {trigger: "<<", replacement: "\\ll", options: "mA"},
    {trigger: "~~", replacement: "\\sim", options: "mA"},
    {trigger: "\\sim ~", replacement: "\\approx", options: "mA"},
    {trigger: "prop", replacement: "\\propto", options: "mA"},
    {trigger: "nabl", replacement: "\\nabla", options: "mA"},
    // {trigger: "del", replacement: "\\nabla", options: "mA"},
    {trigger: "xx", replacement: "\\times", options: "mA"},
    {trigger: "**", replacement: "\\cdot", options: "mA"},
    {trigger: "\\cdot*", replacement: "\\cdots", options: "mA"},
    {trigger: "para", replacement: "\\parallel", options: "mA"},


    {trigger: "xnn", replacement: "x_{n}", options: "mA"},
    {trigger: "xii", replacement: "x_{i}", options: "mA"},
    {trigger: "xjj", replacement: "x_{j}", options: "mA"},
    {trigger: "xp1", replacement: "x_{n+1}", options: "mA"},
    {trigger: "ynn", replacement: "y_{n}", options: "mA"},
    {trigger: "yii", replacement: "y_{i}", options: "mA"},
    {trigger: "yjj", replacement: "y_{j}", options: "mA"},


    {trigger: "mcal", replacement: "\\mathcal{$0}$1", options: "mA"},
    {trigger: "mbb", replacement: "\\mathbb{$0}$1", options: "mA"},
    {trigger: "ell", replacement: "\\ell", options: "mA"},
    {trigger: "lll", replacement: "\\ell", options: "mA"},
    {trigger: "LL", replacement: "\\mathcal{L}", options: "mA"},
    {trigger: "HH", replacement: "\\mathcal{H}", options: "mA"},
    {trigger: "CC", replacement: "\\mathbb{C}", options: "mA"},
    {trigger: "RR", replacement: "\\mathbb{R}", options: "mA"},
    {trigger: "ZZ", replacement: "\\mathbb{Z}", options: "mA"},
    {trigger: "NN", replacement: "\\mathbb{N}", options: "mA"},
    {trigger: "II", replacement: "\\mathbb{1}", options: "mA"},
    {trigger: "\\mathbb{1}I", replacement: "\\hat{\\mathbb{1}}", options: "mA"},
    {trigger: "AA", replacement: "\\mathcal{A}", options: "mA"},
    {trigger: "BB", replacement: "\\mathbf{B}", options: "mA"},
    {trigger: "EE", replacement: "\\mathbf{E}", options: "mA"},



    // Unit vectors
    // {trigger: ":i", replacement: "\\mathbf{i}", options: "mA"},
    // {trigger: ":j", replacement: "\\mathbf{j}", options: "mA"},
    // {trigger: ":k", replacement: "\\mathbf{k}", options: "mA"},
    // {trigger: ":x", replacement: "\\hat{\\mathbf{x}}", options: "mA"},
    // {trigger: ":y", replacement: "\\hat{\\mathbf{y}}", options: "mA"},
    // {trigger: ":z", replacement: "\\hat{\\mathbf{z}}", options: "mA"},



    // Derivatives
    {trigger: "pp", replacement: "\\frac{ \\partial $0 }{ \\partial $1 } $2", options: "m"},
    {trigger: "dd", replacement: "\\frac{ \\mathrm{d} $0 }{ \\mathrm{d} $1 } $2", options: "m"},
    // {trigger: "par", replacement: "\\frac{ \\partial ${0:y} }{ \\partial ${1:x} } $2", options: "m"},
    // {trigger: "pa2", replacement: "\\frac{ \\partial^{2} ${0:y} }{ \\partial ${1:x}^{2} } $2", options: "mA"},
    // {trigger: "pa3", replacement: "\\frac{ \\partial^{3} ${0:y} }{ \\partial ${1:x}^{3} } $2", options: "mA"},
    // {trigger: "pa([A-Za-z])([A-Za-z])", replacement: "\\frac{ \\partial [[0]] }{ \\partial [[1]] } ", options: "rm"},
    // {trigger: "pa([A-Za-z])([A-Za-z])([A-Za-z])", replacement: "\\frac{ \\partial^{2} [[0]] }{ \\partial [[1]] \\partial [[2]] } ", options: "rm"},
    // {trigger: "pa([A-Za-z])([A-Za-z])2", replacement: "\\frac{ \\partial^{2} [[0]] }{ \\partial [[1]]^{2} } ", options: "rmA"},
    // {trigger: "de([A-Za-z])([A-Za-z])", replacement: "\\frac{ d[[0]] }{ d[[1]] } ", options: "rm"},
    // {trigger: "de([A-Za-z])([A-Za-z])2", replacement: "\\frac{ d^{2}[[0]] }{ d[[1]]^{2} } ", options: "rmA"},
    // {trigger: "ddt", replacement: "\\frac{\\mathrm{d}}{\\mathrm{d}t} ", options: "mA"},



    // Integrals
    {trigger: "oinf", replacement: "\\int_{0}^{\\infty} $0 \\, \\mathrm{d}${1:x} $2", options: "mA"},
    {trigger: "infi", replacement: "\\int_{-\\infty}^{\\infty} $0 \\, \\mathrm{d}${1:x} $2", options: "mA"},
    {trigger: "dint", replacement: "\\int_{${0:0}}^{${1:\\infty}} $2 \\, \\mathrm{d}${3:x} $4", options: "mA"},
    {trigger: "oint", replacement: "\\oint", options: "mA"},
    {trigger: "iiint", replacement: "\\iiint", options: "mA"},
    {trigger: "iint", replacement: "\\iint", options: "mA"},
    {trigger: "int", replacement: "\\int $0 \\, \\mathrm{d}${1:x} $2", options: "mA"},



    // Physics
    // {trigger: "kbt", replacement: "k_{B}T", options: "mA"},
    {trigger: "kB", replacement: "k_{\\mathrm{B}}", options: "mA"},


    // Quantum mechanics
    {trigger: "hba", replacement: "\\hbar", options: "mA"},
    {trigger: "dag", replacement: "^{\\dagger}", options: "mA"},
    {trigger: "o+", replacement: "\\oplus ", options: "mA"},
    {trigger: "ox", replacement: "\\otimes ", options: "mA"},
    {trigger: "ot\\mathrm{Im}es", replacement: "\\otimes ", options: "mA"}, // Handle conflict with "im" snippet
    {trigger: "bra", replacement: "\\bra{$0} $1", options: "mA"},
    {trigger: "ket", replacement: "\\ket{$0} $1", options: "mA"},
    {trigger: "brk", replacement: "\\braket{ $0 | $1 } $2", options: "mA"},
    {trigger: "\\\\bra{([^|]+)\\|", replacement: "\\braket{ [[0]] | $0 ", options: "rmA", description: "Convert bra into braket"},
    {trigger: "\\\\bra{(.+)}([^ ]+)>", replacement: "\\braket{ [[0]] | $0 ", options: "rmA", description: "Convert bra into braket (alternate)"},
    {trigger: "outp", replacement: "\\ket{${0:\\psi}} \\bra{${0:\\psi}} $1", options: "mA"},



    // Chemistry
    {trigger: "pu", replacement: "\\pu{ $0 }", options: "mA"},
    {trigger: "msun", replacement: "M_{\\odot}", options: "mA"},
    {trigger: "solm", replacement: "M_{\\odot}", options: "mA"},
    {trigger: "ce", replacement: "\\ce{ $0 }", options: "mA"},
    {trigger: "iso", replacement: "{}^{${0:4}}_{${1:2}}${2:He}", options: "mA"},
    {trigger: "hel4", replacement: "{}^{4}_{2}He ", options: "mA"},
    {trigger: "hel3", replacement: "{}^{3}_{2}He ", options: "mA"},



    // Environments
    {trigger: "pmat", replacement: "\\begin{pmatrix}\n$0\n\\end{pmatrix}", options: "mA"},
    {trigger: "bmat", replacement: "\\begin{bmatrix}\n$0\n\\end{bmatrix}", options: "mA"},
    {trigger: "Bmat", replacement: "\\begin{Bmatrix}\n$0\n\\end{Bmatrix}", options: "mA"},
    {trigger: "vmat", replacement: "\\begin{vmatrix}\n$0\n\\end{vmatrix}", options: "mA"},
    {trigger: "Vmat", replacement: "\\begin{Vmatrix}\n$0\n\\end{Vmatrix}", options: "mA"},
    {trigger: "case", replacement: "\\begin{cases}\n$0\n\\end{cases}", options: "mA"},
    {trigger: "align", replacement: "\\begin{align}\n$0\n\\end{align}", options: "mA"},
    {trigger: "array", replacement: "\\begin{array}\n$0\n\\end{array}", options: "mA"},
    {trigger: "matrix", replacement: "\\begin{matrix}\n$0\n\\end{matrix}", options: "mA"},



    // Brackets
    {trigger: "avg", replacement: "\\langle $0 \\rangle $1", options: "mA"},
    {trigger: "norm", replacement: "\\lvert $0 \\rvert $1", options: "mA", priority: 1},
    {trigger: "mod", replacement: "|$0|$1", options: "mA"},
    {trigger: "(", replacement: "(${VISUAL})", options: "mA"},
    {trigger: "[", replacement: "[${VISUAL}]", options: "mA"},
    {trigger: "{", replacement: "{${VISUAL}}", options: "mA"},
    {trigger: "(", replacement: "($0)$1", options: "mA"},
    {trigger: "{", replacement: "{$0}$1", options: "mA"},
    {trigger: "[", replacement: "[$0]$1", options: "mA"},
    {trigger: "lr(", replacement: "\\left( $0 \\right) $1", options: "mA"},
    {trigger: "lr|", replacement: "\\left| $0 \\right| $1", options: "mA"},
    {trigger: "lr{", replacement: "\\left\\{ $0 \\right\\} $1", options: "mA"},
    {trigger: "lr[", replacement: "\\left[ $0 \\right] $1", options: "mA"},
    {trigger: "lra", replacement: "\\left< $0 \\right> $1", options: "mA"},



    // Misc
    {trigger: "taylor", replacement: "${0:f}(${1:x} + ${2:h}) = ${0:f}(${1:x}) + ${0:f}'(${1:x})${2:h} + ${0:f}''(${1:x}) \\frac{${2:h}^{2}}{2!} + \\dots$3", options: "mA"},
]
```
### Publish
The file-based logic of Obsidian makes it really easy to implement an automatic publishing workflow, and it has a great synergy when being used along with static blog generator such as [Hugo](https://gohugo.io). I will show you how to automatically or semi-automatically publish your notes onto the web.