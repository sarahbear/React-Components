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

