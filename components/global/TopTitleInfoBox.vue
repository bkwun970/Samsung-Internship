<template>
  <div class="titleContainer">
    <h1>{{ article.title }}</h1>
    <p class="description">{{ article.description }}</p>
  </div>
</template>

<script>
export default {
  name: "TopTitleInfoBox",
  props : {
    article : Object
  }
}
</script>

<style scoped>
.description {
  font-size: 20px;
}

.titleContainer {
  width: 80%;
  height: 200px;
  border-bottom: solid black 1px;
}
</style>
