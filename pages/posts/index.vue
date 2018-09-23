<template>
  <div>
    <!-- for test and understanding vuex in nuxtjs -->
    <v-btn @click="$store.commit('increment')" light>{{ $store.state.counter }}</v-btn>
    <p>Hi from {{ name }}</p>
    <PostList :posts="loadedPosts" />
  </div>
</template>


<script>
import PostList from '@/components/Posts/PostList'

export default {
  asyncData () {
    return {
      name: process.static ? 'static' : (process.server ? 'server' : 'client')
    }
  },
  // middleware: 'log',
  components: {
    PostList
  },
  computed: {
    loadedPosts () {
      return this.$store.getters.loadedPosts
    }
  }
}
</script>
