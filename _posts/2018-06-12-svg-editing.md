---
title:  "用文档表示的SVG图像"
modified: 2018-06-12T16:03:49-04:00
categories: 
  - 网页设计
tags:
  - svg
---

{% include base_path %}

{% include toc title="Getting Started" %}

SVG是使用XML（eXtensible Markup Language， 可拓展标记语言）来进行描述的，所以不仅机器可以阅读和理解SVG图像，我们也可以。

![星星SVG图]({{ site.url }}{{ site.baseurl }}/images/Star.svg)  

## SVG的根元素  
  
SVG的根元素有width、height和viewbox属性。
   
    <svg width="198px" height="188px" viewBox="0 0 198 188"
	
这三个属性在SVG展示的时候都起到了十分重要的作用。
  
宽度和高度属性对于创造一个视口十分有用。透过这个定义的视口，我们可以看到内部定义的SVG形状。和普通的Web页面一样，SVG的内容可能会比视口大，但是这不意味着多余的部分 就不存在，只是我们看不到而已。  

另一方面，视框（viewbox）则定义了SVG中所有形状都需要遵循的坐标系。 

你可以把视框值0 0 198 198视为对矩形左上角和右下角的描述。前两个值被称为min-x 和min-y，用于描述左上角的位置。而接下来的两个值被称作宽度和高度，可以描述右下角的位置。 

因此viewbox属性可以让你缩放图片。例如，你可以这么设置viewbox属性： 
    <svg width="198px" height="188px" viewBox="0 0 99 94"   

那么其中的形状为了填满SVG的宽度和高度，就会被放大。   

## SVG的命名空间  

SVG会有一个由生成它的图形编辑程序定义的命名空间（xmlns是XML命名空间的缩写）。 

    xmlns:sketch="http://www.bohemiancoding.com/sketch/ns"   

这些命名空间往往只是在生成SVG的程序中使用，所以在Web页面上展示SVG的时候它们并不是必需的。因此在优化流程中，为了减小SVG的大小，通常会把它们去掉。 

##  SVG的标题和描述标签

title和desc标签提高了SVG文档的可读性。   
    
	<title>Star 1</title>   
    <desc>Created with Sketch.</desc> 
	
这些标签可以用来在图像不可见的情况下描述图像的内容。然而，当SVG图片被应用为背景 图片的时候，可以去除这些标签来减小文件大小。  

## defs标签  

    <defs></defs>  

这是一个十分重要的元素，它是用于储存所有可以复用 的元素定义的地方，如梯度、符号、路径等。  

## 元素g  

g元素能把其他元素捆绑在一起。例如，你要画一辆车的SVG，你会把用来构成车轮的形状 用g标签集合起来。 
  
    <g id="Page-1" stroke="none" stroke-width="1" fill="none" fillrule=" evenodd" sketch:type="MSPage"> 
	
在g标签中我们可以看到先前的命名空间。这会有助于图形编辑软件再次打开这个图像，但 是它对于这个图片在其他地方展示并没有影响。  

## SVG形状元素  

下例节点是一个多边形（polygon）。 

    <polygon id="Star-1" stroke="#979797" stroke-width="3" fill="#F8E81C" sketch:type="MSShapeGroup" points="99 154 40.2214748 184.901699 51.4471742 119.45085 3.89434837 73.0983006 69.6107374 63.5491503 99 4 128.389263 63.5491503 194.105652 73.0983006 146.552826 119.45085 157.778525 184.901699 "></polygon>  

SVG拥有一系列可用的现成形状（path、rect、circle、ellipse、line、polyline、 polygon）。   

## SVG的路径  

SVG路径和其他SVG形状有所区别，因为它们是由任意数量的连接点组成的（允许你自由创造你想要的形状）。  
这是SVG文件的价值所在。SVG的代码可以手写，也可以利用图像工具来生成。 

