# sass语法

.scss 类似 .less
.sass 类似 .styl

## 安装调试插件

插件：live sass compiler

新建一个demo.scss，点击状态栏处watch sass，就会生成demo.css

## 变量入门

$color = 'red'

_variables.scss 前面加下划线，插件就会忽略该文件，不进行编译

## 嵌套

@import './_variable.scss'
简写
@import 'variable'

## Mixin

``` css
_mixins.scss

@mixin singleline-ellipsis {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}


@import 'mixins'

@include singleline-ellipsis

```

``` css
@mixin singleline-ellipsis($width) {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    width: $width
}

@import 'mixins'

@include singleline-ellipsis(600px)
@include singleline-ellipsis(1000px)
```

## 媒体查询与Mixin的配合

@content

``` css
.header {}
.footer {}

@media screen and (min-width: 768px) {
    .header{}
    .footer{}
}
```

``` css
@mixin ipad {
    @media screen and (min-width: 768px) {
        @content;
    }
}

.header {
    width: 1000px;
    @include ipad {
        width: 600px;
    }
}
```

``` css
@mixin ipad($height) {
    @media screen and (min-width: 768px) {
        height: $height;
        @content;
    }
}

.header {
    width: 1000px;
    @include ipad(100px) {
        width: 600px;
    }
}
```
