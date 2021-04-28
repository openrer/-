[TOC]

#  一、页面布局

问题：假设容器的高度默认100px，请写出三栏布局，其中左栏、右栏的宽度各为300px，中间的宽度自适应。

总共五种方法

- 方法一：浮动
- 方法二：绝对定位
- 方法三：flexbox。移动开发里面经常用到
- 方法四：表格布局table。虽然已经淘汰了，但应该了解。
- 方法五：网格布局grid。

##  方法一：浮动

左侧设置左浮动，右侧设置右浮动即可，中间会自动的适应.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0px;
            margin: 0px;
        }

        .layout {
            margin-bottom: 150px;
        }

        .layout article div {
            height: 100px;
        }

        /* 方法一  start*/
        .layout.float .left {
            float: left;
            width: 300px;
            background: red;
        }

        .layout.float .right {
            float: right;
            width: 300px;
            background: blue;
        }

        .layout.float .center {
            background: green;
        }
    </style>
</head>
<body>
    <!-- 方法一：浮动 start -->
    <!-- 输入 section.layout.float，即可生成  -->
    <section class="layout float">
        <article class="left-right-center">
            <div class="left">
                我是left
            </div>
            <div class="right">
                我是right
            </div>
            <div class="center">
                方法一:浮动解决方案
                我是 center
            </div>
        </article>
    </section>
</body>
</html>
```

##  方法二：绝对定位

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0px;
            margin: 0px;
        }

        .layout article div{
            height: 100px;
        }

        /* 方法二 绝对定位 start */
        .layout.absolute .left-center-right {
            position: relative;
        }

        .layout.absolute .left {
            position: absolute;
            left: 0;
            width: 300px;
            background: red;
        }

        /* 重要！！！！中间的区域定位300px，右侧定位300px，即可完成。宽度会自动使用 */
        .layout.absolute .center {
            position: absolute;
            left: 300px;
            right: 300px;
            background: green;
        }

        .layout.absolute .right {
            position: absolute;
            right: 0;
            width: 300px;
            background: blue;
        }
    </style>
</head>
<body>
    <section class="layout absolute">
        <article class="left-center-right">
            <div class="left">
                我是left
            </div>
            <div class="right">
                我是right
            </div>
            <div class="center">
                <h1>绝对定位解决方案</h1>
                我是center
            </div>
        </article>
    </section>
</body>
</html>
```

##  方法三：flex布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0px;
            margin: 0px;
        }

        .layout article div {
            height: 100px;
        }

        .left-center-right {
            display: flex;
        }

        .layout.flex .left {
            width: 300px;
            background: red;
        }

        .layout.flex .center {
            flex: 1;
            background: green;
        }

        .layout.flex .right {
            width: 300px;
            background: blue;
        }
    </style>
</head>
<body>
    <section class="layout flex">
        <article class="left-center-right">
            <div class="left">
                我是left
            </div>
            <div class="center">
                <h1>flex布局解决方案</h1>
                我是center
            </div>
            <div class="right">
                我是 right
            </div>
        </article>
    </section>
</body>
</html>
```

##  方法四：表格布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0px;
            margin: 0px;
        }

        layout.table div {
            height: 100px;
        }

        /* 重要：设置容器为表格布局，宽度为100% */
        .layout.table .left-center-right {
            width: 100%;
            display: table;
            height: 100px;
        }

        .layout.table .left-center-right div {
            display: table-cell;     /* 重要：设置三个模块为表格里的单元 */
        }

        .layout.table .left {
            width: 300px;
            background: red;
        }

        .layout.table .center {
            background: green;
        }

        .layout.table .right {
            width: 300px;
            background: blue;
        }
    </style>
</head>
<body>
    <section class="layout table">
        <article class="left-center-right">
            <div class="left">
                我是left
            </div>
            <div class="center">
                <h1>表格布局解决方案</h1>
                我是center
            </div>
            <div class="right">
                我是right
            </div>
        </article>
    </section>
</body>
</html>
```



##  方法五：网格布局grid

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        /* 重要：设置容器为网格布局，宽度为100% */
        .layout.grid .left-center-right {
            display: grid;
            width: 100%;
            grid-template-rows: 100px;
            grid-template-columns: 300px auto 300px;   /* 重要：设置网格为三列，并设置每列的宽度即可*/
        }

        .layout.grid .left {
            background: red;
        }

        .layout.grid .center {
            background: green;
        }

        .layout.grid .right {
            background: blue;
        }
    </style>
</head>
<body>
    <section class="layout grid">
        <article class="left-center-right">
            <div class="left">
                我是 left
            </div>
            <div class="center">
                <h1>网格布局解决方案</h1>
                我是 center
            </div>
            <div class="right">
                我是 right
            </div>
        </article>
    </section>
</body>
</html>
```

##  延伸：五种方法的对比

*  五种方法的优缺点
* 考虑中间模块的高度问题
* 兼容性问题：实际开发中，哪个最实用

###  方法1：浮动：

* 优点：兼容性好。
* 缺点：浮动会脱离标准文档流，因此要清除浮动。我们解决好这个问题即可。

###  方法2：绝对定位

* 优点：快捷。
* 缺点：导致子元素也脱离了标准文档流，可用性差。

###  方法3：flex布局（CSS3中出现的）

* 优点：解决上面两个的不足，flex布局比较完美。移动端基本用flex布局。

###  方法4：表格布局table

* 优点：表格布局在很多场景中很实用，兼容性很好。IE8之前不支持flex，此时可以用表格布局
* 缺点：因为三个部分当成单元格来对待，此时，如果中间的部分变高了，其余部分也会强制变高，然而在实际场景中，我们并不需要两侧的高度也增高。

什么时候用flex布局或者表格布局，看具体的场景。二者没有绝对的优势或者劣势。

###  方法5：网格布局grid（CSS3中新出现的）

* CSS3中引入的布局，很好用。代码量简化了很多。

**PS：面试提到网格布局，说明我们对新技术是有追求的。**

##  延伸：如果题目中去掉高度已知

问题：题目中，如果去掉高度已知，我们往中间的模块里塞很多内容，让中间的模块撑开。会发生什么变化？哪个布局就不能用了？

分析：其实可以这样理解，我们回去看上面的动画效果，当中间的模块变得很挤时，会发生什么效果？就是我们想要的答案。

答案是：**flex 布局和表格布局可以通用**，其他三个布局都不能用了。

##  总结

涉及到的知识点：

（1）语义化掌握到位：每个区域用`section`、`article`代表容器、`div`代表块儿。如果通篇都用 div，那就是语义化没掌握好。

（2）页面布局理解深刻。

（3）CSS基础知识扎实。

（4）思维灵活且积极上进。题目中可以通过`网格布局`来体现。

（5）代码书写规范。注意命名。上面的代码中，没有一行代码是多的。