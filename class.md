# class 란?

- class는 객체(Object)와 관련이 있다.
- 클래스는 객체를 생성하기 위한 템플릿이다.
- 클래스를 통해 원하는 구조의 객체 틀을 짜놓고 비슷한 모양의 객체를 공장처럼 찍어낼 수 있다.(클래스 = 붕어빵 기계, 그리고 객체 = 붕어빵)
- 객체를 만들어내기 위한 설계도 혹은 틀이며,연관되어 있는 변수와 메서드의 집합이다.
- 클래스는 말 그대로 하나의 그룹, 또는 묶음이라고 생각하면 편하다.가령, '이름', '성별', '나이' 라는 속성이 있고, '이름 부르기', '개명하기', '나이 계산하기' 등의 메서드 (기능) 이 있다고 하자. '
이름' 속성과 '이름 부르기', '개명하기' 메서드를 하나로 그룹화하여 관리하는 것이 이들을 개별적으로 분산시키는 것보다 훨씬 작업에 용이할 것이다. 
이렇게 비슷한 기능을 하거나 속성을 갖는 요소들을 하나의 객체에 담아 사용하고 관리할 수 있도록 하는 자료구조를 클래스라고 한다. 
- 클래스는 함수다. 클래스는 값처럼 사용할 수 있는 일급 객체다.

### 일급객체란 무엇일까?
> - 일급객체(First-class Object)란 다른 객체들에 일반적으로 적용 가능한 연산을 모두 지원하는 객체를 가리킨다.
> - 변수에 할당(assignment)할 수 있다.
> - 다른 함수를 인자(argument)로 전달 받는다.
> - 다른 함수의 결과로서 리턴될 수 있다.

## 자바스크립트와 클래스의관계
- 자바스크립트는 "프로토타입 기반 객체지향 언어"이다.이말은 클래스가 필요없는 객체지향 언어라는 뜻이다.ES5시절까지만 해도 생성자 함수와 프로토타입을 통해 상속을 구현했지만,ES6에서 도입된 "클래스"개념덕분에 객체지향 프로그래밍을 훨씬 간편하게 구현할 수 있게 되었다.

### 기존ES5에도 객체지향을 구현가능했다면 굳이 새로 클래스를 도입 한 이유
- 생성자 함수도 프로토타입 기반의 인스턴스를 생성하기는 하나,제공하지 않는 여러 기능으로 인해 객체지향을 완전히 구현하는 데에는 제약이 있었기 때문이다.
> new 연산자 없이 호출 : 생성자 함수는 일반 함수로 호출되지만,클래스는 오류가 난다.
> extends 와 super:생성자 함수에는 제공되지 않지만, 클래스에는 제공된다.
> 호이스팅 : 생성자 함수에는 호이스팅이 발생하나, 클래스에는 발생하지 않는다.
> strict mode : 생성자 함수에는 암묵적으로 지정되지 않지만,클래스에는 암묵적으로 지정된다.
> [[Enumerable]] : 클래스의 constuctor,프로토타입 메서드, 정적 메서드는 모두 [[Enumerable]]의 값이 false다.
- 클래스는 생성자 함수보다 상속 관계 구현을 더욱 명료하게 하기 때문데, 객체지향을 더욱 견고하게 만든다고 하기도 한다.



## 클래스의 정의와 메서드

> Pascal Case사용
```js
class Per{
    code...
}
```

> new 연산자사용
```js
const a = new Per();
// new 연산자 없을 경우
const b = per();


class User {
  constructor({name}){
    this.name = name;
  }
  welcome(){
    console.log(`Welcome ${this.name}`)
  }
}
let user1 = new User({name : 'Bob'});
user1.welcome(); // 'Welcome Bob'

```
# 자바스크립트 클래스 문법

