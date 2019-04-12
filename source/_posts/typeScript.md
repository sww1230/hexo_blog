---
title: typeScript
date: 2019-04-05
tags: js
---

> 什么是 TypeScript？
TypeScript 是一种由微软开发的自由和开源的编程语言，它是 JavaScript 的一个超集，扩展了 JavaScript 的语法。
TypeScript的设计目的应该是解决JavaScript的“痛点”：弱类型和没有命名空间，导致很难模块化


#### 1.声明变量类型 

```` javascript
var foo: string;
foo = true; //error: Cannot convert 'boolean' to string
interface Phone {
    model: string
    readonly price: number // readonly 标记某个属性是只读的
    producer?: string  // ?标记 表示这个属性是可选的
    [propName: string]: any // any 任意属性 包括 string 和 number 类
}
let newPhone: Phone = {
    model: 'iPhone XS',
    price: 8599, // OK
}
let phoneB: Phone = {
    model: 'iPhone XS',
    price: 8599,
    producer: 'Apple', // OK
} 
````

#### 2.类型批注

> 对于基本类型的批注是number, bool和string。而弱或动态类型的结构则是any类型。

```` javascript
function area(shape: string, width?: number, height: number):string {
    var area = width * height;
    return "I'm a " + shape + " with an area of " + area + " cm squared.";
}
console.log(area("rectangle", 30, 15));
````

#### 3.接口

> 接口可以作为一个类型批注。

```` javascript
  interface Shape {
    name: string;
    width: number;
    height: number;
    color?: string;
}
function area(shape : Shape) {
    var area = shape.width * shape.height;
    return "I'm " + shape.name + " with area " + area + " cm squared";
}
console.log( area( {name: "rectangle", width: 30, height: 15} ) );
console.log( area( {name: "square", width: 30, height: 30, color: "blue"} ) );
````

#### 4.类

> TypeScript支持集成了可选的类型批注支持的ECMAScript 6的类
  类中有两个属性 area 和 color，一个构造器 (constructor()), 一个方法是 shoutout()
  可以使用三种修饰符：public、private、protected

```` javascript
class Shape {
    area: number;
    private color: string;
    constructor ( public name: string, width: number, height: number ) {
        this.area = width * height;
        this.color = "pink";
    };
    shoutout() {
        return "I'm " + this.color + " " + this.name +  " with an area of " + this.area + " cm squared.";
    }
}
var square = new Shape("square", 30, 30);
````

#### 5.继承

> 继承使用关键字 extends;
super( name, width, height )

```` javascript
class Shape3D extends Shape {
    volume: number;
    constructor ( public name: string, width: number, height: number, length: number ) {
        super( name, width, height );
        this.volume = length * this.area;
    };
    shoutout() {
        return "I'm " + this.name +  " with a volume of " + this.volume + " cm cube.";
    }
    superShout() {
        return super.shoutout();
    }
}
var cube = new Shape3D("cube", 30, 30, 30);
console.log( cube.shoutout() );
console.log( cube.superShout() );
````

#### 6.抽象类

> 抽象类是某个类具体实现的抽象表述，作为其他类的基类使用。
TypeScript 中使用 abstract 关键字表示抽象类以及其内部的抽象方法

**它具有两个特点：**
1. 不能被实例化
2. 其抽象方法必须被子类实现

```` javascript
abstract class Animal {
    public abstract makeSound(): void
    public move() {
        console.log('Roaming...')
    }
}
class Cat extends Animal {
    makeSound() {
        console.log('Meow~')
    }
}
let tom = new Cat()
tom.makeSound() // => 'Meow~'
tom.move() // => 'Roaming...'
````

> 上述例子中，我们创建了一个抽象类 Animal，它定义了一个抽象方法 makeSound。然后，我们定义了一个 Cat 类，继承自 Animal。因为 Animal 定义了 makeSound 抽象类，所以我们必须在 Cat 类里面实现它。不然的话，TS 会报错。


#### 7.类与接口

> 类可以实现（implement）接口。通过接口，你可以强制地指明类遵守某个契约。你可以在接口中声明一个方法，然后要求类去具体实现它。

```` javascript
interface ClockInterface {
    currentTime: Date
    setTime(d: Date)
}
class Clock implements ClockInterface {
    currentTime: Date
    setTime(d: Date) {
        this.currentTime = d
    }
}
````

**接口与抽象类的区别**

1. 类可以实现（implement）多个接口，但只能扩展（extends）自一个抽象类。
2. 抽象类中可以包含具体实现，接口不能。
3. 抽象类在运行时是可见的，可以通过 instanceof 判断。接口则只在编译时起作用。
4. 接口只能描述类的公共（public）部分，不会检查私有成员，而抽象类没有这样的限制。
