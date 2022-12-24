---
title: Java 기본 개념
author: Suhwan
date: 2022-12-24 
categories: [Java]
tags: [typography]
math: true
mermaid: true
toc : true                  # Table of Contents. 포스트의 헤더들만 보여주는 목차를 사용할 것인지의 여부. 
                            # ture 로 해주면 포스트의 목차가 보이게 된다.
toc-sticky : true           # 목차가 스크롤을 따라 움직인다.
# image:
#   path: /commons/devices-mockup.png
#   width: 800
#   height: 500
#   alt: Responsive rendering of Chirpy theme on multiple devices.
---
자바기초 지식
===
<br/>

**1. 자바의 특징**
<hr/>

- 이식성이 높은언어(운영체제가 달라도 프로그램을 실행할 수 있다.)
- 객체지향언어(Object oriented : 필요한 기능을 파악하고 이를 객체화하여 객체간의 상호작용을 통해 프로그램을 구동)

<br/>

**2. 변수**
<hr/>

- 변수란 값을 저장할 수 있는 메모리 상의 공간

<br/>

**3. 변수의 명명규칙**
<hr/>

- 대소문자는 구분되며 길이의 제한이 없다.
- 예약어 사용 불가
- 숫자로 시작하면 안된다.

<br/>

**4. JVM (Java Virture Machine)**
<hr/>

- 자바 인터프리터(interpreter) : 자바 컴파일러에 의해 자바 바이트 코드(기계어)를 읽고 해석하는 역할
- 클래스 로더(class loader) : 동적으로 클래스를 로딩해주는 역할을 함.
- JIT (Just-in-Time Complier) : 실행중인 런타임에 기계어로 변환해주는 컴파일러(dynamic translation)이라고도 불린다.
- Garbage collector : 사용하지 않는 메모리를 자동 회수
- Excution Engine : 클래스를 실행시키는 역할

<br/>

**5. GET과 POST의 차이**
<hr/>

**GET**<br>URL의 끝에 ?와 함께 이름과 값으로 쌍을 이루는 요청피라미터를 통해 데이터를 전송한다.
<br/>

**POST**<br>URL에 데이터를 노출하지 않고 요청한다.(보안에 좋음)

<br/>

**6. call by value와 call by referance 차이**
<hr/>
<u>메서드를 호출할때 파라미터를 전달하는 방법에는 두가지가 있음</u>

<br/>

**Call by value**<br>메서드를 호출할 때 값을 넘겨주기 때문에 Pass by value라고도 부름<br>메서드를 호출하는 호출자(Caller)의 변수와 호출 당하는 수신자의 파라미터는 복사된 서로 다른 변수이다.<br>값만을 전달하기 때문에 수신자의 파라미터를 수정해도 호출자의 변수에는 아무런 영향이 없음

<br/>

**Call by referance**<br>참조(주소)를 직접 전달함<br>
참조를 직접 넘기기 때문에 호출자의 변수와 수신자의 파라미터는 완전히 동일한 변수임

<br/>

**7. Thread**
<hr/>

- 프로세스 내에서 실제로 작업을 수행하는 주체
- 모든 프로세서에서는 한개 이상의 쓰레드가 존재. 두개이상이면 멀티쓰레드라고 한다.
- CPU의 사용률을 향상시킴.

<br/>

**8. List와 Array 차이**
<hr/>

|Array|List|
|---|---|
|인덱스를 가진 데이터|인덱스없이 순차적으로 저장된 데이터의 집합|
|메모리에 연속적으로 저장|메모리에 분산되어 저장
|<span style="color:red">랜덤 엑세스</span>가 가능하지만 중간에 <span style="color:yellow">데이터 삽입/삭제가 어려움</span>|<span style="color:red">랜덤 엑세스</span>가 불가능 하지만 중간에 <span style="color:yellow">데이터 삽입/삭제가 쉬움</span>
||구현하는 가장 일반적인 방법은 Linked List|

<br/>

**9. Java와 JavaScript의 차이**
<hr/>

|Java|JavaScript|
|---|---|
|OOP(object-oriented Programming)<br>객체지향언어|OOP스크립팅 언어|
|가상시스템 or 브라우저에서<br>실행되는 응용프로그램을 작성|브라우저에서만 실행됨|
|컴파일이 필요|컴파일이 필요없음|

<br/>

**10. 싱글톤 패턴(Singleton Pattern)**
<hr/>

- 애플리케이션 전체에서 단 한개의 객체만 생성해서 사용하고 싶다면 싱글톤 패턴을 적용 할 수 있다.
- 클래스는 생성자가 여러차례 호술되더라도 실제로 생성되는 객체는 하나
- 이후는 최초의 생성자가 생성한 객체를 리턴함.
- 주로 DBCP(DataBase Connection Pool)와 같은 상황에서 많이 사용

<br>

ex) 싱글톤은 **생성자에 private**을 붙인다.
```java
private 클래스() {}
```
! 싱글톤 패턴의 핵심은 생성자 호출을 할 수 없는것.<br>
생성자 호출을 할 수 없으니, 외부에서 객체를 생성하는 것이 불가능 하다.<br>
<span style="color:yellow">대신 싱글톤 패턴이 제공하는 정적 메소드를 통해 간접적으로 객체를 얻을 수 있다.</span>!
```java
public class 클래스 {
    //private 접근 권한을 갖는 정적 필드 선언과 초기화
    private static 클래스 singleton = new 클래스();

    //private 접근 권한을 갖는 생성자 선언
    private 클래스(){}

    //public 접근 권한을 갖는 정적 메소드 선언
    //외부에서 객체를 얻는 유일한 방법은 getInstance()메서드를 호출하는것.
    public static 클래스 getInstance() {
        return singleton;
    }
}
```
<br/>

**11. 팩토리 패턴(Factory Method Pattern)**
<hr/>

- 객체지향 디자인 패턴
- 부모 클래스에 알려지지 않은 구체 클래스를 생성하는 패턴
- 자식 클래스가 어떤 객체를 생성할지 결정하도록하는 패턴

<br/>

**12. DB정규화**
<hr/>

- 테이블간 중복된 데이터를 허용하지 않음
- 중복된 데이터를 허용하지 않음으로써 무결성(Integrity)를 유지할 수 있다.

**13. 인터페이스(Interface)와 추상 클래스(Abstract Class)**
<hr/>

**Interface**<br>인터페이스안에 있는 메서드는 모조리 추상메서드. 구현메서드를 갖을 수 없다.
<br>사용하는 이유 : 설계도 같은 역할

<br/>

**Abstract Class**<br>추상메서드와 일반 메서드를 갖을 수 있다.
```java
//추상클래스
abstract class cat{

    //일반 메서드
    public void eat(int food){
        //기능 구현
    }
    //추상 메서드
    abstract public void love(String who);
    abstract public void coding();
}

class robot extends cat{
    
    //추상메서드를 호출할땐 overriding을 해야한다.
    @Override
    public void love(String who){
        //기능 구현
    }

    @Override
    public void coding(){
        //기능 구현
    }
}

public static void main(String[] args) {
    cat a = new cat(); 
    // X주의X 추상클래스는 인스턴스객체를 생성할 수 없다. 추상클래스는 실행코드를 갖고 있지 않을 수 있기 때문에.
    robot r = new robot(); //이렇게 상속받은 클래스를 사용해야 한다.
}
```