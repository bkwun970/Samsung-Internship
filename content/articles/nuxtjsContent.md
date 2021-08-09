---
title: nuxtjsContent
description: nuxt.js content에 대해서
img: /nuxtcontent.png
alt: my first blog post
author:
  name: Andrew Byoungil Kwun
  bio: hello :)

---

# nuxt/content module
writes in content/ directory and fetch Markdown, JSON, YAML, XML,
and CSV files through a MongoDB like API, acting as a Git-based Headless CMS.

- 시작하기전에....
  - npm install @nuxt/content
  
- content/articles directory 안에 md file들을 넣어준다

##### content display
- we can use dynamic page by prefixing the page with an underscore('_')
- example : created _slug.vue
- use the params.slug variable provided by vue router to get the name of each article
```
<script>
  export default {
    async asyncData({ $content, params }) {
      const article = await $content('articles', params.slug).fetch()

      return { article }
    }
  }
</script>
```
