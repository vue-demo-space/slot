<template>
  <div>
    <slot name="up" :user="user"></slot>
    <slot name="default"></slot>
    <ul>
      <li>apple</li>
      <li>orange</li>
    </ul>
    <slot name="down"></slot>
  </div>
</template>

<script>
export default {
  data () {
    return {
      user: 'fish'
    }
  }
}
</script>

<style>

</style>