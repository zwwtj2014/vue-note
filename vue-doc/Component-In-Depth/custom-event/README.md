- 事件名不建议驼峰，因为HTML不区分大小写，导致在监听的时候找不到对应的事件。所以我们推荐使用带中横线的方式：`**kebab-case** `

- 自定义组件的`v-model`：默认是绑定的是`value`属性和`input`事件。其它组件的话需要使用model属性来指明prop和事件。比如是checkbox组件：

  ```js 
  model: {
      prop: 'checked', // 指明v-model绑定的属性是checked
      event: 'change' // 指明v-model绑定的事件是change
  }
  ```

- 绑定到原生事件：`.native`修饰符

- `$listeners`：它是一个对象，里面包含了作用在这个组件上的所有监听器。听过在组件内部使用`v-on="$listeners"`即可将所有的事件监听器指向组件的子元素上

- `.suyc`修饰符：对一个prop进行"双向绑定"，是为了简化下面的场景：

  ```js 
  <text-document
    v-bind:title="doc.title"
    v-on:update:title="doc.title = $event"
  ></text-document>
  ```

  