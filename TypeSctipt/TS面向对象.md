---
title: TS面向对象
date: 2022-11-09T10:49:41Z
lastmod: 2022-11-09T21:11:22Z
---

# TS面向对象

# 基本语法:

```js
class Person { 
    age: number = 19;
   
    hello() {
        console.log("hello");
    }   
}

const p = new Person();
```

## 静态属性

属性和方法可用 `static`​​ ​修饰, 修饰之后变为静态属性/方法, 此时不能通过实例调用, 只能通过类名调用

## 只读属性

属性使用`readonly`​修饰, 变为只读属性

注意: 类内的属性和方法, 不需要`let ​`​或`function`​声明

‍

```js
class Person {
    // 实例属性 只有实例对象上可以读取
    age: number = 19;
    // 静态属性 只能通过类名.属性名调用, 实例对象内无此属性
    static Pname: string = "tim";
    // 只读属性
    readonly job = "front end";
    // 静态只读属性
    static readonly jobs = "front end";
    // 实例方法 只有在实例中才可调用
    hello() {
        console.log("hello");
    }
    // 静态方法 只能直接调用类名
    static hi() {
        console.log("static hi");
    }
}

const p = new Person();
```

# 继承

使用 `extends ​`​关键字实现继承

```js
{
    class Animal {
        aniName: string;
        constructor(name: string) {
            this.aniName = name;
        }
        hello() {
            console.log("hello===" + this.aniName);
            console.log(this);
        }
    }

    class Dog extends Animal {
        // 重写方法
        hello(): void {
            console.log("汪汪汪", this.aniName);
        }
    }
    class Cat extends Animal {
        sex: string;
        constructor(name: string, sex: string) {
            super(name);
            this.sex = sex;
        }
        hello(): void {
            // console.log("喵喵喵", this.aniName);
            super.hello();
        }
    }

    let dog = new Dog("dog");
    let cat = new Cat("cat", "male");

    dog.hello();
    cat.hello();
}
```

## super关键字

使用`super`​关键字可以调用父类中的方法: `super.hello()`​

也可以调用父类的构造函数 `super()`​

## 重写方法

父类中定义了的方法, 在子类中重复定义, 那么就是重写, 以子类中的为准

‍

# 抽象类

使用 `abstract`​修饰的类称为抽象类, 抽象类不能被实例化, 只能被子类继承

抽象类中可以含有普通方法以及抽象方法, 抽象类也可以有构造函数供子类使用

## 抽象方法

使用 `abstract`​修饰的方法称为抽象方法, 抽象方法不含有实现, 子类必须实现该抽象方法

抽象方法必须包含在抽象类中, 但是抽象类不一定含有抽象方法

```js
{
    // 定义抽象类, 抽象类不能被直接new出来, 只能用于继承
    abstract class Animal {
        aniName: string;
        constructor(name: string) {
            this.aniName = name;
        }
        // 抽象方法: 子类必须重写该方法, 抽象方法不能有实现
        // 抽象方法必须包含在抽象类中, 但是抽象类不一定必须含有抽象方法
        abstract hello(): void;
    }

    class Dog extends Animal {
        // 重写方法
        hello(): void {
            console.log("汪汪汪", this.aniName);
        }
    }
    class Cat extends Animal {
        sex: string;
        constructor(name: string, sex: string) {
            super(name);
            this.sex = sex;
        }
        hello(): void {
            console.log("喵喵喵", this.aniName);
        }
    }

    let dog = new Dog("dog");
    let cat = new Cat("cat", "male");

    dog.hello();
    cat.hello();
}
```

# 接口

使用 `interface`​定义的称为接口

接口是类的一种约束, 用来规定类中必须实现的属性和方法, 接口中的属性和方法必须都是抽象的, 接口中不允许有构造方法

接口可以重名, 同名接口的内容会合并

类使用`implements`​来实现接口

```js
{
    // 定义接口
    interface animalInterface {

        name: string;
        sex: string;

    }
    // 可以定义两个重名接口, 接口内容会合并
    interface animalInterface {
        say(): void;
    }

    // 实现接口
    abstract class Animal implements animalInterface {
        name: string;
        sex: string;

        constructor(name: string, sex: string) {
            this.name = name;
            this.sex = sex;
        }
        abstract say(): void;
    }

    // 继承animal抽象类
    class Dog extends Animal {
        say(): void {
            console.log("汪汪汪", this.name);
        }
    }

    // 实例化对象
    const dog = new Dog("tim", "male");
    dog.say();
}
```

# 属性的封装

## 属性修饰符

* ​`public ​`​公开, 默认 可以自由读取修改该属性
* ​`private`​: 私有. 只有在类内部才能修改
* ​`protected`​: 被保护. 只有类及其子类才能读取修改

## getter / setter

### 手动实现

```js
        public getter() {
            return this.age;
        }
        public setter(v: number) {
            this.age = v;
        }
```

这种方法实现需要手动函数调用的形式来读取或修改

### get / set

```js
        public get getAge(): number {
            return this.age;
        }

        public set setAge(v: number) {
            this.age = v;
        }
```

这种方法只需要使用原来读取或修改属性的方法即可`​ .属性值`​​​

不需要手动声明属性

# 构造函数的简写

```js
        // constructor(name: string, age: number, job: string) {
        //     this.name = name;
        //     this.age = age;
        //     this.job = job;
        // }
        // 构造函数简写
        constructor(
            public name: string,
            private age: number,
            protected job: string,
        ) {}
```

前面不再需要声明属性类型

# 泛型

泛型（Generics）是指在定义函数、接口或类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。

```js
{
    // 泛型类
    class Person<T> {
        constructor(public name: T, public age: T) {}
    }

    const p = new Person("tim", "dog");
    // 泛型函数
    function fun<T>(v: T): T {
        return v;
    }

    let v = {};
    fun(v);
}
```
