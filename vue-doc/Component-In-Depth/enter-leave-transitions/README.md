## 单元素/组件的过渡

- `transition`可作用于下列组件

  - 条件渲染(`v-if`)
  - 条件展示（`v-show`）
  - 动态组件
  - 组件根节点

- 当插入或删除包含在`transition`组件中的元素时，Vue将会做下面处理：

  - 自动嗅探目标元素是否应用了CSS过渡或者动画，如果是，则在恰当的时机添加/删除 CSS类名
  - 如果过渡组件提供了**JavaScript钩子函数**，这些钩子函数将在恰当的时机被调用
  - 如果上述两点都没有，则DOM操作（插入/删除）在下一帧中立即执行

- 过渡的类名

  - `v-enter`

  - `v-enter-active`

  - `v-enter-to`

  - `v-leave`

  - `v-leave-active`

  - `v-leave-to`

    ![Transition Diagram](https://cn.vuejs.org/images/transition.png) 

- CSS 动画

  - 与过渡的区别是`v-enter`类名在插入DOM后不会立即删除，而是在`animationend`事件触发时删除

- 自定义过渡的类名：优先级高于普通类名，对于集成第三方CSS动画库很有用

  - `enter-class`
  - `enter-active-class`
  - `enter-to-class` (2.1.8+)
  - `leave-class`
  - `leave-active-class`
  - `leave-to-class` (2.1.8+)

- 同时使用过渡和动画时，需要通过`type="animation|transition"`的方式来指明需要Vue监听的类型

- 显性的过渡持续时间

  - `:duration`

- JS钩子，可以通过钩子改变对应的状态，可以和Velocity这种配合，直接操作DOM来实现动画

  - `before-enter`
  - `enter`
  - `after-enter`
  - `enter-cancelled`
  - `before-leave`
  - `leave`
  - `after-leave`
  - `leave-cancelled`

- 初始渲染的过渡：`appear`

  - `appear-class`
  - `appear-to-class`
  - `appear-active-class`

- 多元素过渡

  - 使用不同key做标识
  - 过渡模式
    - `in-out`：新元素先进行过渡，完成只会当前元素多度离开
    - `out-in`：当前元素先进行过渡，完成只会新元素过渡进入

- 多组件过渡：使用动态组件即可

- 列表过渡：`transition-group`

  - 不同于 `<transition>`，它会以一个真实元素呈现：默认为一个 `<span>`。你也可以通过 `tag` 特性更换为其他元素。
  - [过渡模式](https://cn.vuejs.org/v2/guide/transitions.html#%E8%BF%87%E6%B8%A1%E6%A8%A1%E5%BC%8F)不可用，因为我们不再相互切换特有的元素。
  - 内部元素 **总是需要** 提供唯一的 `key` 属性值。
  - 排序过渡：`v-move`，[可以多维](https://jsfiddle.net/chrisvfritz/sLrhk1bc/)