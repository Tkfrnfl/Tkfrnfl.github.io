---
layout: post
title:  JavaScript Deep Dive 를 읽고
categories: [javascript]
tags: [javascript]
fullview: true
comments: true
---

JavaScript기초가 좀 부족하다고 생각하여 JavaScript Deep Dive라는 책을 읽게 되었다.
예상대로 몰랐던 내용이 많았으며, 이 중 몇가지를 정리하여 기록하고자 한다.

### 1. 함수를 통한 생성자 작성시 return 값은 없어야 한다.

```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;

    // 명시적인 return 없음 (암묵적으로 this 반환)
}
```


### 2. == 은 형변환이 되고, ===은 형변환이 안된채로 비교한다.

### 3. let, const는 TDZ(temporary dead zone)이 발생한다.

### 4. 함수= 일급객체 이다. 
일급객체란, 런타임 생성가능, 함수의 파라미터, 반환값, 자료구조에 저장 이 가능한것을 뜻함 


### 5. 중첩 '함수'(메소드아님)에서의 this: 전역상태의 this를 받아옴, 단, 화살표 함수에선 상위 스코프의 this를 받아온다.

### 6. js에서 코드 수행은 실행 컨텍스트 스택에따라 순차적으로 수행된다.

### 7. js는 렉시컬 스코프(정적 스코프)를 따른다. 즉, 선언 되었을때의 기준으로 환경이 구성된다.
이때 클로저 함수를 통해 외부 스코프를 기억하여 접근가능하게 해준다.
### 8. static을 붙인 정적 메소드는 class를 통해서만 호출 가능하다.(this를 사용하지 않는 메소드)

```javascript
class MathUtils {
    static add(x, y) {
        return x + y;
    }
}

// 클래스 이름을 통해 직접 호출
console.log(MathUtils.add(5, 3)); // 8

// 인스턴스를 통해 호출하면 오류 발생
const math = new MathUtils();
console.log(math.add(5, 3)); // TypeError
```


### 9. 비동기함수란, 자바스크립트 엔진의 콜스택과 따로 함수 종료후 태스크큐 에서 관리하여 이벤트 루프를 통해 콜스택에 들어가서 실행되는 구조이다.

### 10. fetch는 404,500 같은 에러를 Error로 반환하지 않는다.(따로 처리해주어야함)


