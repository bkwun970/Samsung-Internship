---
title: Nuxt.js content Blog 
description: Learning how to use nuxt/content to create a blog
img: /blog.jpeg
alt: my first blog post
author:
  name: Byoungil Kwun
  bio: Georgia Tech
---





## nuxt/content module
writes in content/ directory and fetch Markdown, JSON, YAML, XML,
and CSV files through a MongoDB like API, acting as a Git-based Headless CMS.


- 시작하기전에...
  - npm install @nuxt/content
  
- content/articles directory 안에 md file들을 넣어준다

### content display
- we can use dynamic page by prefixing the page with an underscore('\_')
- example : created \_slug.vue
- use the params.slug variable provided by vue router to get the name of each article
- have access to our content through the context by using the variable $content  
- use asycnData in our page component to fetch our article content before the page has been rendered.
- need to know wich article to fetch -> params.slug(avaiable through the context)
- fetched our content using the await folled by $content. (pass into content what we want to fetch, which is the article folder)

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

- use <nuxt-content /> component to display our content. 
- pass in the variable we returned into the document prop.
- run the dev serer and we can go to the route  http://localhost:3000/blog/my-first-blog-post
```
<template>
  <article>
    <nuxt-content :document="article" />
  </article>
</template>
```
### Default injected variable 
- The nuxt content module gives us access to injected variables that we can access and show in our template.
  - body: body text
  - dir : directory
  - extension : file extension(.md in this example)
  - path : the file path
  - slug : the file slug
  - toc : an array containing our table of contents
  - createdAt : the file creation date
  - updatedAt : the date of the last file update
- We can access all these variables by using the article variable that we created earlier.
- example : inspect article object:
```
<pre> {{ article }} </pre>
```
### if we want to write nicely format the updated date for an article
```
methods: {
formatDate(date) {
    const options = { year: 'numeric', month: 'long', day: 'numeric' }
    return new Date(date).toLocaleDateString('en', options)
    }
}
```

```
<p>Article last updated: {{ formatDate(article.updatedAt) }}</p>
```
### Custom injected variables
- add a block of YAML front matter to the markdown file
- It must be at the top of the file and must be a valid YAML format
- example : 

```
---
title: My first Blog Post
description: Learning how to use @nuxt/content to create a blog
img: first-blog-post.jpg
alt: my first blog post
---
```
- Then, we can access by using our article object variable.

```
<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" />
    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

    <nuxt-content :document="article" />
  </article>
</template>
```

### Styling the markdown content
- can easily add styles to all our elements coming from our markdown file by wrapping them in the nuxt-content class.
```
<style>
  .nuxt-content h2 {
    font-weight: bold;
    font-size: 28px;
  }
  .nuxt-content h3 {
    font-weight: bold;
    font-size: 22px;
  }
  .nuxt-content p {
    margin-bottom: 20px;
  }
</style>
```

- for an example, we can create our InfoBox compoenent(InfoBox.vue)
```
<template>
  <div class="p-4 mb-4 text-white bg-blue-500">
    <p><slot name="info-box">default</slot></p>
  </div>
</template>
```
- then in our markdown, we can use them :
```
  <info-box>
  <template #info-box>
  This is a vue component inside markdown using slots
  </template>
  </info-box>
```

### Adding an Author compoenent with props
- in markdown page,
```
---
author:
name: Benjamin
bio: All about Benjamin
image: https://images.unsplash.com/.....
---
```

- can create Author component
```
<template>
  <div>
    <img :src="author.image" />
    <div>
      <h4>Author</h4>
      <p>{{ author.name }}</p>
      <p>{{ author.bio }}</p>
    </div>
  </div>
</template>
```
- Then in our script tag we can add our props of author which is an object and set required to true.
```
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
```

- To use the component we will need to add it to our markdown and pass in our props.
```
<author :author="author"></author>
```
- in \_slug.vue for example, we can use like : 
```
<author :author="article.author" />
```


### Creating a previous and next component
- In this component we use a v-if inside our NuxtLink component to see if there is a previous blog post and if there is we add a link to it.
- In our component,
```
<template>
  <div class="flex justify-between">
    <NuxtLink
      v-if="prev"
      :to="{ name: 'blog-slug', params: { slug: prev.slug } }"
      class="font-bold text-primary hover:underline"
    >
      {{ prev.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
    <NuxtLink
      v-if="next"
      :to="{ name: 'blog-slug', params: { slug: next.slug } }"
      class="font-bold hover:underline"
    >
      {{ next.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
  </div>
</template>
```
- In our component we pass the props prev and next to makes them available to us on our blog post page.
```
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
```
- now, in our slug.vue, 
```
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
},
```
- now we can use our compoenent :
```
  <prev-next :prev="prev" :next="next" />
  ```
#### List all the blog posts
- we will make a list of all blog posts in our index.vue
```
<script>
  export default {
    async asyncData({ $content, params }) {
      const articles = await $content('articles')
        .only(['title', 'description', 'img', 'slug', 'author'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        articles
      }
    }
  }
</script>
```

```
<template>
  <div>
    <h1>Blog Posts</h1>
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          <img :src="article.img" />
          <div>
            <h2>{{ article.title }}</h2>
            <p>by {{ article.author.name }}</p>
            <p>{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>
```
