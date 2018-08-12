- `v-if` & `v-else-if` & `v-else`
- `v-show`：元素始终都在 DOM 中, 类似 ng-show
- 频繁的切换, 则使用`v-show`好, 因为不会涉及到 DOM 的销毁和新建。相应的使用`v-if`

- `v-for`具有比 `v-if`更高的优先级

- key 的作用：
  - `v-for`的時候复用已有元素
  - 管理可复用的元素, 使用 key 标识不同的组件，避免组件复用
