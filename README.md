# mixins

sass mixins，require `Sass ~> 3.3.0`

**utility**

* [`prefix`](#prefix)
* [`clearfix`](#clearfix)
* [`float`](#float)
* [`text-overflow`](#text-overflow)
* [`animation`](#animation)
* [`placeholder`](#placeholder)
* [`rem`](#rem)
* [`opacity`](#opacity)
* [`arrow`](#arrow)
* [`triangle`](#triangle)
* [`center`](#center)
* [`media`](#media)
* [`box-sizing`](#box-sizing)
* [`touch-scroll`](#touch-scroll)
* [`font`](#font)
* [`onepx`](#onepx)

**functions**

*string*

* [`str-split`](#str-split)
* [`str-repeat`](#str-repeat)
* [`str-replace`](#str-replace)

*list*

* [`first`](#first)
* [`last`](#last)
* [`prepend`](#prepend)
* [`insert-nth`](#insert-nth)
* [`replace`](#replace)
* [`replace-nth`](#replace-nth)
* [`remove`](#remove)
* [`remove-nth`](#remove-nth)
* [`slice`](#slice)
* [`to-string`](#to-string)
* [`shift`](#shift)
* [`contain`](#contain)

## install

```shell
npm i mixins-sass --save
```

## utility

### `prefix`

```scss
// scss 默认前缀：webkit moz ms o
.test {
	@include prefix((transliton: all 0.5s ease-out), webkit);
}
// css
.test {
	-webkit-transliton: all 0.5s ease-out;
   	transliton: all 0.5s ease-out;
}

```

### clearfix

```scss
@include clearfix;
```

### float

```scss
@include float(left);
```

### text-overflow

文字超出显示省略号，支持多行，`$substract`为预留区域百分比%

```scss
@mixin text-overflow($line: 1, $substract: 0);
```

### animation

```scss
@include animation(slideUp 900ms ease both) {
	0% {
        transform: translate3d(0, -200px, 0);
    }
    100% {
        transform: translate3d(0, 0, 0);
    }
}
```


### placeholder

```scss
// scss
@include placeholder() {
	...
}
// css
::-webkit-input-placeholder {
    ...
}
::-moz-placeholder {
    ...
}
:-ms-input-placeholder {
   ...
}
```

### rem

px转rem

```scss
// @mixin rem($property, $values, $support-ie: true, $base: null)
// $support-ie不支持rem的浏览器使用px
// $base 如果未传，会搜索全局变量 $base-font，如果没有默认为 16px

@include rem('padding', '10px 5px 5px 10px', true, '16px');
```

### opacity

兼容ie的透明度

### arrow

生成上下左右的小箭头：[http://lugolabs.com/caret](http://lugolabs.com/caret)

```scss
// @mixin arrow($width, $border-width, $direction, $color, $background-color, $position: relative)
// 箭头宽度  线宽 方向 颜色 背景颜色（一般和父级背景同色）

@include arrow(10px, 1px, 'bottom', '#00f', '#fff');
```

### triangle

三角形生成

```scss
// @mixin triangle($width, $height, $color: #000, $direction: down)

@include triangle(10px, 5px);
```

### center

居中

```scss
// horizontal,vertical,both

@include center(both);
```

### media

媒体查询相关

```scss
// min-width max-width

@mixin screen($min, $max)
@mixin max-screen($width)
@mixin min-screen($width)
@mixin hidpi($ratio: 1.3)
@mixin retina-image($filename, $retina-filename, $ratio: 1.3, $background-size: 100%)
@mixin iphone6($orientation: all)
@mixin iphone6plus($orientation: all)
@mixin iphone5($orientation: all)
@mixin iphone4($orientation: all)
@mixin ipad($orientation: all)
@mixin ipad-mini($orientation: all)
@mixin ipad-retina($orientation: all)

@include retina-image(test.png, test@2.png test@3.png, 2 3);
```

### box-sizing

```scss
html {
	@include box-sizing(border-box);
}
```

### touch-scroll

```scss
body {
	@include touch-scroll;
}
// css
body {
	-webkit-overflow-scrolling: touch;
	overflow-scrolling: touch;
}
```

### font

中文字体解决方案，来自[https://github.com/zenozeng/fonts.css](https://github.com/zenozeng/fonts.css)，有`font-hei`、`font-kai`、`font-song`、`font-fang-song`。

```scss
body {
    @include font-hei;
}
```

### onepx

移动端`1像素`方案

```scss
// $color $direction: top bottom left right vertical all(可不传，四周边框)
.border-l {
    @include onepx(#eee, left);
}
```

## functions

**string**

### str-split

字符串分隔

```scss
@function str-split($string, $delimiter: " ")
```

### str-repeat

字符串重复

```scss
@function str-repeat($string, $times)
```

### str-replace

字符串替换

```scss
@function str-replace($string, $search, $replace: "")
```

**list** 

### first

返回列表第一项

```scss
@function first($list)
```

### last

返回列表最后一项

```scss
@function last($list)
```

### prepend

向列表前面插入一个

```scss
@function prepend($list, $value)
```

### insert-nth

向列表某个位置插入

```scss
@function insert-nth($list, $index, $value)
```

### replace

替换列表的某个元素 `$recursive` 是否全部替换

```scss
@function replace($list, $old-value, $new-value, $recursive: false)
```

### replace-nth

替换列表某个位置的元素

```scss
@function replace-nth($list, $index, $value)
```

### remove

删除列表某个元素 `$recursive` 是否删除所有

```scss
@function remove($list, $value, $recursive: false)
```

### remove-nth

删除列表指定位置元素

```scss
@function remove-nth($list, $index)
```

### slice

截取列表中的一部分

```scss
@function slice($list, $start: 1, $end: length($list))
```

### to-string

列表变成字符串，`$glue`为连接符，`$is-nested`是否是嵌套的列表

```scss
@function to-string($list, $glue: '', $is-nested: false)
```

### shift

将列表部分元素前置

```scss
@function shift($list, $index: 1)
```

### contain

列表是存在某个值

```
@function contain($list, $value)
```