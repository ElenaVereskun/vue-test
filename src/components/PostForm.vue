<template>
  <div>
    <form class="form" @submit.prevent>
      <h4>Добавить задачу</h4>
      <my-input v-model="post.title" type="text" placeholder="название" />
      <my-input v-model="post.body" type="text" placeholder="описание" />
      <my-button @click="createPost">Добавить</my-button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>
<style scoped>
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
