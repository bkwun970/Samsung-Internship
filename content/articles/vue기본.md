---
title: vue 기본
description: vue의 기본문법/구조
img: /sampleImage.jpeg
alt: my first blog post
author:
  name: Andrew Byoungil Kwun
  bio: Georgia Tech

---


# vue 기본 07.09.2021

##### v-if
##### v-bind (:)
##### v-on (@)
######  @click.stop : event bubbling 을 막아줌

- frog.vue
```
<template>
<div class="water">
  <div class="leaf" @click.stop="frogClicked">
    {{age}}
    {{view}}
  </div>
  <div class="leaf"></div>
  <div class="leaf" v-if="view"></div>
</div>
</template>

<script>
export default {
  name: "Frog",
  props: {
    age: Number
  },

  data : function(){
    return {
      view : true
    }
  },
  methods: {
    frogClicked() {
      console.log('frog1 is clicked~')
    }
  },

}


</script>

<style scoped>
.water {
  display : flex;
  width : 100%;
  height : 200px;
  background-color: skyblue;
  justify-content: space-between;
}

.leaf {
  width : 200px;
  height : 190px;
  border : 5px solid black;
background-color: greenyellow;
}
</style>
```

- App.vue
```
<template>
  <div id="app" @click="allClicked">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Frog :age="age" >

    </Frog>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Frog from './components/Frog.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Frog
  },
  data : function(){
    return {
      age : 20
    }
  },
  methods: {
    allClicked() {
      console.log('Hello~')
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

```
