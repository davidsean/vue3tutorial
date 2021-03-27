<template>
  <div>
      THIS IS PAGE HOME
      <div v-for="thread in threads" v-bind:key="thread.id">
        <h2> {{ thread.title }} </h2>
        <div v-for="postId in thread.posts" v-bind:key="postId">
          <p><b> {{ userById(postById(postId).userId).name }} </b></p>
          <p> {{ postById(postId).text }} </p>
        </div>
      </div>
  </div>
</template>

<script>
import sourceData from '@/data.json'

export default {
  data () {
    return {
      threads: sourceData.threads,
      posts: sourceData.posts,
      users: sourceData.users
    }
  },
  methods: {
    userById (userId) {
      return this.users.find(u => u.id === userId)
    },
    postById (userId) {
      return this.posts.find(p => p.id === userId)
    }
  }

}

</script>

<style>

</style>
