

# [정보처리기사 089] - 뷰(View) 설계 ★



# **# 뷰(View)**

**1) 개요**

· 뷰는 사용자에게 접근이 허용된 자료만을 제한적으로 보여주기 위한 가상 테이블이다.

· 하나 이상의 기본 테이블로부터 유도된 결과물로, 데이터 보정 작업이나 처리 과정 시험 등 임시 작업을 위한 용도로 활용된다.

· 사용상의 편의성 최대를 위해 조인문의 사용을 최소화 한다.

· 뷰를 생성하면, 뷰 정의가 시스탬 내에 저장되었다가, 쿼리문에서 뷰 이름을 사용할 경우 정의된 기본 테이블로 대체되어 기본 테이블에 대해 실행된다.



**2) 특징 + 장단점**

**[특징]**

​    · 기본 테이블로부터 유도되었기 때문에 기본 테이블과 같은 구조를 갖고, 조작도 같다.

​    · 뷰는 가상 테이블이기 때문에 물리적으로 구현되어 있지 않지만, 데이터의 논리적 독립성은 제공한다.

​    · 필요한 데이터만 뷰로 정의해서 처리할 수 있어서 관리가 용이하고 명령문이 간단하다.

​    · 뷰를 통해서만 데이터에 접근하게 하면, 뷰에 나타나지 않은 데이터를 안전하게 보호하는 기법으로 사용할 수 있다.

​    · 기본 테이블의 PK를 포함한 열(속성) 집합으로 뷰를 구성해야만 삭입/삭제/갱신 연산이 가능하다.

​    · 정의된 뷰는 다른 뷰 정의에 기초가 될 수 있다.

​    · 뷰가 정의된 기본 테이블이나 뷰를 삭제하면, 그 테이블/뷰를 기초로 정의된 다른 뷰도 자동적으로 삭제된다.

**[장점]**

​    · 논리적 데이터 독립성을 제공하고 접근 제어를 통한 자동 보안을 제공한다.

​    · 동일 데이터에 대해 동시에 여러 사용자의 다른 응용이나 요구를 지원해준다.

​    · 사용자의 데이터 관리를 간단하게 해준다.

**[단점]**

​    · 독립적인 인덱스를 가질 수 없다.

​    · 뷰 정의를 변경할 수 없다.

​    · 뷰로 구성된 내용에 대한 삽입/삭제/갱신 연산에 제약이 따른다.



**3) 설계**

**[순서]**

​    1) 대산 테이블 선정

​        \- 외부 시스템과 인터페이스를 관려하는 테이블

​        \- CRUD 매트릭스를 통해 여러 테이블이 동시에 자주 조인되고 접근되는 테이블

​        \- SQL문 작성 시 거의 모든 문장에서 인라인 뷰* 방식으로 접근되는 테이블

​            cf) Inline View : From 절 안에 사용되는 서브 쿼리

​    2) 대상 컬럼 선정

​        \- 보안을 유지해야 하는 컬럼은 주의해서 선별

​    3) 정의서 작성

​        \-  참고 : https://blog.naver.com/ydg0620/220527513076

**[설계 시 고려사항]**

​    · 테이블 구조가 단순화 될 수 있도록 반복적으로 조인을 설정하여 사용하거나 동일한 조건절을 사용하는  테이블을 뷰로 생성한다.

​    · 동일 테이블이더라도 업무에 따라 테이블을 이용하는 부분이 달라질 수 있으므로 사용할 데이터를 다양한 관점에서 제시한다.

​    · 데이터 보안 유지를 고려한다.