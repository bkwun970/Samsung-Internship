<template>
  <div class="authorContainer">
    <author :author="article.author" />
    <p>{{ formatDate(article.updatedAt) }}</p>
  </div>
</template>

<script>
export default {
  name: "ExtraInfo",
  props : {
    article : Object
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
  }
}
</script>

<style scoped>

.authorContainer {
  width : 20%;
  height: 200px;
  display: flex;
  flex-direction: column;
}

</style>
