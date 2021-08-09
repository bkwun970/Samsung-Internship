---
title: priorityQueue
description: priority queue (java)
img: /pq.jpeg
alt: my first blog post
author:
  name: Andrew Byoungil Kwun
  bio: Georgia Tech

---

# 우선순위 큐(Priority Queue)

-  큐는 원래 들어간 데이터가 FIFO(First in First out) 식으로 먼저 들어간 데이터가 먼저 나오는 구조이다.
- 우선순위 큐는 우선순위를 정하고 우선순위가 가장 높은 데이터가 가장 먼저 나오게된다.

### 우선 순위 변경 방법 (객체)
- ball이라는 객체가 있을때, 우선순위를 바꾸는 방법
```
class Ball implements Comparable<Ball>{
    int size;
    int color;
    public Ball(int size, int color) {
        this.size = size;
        this.color = color;
    }
    
     @Override
    public int compareTo(Ball o) {
        if(this.size == o.size) {
            return Integer.compare(this.color, o.color);
        }
        return Integer.compare(this.size, o.size);
    }
}
```
- 자바에서는 우선순위큐를 사용할때(객체) 큐에 저장할 객체는 Comparable 인터페이스를 사용해야한다.
- compareTo 메서드를 override 하면 된다.
