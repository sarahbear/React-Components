# React-Components
我们React Components的最佳实践

使用ES6、ES7

### 文件引入
```javascript
import React, {Component} from 'react'

import ExpandableForm from './ExpandableForm'
```

引入依赖和引入本地文件之间空一行

### 初始化State
```javascript
import React, {Component} from 'react'

import ExpandableForm from './ExpandableForm'

export default class UserContainer extends Component {
  state = { expanded: false }
}
```

以上是 ES7 简洁的语法，使用的是```Property initializers```特性，也可以使用熟悉的 ES6 语法在 constructor 中初始化，
见[https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html](https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html)

### propTypes 和 defaultProps

对于并非 isRequired 的 proptype，必须对应设置 defaultProps，避免再增加 if 分支带来的负担
所有的组件都应该要做propTypes验证
```javascript
import React, {Component} from 'react'
import {observer} from 'mobx-react'
import ExpandableForm from './ExpandableForm'
import './styles/ProfileContainer.css'
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
  ```
  
