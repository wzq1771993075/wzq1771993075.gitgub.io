---
layout: post
title: 2017年8月笔记
category: 笔记
comments: true

---

## CSS 伪元素 (Pseudo-elements)

:first-letter       向文本的第一个字母添加特殊样式。

    p:first-letter
    {
      color:#ff0000;
      font-size:xx-large;/*最大*/
    }

:first-line         向文本的首行添加特殊样式。

    p:first-line
    {
      color:#ff0000;
      font-variant:small-caps;/*把段落设置为小型大写字母字体*/
    }

:before             在元素之前添加内容。

    h1:before /*在元素的内容前面添加新内容*/
    {
      content:url(logo.gif);
    }

:after              在元素之后添加内容。

    h1:after
    {
      content:url(logo.gif);
    }

注意：:before和:after添加的内容是属于选中元素的，而不是选中元素的兄弟元素

## 弹性盒子（flex布局）

justify-content实例

![justify_content](https://raw.githubusercontent.com/wzq1771993075/wzq1771993075.github.io/master/assets/upload/justify_content.png)

## 伪类和伪元素

#### 伪类：
伪类选择元素基于的是当前元素处于的状态，或者说元素当前所具有的特性，而不是元素的id、class、属性等静态的标志。由于状态是动态变化的，所以一个元素达到一个特定状态时，它可能得到一个伪类的样式；当状态改变时，它又会失去这个样式。由此可以看出，它的功能和class有些类似，但它是基于文档之外的抽象，所以叫伪类。 
- :first-child 
- :link
- :visitive 
- :hover 
- :active 
- :focus 
- :lang 

#### 伪元素： 
与伪类针对特殊状态的元素不同的是，伪元素是对元素中的特定内容进行操作，它所操作的层次比伪类更深了一层，也因此它的动态性比伪类要低得多。实际上，设计伪元素的目的就是去选取诸如元素内容第一个字（母）、第一行，选取某些内容前面或后面这种普通的选择器无法完成的工作。它控制的内容实际上和元素是相同的，但是它本身只是基于元素的抽象，并不存在于文档中，所以叫伪元素。
- :first-line 
- :first-letter 
- :before 
- :after 

## input标签里 value 和 placeholder的区别

placeholder顾名思义是一个占位符。
在你的value为空的时候它才会显示出来，但是它本身并不是value，也不会被表单提交

## HTML5 input标签中的required属性

    <input type="text" name="usr_name" required="required" />
    <input type="text" name="usr_name" required="" />
    <input type="text" name="usr_name" required />

三种写法的意思一样，都表示这个输入框是必填项，而且访问required属性返回的都是true.

## HTML5 form标签中的novalidate属性

novalidate属性规定当提交表单时不对输入进行验证。
用法与required类似，novalidate 属性适用于： `<form>`，以及以下类型的`<input>` 标签：text, search, url, telephone, email, password, date pickers, range 以及 color.

## CSS3 resize属性

规定是否可由用户调整元素大小

    div         /*可以由用户调整 div 元素的大小*/
    {
      resize:both;
      overflow:auto;
    }

## CSS3 transition属性

transition 属性是一个简写属性，用于设置四个过渡属性:  
- transition-property  
- transition-duration  
- transition-timing-function  
- transition-delay

## 强制换行

word-break:break-all;