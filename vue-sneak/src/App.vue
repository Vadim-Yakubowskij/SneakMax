<script>
import { ref } from 'vue'
import PostForm from './components/PostForm.vue'
import PostList from './components/PostList.vue'

export default {
  components: {
    PostForm,
    PostList
  },
  setup() {
    const posts = ref([
      {id: 1, title: 'JS 1', body: 'Описание поста 1'},
      {id: 2, title: 'JS 2', body: 'Описание поста 2'},
      {id: 3, title: 'JS 3', body: 'Описание поста 3'},
    ])

    const createPost = (post) => {
      posts.value.push(post)
    }

    return {
      posts,
      createPost
    }
  }
}
</script>

<template>
  <div class="app">
    <post-form
        @create="createPost"
    />
    <post-list
        :posts="posts"
    />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>