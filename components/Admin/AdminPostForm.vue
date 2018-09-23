<template>
  <div>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field v-model="editedPost.title" :rules="titleRules" :counter="100" label="Title" required>
      </v-text-field>
      <v-text-field v-model="editedPost.postImage" :rules="[v => !!v || 'PostImage is required']" label="PostImage" required>
      </v-text-field>
      <v-text-field v-model="editedPost.description" :rules="[v => !!v || 'Description is required']" label="Description" required>
      </v-text-field>
      <v-select v-model="editedPost.category" :items="items" :rules="[v => !!v || 'Category is required']" label="Category" required>
      </v-select>
      <v-checkbox v-model="checkbox" :rules="[v => !!v || 'You must agree to continue!']" label="Do you agree?" required>
      </v-checkbox>

      <v-btn :disabled="!valid" @click="submit">
        submit
      </v-btn>
      <v-btn @click="clear">
        clear
      </v-btn>
    </v-form>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: false
    }
  },
  data () {
    return {
      valid: true,
      editedPost: this.post ? { ...this.post } : {
        title: '',
        postImage: '',
        category: null
      },
      titleRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 100) || 'Name must be less than 10 characters'
      ],
      items: [
        'News',
        'VueJS',
        'PHP',
        'Android'
      ],
      checkbox: false
    }
  },
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        this.$emit('submit', this.editedPost)
      }
    },
    clear () {
      this.$refs.form.reset()
    }
  }
}
</script>
