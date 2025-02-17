# Price 價格

### 介紹

用來對商品價格數值的小數點前後部分應用不同樣式，還支持人民幣符號、千位分隔符、設置小數點位數等功能。

### 安裝

```javascript
import { Price } from '@nutui/nutui-react'
```

## 代碼演示

### 基本用法

:::demo

```tsx
import  React from "react"
import { Price, Cell } from '@nutui/nutui-react'

const App = () => {
  return (
    <Cell>
        <Price price={1010} needSymbol={false} thousands />
    </Cell>
  );
};
export default App;
```

:::

### 有人民幣符號，無千位分隔

:::demo

```tsx
import  React from "react"
import { Price, Cell } from '@nutui/nutui-react'

const App = () => {
  return (
    <Cell>
        <Price price={10010.01} needSymbol thousands={false} />
    </Cell>
  );
};
export default App;
```

:::

### 帶人民幣符號，有千位分隔，保留小數點後三位

:::demo

```tsx
import  React from "react"
import { Price, Cell } from '@nutui/nutui-react'

const App = () => {
  return (
    <Cell>
        <Price price={15213.1221} decimalDigits={3} needSymbol thousands />
    </Cell>
  );
};
export default App;
```

:::

### 異步隨機變更

:::demo

```tsx
import React, { useState, useEffect } from 'react'
import { Price, Cell } from '@nutui/nutui-react'

const App = () => {
  const [price, setPrice] = useState(Math.random() * 10000000)

  useEffect(() => {
    const timer = setInterval(() => {
      setPrice(Math.random() * 10000000)
    }, 1000)
    return () => {
      clearInterval(timer)
    }
  }, [])
  return (
    <Cell>
      <Price price={price} decimalDigits={3} needSymbol thousands />
    </Cell>
  );
};
export default App;
```

:::

## API

### Props

| 參數           | 說明                     | 類型    | 默認值 |
| -------------- | ------------------------ | ------- | ------ |
| price          | 價格數量                 | Number  | 0      |
| needSymbol    | 是否需要加上 symbol 符號 | Boolean | true   |
| symbol         | 符號類型                 | String  | &yen;  |
| decimalDigits | 小數位位數               | Number  | 2      |
| thousands      | 是否按照千分號形式顯示   | Boolean | false  |
