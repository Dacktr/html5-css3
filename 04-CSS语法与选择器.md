# CSS语法与选择器 #

----------
## 1. CSS简介 ##

### 层叠样式表 ###
网页实际上是一个多层的结构，通过CSS可以分别为网页的每一个层来设置样式，而最终我们能看到只是网页的最上边一层

总之一句话，CSS用来设置网页中元素的样式

使用CSS来修改元素样式的方式大致可以分为3种

### 内联样式（行内样式） ###
在标签内部通过style属性来设置元素的样式

	<p style="color:red;font-size:60px;">内联样式（行内样式）</p>

问题：使用内联样式，样式只能对一个标签生效。如果希望影响到多个元素，必须在每一个元素中都复制一遍；并且当样式发生变化时，我们必须要一个一个的修改，非常的不方便。（注意：开发时绝对不要使用内联样式）

### 内部样式表 ###
将样式编写到head中的style标签里然后通过css的选择器来选中元素并为其设置各种样式可以同时为多个标签设置样式，并且修改时只需要修改一处即可。内部样式表更加方便对样式进行复用

	<style>
	p{
	    color:green; 
	    font-size:50px;
	}
	</style>
问题：我们的内部样式表只能对一个网页起作用，它里边的样式不能跨页面进行复用

### 外部样式表 ###

可以将css样式编写到一个外部的CSS文件中，然后通过link标签来引入外部的CSS文件

	<link rel="stylesheet" href="./style.css">

外部样式表需要通过link标签进行引入，意味着只要想使用这些样式的网页都可以对其进行引用使样式，可以在不同页面之间进行复用

将样式编写到外部的CSS文件中，可以使用到浏览器的缓存机制，从而加快网页的加载速度，提高用户的体验。
## 2. CSS基本语法 ##

### 注释 ###

#### css中的注释 ####

只能使用/*和*/包裹。即不管是单行注释，还是多行注释，都是以/*开头，以*/结尾

	/* css中的单行注释 */
	
	/* 
	css中的多行注释
	css中的多行注释
	css中的多行注释
	*/

我们对比下其他几种前端语言的注释

#### html中的注释 ####
只能使用<!--和-->包裹。即不管是单行注释，还是多行注释，都是以<!--开头，以-->结尾

	<!-- html中的单行注释 -->
	
	<!-- 
	html中的多行注释
	html中的多行注释
	html中的多行注释
	-->


#### JS(JavaScript)和JQuery中的注释 ####
单行注释使用//。多行注释使用/*和*/包裹，以<!--开头，以-->结尾
/* JS(JavaScript)和JQuery中的单行注释*/

	/* JS(JavaScript)和JQuery中的单行注释*/
	
	/*
	JS(JavaScript)和JQuery中的多行注释
	JS(JavaScript)和JQuery中的多行注释
	JS(JavaScript)和JQuery中的多行注释
	*/
### 基本语法 ###

选择器 声明块

#### 选择器 ####

通过选择器可以选中页面中的指定元素

● 比如p的作用就是选中页面中所有的p元素声明块

#### 声明块 ####

通过声明块来指定要为元素设置的样式

●  声明块由一个一个的声明组成，声明是一个名值对结构
 
●  一个样式名对应一个样式值，名和值之间以:连接，以;结尾

	 h1{
	    color: green;
	}
## 3. CSS选择器 ##

通配选择器（Universal selector）

● 作用：选中页面中的所有元素

● 语法：*

● 例子：*{}

	*{
	    color: red;
	}
### 元素选择器（Type selector） ###

也叫类型选择器、标签选择器

● 作用：根据标签名来选中指定的元素

● 语法：elementname{}

● 例子：p{} h1{} div{}

	p{
	    color: red; 
	}
	
	h1{
	    color: green;
	}

### 类选择器（Class selector） ###

● 作用：根据元素的class属性值选中一组元素

● 语法：.classname

● 例子：.blue{}

	.blue{
	    color: blue;
	}
	.size{
	    font-size: 20px;
	}
class是一个标签的属性，它和id类似，不同的是class

● 可以重复使用，

● 可以通过class属性来为元素分组，

● 可以同时为一个元素指定多个class属性

	<p class="blue size"> 类选择器（Class selector）</p>

### ID选择器（ID selector） ###

● 作用：根据元素的id属性值选中一个元素

● 语法：#idname{}

● 例子：#box{} #red{}

	#red{
	    color: red;
	}

属性选择器（Attribute selector）

● 作用：根据元素的属性值选中一组元素

● 语法1：[属性名] 选择含有指定属性的元素

● 语法2：[属性名=属性值] 选择含有指定属性和属性值的元素

● 语法3：[属性名^=属性值] 选择属性值以指定值开头的元素

● 语法4：[属性名$=属性值] 选择属性值以指定值结尾的元素

● 语法5：[属性名*=属性值] 选择属性值中含有某值的元素

