<template>
  <div>
    <div class="authorInfoContainer">
      <div class="authorImageContainer">
        <img class="authorImage" src="https://mblogthumb-phinf.pstatic.net/20120821_12/iubesc_1345512925092gH9CS_JPEG/%B0%B3%B1%B8%B8%AE%C1%DF%BB%E7_%C4%C9%B7%CE%B7%CE04.jpg?type=w2"/>
      </div>
      <div>
        <div class="authorName">{{ author.name }}</div>
        <p class="authorInfo">{{ author.bio }}</p>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: {
    author: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
.authorInfo {
  font-size: small;
  margin-top: 2px;
  margin-left: 10px;
}

.authorName {
  margin-left: 10px;

}

.authorImage {
  width: 40px;
  height: 40px;
  border-radius: 100px;
}

.authorInfoContainer {
  display: flex;

}

</style>
