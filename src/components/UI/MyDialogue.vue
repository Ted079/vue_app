<template>
  <div class="dialogue" v-if="show" @click="hideShow">
    <div @click.stop class="dialogue__content">
      <!-- <my-button @click="hideShow">close</my-button> -->
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-dialogue',
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    hideShow() {
      this.$emit('update:show', false)
    },
  },
}
</script>

<style scoped>
.dialogue {
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgb(0, 0, 0, 0.5);
  display: flex;
  position: fixed;
}

.dialogue__content {
  background: white;
  margin: auto;
  min-width: 400px;
  min-height: 50px;
  border-radius: 10px;
  padding: 20px;
}
</style>