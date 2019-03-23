<template>
  <div>
    <v-container fluid>
      <v-layout row wrap>
        <PostPreview v-for="post in posts"
        :key="post.id"
        :id="post.id"
        :is-admin="isAdmin"
        :postImage="post.postImage"
        :title="post.title"
        :description="post.description"
        :category="post.category" />
      </v-layout>
    </v-container>
  </div>
</template>


<script>
import PostPreview from '@/components/Posts/PostPreview'

export default {
  components: {
    PostPreview
  },
  props: {
    isAdmin: {
      type: Boolean,
      default: false
    },
    posts: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      profileImage: 'https://cdn.vuetifyjs.com/images/cards/sunshine.jpg'
    }
  }
}
</script>
