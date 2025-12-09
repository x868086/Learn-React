## React学习路线

![react学习路线](./imgs/mermaid-chart-20251208T034437.png)


### 组件函数
react组件是返回html标签的JS函数
**组件就是一个js函数**，jsx描述了UI，**jsx中的{}部分是执行JS表达式的地方**。
**react组件**就是**函数**，这个函数**接受数据（通过props）**,**包含逻辑（如事件处理函数）**，返回描述**UI的JSX**
返回组件时**不能有多个JSX标签**，必须将其包裹到**一个空标签**或**一个div中**。

jsx文件是javascript xml的缩写，最终会被编译诚JS代码。jsx是react.createElement()的语法糖

### Hook
use开头的函数被称为Hook，可以通过组合现有的Hook来编写属于自己的hook.

### useState
1. useState()执行时，返回的是一个数组：`[stateValue, setStateFunction]`
2. const [a, b] = useState 相当于是给**stateValue**和**SetStateFunction**起了个**别名**
3. useState(0)中传入的参数是用来**指定stateValue的初始值**

#### 组件间共享数据
状态提升：将state“向上”移动到最接近包含所有子组件的组件中，实现组件共享使用
```jsx
import {useState} from 'react'

export default function App(){
    const [count, setCount] = useState(0)

    function handlerClick(){
        setCount(count + 1);
    }

    return (
        <div>
            <h2>共享state按钮</h2>
            <MyButton count={count} onClick={handlerClick} />
            <MyButton count={count} onClick={handlerClick} />
        </div>
    )
}

// 这里的参数{count,onClick}，就是父组件props中传入的count, onClick
    function MyButton({count,onClick}){
        return(
            <button onClick={onClick}>点了{count}次</button>
        )
    }
```