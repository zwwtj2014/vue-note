- 父组件模板的所有东西都会在父级作用域内编译；子组件模板的所有东西都会在子级作用域内编译 

- 作用域插槽解决的问题：在提供给别人用的组件的时候，可以使从子组件获取数据。是在父组件使用子组件数据的一种形式 

  ```js 
         // 子组件
         Vue.component('todo-list', {
              props: ['todos'],
              template: `
                  <ul>
                      <li v-for="todo in todos" :key="todo.id">
  					  // 预留插槽，父组件在使用的时候可以插入任何逻辑， 但是对于想在父组件使用这里的todo的时候就需要使用作用域插槽了
                          <slot :todo="todo">
                              {{todo.text}}
                          </slot>
                      </li>
                  </ul>
              `
          });
  ```

  ```js 
  	   // 这是普通插槽的用法，没有指定name的时候，使用的都是default, 在子组件有for, 所以会报错如下
         // Duplicate presence of slot "default" found in the same render tree - this will likely cause render errors.
         <todo-list :todos="todos">
              <span>123</span>
         </todo-list>
  ```

  ```js 
          <todo-list :todos="todos">
              <!-- 
                  作用域插操的主要作用是为了在使用的使用可以从todo-list中获取到数据, 是在父组件使用子组件数据的一种形式
                  即: slotProps 是todo-list组件所有的属性集合
               -->
              <template slot-scope="slotProps">
                  // 这里是在父组件中使用子组件中的数据
                  <span v-if="slotProps.todo.isComplete">
                      {{ slotProps.todo.text }} - {{slotProps}}
                  </span>
              </template>
          </todo-list>
  ```

  