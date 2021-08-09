<template>
  <div class="prevNNext">
    previous  :
    <NuxtLink
      v-if="prev"
      :to="{ name: 'blog-slug', params: { slug: prev.slug } }"
      class="prev"
    >
     {{ prev.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
    next :
    <NuxtLink
      v-if="next"
      :to="{ name: 'blog-slug', params: { slug: next.slug } }"
      class="next"
    >
     {{ next.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
  </div>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null
    },
    next: {
      type: Object,
      default: () => null
    }
  }
}
</script>
<style>
.prevNNext {
  border-top: solid black 1px;
  margin-top: 50px;
  padding-top : 20px;
}
.prev {
  margin-right: 50px;
}
</style>
