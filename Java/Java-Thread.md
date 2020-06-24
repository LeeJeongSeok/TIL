# Thread

- 스네이크 게임을 만들면서 가장 큰 이슈였던 쓰레드에 대해 대략적으로 정리해볼려고 함

### Process
- 간단히 말해서 실행 중인 프로그램이라고 볼 수 있음
- 프로그램을 실행하면 OS로 부터 실행에 필요한 메모리를 할당받아 프로세스가 된다.
- 프로세스는 프로그램을 수행하는 데 필요한 데이터와 메모리 등의 자원 그리고 쓰레드로 구성되어있다고 하는데.. 이번 글에서는 프로세스의 개념, 프로세스와 쓰레드의 관계, 쓰레드의 개념을 잡기 위한 글이기에 그 외 정보들에 대해선 다루지 않을 예정
- 여기서 우리가 딱 집중할 곳은 바로 쓰레드가 프로세스안에 구성되어있다는 점이다.
![](https://images.velog.io/images/ljs0429777/post/583cee19-981c-4656-8d2c-b66ed6865c0a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-06-24%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.26.48.png) (현재 내 PC에서 실행중인 프로세스들이다)
![](https://images.velog.io/images/ljs0429777/post/10e0fa29-a7fa-4dd2-9c81-e796a9c32c18/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-06-24%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%204.34.56.png)


### Thread란?
- 프로세스의 자원을 이용해서 실제로 작업을 수행하는 것을 쓰레드라고 부름
- 다시 쉽게 표현하면 쓰레드를 프로세스라는 작업공간(공장)에서 작업을 처리하는 일꾼(worker)으로 생각하면 이해가 쉽다
- 모든 프로세스에는 최소한 하나 이상의 쓰레드가 존재하며, 둘 이상의 쓰레드를 가진 프로세스를 멀티쓰레드 프로세스라고 부름 👏

### 특징
- 하나의 프로세스가 가질 수 있는 쓰레드의 개수는 제한되어 있지 않으나 쓰레드가 작업을 수행하는데 개별적인 메모리공간을 필요로 하기 때문에 쓰레드는 메모리 공간과 의존적인 관계라는 것만 알아두자 (두뇌보호 차원) 😝

- 한 번 사용한 쓰레드는 다시 재사용할 수 없다. 다시 말해 하나의 쓰레드에 대해 start()가 한 번만 호출된다는 뜻이다.

```java
Thread th1 = new Thread();

th1.start()
th1.start() ---> 이렇게 호출할 수 없다.
```


```java
Thread th1 = new Thread();
th1.start()

Thread th2 = new Thread();
th2.start() ---> 하나의 새로운 쓰레드를 생성하여 사용할 수 있다.
```

### 구현
- 쓰레드를 구현하는 방법은 2가지가 있다.
- 먼저 첫번째 방법인 Thread 클래스를 상속받는 방법

```java
public class ThreadTest extends Thread{

}
```

- 두번째 방법인 Runnable 인터페이스를 구현하는 방법

```java
public class ThreadTest implements Runnable{

   @Override
    public void run() {
    	// Runnable 인터페이스를 구현하기 위해 자동으로 생성되는 run()메소드
    }
}


```
위와 같이 두 가지 방법 중 어느 쪽을 사용해도 사실 별 문제는 읎다..
다만 일반적으로 자주 사용하는 방법은 Runnable 인터페이스를 구현하는 방법이다.

어쨋든 우리는 Thread와 Runnable 인터페이스 안에 있는 run() 내용만 채워주면 된다.

그 후 start() 메소드 호출만 해주면 작업을 시작한다.


- Main
```java
public class Main {
    public static void main(String[] args) {

        new ThreadTest1().start();

        ThreadTest2 threadTest2 = new ThreadTest2();
        Thread thread = new Thread(threadTest2);

        thread.start();
    }
}

```

- 클래스를 상속받은 클래스

```java
public class ThreadTest1 extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("extend Thread : " + getName() + i);
        }
    }
}

```

- 인터페이스를 구현한 클래스
```java
public class ThreadTest2 implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("implement Thread : " + Thread.currentThread().getName() + i);
        }
    }
}
```

- 실행할때 마다 달라지겟지만 위에 코드를 실행해보면 아래와 같은 결과를 얻는다.

extend Thread : Thread-00
extend Thread : Thread-01
extend Thread : Thread-02
implement Thread : Thread-10
implement Thread : Thread-11
implement Thread : Thread-12
implement Thread : Thread-13
implement Thread : Thread-14
extend Thread : Thread-03
extend Thread : Thread-04


Thread 클래스를 상속받은 경우와 Runnable 인터페이스를 구현한 경우의 객체를 생성하는 방법이 조금 다르다

Thread 클래스를 상속받으면 Thread 클래스의 메소드를 직접 호출 할 수 있지만, Runnable을 구현하면 Thread 클래스의 static 메소드인 currentThread()를 호출하여 쓰레드에 대한 참조를 얻어 와야 호출이 가능하기 때문이다.


```java
Thread currentThread() - 현재 실행중인 쓰레드의 참조를 반환한다.
String getName() - 쓰레드의 이름을 반환한다
```



### Event Dispatch Thread (EDT)

- Swing 컴포넌트의 UI 상태를 변경하는 것은 Event Dispatch Thread는 단일 스레드 체계에 의해 관리가 된다.
- 즉,  Move-Pratice2 프로젝트에서 KeyListener와 ActionListener를 동시에 사용할 수 없다는 이야기이다..
- GUI 응용 프로그램을 사용할 때 버튼을 누른다든가, 마우스를 이동을 한다. 통상 이러한 동작들에 대해 GUI 프로그램이 처리 되면 우리는 흔히 이벤트가 발생했다라고 말한다
- 그냥 한마디로 사용자가 마우스를 움직이든, 키보드를 누르던 그것을 다 이벤트라고 칭한다.
- 이 사실을 조금만 더 빨리 알았다면 삽질을 덜 했을탠대..(삽질의 장단점)
- 대략적으로 정리한 것이고, 아직 이해가 되지 않은 부분이 많다...
- 아직 정리하는 중이라 시간이 쪼오오끔은.. 걸릴것같다...흑..