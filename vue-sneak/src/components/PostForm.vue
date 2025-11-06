<script>
import { ref } from 'vue'
import MyInput from "@/components/UI/MyInput.vue"

export default {
  components: { MyInput },
  emits: ['create'],
  setup(props, { emit }) {
    const post = ref({
      title: '',
      body: '',
    })

    const createPost = () => {
      post.value.id = Date.now()
      emit('create', { ...post.value })
      post.value = {
        title: '',
        body: '',
      }
    }

    return {
      post,
      createPost
    }
  }
}
</script>

<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <my-input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Название"
    />
    <my-input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Описание"
    />
    <my-button
        style="align-self: flex-end; margin-top: 15px"
        @click="createPost"
    >
      Создать
    </my-button>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>