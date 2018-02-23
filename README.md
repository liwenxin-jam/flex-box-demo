---
title:  flex布局使用小结
author: 黎文欣
tags: 前端
categories:
  - CSS
blogexcerpt: 文字摘要
date: 2018-01-14 21:32:51
thumbnail:
---
布局的传统解决方案，基于盒状模型，依赖display属性+position属性+float属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。Flex是Flexible-Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。任何一个容器都可以指定为Flex布局，行内元素也可以使用Flex布局，不管是什么布局，Flex往往都可以几行命令搞定，Flex布局将成为未来布局的首选方案。

- 采用Flex布局的元素，称为Flex容器（flex-container），简称"容器"。它的所有子元素自动成为容器成员，称为Flex项目（flex-item），简称"项目"。设为flex的容器可以设置以下六种属性flex-direction、flex-wrap、flex-flow、justify-content、align-items、align-content。注意，Webkit内核的浏览器，必须加上-webkit前缀，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。

1、flex-direction属性，决定主轴的方向（即项目的排列方向）
flex-direction: row | row-reverse | column | column-reverse;
- row（默认值）：主轴为水平方向，起点在左端。
- row-reverse：主轴为水平方向，起点在右端。
- column：主轴为垂直方向，起点在上沿。
- column-reverse：主轴为垂直方向，起点在下沿。

2、flex-wrap属性，默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
flex-wrap: nowrap | wrap | wrap-reverse;
- nowrap（默认）：不换行。
- wrap：换行，第一行在上方。
- wrap-reverse：换行，第一行在下方。

3、flex-flow属性，flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。
flex-flow: <flex-direction> || <flex-wrap>;

4、justify-content属性，定义了项目在主轴上的对齐方式。
justify-content: flex-start | flex-end | center | space-between | space-around;
- flex-start（默认值）：左对齐
- flex-end：右对齐
- center： 居中
- space-between：两端对齐，项目之间的间隔都相等。
- space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

5、align-items属性，定义项目在交叉轴上如何对齐。
align-items: flex-start | flex-end | center | baseline | stretch;
- flex-start：交叉轴的起点对齐。
- flex-end：交叉轴的终点对齐。
- center：交叉轴的中点对齐。
- baseline: 项目的第一行文字的基线对齐。
- stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

6、align-content属性，定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
align-content: flex-start | flex-end | center | space-between | space-around | stretch;
- flex-start：与交叉轴的起点对齐。
- flex-end：与交叉轴的终点对齐。
- center：与交叉轴的中点对齐。
- space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
- space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
- stretch（默认值）：轴线占满整个交叉轴。

- 设为flex的容器，它的所有子元素自动成为容器成员，称为Flex项目（flex-item），简称"项目"。项目也是可以设置以下六种属性order、flex-grow、flex-shrink、flex-basis、flex、align-self。

1、order属性，定义项目的排列顺序。数值越小，排列越靠前，默认为0。
order: <integer>;

2、flex-grow属性，定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
flex-grow: <number>; 

3、flex-shrink属性，定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。注意，负值对该属性无效。
flex-shrink: <number>;

4、flex-basis属性，定义了在分配多余空间之前，项目占据的主轴空间（main-size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。
flex-basis: <length> | auto; 

5、flex属性，flex属性是flex-grow,flex-shrink和flex-basis的简写，默认值为0 1 auto，其中后两个属性可选。该属性有两个快捷值：auto(1 1 auto)和none(0 0 auto)。建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。
flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]

6、align-self属性，允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。该属性可以取6个值，除了auto，其他都与align-items属性完全一致。
align-self: auto | flex-start | flex-end | center | baseline | stretch;

- 以下示例是参照阮一峰老师教程的实例，我只是做了补充，把flex-basis也补上。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>flex-box-demo</title>
    <style type="text/css">
    .first-face {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .second-face {
        display: flex;
        justify-content: space-between;
    }
    .second-face .pip:nth-of-type(2) {
        align-self: flex-end;
    }
    .third-face {
        display: flex;
        justify-content: space-between;
    }
    .third-face .pip:nth-of-type(2) {
        align-self: center;
    }
    .third-face .pip:nth-of-type(3) {
        align-self: flex-end;
    }
    .fourth-face,
    .sixth-face {
        display: flex;
        justify-content: space-between;
    }
    .fourth-face .column,
    .sixth-face .column {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .fifth-face {
        display: flex;
        justify-content: space-between;
    }
    .fifth-face .column {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .fifth-face .column:nth-of-type(2) {
        justify-content: center;
    }
    /* OTHER STYLES */
    * {
        box-sizing: border-box;
    }
    html,
    body {
        height: 100%;
    }
    body {
        display: flex;
        align-items: center;
        justify-content: center;
        vertical-align: center;
        flex-wrap: wrap;
        align-content: center;
        font-family: 'Open Sans', sans-serif;

        background: linear-gradient(top, #222, #333);
    }
    [class$="face"] {
        margin: 16px;
        padding: 4px;
        background-color: #e7e7e7;
        width: 104px;
        height: 104px;
        object-fit: contain;
        box-shadow: inset 0 5px white,
        inset 0 -5px #bbb,
        inset 5px 0 #d7d7d7,
        inset -5px 0 #d7d7d7;
        border-radius: 10%;
    }
    .pip {
        display: block;
        width: 24px;
        height: 24px;
        border-radius: 50%;
        margin: 4px;
        background-color: #333;
        box-shadow: inset 0 3px #111, inset 0 -3px #555;
    }
    /*补充flex-basis写法*/
    #fourth-basic{
        flex-wrap: wrap;
        align-content: space-between;
    }
    #fourth-basic .column{
        flex-direction: row;   /*覆写原来的样式column*/
        flex-basis: 100%;
    }
    </style>
</head>

<body>
    <div class="first-face">
        <span class="pip"></span>
    </div>
    <div class="second-face">
        <span class="pip"></span>
        <span class="pip"></span>
    </div>
    <div class="third-face">
        <span class="pip"></span>
        <span class="pip"></span>
        <span class="pip"></span>
    </div>
    <div class="fourth-face">
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
    </div>
    <div id="fourth-basic" class="fourth-face">
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
    </div>
    <div class="fifth-face">
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
        <div class="column">
            <span class="pip"></span>
        </div>
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
    </div>
    <div class="sixth-face">
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
        <div class="column">
            <span class="pip"></span>
            <span class="pip"></span>
            <span class="pip"></span>
        </div>
    </div>
</body>

</html>
```

如果需要上面栗子源码可以从本人github[flex-box-demo](https://github.com/liwenxin-jam/flex-box-demo "flex-box-demo")上下载。

- 参考文献
1、[Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
2、[Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)