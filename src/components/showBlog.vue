<template>
  <div id="single-blog">
    <h1>{{ blog.title }}</h1>
    <article>{{ blog.content }}</article>
    <p>Author: {{ blog.author }}</p>
    <ul>
      <li v-for="cat in blog.categories">{{ cat }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id, 
      blog: {}
    }
  },
  created() {
    this.$http.get('https://vue-blog-1699f.firebaseio.com//posts/' + this.id + '.json').then(function(data){
      return data.json()
    }).then(function(data){
      this.blog = data
    })
  }
}

</script>

<style lang='sass'>
#single-blog
  max-width: 960px
  margin: 0 auto
  padding: 20px
  background: #eee
  border: 1px dotted #aaa

</style>