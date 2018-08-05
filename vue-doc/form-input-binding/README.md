- `v-model`会忽略所有表单元素的`value`,`checked`，`selected`的初始值
- 对于需要使用输入法的语言，`v-model`不会再输入法组合文字过程中得到更新，想更新需要使用`input`事件
- **在文本区域插值 (`<textarea></textarea>`) 并不会生效，应用 `v-model` 来代替 什么意思？** 

### 修饰符

- `.lazy`：在默认情况下，`v-model` 在每次 `input` 事件触发后将输入框的值与数据进行同步 (除了[上述](https://cn.vuejs.org/v2/guide/forms.html#vmodel-ime-tip)输入法组合文字时)。你可以添加 `lazy` 修饰符，从而转变为使用 `change` 事件进行同步 
  - 这达到的效果就是我一直在文本框中输入，但是都不同步，当失去焦点的时候出发change事件的时候才同步
- `.number`：自动将用户的输入值转为数值类型
- `.trim`：自动过滤用户输入的首尾空白字符 