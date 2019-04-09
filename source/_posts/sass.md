---
title: Sass 是对 CSS 的扩展，让 CSS 语言更强大、优雅
date: 2019-03-05
tags:
---

### 主要功能
  * 变量定义
  * @for from to 遍历
  * @each in 遍历
  * @mixin @include 混合定义 
  * @if @else
  * @extend 继承

### 例子
``` css

$color1: purple;
$color2: orange;
$color3: red;
$color4: green;

@for $i from 1 to 5 {
  @each $cor in $color1, $color2, $color3, $color4 {
    .border-#{$cor}-#{$i} {
      border: #{$i}px solid $cor;
    }
  }
}

@mixin createType($pm, $fx, $size){
  #{$pm}-#{$fx}: #{$size*10}px;
}

@each $pm in padding, margin {
  @each $type in top, right, bottom, left {
    @for $i from 1 to 6 {
      .#{$pm}-#{$type}-#{$i}{
          @include createType($pm,$type,$i)
      }
    }
  }
}

@each $pm in padding, margin {
  @for $i from 1 to 6 {
    .#{$pm}-#{$i}{
      #{$pm}: #{$i*10}px;
    }
  }
}
  
$text-color: purple;
.cc{
  font-weight:bold;
}

@mixin my{
  color: $text-color;
  font-size:20px;
}

@mixin createBorder($side, $width, $color){
  border: $side $width $color;
}

.aa{
    .color:$text-color;
    $bgCor:blue;
    .b{
      color:red;
      @extend .cc;
      .c#{$text-color}{
        background:$bgCor;
        &:hover{
          font-size:16px;
          @include my;
        }
      }
    }
}

```