> constructor는 인스턴스를 생성하고 클래스 필드를 초기화하기위한 특수한 메서드다.
> constructor는 클래스 안에 한개만 존재할 수 있다. 2개이상 있을경우 Syntax Error발생하니 주의
```js
class Per {

}
let lkj = new Per();
console.log(lkj);



class Person {
   height = 180; // 인스턴스 변수
   // constructor는 이름을 바꿀 수 없다.
   constructor(name, age) {
    // this는 클래스가 생성할 인스턴스를 가리킨다.
    this.name = name;
    this.age = age;
   }
}

let lkj = new Person('kj', 20);
console.log(lkj.name); // kj
console.log(lkj.age); // 20
console.log(lkj.height); // 180
```
- 클래스 필드의 선언과 초기화는 반드시 constructor내부에서 실시한다.
- constructor 내부에선언란 클래스 필드는 클래스가 생성할 인스턴스에 바인딩 된다.

## class 메소드 정의

```js
class C{
    add(x,y) {
        return x+y;
    }
    su(x,y){
        return x-y;
    }
}
let calc = new C();
calc.add(1,2) // 3
calc.su(5,2) // 3
```

## Getter / Setter
> 클래스 내에서 Getter 혹은 Setter를 정의하고 싶을 때는 메소드 이름앞에 get또는 set을 붙여주면 된다.
> 

```js
class Acc {
  constructor() {
    this._balance = 0;
  }
  get balance() {
    return this._balance;
  }
  set balance(newBalance) {
    this._balance = newBalance;
  }
}

const account = new Acc();
account.balance = 10000;
account.balance; // 10000
```

> 정적 메서드 (Static)
- 정적 메서드는 클래스의 인스턴스가 아닌 클래스 이름으로 곧바로 호출되는 메서드이다.
- static 키워드를 메소드 이름 앞에 붙여주면 해당 메소드는 정적 메소드가 된다.
- 인스턴스를 생성하지 않아도 호출할 수 있는 메서드
```js
class Per {
   constructor({ name, age }) { // 생성자 인스턴스
      this.name = name;
      this.age = age;
   }
   static static_name = 'STATIC'; // 정적 인스턴스

   getName() { // 인스턴스(프로토타입) 메소드
      return this.name;
   }
   static static_getName() { // 정적 메소드
      return this.static_name;
   }
}
const per = new Per({ name: 'jeff', age: 20 });
per.getName(); 
Per.static_getName(); 



class Per {
   constructor({ name, age }) {
      this.name = name;
      this.age = age;
   }

   // 이 메소드는 정적 메소드
   static static_sumAge(...people) {
      /*
         함수 파라미터 people를 전개연산자 ...people를 통해 배열로 만듬
         [ {"name": "윤아준", age": 19}, { "name": "신하경","age": 20 }]   
      */

      // 그리고 각 객체의 age값을 얻어와 합침
      return people.reduce((acc, per) => acc + per.age, 0);
   }
}

const per1 = new Per({ name: '윤아준', age: 19 });
const per2 = new Per({ name: '신하경', age: 20 });

Per.static_sumAge(per1, per2); 
```

> 정적 메서드가 바인딩 된 클래스는 인스턴스의 프로토타입 체인 상에 존재하지 않는다.

## 클래스 호이스팅
> 클래스는 함수로 평가된다.
> 클래스 선언문으로 정의한 클래스는 함수 선언문과 같이 소스코드 평가 과정, 즉 런타임 이전데 먼저 평가되어 함수 객체를 생성한다.

## 인스턴스 생성
> 클래스는 생성자 함수이며 new 연산자와 함께 호출되어 인스턴스를 생성한다.
> 함수는 new 사용 여부에 따라 일반 함수나 생성자 함수로 호출되지만 클래스는 생성자 함수이므로 반드시 new 연산자와 함께 호출해야 한다.
> 클래스 표현식으로 정의된 클래스의 경우 다음처럼 기명 클래스 표현식의 클래스 이름으로 인스턴스를 생성할 수 없다.

