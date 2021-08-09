<template>
<div class="allContainer">
  <MainBigImage :article="article"/>

  <div class="topInfoContainer">
    <TopTitleInfoBox :article="article"/>
    <ExtraInfo :article="article"/>
  </div>
  <div class="articleContainer">
    <article>
      <nuxt-content :document="article" />
      <prev-next :prev="prev" :next="next" />
      <AppSearchInput class="appSearch"/>
    </article>
    <div class="leftSpace"/>
  </div>


</div>


</template>

<script>
import MainBigImage from "../../components/MainBigImage";
import TopTitleInfoBox from "../../components/global/TopTitleInfoBox";
import ExtraInfo from "../../components/ExtraInfo";
export default {
  components: {ExtraInfo, TopTitleInfoBox, MainBigImage},
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    const [prev, next] = await $content('articles')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      article,
      prev,
      next
    }
  }
}
</script>

<style>
.allContainer {
  padding:40px;
}

h1 {
  font-size: xxx-large;
}

.topInfoContainer {
  display: flex;
}

.nuxt-content h1 {
  font-size : 40px;
}

.nuxt-content {
  font-size: 20px;
}

article {
  width: 80%;
}
leftSpace {
  width: 20%;
}
.articleContainer {
  display: flex;

}
.appSearch {
  margin-top: 30px;
}
</style>
