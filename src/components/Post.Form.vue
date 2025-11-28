<template >
  <form @submit.prevent>
    <h4>Add the Post</h4>
    <my-input v-model="post.title" type="text" placeholder="title" />
    <my-input v-model="post.body" type="text" placeholder="description" />
    <my-button style="margin-top: 15px; align-self: flex-end" @click="addPost">Add</my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
    }
  },
  methods: {
    inputTitle(e) {
      this.post.title = e.target.value
    },

    addPost(e) {
      e.stopPropagation()
      e.preventDefault()
      if (!this.post.body || !this.post.title) {
        alert('You must fill in all fields!')
        return
      }

      this.post.id = new Date()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: '',
      }
    },
  },
}
</script>

<style scoped>
form {
  width: 100%;
  padding: 15px;
  display: flex;
  flex-direction: column;
}
</style>


