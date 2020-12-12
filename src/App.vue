<template>
  <div id="app">
    <div class="post" v-for="post in allPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';

export default {
  name: 'App',
  computed: {
    ...mapGetters(['allPosts'])
  },
  methods: {
    ...mapActions(['fetchPosts'])
  },
  async mounted() {
    this.fetchPosts()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.post {
  margin: 0 auto;
  border-radius: 5px;
  width: 400px;
  border: 1px solid #ccc;
  margin-bottom: 1rem;
}
</style>
