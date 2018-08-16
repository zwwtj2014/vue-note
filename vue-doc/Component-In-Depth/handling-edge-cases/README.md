- 绝大多数情况下，我们最好不要触达另一个组件实例内部或手动操作DOM元素

- 访问根实例：`$root`

- 访问父级组件实例：`$parent`

- 访问子组件实例或子元素：`$refs`

  - 只会在组件渲染完成只会生效，并且不是响应式的。所以应该避免在魔板或计算属性中访问`$refs`

- 依赖注入：`provide` & `inject`  大范围有效的prop

  - `provide`：允许我们制定我们想要提供给后代组件的数据/方法
  - `inject`：在任何后代组件中，我们都可以使用`inject`来接收指定的我们想要添加在这个实例上的属性
  - 缺点：
    - 它将你的应用以目前的组件组织方式耦合了起来，使重构变得更加困难 
    - 提供的属性是非响应式的

- 循环引用

  - 递归组件：一般是通过name来引用的，和那可能造成栈溢出
  - 组件之间的循环引用：A => B, B => A, A => B，这样的话需要找个点来解开，一般是`beforeCreate`

- 模板定义

  - `inline-template`：一般不使用
  - `type="text/x-template"`

- 控制更新

  - 强制更新：`$forceUpdate`

  - 通过`v-once`创建低开销的静态组件

    - 当需要渲染大量静态内容时才会有效

      ```js
      Vue.component('terms-of-service', {
        template: `
          <div v-once>
            <h1>Terms of Service</h1>
            ... a lot of static content ...
          </div>
        `
      })
      ```