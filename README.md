# slot ([docs](https://cn.vuejs.org/v2/guide/components-slots.html))

vue 2.6.0 开始，新增了 v-slot 指令，废弃了 slot 具名插槽和 slot-scope（将会在 vue 3.0 正式废弃）

## slot 和 slot-scope

* [具名插槽](https://cn.vuejs.org/v2/guide/components-slots.html#%E5%B8%A6%E6%9C%89-slot-%E7%89%B9%E6%80%A7%E7%9A%84%E5%85%B7%E5%90%8D%E6%8F%92%E6%A7%BD)
* [作用域插槽](https://cn.vuejs.org/v2/guide/components-slots.html#带有-slot-scope-特性的作用域插槽)

作用域插槽实际应用，比如 ElementUI table 中的 [自定义列模版](https://element.eleme.io/#/zh-CN/component/table#zi-ding-yi-lie-mo-ban)，其实就是子组件在 slot 中定义的一些值，可以在父组件中被获取，通过 slote-scope 中定义的那个变量去获取

注意被废弃的是带有 slot 特性的 **具名插槽**，和带有 slot-scope 特性的 **作用域插槽**，slot 组件还是存在的

## v-slot

注意：一个不带 name 的 <slot> 出口会带有隐含的名字 “default”

在向具名插槽提供内容的时候，我们可以在一个 <template> 元素上使用 v-slot 指令，并以 v-slot 的参数的形式提供其名称：（这里 slot name 为 up)

```vue
<template v-slot:up>
  <div>这在上面</div>
</template>
```

现在 <template> 元素中的所有内容都将会被传入相应的插槽。任何没有被包裹在带有 v-slot 的 <template> 中的内容都会被视为默认插槽的内容

当然你也可以指定名字为 default，但是我测试了下，不指定的话，**所有** 没被指定的内容，都会被塞入默认的插槽下，但是指定了的话，只取最后一个了

slot-scope 的使用也更加方便：

```vue
<template v-slot:up="scope">
  <div>这在上面 {{ scope.user }}</div>
</template>
```

v-slot 一般情况下是在 template 上的，但是如果插槽只有一个默认插槽（独占默认插槽），就可以直接写在组件的标签上（此时不需要 template 了）：

```vue
<current-user v-slot:default="slotProps">
  {{ slotProps.user.firstName }}
</current-user>
```

可以省略为：

```vue
<current-user v-slot="slotProps">
  {{ slotProps.user.firstName }}
</current-user>
```

具名插槽还能缩写：(v-slot:up 能被缩写成  #up)

```vue
<template #up="{ user }">
  <div>这在上面 {{ user }}</div>
</template>
```