# 객체지향 설계 5원칙 SOLID
- SRP(Single Responsibility Principle): 단일 책임 원칙
- OCP(Open Closed Principle): 개방 폐쇄 원칙
- LSP(Listov Substitution Principle): 리스코프 치환 원칙
- ISP(Interface Segregation Principle): 인터페이스 분리 원칙
- DIP(Dependency Inversion Principle): 의존 역전 원칙
>
#### 1. SRP(Single Responsibility Principle): 단일 책임 원칙
> SRP란 Single Responsibility Principle 라는 단일 책임 원칙을 의미하며 말 그대로 단 하나의 책임을 가져야 한다는 것을 의미한다. 여기서 말하는 책임의 기본 단위는 객체를 의미하며 하나의 객체가 하나의 책임을 가져야 한다는 의미이다. 그렇다면 책임은 무엇인가? 객체지향에 있어서 책임이란 객체가 할 수 있는 것 과 해야 하는 것 으로 나뉘어져 있다. 즉 하나의 객체는 자신이 할 수 있는 것과 해야하는 것만 수행할 수 있도록 설계되어야 한다는 법칙이다.
클래스는 그 책임을 완전히 캡슐화해야 함을 말한다.

#### 2. OCP(Open Closed Principle): 개방 폐쇄 원칙
> 개방 폐쇄 원칙이란 간단하게 말해 기존의 코드를 변경하지 않으면서 기능을 추가할 수 있도록 설계되어야 한다는 뜻이다. OCP에서 중요한 것은 요구사항이 변경되었을 때 코드에서 변경되어야 하는 부분과 변경되지 않아야하는 부분을 명확하게 구분하여, 변경되어야 하는 부분을 유연하게 작성하는 것을 의미한다. 또한 확장에는 유연하게 반응하며 변경은 최소화하는 것을 의미한다.

#### 3. LSP(Listov Substitution Principle): 리스코프 치환 원칙
> 리스코프 치환 원칙은 단순하게 풀어보면 LSP는 일반화 관계에 대한 이야기이며 자식 클래스는 최소한 자신의 부모 클래스에서 가능한 행위를 수행할 수 있어야 한다는 의미이다. 좀 더 쉽게 이야기하면 LSP를 만족하면 프로그램에서 부모 클래스의 인스턴스 대신에 자식 클래스의 인스턴스로 대체해도 프로그램의 의미는 변화되지 않는다. 이를 위해 부모 클래스와 자식 클래스의 행위는 일관되어야 한다.

#### 4. ISP(Interface Segregation Principle): 인터페이스 분리 원칙
> Interface Segregation Principle 인터페이스 분리 원칙은 클라이언트에서는 클라이언트 자신이 이용하지 않는 기능에는 영향을 받지 않아야 한다는 내용이 담겨 있다. 예를 들어 복합기를 이용하는 다양한 사람을 생각해보자. 복사를 하고 싶은사람과 프린트를 하고 싶은사람, 팩스를 보내고 싶은 사람은 복합기가 다양한 기능을 제공하고 있지만 본인이 원하는 기능만이 작동하면 되며 자신이 이용하지 않는 기능에 대해서는 영향을 받지 않는다. 이러한 기능을 제공하고 싶을 때 사용되는 것이 ISP이며 사용 방법은 범용의 인터페이스를 만드는 것이 아니라 클라이언트에 특화된 인터페이스를 사용해야한다. 즉 인터페이스를 클라이언트에 특화되도록 분리시키라는 설계 원칙이라고 할 수 있다.

#### 5. DIP(Dependency Inversion Principle): 의존 역전 원칙
> 고차원 모듈은 저차원 모듈에 의존하면 안 된다. 이 두 모듈 모두 다른 추상화된 것에 의존해야 한다.
추상화된 것은 구체적인 것에 의존하면 안 된다. 구체적인 것이 추상화된 것에 의존해야 한다.
자주 변경되는 구체(Concrete) 클래스에 의존하지 말것.

> 객체지향 프로그래밍에서 객체는 서로 도움을 주고 받으며 의존 관계를 발생시킨다. Dependency Inversion Principle은 그러한 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 가이드라인을 제공하는 원칙이다.

