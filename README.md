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

以上是ES7简洁的语法，使用的是```Property initializers```特性，也可以使用熟悉的ES6语法在constructor中初始化，
见[https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html](https://facebook.github.io/react/blog/2015/01/27/react-v0.13.0-beta-1.html)

### propTypes 和 defaultProps

