<template>
  <div>
    <AdminPostForm @submit="onSubmitted" />
  </div>
</template>

<script>
import AdminPostForm from '@/components/Admin/AdminPostForm'

export default {
  middleware: ['check-auth', 'auth'],
  components: {
    AdminPostForm
  },
  methods: {
    onSubmitted (postData) {
      this.$store.dispatch('addPost', postData).then(() => {
        this.$router.push('/admin')
      })
    }
  }
}
</script>