● 例子：p[title]{} p[title=e]{} p[title^=e]{} p[title$=e]{} p[title*=e]{}

	p[title]{
	    color: orange;
	}
	p[title=e]{
	    color: orange;
	}
	p[title^=e]{
	    color: orange;
	}
	p[title$=e]{
	    color: orange;
	}
	p[title*=e]{
	    color: orange;
	}

## 4. 复合选择器 ##

### 交集选择器 ###

● 作用：选中同时复合多个条件的元素

● 语法：选择器1选择器2选择器3选择器n{}

● 注意点：交集选择器中如果有元素选择器，必须使用元素选择器开头

	div.red{
	    font-size: 30px;
	}
	
	.a.b.c{
	    color: blue;
	}

### 并集选择器（选择器分组） ###

● 作用：同时选择多个选择器对应的元素

● 语法：选择器1,选择器2,选择器3,选择器n{}

● 例子：#b1,.p1,h1,span,div.red{}

	h1,span{
	    color: green;
	}

## 5. 关系选择器 ##

● 父元素：直接包含子元素的元素叫做父元素

● 子元素：直接被父元素包含的元素是子元素

● 祖先元素：直接或间接包含后代元素的元素叫做祖先元素；一个元素的父元素也是它的祖先元素

● 后代元素：直接或间接被祖先元素包含的元素叫做后代元素；子元素也是后代元素

● 兄弟元素：拥有相同父元素的元素是兄弟元素

### 子元素选择器（Child combinator） ###

● 作用：选中指定父元素的指定子元素

● 语法：父元素 > 子元素

● 例子：A > B

	div.box > p > span{
	    color: orange;
	}

### 兄弟元素选择器（Sibling combinator） ###

● 作用：选择下一个兄弟

● 语法：前一个 + 下一个 前一个 + 下一组

● 例子1：A1 + A2（Adjacent sibling combinator）

● 例子2：  A1 ~ An（General sibling combinator）

	p + span{
	    color: red;
	}
	
	p ~ span{
	    color: red;
	}
## 6. 伪类选择器 ##

伪类（不存在的类，特殊的类）

伪类用来描述一个元素的特殊状态，比如：第一个子元素、被点击的元素、鼠标移入的元素.…

伪类一般情况下都是使用:开头

	● :first-child 第一个子元素
	● :last-child 最后一个子元素
	● :nth-child() 选中第n个子元素 
	  ○ n：第n个，n的范围0到正无穷
	  ○ 2n或even：选中偶数位的元素
	  ○ 2n+1或odd：选中奇数位的元素
 
以上这些伪类都是根据所有的子元素进行排序的

	● :first-of-type 同类型中的第一个子元素
	● :last-of-type 同类型中的最后一个子元素
	● :nth-of-type() 选中同类型中的第n个子元素

这几个伪类的功能和上述的类似，不同点是他们是在同类型元素中进行排序的

	
	● :not()否定伪类，将符合条件的元素从选择器中去除

	/* ul下所有li，黑色 */
	ul>li {
	    color: black;
	}
	
	/* ul下第偶数个li，黄色 */
	ul>li:nth-child(2n) {
	    color: yellow;
	}
	
	/* ul下第奇数个li，绿色 */
	ul>li:nth-child(odd) {
	    color: green;
	}
	
	/* ul下第一个li，红色 */
	ul>li:first-child {
	    color: red;
	}
	
	/* ul下最后一个li，黄色 */
	ul>li:last-child {
	    color: orange;
	}

![](img/4/1.png)

	● :link 未访问的链接
	● :visited 已访问的链接 
	  ○ 由于隐私的原因，所以visited这个伪类只能修改链接的颜色
	 
	● :hover 鼠标悬停的链接
	● :active 鼠标点击的链接

	/* unvisited link */
	a:link {
	  color: red;
	}
	
	/* visited link */
	a:visited {
	  color: yellow;
	}
	
	/* mouse over link */
	a:hover {
	  color: green;
	}
	
	/* selected link */
	a:active {
	  color: blue;
	}

![](img/4/2.gif)

## 7. 伪元素选择器 ##

伪元素，表示页面中一些特殊的并不真实的存在的元素（特殊的位置）

伪元素使用::开头

	● ::first-letter 表示第一个字母
	● ::first-line 表示第一行
	● ::selection 表示选中的内容
	● ::before 元素的开始
	● ::after 元素的最后
	● ::before和::after 必须结合content属性来使用

	/* 段落首字母设置大小为30px */
	p::first-letter{
	    font-size: 30px;
	}
	
	/* 段落第一行设置为黄色背景 */
	p::first-line{
	    background-color: yellow;
	}
	
	/* 段落选中的部分变绿色 */
	p::selection{
	    background-color: green；
	}
	
	/* div前加上内容 */
	div::before{
	    content: 'BEFORE';
	    color: red;
	}
	
	/* div后加上内容 */
	div::after{
	    content: 'AFTER';
	    color: blue;
	}

![](img/4/3.gif)

## 8. CSS Dinner游戏 ##

官方地址：CSS Diner - Where we feast on CSS Selectors!

CSS Dinner是一个帮助初学者快速熟悉css各种选择器的网页游戏

![](img/4/4.png)