# 命名

1. 以英文为基础的计算机语言禁止以中文字符或拼音命名（JS，TS包含在内）
2. 不得以无意义字符命名
3. 不得已开发者自己名称命名
4. 旧版ES规范中由于没有`私有属性`，约定以`单下划线`开头。

```ts
/**
 * bad !
 */
const 用户名 = "abc"; // 中文
const abc = "123"; // 张三的拼音
const zhangsan = "zhangsan"; // 张三的拼音

/**
 * js中允许使用的约定
 * ts有私有属性关键字
 */
class MyClass {
  // js
  _privateProperty:string = "abc"
  // ts
  private property:string = "abc"
}
```

## 一、驼峰命名法 - Camel

正如它的名称所表示的那样，是指混合使用大小写字母来构成变量和函数的名字。驼峰命名法跟帕斯卡命名法相似，只是首字母为小写，如userName。因为看上去像驼峰，因此而得名。

### 适用范围

* 函数（方法）名
* 函数（方法）内部的常量名
* 变量名
* 参数名
* 一般的文件夹以驼峰命名法命名

```typescript

// 注：两处 string 分别是TS参数类型和函数返回值的类型
function exampleFunctionName (argumentName : string) : string {
  const prefix = "pre-"
  return prefix + argumentName
}

// 一般性的，文件夹名称，文件名称
import { exampleFunctionName } from "./utilFunctionPath/fileName.ts"
```

## 二、帕斯卡命名法（大驼峰命名法）- Pascal

在小驼峰的基础上将首字母大写

### 适用范围

* ES-Class 类名(ES5以函数方式定义的构造函数)
* ES-Component 组件名
* TS-Type 类型名
* TS-Abstract 抽象类名
* TS-Enum 枚举名
* TS-Interface 接口名
* Template-Component 组件名
* 文件夹内是对单个`类、组件、类型`的拆分，以大驼峰命名

注：不建议以I开头作为接口名称。

```ts
// 类型
type UserStatus = "enabled" | "disabled";

// 枚举类型
enum UserGender {
  "male",
  "female"
};

// 抽象类名
abstract class UnkonwUser {
  constructor(public name: string){}
  name: string
  getName(): void
}

// 类名 
class MyUser extends {
  constructor(name: string) {
    super(name);
    this.name = name
  }
  name: string
  getName(): void {
    return this.name
  }
}

// 接口名
interface UserProfile {
  userName: string
  userStatus: UserStatus
  userGender: UserGender
}


// 1.文件夹内是对单个`类、组件、类型`的拆分，以大驼峰命名
// 2.组件的名称
import MyComponent from "./MyComponent/index.ts"

// template的组件名称
<template>
  <MyComponent />
</template>
```

## 连接线命名法（减号命名法、烤串命名法）- Kebab

以小写字符和减号连接

### 适用范围

* Css-class 样式类名

> 我记得有一个以Kebab为基础，带下划线的css命名规范，但忘记了规范名称。留个坑找到了再填

```html
<div class="my-box">red</div>
<style>
  .my-box {
    color:red;
  }
</style>

```

> 属性名原则上禁用，但迫不得已偶尔会用到在属性名的定义上

```js
const obj = {
  "my-name": 1
}

const suffix = "-suffix"

const obj = {
  ["my-name" + suffix]: 1
}
```
## 下划线命名法（蛇形命名法）-snake

以小写加下划线命名


原则上禁用，如必须使用时参照驼峰命名法的适用范围

```js
const my_name = "Alice"
```
## 大写命名法 - upper

全大写命名法：名称中所有字母采用大写的命名方法。可以用下划线进行分割。

### 适用范围

* 环境变量
* 应用级别常量

与语言系统变量不冲突的常量允许使用双下划线开头或结尾

```JS
const NODE_ENV = "development"
const __ROOT_DIR__ = "/app-dir"
const MAX_COUNT = 10
const BASE_URL = 'https://www.baidu.com/'
```

## 首字母大写命名法 - upperFirst

首字母大写，余下字符小写，单词以下划线连接

>原则上禁用,如需使用参照大写命名法

```ts
const My_Name = "Bob"
```

# 缩写

## 允许的常见缩写

str => string
num => number
obj => object
fun => function
arr => array
res,rest => result
res,resp => response
req => request

注：res在语义不冲突时可用

## 循环内部常见缩写

> 原则上成对出现

i => item // 语义不冲突可以用
i => index, o => object

n => 表示第n项, m => member
k => key, v => value


# 函数命名动词前缀

命名规则 : 前缀为动词

|动词|含义|返回值|
| - | - | - |
|has|判断是否含有某个值|函数返回一个布尔值。true：含有此值；false：不含有此值|
|is |判断是否为某个值|函数返回一个布尔值。true：为某个值；false：不为某个值|
|get|获取某个值|函数返回一个需要获取的值，或获取失败状态|
|set|设置某个值|无返回值、返回是否设置成功或者返回链式对象、返回设置成功状态|