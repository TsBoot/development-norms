# 异步代码



## setTimeout,setInterval 使用结束需要及时销毁

```js
const timeoutID = setTimeout(() => {
  clearTimeout(timeoutID)
}, 100); 


let i = 0
const intervalID = setInterval(() => {
  if (i>5) {
    clearInterval(intervalID);
  }
}, 100);
```

## 原则上禁止使用宏任务代码解决同步代码和微任务Bug

例如：

1. 页面不跳转时获取不到数据，使用setTimeout跳转页面
2. 修改页面数据不更新，使用setTimeout刷新页面
3. 无法触发某个功能或事件，使用setTimeout触发事件

## 禁止直接操作DOM

## 尽量使用async await编写异步代码

1. 使用`async/await`编写时，需要`确保`最外层有`try catch`进行异常捕获。
2. `async/await` 不是银弹，并不能解决所有的异步场景。必要时请使用`Promise`。
