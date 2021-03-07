

# [정보처리기사 113] - ORM(Object-Relational Mapping) ☆



# **# ORM**

**개요**

· 객체 지향 프로그래밍의 객체(Object)와 관계형 DB의 데이터를 연결하는 기술

· 객체 지향 프로그래밍에서 사용할 수 있는 가상의 객체 지향 DB를 만들어 프로그래밍 코드오와 데이터를 연결

· ORM으로 생성된 가상의 객체 지향 DB는 프로그래밍 코드 또는 DB와 독립적이므로 재사용 및 유지보수가 용이

· ORM은 SQL 코드를 직접 입력하지 않고, 선언문이나 할당 같은 부수적인 코드가 생략되기 때문에 직관적이고 간단하게 데이터를 조작할 수 있다.



**ORM 프레임워크**

· JAVA : JPA, Hibernate, EclipseLink, DataNucleus, Ebean 등

· C++ : ODB, QxOrm 등

· Python : Django, SQLAlchemy, Storm 등

· iOS : DatabasObjects, Core Data 등

· .NET : NHibernate, DatabaseObjects, Dapper 등

· PHP : Doctrine, Propel, RedBean 등



**ORM의 한계**

· 프레임워크가 자동으로 SQL을 작성하기 때문에 의도대로 작성되었는지 확인해야 한다.

· 객체지향적인 사용을 고려하고, 설계된 DB가 아닌 경우 프로젝트가 크고 복잡해질수록 ORM 기술을 적용하기가 어려워진다.

· 기존 기업들은 ORM을 고려하지 않은 DB를 사용하기 때문에 ORM에 적합하게 변환하려는 시간과 노력이 필요하다.