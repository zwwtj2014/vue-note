- `keep-alive`：实现缓存失活的组件的目的

- 异步组件

  - 普通的异步：工厂函数

    ```js
    Vue.component('async-example', function (resolve, reject) {
      setTimeout(function () {
        // 向 `resolve` 回调传递组件定义
        resolve({
          template: '<div>I am async!</div>'
        })
      }, 1000)
    })
    ```

  - 配合webpack

    - 全局

      ```js
      Vue.component('async-webpack-example', function (resolve) {
        // 这个特殊的 `require` 语法将会告诉 webpack
        // 自动将你的构建代码切割成多个包，这些包
        // 会通过 Ajax 请求加载
        require(['./my-async-component'], resolve)
      })
      
      // 或者
      
      Vue.component(
        'async-webpack-example',
        // 这个 `import` 函数会返回一个 `Promise` 对象。
        () => import('./my-async-component')
      )
      ```

    - 局部

      ```js
      new Vue({
        // ...
        components: {
          'my-component': () => import('./my-async-component')
        }
      })
      ```