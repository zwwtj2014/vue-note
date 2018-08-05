1.  在`v-for`中, 我们拥有对父作用域属性的完全访问权限
2.  可以使用`of`替代`in`
3.  `v-for` 支持数组、对象
4.  数组场景：Vue 包含一组观察数组的变异方法，所以它们也将会触发视图更新 
    - `push()`
    - `pop()`
    - `shift()`
    - `unshift()`
    - `splice()`
    - `sort()`
    - `reverse()`
5.  以下两种Vue不能检测以下变动的数组
    - 当你利用索引直接设置一个项时，使用方法：`Vue.set(this.items, 1, 'y') `
    - 当你修改数组的长度时 ：`this.items.splice(newLength)`
6.  Vue不能检测对象属性的添加或删除
    - 我们同样使用 `Vue.set(object, key, value) ` 来更改并触发响应式
