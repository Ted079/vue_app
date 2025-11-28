<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
}
</script>

<style scoped>
.btn {
  padding: 10px 45px;
  color: white;
  align-self: flex-end;
  background: teal;
  border: 1px solid teal;
  border-radius: 10px;
}
</style>