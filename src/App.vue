<template>
  <div id="app">
    <CreatePost />
    <h2>Quantity posts: {{postsCount}}</h2>
    <div class="post" v-for="post in allPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import CreatePost from './components/CreatePost'

export default {
  name: 'App',
  computed: mapGetters(['allPosts', 'postsCount']),
  components: {
    CreatePost
  },
  methods: mapActions(['fetchPosts']),
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
  margin: 0 auto;
  width: 400px;
}

.post {
  margin: 0 auto;
  border-radius: 5px;
  width: 400px;
  border: 1px solid #ccc;
  margin-bottom: 1rem;
}
</style>
