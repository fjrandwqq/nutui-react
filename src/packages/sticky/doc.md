
#  Sticky组件

## 介绍

效果同 css 中的 position: sticky,对低端浏览器可使用其做兼容

## 安装
```tsx
import { Sticky } from '@nutui/nutui-react';
```

## 代码演示

### 基础用法
:::demo
```tsx

import React, { useEffect, useRef, useState } from 'react'
import {Button,Cell, Sticky } from '@nutui/nutui-react'

const App = () => {
  const handleChange = (val: boolean) => {
    console.log('吸顶状态发生了改变,当前fixed为', val)
  }
return(
    <>
        <h2>基础用法</h2>
        <Cell style={{ height: '300px' }}>
          <Sticky threshold={57} onChange={handleChange}>
            <Button type="primary">吸顶</Button>
          </Sticky>
        </Cell>
        <h2>吸顶距离</h2>
        <Cell  style={{ height: '300px' }}>
          <Sticky threshold={120}>
            <Button type="primary">距离顶部120px</Button>
          </Sticky>
        </Cell>
        <h2>吸底距离</h2>
        <Cell style={{ height: '64px' }}>
          <Sticky threshold={0} position="bottom">
            <Button type="primary">距离底部0px</Button>
          </Sticky>
        </Cell>
    </>
)
   
}
export default App;
```
:::

### 指定容器内
:::demo
```tsx
import React, { useEffect, useRef, useState } from 'react'
import {Button,Cell, Sticky } from '@nutui/nutui-react'

const App = () => {
  const containerTopRef = useRef(null)
  const containerRef = useRef(null)

   return(
    <>
        <h2>指定容器内吸顶</h2>
        <Cell>
          <div
            className="sticky-container"
            ref={containerTopRef}
            style={{ height: '300px' }}
          >
            <Sticky container={containerTopRef} threshold={57}>
              <Button type="info">
                指定容器内吸顶
              </Button>
            </Sticky>
          </div>
        </Cell>
        <h2>指定容器吸底</h2>
        <Cell>
          <div
            className="sticky-container"
            ref={containerRef}
            style={{ height: '300px' }}
          >
            <Sticky position="bottom" container={containerRef} threshold={0}>
              <Button  type="info">
                指定容器吸底
              </Button>
            </Sticky>
          </div>
        </Cell>
      
    </>
   )
}
export default App;
```
:::

## Sticky

### Props

| 参数         | 说明                             | 类型   | 默认值           |
|--------------|--------------------------------|--------|------------------|
| position     | 吸附位置（top、bottom）               | string | `top`             |
| threshold          | 距离，当 position 为 top 时，设置的是 top | number | `0`               |
| zIndex      | 吸附时的层级                         | number | `2000`            |
| container    | 容器的 ref                        | `React.RefObject<HTMLElement>`| - |
| onChange  | 吸附状态改变时触发  | `val: boolean` | - |
