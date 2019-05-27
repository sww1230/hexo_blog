---
title: js常用工具类库
date: 2019-05-27
tags: js
---

### 一. momentJS日期处理
日期处理类库
[http://momentjs.cn/](http://momentjs.cn/) 
````
  npm install moment
  var moment = require('moment');
  moment().format();
  moment().format('MM/DD/YYYY hh:mm:ss a dddd MMMM Do')
````

### 二. validatorJS验证处理

表单数据验证
[github地址](https://github.com/chriso/validator.js)

````
  npm install validator
  import validator from 'validator';
  validator.isEmail('foo@bar.com'); //=> true
  ......
````


### 三. LodashJS数据处理
是一个一致性、模块化、高性能的 JavaScript 实用工具库。
[https://www.lodashjs.com/](https://www.lodashjs.com/)
#### 为什么选择 Lodash ？
  Lodash 通过降低 array、number、objects、string 等等的使用难度从而让JavaScript 变得更简单。
  Lodash 的模块化方法 非常适用于：
  1. 遍历 array、object 和 string
  2. 对值进行操作和检测
  3. 创建符合功能的函数

````
  npm i --save lodash
  var _ = require('lodash'); // 24Kb
  var _ = require('lodash/core'); // 4Kb
  ......
````


### 四. 卡片|泳道拖拽
[git地址](https://github.com/SortableJS/Vue.Draggable)

````
  npm i -S vuedraggable
  import draggable from 'vuedraggable'
  ......
  <draggable v-model="myArray">
    <transition-group>
        <div v-for="element in myArray" :key="element.id">
            {{element.name}}
        </div>
    </transition-group>
  </draggable>
````

### 五. threeJS数据驱动的三维图形可视化

[github地址](https://github.com/mrdoob/three.js)
[文档](https://threejs.org/docs/)
该项目的目的是使用默认的WebGL渲染器创建一个易于使用，轻量级的3D库。该库还在示例中提供了Canvas 2D，SVG和CSS3D渲染器。


