# [정보처리기사 022] - 객체지향(Object-Oriented) ★



# **# 객체지향 개요**

소프트웨어를 개발할 때 객체들을 조립해서 작성할 수 있는 기법을 말한다.



객체지향 기법은 구조적 기법의 문제점으로 인한 소프트웨어 위기 해결책으로 사용된다.

여기서 **구조적 기법**은 절차에 근간을 두고 하나의 커다란 작업을 여러 작은 작업으로 분할하고, 분할된 각 소작업을 수행하는 모듈을 작성한다. 그 다음 하나로 통합해 최종 작업을 수행하는 하나의 완벽한 프로그램을 작성하는 방법이다.

이는 유지보수를 고려하지 않고 개발 공정에 집중하기 때문에 추가 요구사항을 반영하기 어렵고, 재사용이 어렵다는 문제점이 있다.



**객체지향**은 소프트웨어의 재사용 및 확장이 용이하고 고품질의 소프트웨어를 빠르게 개발할 수 있고 유지보수가 쉽다.

복잡한 구조를 단계적, 계층적으로 표현하고, 멀티미티어 데이터 및 병렬 처리를 지원한다.



# **# 구성 요소와 개념**

**1) 객체(Object)**

​        · 데이터와 데이터를 처리하는 함수를 캡슐화한 하나의 소프트웨어 모듈이다.

​        · **데이터** : 객체가 가지고 있는 정보로 속성, 상태, 분류, 변수, 상수 등을 나타낸다.

​        · **함수** : 객체가 수행하는 기능으로 데이터를 처리하는 알고리즘이다.

​        · 객체는 독립적으로 식별 가능한 이름을 갖는다.

​        · 객체가 가질 수 있는 조건을 상태라고 하는데, 상태는 시간에 따라 변한다.

​        · 객체와 객체는 상호 연관성에 의한 관계를 형성한다.

​        · 객체가 반응할 수 있는 집합을 행위라고 하며, 객체는 행위의 특징을 나타낸다.

 <img src='/img/022_01.png'>

<center>
<center>* 출처 : http://jidum.com/jidums/view.do?jidumId=300</center>

**2) 클래스(Class)**

​        · 공통된 속성과 연산 행위를 갖는 객체의 집합으로, 객체의 일반적인 타입을 뜻한다.

​        · 즉, 클래스는 각 객체들이 갖는 속성과 연산을 정의하고 있는 틀이다.

​        · 클래스에 속한 각각의 객체를 인스턴스(Instance)라고 하며, 클래스로부터 새로운 객체를 생성하는 것을 인스턴스화(Instantitaion)라고 한다.

​        · 같은 클래스에 속한 객체들은 공통된 속성과 행위를 갖고 있으며, 그 속성에 대한 정보가 다르기 때문에 동일한 기능을 하는 객체가 여러가지가 된다.

​        · **슈퍼 클래스**는 특정 클래스의 상위(부모) 클래스이고, **서브 클래스**는 하위(자식) 클래스를 의미한다.

**3) 캡슐화(Encapsulation)**

​        · 데이터와 함수를 하나로 묶는 것을 의미하고, 캡슐화 된 객체는 재사용이 용이하다.

​        · 캡슐화 된 객체는 인터페이스를 제외한 세부 내용이 정보 은닉되어 외부에서의 접근이 제한되며, 외부 모듈의 변경으로 인한 파급효과가 적다.

​        · 객체들 간의 상호작용에서 상대 객체의 세부 내용은 알 필요가 없으므로 인터페이스가 단순해지고, 객체 간 결합도가 낮아진다.

**4) 상속(Inheritance)**

​        · 사전에 정의된 상위 클래스의 모든 속성과 연산을 하위 클래스가 물려받는 것이다.

​        · 하위 클래스는 상위 클래스의 모든 속성과 연산을 자신의 클래스에서 다시 정의하지 않고서도 사용할 수 있다.

​        · 또한, 상위 클래스로부터 상속받은 속성과 연산에 추가적으로 새로운 속성과 연산을 첨가하여 사용할 수도 있다.

​        · 상위 클래스의 속성과 연산을 사용하기 때문에 객체와 클래스의 재사용을 높인다.

​        · **다중 상속**(Multiple Inheritance) : 한 개의 클래스가 두 개 이상의 상위 클래스로부터 속성과 연산을 상속받는 것을 뜻한다.

**5) 다형성(Polymorphism)**

​        · 메시지에 의해 객체가 연산을 수행하게 될 때 하나의 메시지에 대해 각각의 객체가 가지고 있는 고유한 방법으로 응답할 수 있는 능력을 의미한다.

​        · 즉, 하나의 메시지에 대해 여러 가지 형태의 응답이 있다는 것을 의미한다.

​        · 객체들은 동일한 메소드명을 사용하며 같은 의미의 응답을 한다.

​        · 응용 프로그램 상에서 하나의 함수나 연산자가 두 개 이상의 서로 다른 클래스의 인스턴스들을 같은 클래스에 속한 인스턴스처럼 수행할 수 있도록 하는 것이다.