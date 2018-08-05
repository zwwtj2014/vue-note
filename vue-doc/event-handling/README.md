### 事件修饰符

- `.stop`
- `.prevent`
- `.capture`
- `.self`
- `.once`
- `.passive`

```js
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
```

### 按键修饰符

- `.enter`
- `.tab`
- `.delete` (捕获“删除”和“退格”键)
- `.esc`
- `.space`
- `.up`
- `.down`
- `.left`
- `.right`

> 可以通过全局`config.keyCodes`对象自定义按键修饰符别名：
>
> ```js
> Vue.config.keyCodes = {
>   v: 86,
>   f1: 112,
>   // camelCase 不可用
>   mediaPlayPause: 179,
>   // 取而代之的是 kebab-case 且用双引号括起来
>   "media-play-pause": 179,
>   up: [38, 87]
> }
> ```



### 系统修饰符

- `.ctrl`
- `.alt`
- `.shift`
- `.meta`
- `.exact`：允许你控制由精确的系统修饰符组合触发的事件 
- Fn键对应的修饰符是?

> 在`keyup`配合使用的时候，需要配合其它键一起被按下才会触发

```js
<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button @click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button @click.ctrl.exact="onCtrlClick">A</button>

<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button @click.exact="onClick">A</button>
```

#### 鼠标按钮修饰符

- `.left`
- `.right`
- `.middle`