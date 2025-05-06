---
layout: post
title:  React Deep Dive 를 읽고
categories: [react]
tags: [react]
fullview: true
comments: true
---

저번 JavaScript에 이어 React Deep Dive라는 책을 읽게 되었다.
예상대로 몰랐던 내용이 많았으며, 이 중 몇가지를 정리하여 기록하고자 한다.

### 1. useState의 게으른 초기화

```javascript
const [value, setValue] = useState(expensiveComputation()); // ❌ 매 렌더마다 실행됨
```
이런식으로 연산비용이 많이드는 작업은 렌더링시 단 한번만 초기화값으로 설정되게 할수 있다.

### 2. useEffect는 클라이언트사이드에서만 실행된다.

### 3.useContext는 상태기반 라이브러리랑 다르다.
상태기반 라이브러리의 조건으론
-상태를 기반으로 다른 상태를 만들수 있어야함
-필요에따라 이러한 상태를 최적화할 수 있어야함
하지만 useContext는 단순 전역 값 전달 도구일 뿐이다.

### 4. useLayoutEffect
useEffect이전에 수행되며, dom 계산후 화면에 paint전에 할 작업이 있을때 사용한다.
단 동기적으로 수행되어 랜더링을 지연하므로 잘 사용하지 않는다.


### 5. 리액트 훅이 최상위,에서만 호출가능한이유
fiber node링크드리스트 순서 정합성 유지를 위해 최상위에서만 사용가능하다.
node 링크드리스트를 함수 이름이아닌 순서로 저장해두기 때문

### 6. <Link>태그
서버사이드, 클라이언트사이드 랜더의 장점을 둘다 합친것(next router 사용)
미리 ssr방식으로 pre-fetch해두고 이후 해당 링크 클릭하면 csr방식으로 페이지를 로드

### 7. useStore의 작동 원리
개별적으로 state를 관리하고, 각각의 컴포넌트를 리랜더할 callback을 Set에저장,
이를 수행하므로써 컴포넌트 랜더링을 유도한다.

### 8. findBy
getBy와 유사하나 비동기 promise 를 반환한다.

### 9. useTransition
상태 업데이트 자체를 나중에 하게하는 함수, 무거운작업을 비동기처리하게 해준다.

```javascript
const [input, setInput] = useState('');
const [list, setList] = useState([]);
const [isPending, startTransition] = useTransition();

const handleChange = (e) => {
  const value = e.target.value;
  setInput(value); // 즉시 업데이트 (빠른 반응)

  startTransition(() => {
    // 무거운 작업은 비동기 처리
    const filtered = heavyFilter(bigData, value);
    setList(filtered);
  });
};

```
### 10. useDeferredValue 
상태 업데이트는 바로 하지만 랜더링을 늦출때 사용한다.

```javascript
const [input, setInput] = useState('');
const deferredInput = useDeferredValue(input);

return (
  <>
    <input value={input} onChange={(e) => setInput(e.target.value)} />
    <SlowComponent input={deferredInput} />
  </>
);


```

### 11. useSyncExternalStore
외부 document, window값 등과 관련된 상태관리필요할때 사용한다.

### 11. 이외 최적화, 보안 관련 팁
- 최적화시 long task를 중점으로 분석한다(light house를 통해 long task확인가능)
- rendering block: &lt;head&gt; 내부 스타일은 다운로드 후에 랜더되므로 이 속성을 수정해준다.

- 보안상 문제가 예상된다면 iframe으로 해당 프로젝트를 불러오기 금지 시킬수 있다.