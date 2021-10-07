<template>
  <div class="container mx-auto space-y-5">
      <h1 class="mt-5">Prueba Strappi Front-end Deploy</h1>
      <div v-for="post in posts" :key="post.id">
        <h1>Título: <span>{{ post.titulo }}</span></h1>
        <p>Descripción: <span>{{ post.descripcion }}</span></p>
        <small>Creado: {{ post.createdAt }}</small>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: []
    }
  },
  created(){
    this.getPosts();
  },
  methods: {
    async getPosts(){
      const res = await this.$axios.get('https://strapi-prueba-backend-deploy.herokuapp.com/posts');
      this.posts = res.data;
    }
  }
}
</script>
