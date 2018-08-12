- HTML中的特性名是大小写不敏感的

- 传值给Prop：可以传任何类型

  - 传纯字符串时可以直接 `xxx="纯字符串"`

  - 其它类型，比如number，boolean，数组等，都需要使用`v-bind:xxx="这是一个表达式"`

  - 传入一个对象的所有属性

    ```html 
    <!-- 传入一个对象的所有属性 -->
    <demo-component v-bind="post"></demo-component>
    ```

  - 在prop会在一个组件实例创建前进行验证，所有实例的属性（如data,computed）在default或validator函数中是不可用的

  - `type`可以是一个原生的类型，也可以一个自定义的构造函数

    ```js 
    String
    Number
    Boolean
    Array
    Object
    Date
    Function
    Symbol
    ```

  - 组件可以接受任意的特性，而这些特性会被添加到这个组件的根元素上。使用`inheritAttrs :false`可以禁用属性继承，可以配合`$attrs`一起使用（注意，`$attrs`不包含class和style属性，还是会继承）

  - 对于绝大多数特性，从外部传递进来的特性会替换掉组件内设置好的值。**但是`class`和`style`是例外，他两会合并两边的值**