# 云客http接口规范

## 初阶

### 字段命名规范

使用下划线格式

### 数据类型保持一致

例如：规定是数字, 不要返回字符串的数字

### 字段的状态需标示全面且清晰

例如, is\_checked, 0：未选中, 1：选中

### 接口输出的颗粒度

考虑页面性能, 尽可能合并

### 返回数据通用结构定义

需包含以下结构:

* `retCode`, 业务状态, 异常时表示业务错误码
* `msg`, 提示信息, 异常时表示异常信息
* `data`, 数据信息

### 不要包含无用字段

### 返回完全JSON格式

属性值不可为json字符串, 例如: data属性值不对

```js
{"data": "{\"key\":1}"}
```

### 查询用GET，修改用POST

### 提交数据长度超过1024b的要采用post方式
复杂数据结构采用`application/json`格式，例如以下多层结构:
```js
{
  filters:[
    {
      name: 'n1',
      value: 'v1'
    },
    {
      name: 'n2',
      value: 'v2'
    },
  ]
}
```


### 空值字段表示
保持数据类型一致

例如:
- 字符串属性p2为空时:
```js
//正确
{
  data:{
    p1: 12,
    p2: ''
  }
}

//错误
{
  data:{
    p1: 12
  }
}

//错误
{
  data:{
    p1: 12,
    p2: null
  }
}
```

- 对象属性p2为空时:
```js
//正确
{
  data:{
    p1: 12,
    p2: null
  }
}

//错误
{
  data:{
    p1: 12
  }
}
```

- 数组属性p2为空时, 需返回空数组:
```js
//正确
{
  data:{
    p1: 12,
    p2: []
  }
}

//错误
{
  data:{
    p1: 12
  }
}

//错误
{
  data:{
    p1: 12,
    p2: null
  }
}
```

### 日期&时间
使用timestamp格式

### 数字不要格式化

### 提供提交参数字段约束条件
比如：长度、手机号码格式

### 修改接口及时更新文档通知关联人



## 进阶

### 数据层级结构
一个 key 对应的数据, 不超出： 数值、字符串、单层数组、单层 plain object



