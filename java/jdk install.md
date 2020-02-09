# macOS에 Java(JDK) 설치

- 스프링 프레임워크(Spring Framework)을 사용하기 위해선 JDK와 통합개발환경(IDE)를 설치해야 한다.
- 스프링 개발에서 가장 많이 사용하는 IDE 도구들로는 Eclipse 기반인 Spring Tool Suite(STS)와 Intellij를 주로 사용한다.  이번 글에서는 먼저 JDK를 설치하는 방법을 작성할 것이다.



1. JDK 다운로드

   - https://www.oracle.com/technetwork/java/javase/downloads/index.html 에 접속하여 최선 버전에 자바를 설치하거나, 자신이 원하는 버전에 자바를 설치할 수 있다. 필자는 Java 1.8 버전을 설치했다.

     <img width="2560" alt="oracle jdk install page 1" src="https://user-images.githubusercontent.com/13554850/74101237-07ac1480-4b7b-11ea-9da8-4ef377949927.png">

     <img width="550" alt="oracle jdk install page 2" src="https://user-images.githubusercontent.com/13554850/74101269-75f0d700-4b7b-11ea-9dbf-624b8aaba54c.png">

   - 여기서 주의할 점은 우리가 설치하려는 것은 JDK이다. JRE가 아니다. 

   - 밑에 보이는 JRE은 무엇인지 궁금해하는 사람이 있을 것이다.(설치 당시 필자도 궁금했다.)

     -  관련된 자료들은 이후에 작성하는 글에서 작성할 것이다. 이 글은 JDK를 설치를 주목적으로 한 글이기 때문이다.

2. JDK 설치 파일 실행

   <img width="615" alt="jdk install 1" src="https://user-images.githubusercontent.com/13554850/74101278-8739e380-4b7b-11ea-89e0-b3b00e329627.png">

   필자가 사용하는 맥의 언어 설정을 영어로 해서 다소 다를 수가 있다....

   밑에 보이는 Continue(계속)를 누르면 비밀번호를 물어보는 창이 있는데 비밀번호 입력 후 설치를 계속 진행한다.

   <img width="620" alt="jdk install 2" src="https://user-images.githubusercontent.com/13554850/74101286-9882f000-4b7b-11ea-8f72-9ba5b5e18dc4.png">

   - 이런 창이 나오면 JDK를 설치를 끝났다.

     자 그럼 이제 JDK가 성공적으로 잘 설치되었는지 확인해봐야 한다.

     맥에서 Terminal이나, iTerm를 실행 시킨다.

3. JDK 설치 확인 

   - Terminal을 열어 명렁어 입력 커서에 "java-version"이라고 입력한 후

   <img width="471" alt="jdk install check 1" src="https://user-images.githubusercontent.com/13554850/74101299-a8023900-4b7b-11ea-9546-0d26de1746f3.png">

   - 이렇게 정상적으로 java version을 확인 성공적으로 나왔다면 "javac -version"을 입력해준다.

   <img width="263" alt="jdk install check 2" src="https://user-images.githubusercontent.com/13554850/74101313-b4869180-4b7b-11ea-988c-543399993ace.png">

   - javac -version까지 성공적으로 출력이 됬다면 JDK를 성공적으로 설치한 것이다.



