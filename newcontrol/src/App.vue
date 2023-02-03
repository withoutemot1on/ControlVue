<template>
  <div class="container column">
    <app-form @block-added="addBlock"></app-form>
    <app-view :blocks="blocks"></app-view>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <app-comments v-else :comments="comments" @load-comments="loadComments"></app-comments>
  </div>
</template>

<script>


import AppLoader from './AppLoader.vue'
import AppForm from './AppForm.vue'
import AppView from './AppView.vue'
import AppComments from './AppComments.vue'
export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    async loadComments() {
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.loading = false
    },
      addBlock(block) {this.blocks.push(block)}
  },
  components: { AppForm, AppView, AppComments,AppLoader }
}
</script>
