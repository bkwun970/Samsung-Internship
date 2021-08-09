---
title: v-for$emit
description: v-for 과 $emit 에대해서
img: /vueLogo.png
alt: my first blog post
author:
  name: Byoungil Andrew Kwun
  bio: Georgia Tech

---


# v-for
자바의 for each list 돌기랑 비슷하다 (예 : for(int s : Set))
```
<ul id="example-1">
  <li v-for="item in items">
    {{ item.message }}
  </li>
</ul>
```
- 위에는 키를 넣어주지 않아서 오류가 생긴다.
- v-for=((item, index, list) in items " v-bind:key="item.message 
- key꼭 붙여주기!
```
 <ul id="example-1">
      <li v-for="item in items" v-bind:key="item.name">
        <Frog :age="age" >

        </Frog>
      </li>
    </ul>
```

- frogItems : [] list는 Array라고 해도 되고 [] 라고 해도된다
- 부모가 준건 변하게 할수 없다
- {{ }} 자바 스크립트 해석 공간

```
<Frog :age="age" :frogItems="frogItems" ></Frog>
```
- hard coding 으로 만든것 부모에서
```
   <div class="water">
      <Frog :age="frogItems[0].age" :name="frogItems[0].name"></Frog>
      <Frog :age="frogItems[1].age" :name="frogItems[1].name"></Frog>
      <Frog :age="frogItems[2].age" :name="frogItems[2].name"></Frog>
    </div>
```
# $emit (자식 ->부모 이벤트 일어난걸 알린다)
- :age="여기는 자바스크립트 해석공간이다"
- data and propes 내꺼는 접근이 가능하다
- this.$emit(eventname(string), value(아무거나))) 
    - 이벤트 간 연결
  ```
   methods: {
    frogClicked() {
      console.log(`my name is : ${this.name}`)
      console.log(`my name is : ${this.age}`)
      console.log(`my name is : ${this.view}`)
      this.$emit('clicked', this.index)
    }
  },
  ```
  - 이렇게 index를 쓰면 부모에서 index를 써서 배열에 바로 접근 가능하다
  ```
  methods: {
    allClicked(index)  {
      console.log(`${this.frogItems[index].age}`)
    }
  ```
