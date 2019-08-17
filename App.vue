<template>
  <Child>
    <template #up="{ user }">
      <div>这在上面 {{ user }}</div>
    </template>

    <template>
    <!-- <template #default> -->
      <div>default1</div>
    </template>

    <template #down>
      <div>这在下面</div>
    </template>

    <template>
    <!-- <template #default> -->
      <div>default2</div>
    </template>
  </Child>
</template>

<script>
import Child from './Child'

export default {
  data () {
    return {
      name: 'fish'
    }
  },
  components: {
    Child
  }
}
</script>

<style>

</style>