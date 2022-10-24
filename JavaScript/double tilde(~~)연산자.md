
### 1. Math.floor() 대신 사용될 수 있다.

숫자에 `~`연산을 하게되면서 소수점들은 버려지게된다. 즉, `~~`를 활용하면 `Math.floor()` 처럼 활용할 수 있다.

`Math.floor()` 대신에 활용하는데 장점과 단점이 있다.

### 장점

속도 측면에서 `~~`가 빠르다고 한다. [The Mysterious Double Tilde (~~) Operation](https://dev.to/asadm/the-mysterious-double-tilde-operation-mih) 이 블로그에 보면 크롬, Safari,iPhone XS 각각`Math.floor`, `~~`, `parseInt` 의 속도를 비교한 결과가 있다.

결과는 `~~` , `Math.floor`, `parseInt` 순으로 `~~`가 가장 빠른 퍼포먼스를 보여줬다.

### 단점

코드에 `~~`가 덕지덕지 있다고 상상해보자. 이해가 쉽지 않을 것이다. 복잡한 코드 또는 협업하는 과정에서는 가독성이 좋지 않기 때문에 사용하지 않는편이 좋을 것 같다.

### 2. undefined 또는 null을 0으로 변환할 때 사용될 수 있다.

위의 경우가 언제쓰일까 싶지만 `undefined+3 => NaN` 이런 상황이 자주 있었을 것이다.

예시 하나만 작성해 보자.배열[1,1,1,2,2,3,3,3,3]을 각 숫자가 몇개인지 객체에 저장해보자.

```
const arr = [1,1,1,2,2,3,3,3,3]
const obj1 = {}

arr.forEach(v=>{
  if(obj1[v]) obj1[v]+=1
  else obj1[v]=1
})
//obj1 {1: 3, 2: 2, 3: 4}
```

위와같이 obj에 key값이 있는지 확인해주는 작업이 필요하다. 그렇지 않으면 NaN이 나올 것이다.

그럼 `~~`를 활용해 다시 코드를 작성해보자.

```
const obj2 = {}
arr.forEach(v=>obj2[v]= ~~obj2[v]+1)
//obj2 {1: 3, 2: 2, 3: 4}
```

`undefined`가 나올 수 있는 상황을 `~~`연산자를 이용해서 간단하게 해결할 수 있다. 알고리즘 답안을 보면서 배운 연산자인 만큼 알고리즘에서 유용하게 사용할 수 있을 것 같다.
