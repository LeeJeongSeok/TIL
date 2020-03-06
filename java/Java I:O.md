# I/O 란?

- Input과 Output의 약자로 입출력을 의미함
- 입출력의 간단한 예로 키보드로 텍스트를 입력하고, 모니터로 입력한 텍스트를 출력하는 것임

# 스트림(stream)
- **Input -> Output** (지극히 개인적인 비유법,,)
👆 식에서 "->" 스트림을 의미함
Input, Output 구분없이 어느 한쪽에서 다른 쪽으로 데이터를 보낼려면 일종의 다리 역할(->)을 하는 친구가 필요하다 그 친구가 바로 스트림(->)이다.

- 추가적으로 스트림의 어원은 연속적인 데이터의 흐름을 물에 비유하여 붙여진 이름이라는데,,,여러 가지로 유사한 점이 많다고 한다.
가장 큰 특징으로는 물이 한뱡향으로 흐르는 것과 같이 스트림은 단방향통신만 가능하다. 즉, 하나의 스트림으로 입출력을 동시에 처리할 수 없다.
만약! 입출력을 동시에 처리하고 싶으면 입력 스트림 1개, 출력 스트림 1개 총 2개의 스트림을 생성하면 된다.
![](https://images.velog.io/images/ljs0429777/post/7434797d-c98c-472f-b0fe-579f421ddd75/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-03-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2012.44.44.png)

# Java I/O 패키지
### Java I/O 패키지란?
- API Document : https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/io/package-summary.html 
문서의 설명되어 있는 말을 가져와보면
> Provides for system input and output through data streams, serialization and the file system. Unless otherwise noted, passing a null argument to a constructor or method in any class or interface in this package will cause a NullPointerException to be thrown.

- 간단하게 첫줄만 번역하면 **데이터 스트림, 직렬화 및 파일 시스템을 통한 시스템 입력 및 출력 제공** 이라는 말을 볼 수가 있다. 즉 Java I/O 패키지 안에는 파일 입출력과 관련된 클래스들로 구성되어 있다는 의미기도 하다.


### 바이트 단위 스트림
- InputStream, OutputStream 둘다 바이트 기반 입출력 스트림의 최상위 클래스로 추상 클래스이다. 관련된 모든 바이트 기반 입출력 스트림은 이 클래스를 상속받아서 만들어 진다.
- 바이트단위로 데이터를 전송하며 입출력 대상에 따라 제공하는 클래스가 다르다.
- 그림, 멀티미디어, 문자 등 모든 종류의 데이터를 주고 받을 수가 있다
- Java I/O 도식표
![](https://images.velog.io/images/ljs0429777/post/9b7ea841-3561-4d68-be8e-901404325151/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-03-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.14.29.png)
- Java I/O 패키지 주요 클래스 및 설명

![](https://images.velog.io/images/ljs0429777/post/7aae3237-b30b-439f-9ece-f765303b912e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-03-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.01.03.png)

### 문자 단위 스트림
- Reader, Writer 둘다 문다 데이터 기반 입출력의 최상위 클래스이다. 관련된 모든 텍스트 기반 입출력은 이 클래스를 상속받아서 만들어 진다.
- 문자데이터를 입출력할 때 사용하는 문자기반의 스트림이다.
- 오로지 문자 데이터를 주고 받기 위해 특화되어있다.
![](https://images.velog.io/images/ljs0429777/post/86c95040-9c2f-4206-bfa4-a5ac00b47072/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202020-03-06%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.01.47.png)

### 보조 스트림
- 스트림의 기능을 보완하기 위해 나온 녀석이다.(입출력 성능 속도 향상, 데이터 포멧 등)
  1. 실제 데이터를 주고 받지 않는다.
  2. 데이터를 주고 받을 수 없기 때문에 먼저 스트림을 생성한 후 사용해야 한다.
  3. 밑에 실험한 코드가 보조 스트림 활용 예시이다.
```
DataInputStream dataInputStream = new DataInputStream(new FileInputStream("test.txt"));
```


### 궁금증 해결하기 및 테스트..?
- Java I/O 공부하던 중 BufferedReader와 FileReader의 차이가 궁금해서 찾아보니, 버퍼의 활용 유무였다. 말로는 저렇다고 하지만 실질적으로 나에게 와닿는 부분은 없다는 기분이 들어서 직접 테스트 해보기로 맘먹었다.
- 시작하기전 테스트할 파일의 용량이 작으면 테스트하는 맛이 없기 때문에 테스트 파일의 용량을 64byte -> 47.2MB로 늘렸다 ㅎㅎ
- 단순히 이 둘의 성능 차이를 눈에 띄게 확인해 보고 싶었다..


#### FileReader로 47.2MB 파일을 읽을 경우
```
package com.lee.collection;

import com.lee.fileio.Properties;

import java.io.FileReader;
import java.io.IOException;

public class Test {

    public static void main(String[] args) throws IOException {

        long startTime = System.currentTimeMillis();

        System.out.println("startTime" + startTime);

        FileReader fileReader = new FileReader(Properties.phonePath);

        int i;

        while (true) {
            i = fileReader.read();

            if (i == -1) {
                break;
            }

            System.out.println((char) i);
        }

        long endTime = System.currentTimeMillis();

        System.out.println("endTime : " + endTime);

        long secDiffer = startTime - endTime;



        System.out.println("시간차이 : " + secDiffer);

    }
}

```
- 결과
3분이 넘어도 빌드하지 못했다..😂

#### BufferReader로 47.2MB 파일을 읽을 경우
```
package com.lee.collection;

import com.lee.fileio.Properties;

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Test2 {

    public static void main(String[] args) throws IOException {

        long starTime = System.currentTimeMillis();

        System.out.println(starTime);

        BufferedReader bufferedReader = new BufferedReader(new FileReader(Properties.phonePath));


        while (true) {

            String str = bufferedReader.readLine();

            if (str == null) {
                break;
            }

            System.out.println(str);
        }

        long endTime = System.currentTimeMillis();
        long sedDiffer = (starTime - endTime);

        System.out.println(endTime);


        System.out.println("시간차이 : " + sedDiffer);


    }
}
```
- 결과
24초만의 빌드 성공 😃



이미지 출처 및 자료 참고 :https://ccm3.net/archives/21118
이미지 출처 및 자료 참고 :https://coding-factory.tistory.com/281