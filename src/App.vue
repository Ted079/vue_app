<template>
  <div class="app">
    <h2>Page with posts</h2>

    <my-button style="margin: 15px 0" @click="changeVisibility">Add post</my-button>
    <my-dialogue v-model:show="dialogueVisibility">
      <post-form @create="addPost" />
    </my-dialogue>
    <post-list @remove="removePost" v-bind:posts="posts" />
  </div>
</template>


<script>
import PostForm from './components/Post.Form.vue'
import PostList from './components/PostList.vue'
import MyButton from './components/UI/MyButton.vue'
import MyDialogue from './components/UI/MyDialogue.vue'
import axios from 'axios'

export default {
  components: {
    PostForm,
    PostList,
    MyDialogue,
    MyButton,
  },
  data() {
    return {
      posts: [],

      dialogueVisibility: false,
    }
  },
  methods: {
    addPost(post) {
      this.posts.push(post)
      this.dialogueVisibility = false
    },

    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id)
    },

    changeVisibility() {
      this.dialogueVisibility = true
    },

    async fetchPosts() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = response.data
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  margin: 15px;
}
</style>