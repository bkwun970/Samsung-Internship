---
title: Creating a previous & next component
description: learning how to create a prev & next component
img: /next.jpeg.jpg
author:
  name: Andrew
  bio: hello :)
---

# Creating a previous & next component

In this component we use a v-if inside our NuxtLink component to see if there is a previous blog post and if there is we add a link to it. We can print out the title of our article using the prev and next variables as these contain all the information from the article. This means we could create a card with an image and description to show the next and previous article but for this example we will just display the title. If there isn't a previous post we just print an empty span which is useful for styling purposes. We then do the exact same with our next link.


![](../../../Downloads/hello-main%204/Andrew/MD%20files/CreatingNextpage/prev.png)


We can now get our previous and next articles by adding them to our asyncData. We create an array of const with the name prev and next and we await the content from the articles folder. This time we only need the title and the slug so we can chain only() to our await and pass in title and slug.

We can use the sortBy() method to sort our data by the createdAt date in ascending order. We then use the surround() method and pass in the slug from params so that it can get the correct slug for the previous and next posts.

We then return prev and next just like we did with article.


![](../../../Downloads/hello-main%204/Andrew/MD%20files/CreatingNextpage/next.png)
