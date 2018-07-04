---
title: "使用miminal-mistakes来设置字体"
categories:
  - Jekyll
tags:
  - minimal-mistakes
  - 字体
  - serif
---

这次代码提交[ca2c487686](https://gitee.com/hanteng/minimal-mistakes/commit/ca2c487686a2b7b69bbb9edebb4908e6c1376315) 展示的是使用miminal-mistakes来设置字体。


### 网页设计常用字体

网页设计字体最基础之知识是[平面设计中的衬线字体及无衬线体](https://www.uisdc.com/30-west-typegraph-in-web-design)，英文专业术语分别是Serif及 Sans-Serif。之所以要学英文专业术语是因为在CSS代码中关於字型的设置常出现，其实这词`sans`源自法语，是英语的without`无`的意思。

衬线字体及无衬线体差异用图可示，见下图：
![英文维基百科用图-ABC](https://upload.wikimedia.org/wikipedia/commons/thumb/2/26/Serif_and_sans-serif_03.svg/314px-Serif_and_sans-serif_03.svg.png)

汉字其实也有衬线字体及无衬线体差异，见下图：
![英文维基百科用图-ABC](https://upload.wikimedia.org/wikipedia/commons/thumb/a/af/Ming_serif.svg/330px-Ming_serif.svg.png)

平面设计的惯例是，内文（body texts）用衬线字体，而标题（heading）用无衬线体。视觉原理是标题用无衬线体比较显明不花边且带有现代风格味，而内文用衬线字体比较能利用微小的衬线区别已经相对较小的字体。

在数字媒体中，通常沿用平面设计的惯例：标题无衬线，内文用衬线。但也会因情况及需要做调整。

像投影片及科学海报，若内文字多的话常沿用标题无衬线，内文用衬线的惯例，但也有内文字不多且是列表式的内容，也有只用无衬线体的情况。

### miminal-mistakes设置字体
本网页2018/07/02以前使用的是miminal-mistakes的预设字体，所以内文（body）原设置是无衬线。

若要把内文（body）改成衬线字体，要如何改？从何改起？

熟练的网站设计师会先找到paragraph元素（标签`p`）的字型设定，使用Chrome Inspector 可以从`Computed分页`回查设置paragraph元素的CSS代码（点按小三角）。

由此，我发现标签`p`的字型值是继承`body`元素的，所以改body元素即可以改动这模版的最基本字型。

miminal-mistakes字体的设置由於是相当基本的，所以是放在[/_sass/minimal-mistakes](https://gitee.com/wuxue_newmedia/minimal-mistakes/tree/master/_sass/minimal-mistakes)目录下的_base.scss之基底scss文档，明眼人可以看到下段代码，规范着body标签：

```css
body {
  margin: 0;
  padding: 0;
  color: $text-color;
  font-family: $global-font-family;
  line-height: 1.5;

  &.overflow--hidden {
    /* when primary navigation is visible, the content in the background won't scroll */
    overflow: hidden;
  }
}
```

这段scss代码和css代码很相似，就是$符号标出了scss变量，所以我推论这模板的基底字型是由`$global-font-family`设置。

那$global-font-family上哪设？

### miminal-mistakes设置scss变量

miminal-mistakes采用的是现代的scss去设置所有的CSS代码，常见的scss作法是有一个文档或一代码区块，定义了所有scss变量，方便设计师及维护进行全局改动及局部调整。

的确，miminal-mistakes的scss变量放在[/_sass/minimal-mistakes](https://gitee.com/wuxue_newmedia/minimal-mistakes/tree/master/_sass/minimal-mistakes)设置的。

在版式的区域Typography下，找到变量`$global-font-family`，原设置的是`$sans-serif`的变量值，所以改成`$serif`变量值（见代码提交[d0cc4d92d0](https://gitee.com/wuxue_newmedia/minimal-mistakes/commit/d0cc4d92d0172ce16f162b89c0beef92229496b4) 和见代码提交[d6fd5942ec](https://gitee.com/wuxue_newmedia/minimal-mistakes/commit/d6fd5942ecde013b48e295cee66ad4006aed91c2) ，如此就可以将预设的文字改成衬线字体，实践「内文用衬线」。

