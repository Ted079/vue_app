<template>
  <div class="wrapper">
    <div v-if="posts.length > 0">
      <h3>User list</h3>
      <post-item
        v-for="post in posts"
        :key="post.id"
        :post="post"
        @remove="$emit('remove', post)"
      />
    </div>
    <div v-else>
      <h2 style="color: red">The post list is empty.</h2>
    </div>
  </div>
</template>

<script>
import PostItem from './PostItem.vue'
export default {
  components: {
    PostItem,
  },
  props: {
    posts: {
      type: String,
      required: true,
    },
  },
  data() {
    return {}
  },
  methods: {},
}
</script>

<style>
.wrapper {
  /* margin: 15px; */
}
h3 {
  margin-left: 15px;
}
</style>
