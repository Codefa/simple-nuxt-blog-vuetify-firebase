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
      profileImage: 'https://scontent.fcok1-1.fna.fbcdn.net/v/t1.0-9/19113766_1097897530354278_8129712611027682718_n.jpg?_nc_cat=0&oh=c32dda46cb47c4091f08fc5252c2d00f&oe=5BC847D3'
    }
  }
}
</script>