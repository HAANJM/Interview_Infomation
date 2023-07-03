# JAVA CS / 면접 질문 리스트

- [GC(가비지 컬렉터)](#gc가비지-컬렉터)
- 오버로딩 / 오버라이딩
- 다형성
- 추상화
- OOP
- 자바의 메모리

</br>

## GC(가비지 컬렉터)

* [가비지 컬렉션 동작 원리 & GC 종류](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC)

## 오버로딩 / 오버라이딩

* 오버로딩 <br>
같은 이름의 메소드가 매개변수가 달라질 때
ex) print, println



* 오버라이딩
같은 이름의 메소드를 상속을 통해 다른 내용으로 재구성하여 사용
ex) toString

## 자바의 메모리

![image](https://github.com/HAANJM/Interview_Infomation/assets/108118635/f013fb1b-6ca9-4ce8-b627-300bb9bc35aa)

1) Method Area
   - JVM이 실행되면서 생기는 공간
   - Class 정보, 전역변수 정보, Static 변수 정보가 저장된다
   - Runtime Constant Pool 에는 말 그대로 상수 정보가 저장되는 공간이다
   - 모든 스레드에서 정보가 공유된다
2) Heap
   - new 연산자로 생성된 객체, Array와 같은 동적으로 생성된 데이터가 저장되는 공간
   - Heap에 저장된 데이터는 Garbage Collector가 처리하지 않는 한 소멸되지 않는다
   - Reference Type의 데이터가 저장되는 공간
   - 모든 스레드에서 정보가 공유된다
3) Stack
   - 지역변수, 메소드의 매개변수와 같이 잠시 사용되고 필요가 없어지는 데이터가 저장되는 공간
   - Last In First Out, 나중에 들어온 데이터가 먼저 나간다
   - 만약, 지역변수지만 Reference Type일 경우에는 Heap에 저장된 데이터의 주소값을 Stack에 저장해서 사용하게 된다
   - 스레드마다 하나씩 존재한다
4) PC Register
   - 스레드가 생성되면서 생기는 공간
   - 스레드가 어느 명령어를 처리하고 있는지 그 주소를 등록한다
   - JVM이 실행하고 있는 현재 위치를 저장하는 역할
5) Native Method Stack
   - Java가 아닌 다른 언어(C, C++)로 구성된 메소드를 실행할 필요가 있을 때 사용되는 공간
