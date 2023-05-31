# JavaScript学习


💭💭

> ✨：JavaScript VS TypeScript 数据类型
> &thinsp;
> 💟：[东非不开森的主页](https://blog.csdn.net/m0_62159662?spm=1000.2115.3001.5343) >&thinsp;
> 💜: 你若盛开，清风自来 💜💜
> &thinsp;
> 🌸: 如有错误或不足之处，希望可以指正，非常感谢 😉
> &thinsp;
>
> @[TOC](TypeScript)

## 一、初识 TypeScript

![在这里插入图片描述](https://img-blog.csdnimg.cn/669dd3f22e974d10931ead04df902acf.png)

### 1.1.TS VS JS

#### 1.1.1.JavaScript 缺点

**JS 缺点**：

- ES5 以及之前的使用的 var 关键字关于作用域的问题
- 最初 JavaScript 设计的数组类型并不是连续的内存空间
- JavaScript 没有加入类型检测这一机制

**JavaScript 不可以在代码编译期间发现代码的错误**

#### 1.1.2.TypeScript 特点

⭐⭐⭐
**特点**：

- 始于 JavaScript，归于 JavaScript TypeScript 可以编译出纯净、 简洁的 JavaScript 代码

**TypeScript 的出现弥补了 JavaScript 类型约束上的缺陷**

- TypeScript 是拥有类型的 JavaScript 超集，它可以编译成普通、干净、完整的 JavaScript 代码

- 我们可以将 TypeScript 理解成加强版的 JavaScript

- JavaScript 所拥有的特性，TypeScript 全部都是支持的，并且它紧随 ECMAScript 的标准，所以 ES6、ES7、ES8 等新语法标准，它都是支持的

- 并且 TypeScript 最终会被编译成 JavaScript 代码，所以你并不需要担心它的兼容性问题

### 1.2.基本安装运行

⭐⭐⭐
两种方式：

- 通过 webpack，配置本地的 TypeScript 编译环境和开启一个本地服务，可以直接运行在浏览器上
- 通过 ts-node 库，为 TypeScript 的运行提供执行环境
  安装
  检测是否安装成功

```bash
npm install typescript -g
tsc -- version
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/7fbc7ce00cee4578ba75c8d7f989fde2.png)

运行

- 安装`ts-node`
- 安装`ts-node`依赖：`tslib  @types/node -g`
- `ts-node f.ts `运行

```bash
npm install ts-node -g

npm install tslib @types/node -g
```

```bash
// 运行
ts-node f.ts
```

## 二、JS 和 TS 相同数据类型

⭐⭐⭐
变量声明：

- 声明了类型后 TypeScript 就会进行类型检测，声明的类型可以称之为类型注解（Type Annotation）；

```typescript
var/let/const 标识符: 数据类型 = 赋值;
```

类型推导

- 声明一个标识符时, 如果有直接进行赋值, 会根据赋值的类型推导出标识符的类型注解 这个过程称之为类型推导
- let 进行类型推导, 推导出来的通用类型
- const 进行类型推导, 推导出来的字面量类型

### 2.1.number、boolean、string

- 数字 布尔 字符串类型

```typescript
let num: number = 123;
let flag: boolean = true;
const name = "kk";
```

### 2.2.null undefined

- null undefined 类型

```typescript
const n1: null = null;
const n2: undefined = undefined;
```

### 2.3.Symbol

- Symbol 类型

```typescript
const title1 = Symbol("title");
const title2 = Symbol("title");
const info = {
  [title1]: "程序员",
  [title2]: "老师",
};
```

- 在对象中不能添加相同的属性名称，但是可以通过 symbol 来定义相同的名称
- 因为 Symbol 函数返回的是不同的值

### 2.4.Array

- 数组类型

1. string[]:数组类型，并且数组中存放的字符串类型
2. Array<string>:数组类型，并且数组中存放的是字符串类型

```typescript
let names: string[] = ["a", "b", "c"];
let nums: Array<number> = [1, 2, 3];
```

PS：

- string: TypeScript 给我们定义标识符时, 提供的字符串类型
- String: JavaScript 中字符串的包装类

### 2.5.Object

- 对象类型

```typescript
const info: object = {
  name: "kk",
  age: 18,
};
```

### 2.6.参数和返回值

- 参数
  在定义一个 TypeScript 中的函数时, 都要明确的指定参数的类型

```typescript
function sum(num1: number, num2: number): number {
  return num1 + num2;
}
const res = sum(1, 2);
```

- 返回值
  返回值可以明确的指定，也可以自动的进行类型推导

### 2.7.匿名函数的参数类型

匿名函数是否需要添加类型注解，最好不要哈哈哈

```typescript
const arr: string[] = ["a", "b", "c"];
arr.forEach(function (item, index, arr) {
  console.log(item, index, arr);
});
```

### 2.8.对象类型和函数类型的结合使用

```typescript
type ZType = {
  x: number;
  y: number;
  z?: number;
};
function KKType(point: ZType) {
  console.log(point.x);
  console.log(point.y);
}
KKType({ x: 1, y: 2 });
```

### 2.9.可选类型

?:

```typescript
type ZType = {
  x: number;
  y: number;
  z?: number;
};
```

## 三、TS 类型

⭐⭐⭐

### 3.1..any

any 类型表示不限制标识符的任意类型，并且可以在该标识符上面进行任意的操作，

- 包括获取不存在的属性、方法；
- 给一个 any 类型的变量赋值任何的值，比如数字、字符串的值；

![在这里插入图片描述](https://img-blog.csdnimg.cn/612e2a13f31a44f58b66977c34152355.png)
这样都是不报错的

### 3.2.unknown

- unknown 类型默认情况下在上面进行任意的操作都是非法的
- 要求必须进行类型的校验，才能根据缩小之后的类型，进行对应的操作

```typescript
let foo: unknown = "aa";
if (typeof foo === "string") {
  console.log(foo.length);
}
```

### 3.3.void

- ts 中如果一个函数没有任何的返回值，那么返回值的类型就是 void 类型
- 如果返回值是 void 类型，那么也可以返回 undefined 类型

```typescript
function sum(num1: number, num2: number): void {
  console.log(num1 + num2);
}
```

### 2.9.never

实际开发中只有进行类型推导时，可能会自动推导出 never，很少使用

- 死循环
- 封装框架/工具库的时候可以使用一下 never

```typescript
function handleMessage(message: string | number | boolean) {
  switch (typeof message) {
    case "string":
      console.log(message.length);
      break;
    case "number":
      console.log(message);
      break;
    case "boolean":
      console.log(Number(message));
      break;
    default:
      const check: never = message;
  }
}

handleMessage("aa");
handleMessage(12);
handleMessage(false);
```

### 2.10.tuple

在函数中使用元组类型是最多的
存这些类型不一样的信息，用对象和元组都可以

```typescript
const info: [string, number, number] = ["kk", 18, 1.7];
```

**tuple 通常可以作为返回的值，在使用的时候会非常的方便；**

