<template>
  <div>
    <h3 class="headline">
      {{ loadedPost.title }} <br>
      {{ loadedPost.description }} <br>
      {{ loadedPost.category }} <br>
    </h3>
    <v-avatar
      size="155"
    >
      <img :src="loadedPost.postImage">
    </v-avatar>
  </div>
</template>

<script>
export default {
  asyncData (context) {
    return context.app.$axios.$get('/posts/' + context.params.id + '.json')
      .then(data => {
        return {
          loadedPost: data
        }
      })
      .catch(e => context.error(e))
  }
}
</script>

