- 选项合并（两种方式：直接在`new Vue`，通过mixins 属性；使用`Vue.extend`）

  - 数据对象(data)在内部会进行浅合并，在和组件的数据发生冲突时以组件数据优先
  - 同名钩子函数将混合为一个数组， 因此都会被调用。另外，混入对象的钩子将在组件自身钩子之前调用
  - 值为对象的选项，例如`methods`,`components`,`directives`,将被混合为同一个对象。两个对象键名冲突时，取组件对象的键值对。

- 全局注册

  - 一旦使用全局混入对象，将会影响到所有之后创建的Vue实例

- 自定义选项合并策略

  - 默认策略：简单的覆盖已有值

  - 自定义策略：向`Vue.config.optionMergeStrategies`添加一个函数

    - 比如直接使用methods的合并策略

      ```js
      var strategies = Vue.config.optionMergeStrategies
      strategies.myOption = strategies.methods
      ```

    - 更高级的自定义

      ```js
      const merge = Vue.config.optionMergeStrategies.computed
      Vue.config.optionMergeStrategies.vuex = function (toVal, fromVal) {
        if (!toVal) return fromVal
        if (!fromVal) return toVal
        return {
          getters: merge(toVal.getters, fromVal.getters),
          state: merge(toVal.state, fromVal.state),
          actions: merge(toVal.actions, fromVal.actions)
        }
      }
      ```

