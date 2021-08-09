<template>
  <div class="imageContainer">
    <img class="mainImage" :src="article.img" />
  </div>
</template>

<script>
export default {
  name: "MainBigImage",
  props : {
    article : Object
  }
}
</script>

<style scoped>
.imageContainer {
  margin-bottom: 50px;
  display: flex;
  justify-content: center;
  width: 100%;
}
.mainImage {
    width: 1460px;
  height : 766px;

}
</style>
