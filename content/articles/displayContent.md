---
title: Styling markdown contents
description: Learning how to style markdown contents
img: /styleContent.png
author:
  name: Andrew
  bio: hi :)
---

# Styling markdown contents

If we inspect this page we can see that everything written inside our markdown is wrapped inside a div with a class of nuxt-content. That means we can easily add styles to all our elements coming from our markdown file by wrapping them in the nuxt-content class.

![](../../../Downloads/hello-main%204/Andrew/MD%20files/StylingContents/styleMD.png)

All other tags that come from our YAML front matter can be styled as normal either using TailwindCSS or adding css in the style tag.

To use scoped styles with the nuxt-content class you need to use a deep selector: /deep/, ::v-deep or >>>

Our markdown tags are converted into the correct tags which means we now have two "h1" tags. We should now remove the one from our markdown file.


### Adding an Author component with props

An other advantage of the YAML properties is that we can make them available to our component through props. For example, we can have an about the author component and if we have guest bloggers the author will change. In our markdown file we can add a new object to our frontmatter which contains the author's name and bio and image.

![](../../../Downloads/hello-main%204/Andrew/MD%20files/StylingContents/authorWithContents.png)


* Putting the component here means we will have to repeat it for every article. In this case it would be better to add it directly to the slug page. We will need to change the author prop to article.author.
  ![](../../../Downloads/hello-main%204/Andrew/MD%20files/StylingContents/putComponents.png)
