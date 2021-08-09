---
title: Vue Props
description: vue props에 대해서
img: /vueProps.png
alt: my first blog post
author:
  name: Andrew Byoungil Kwun
  bio: Georgia Tech

---

# Vue.js
### Single file components
- template
- script
- style

#### 단일 파일 컴포넌트의 동작 과정
1. 어플리케이션 코드를 자바스크팁트 파일로 번들링
2. 템플릿을 HTML로 렌더링
3. 스타일 삽입

![Vue Component](img/vueComponent.png)

#### props
- 부모 -> 자식 (data)
- 부모에서 import 하고 compoenents 에 추가
```
<script>
import HelloWorld from './components/HelloWorld.vue'
import frog from './components/frog.vue'


export default {
  name: 'app',
  components: {
    HelloWorld,
    frog
  }
}
</script>
```
- 컴포넌트 에서 props 정의
- 문자열 전달 가능
```
<script>


  export default {
    name: 'frog',
    props: {
      age: String
    }
  }
</script>
```
