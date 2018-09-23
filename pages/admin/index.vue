<template>
  <div>
    <h2>Admin page</h2>
    <v-btn
    color="success"
    @click="$router.push('/admin/new-post')"
    >
    create new post
    </v-btn>
    <v-btn
    color="success"
    @click="onLogout"
    >
    Logout
    </v-btn>
    <br><br>
    <h3 class="healine3">Existing Posts</h3>
    <p>Hi from {{ name }}</p>
    <v-divider></v-divider>
    <PostList
    :posts="loadedPosts"
    isAdmin
    />
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
  middleware: ['check-auth', 'auth'],
  components: {
    PostList
  },
  computed: {
    loadedPosts () {
      return this.$store.getters.loadedPosts
    }
  },
  methods: {
    onLogout () {
      this.$store.dispatch('logout')
      this.$router.push('/admin/auth')
    }
  }
}
</script>
