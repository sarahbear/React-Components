# React-Components
我们React Components的最佳实践

使用ES6、ES7

### 文件引入

引入依赖和引入本地文件之间空一行
```javascript
import React, {Component} from 'react'

import ExpandableForm from './ExpandableForm'
```

### 初始化State

使用 ES7 简洁的语法，使用的是```Property initializers```特性，也可以使用熟悉的 ES6 语法在 constructor 中初始化，
见[https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html](https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html)

```javascript
import React, {Component} from 'react'

import ExpandableForm from './ExpandableForm'

export default class UserContainer extends Component {
  state = { expanded: false }
}
```

### propTypes 和 defaultProps

对于并非 isRequired 的 proptype，必须对应设置 defaultProps，避免再增加 if 分支带来的负担

所有的组件都应该要做propTypes验证

如有必要，使用 PropTypes.shape 明确指定需要的属性，避免 PropTypes.any

```javascript
import React, {Component} from 'react'
import ExpandableForm from './ExpandableForm'

export default class ProfileContainer extends Component {
  state = { expanded: false }
 
  static propTypes = {
    model: React.PropTypes.object.isRequired,
    title: React.PropTypes.string
  }
 
  static defaultProps = {
    model: {
      id: 0
    },
    title: 'Your Name'
  }
}
```
  
  
### 闭包

避免如下代码

```javascript
  <input
    type="text"
    value={model.name}
    onChange={(e) => { model.name = e.target.value }}
    placeholder="Your Name"/>
```


每次父组件渲染，都会给子组件传入一个新function，这会触发重新渲染，不管是否有props的变化，重新渲染代价很大

使用：
```javascript
  <input
    type="text"
    value={model.name}
    onChange={this.handleChange}
    placeholder="Your Name"/>
```

  
### 方法

使用箭头函数绑定

Handler 命名风格:

- 使用 `handle` 开头
- 以事件类型作为结尾 (如 `Click`, `Change`)
- 使用一般现在时

```javascript
  handleExpand = (e) => {
    e.preventDefault()
    this.setState({ expanded: !this.state.expanded })
  }
```


### setState

setState 是异步的，调用后setState不会立即执行

可以向 setState 传递一个函数

```javascript
this.setState({ expanded: !this.state.expanded })
```

```javascript
this.setState(prevState => ({ expanded: !prevState.expanded }))
```






















