<template>
  <div>
    <AdminPostForm :post="loadedPost" @submit="onSubmitted" />
  </div>
</template>

<script>
import AdminPostForm from '@/components/Admin/AdminPostForm'

export default {
  middleware: ['check-auth', 'auth'],
  components: {
    AdminPostForm
  },
  asyncData (context) {
    return context.app.$axios.$get('/posts/' + context.params.postId + '.json')
      .then(data => {
        return {
          loadedPost: {...data, id: context.params.postId}
        }
      })
      .catch(e => context.error(e))
  },
  methods: {
    onSubmitted (editedPost) {
      this.$store.dispatch('editPost', editedPost).then(() => {
        this.$router.push('/admin')
      })
    }
  }
}
</script>