# macOS에 Java(JDK) 설치

- 스프링 프레임워크(Spring Framework)을 사용하기 위해선 JDK와 통합개발환경(IDE)를 설치해야 한다.
- 스프링 개발에서 가장 많이 사용하는 IDE 도구들로는 Eclipse 기반인 Spring Tool Suite(STS)와 Intellij를 주로 사용한다.  이번 글에서는 먼저 JDK를 설치하는 방법을 작성할 것이다.



1. JDK 다운로드

   - https://www.oracle.com/technetwork/java/javase/downloads/index.html 에 접속하여 최선 버전에 자바를 설치하거나, 자신이 원하는 버전에 자바를 설치할 수 있다. 필자는 Java 1.8 버전을 설치했다.

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93855348-02e7-4136-8bd6-57f05e91ea18/Screen_Shot_2020-02-04_at_11.13.41_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93855348-02e7-4136-8bd6-57f05e91ea18/Screen_Shot_2020-02-04_at_11.13.41_PM.png)

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/563733a1-04d2-4570-a0a2-1e7afb9479cb/Screen_Shot_2020-02-04_at_11.13.08_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/563733a1-04d2-4570-a0a2-1e7afb9479cb/Screen_Shot_2020-02-04_at_11.13.08_PM.png)

   - 여기서 주의할 점은 우리가 설치하려는 것은 JDK이다. JRE가 아니다. 

   - 밑에 보이는 JRE은 무엇인지 궁금해하는 사람이 있을 것이다.(설치 당시 필자도 궁금했다.)

     -  관련된 자료들은 이후에 작성하는 글에서 작성할 것이다. 이 글은 JDK를 설치를 주목적으로 한 글이기 때문이다.

2. JDK 설치 파일 실행

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75aaf890-59cf-4fad-b084-2e6877cda86b/Screen_Shot_2020-02-04_at_11.16.18_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75aaf890-59cf-4fad-b084-2e6877cda86b/Screen_Shot_2020-02-04_at_11.16.18_PM.png)

   필자가 사용하는 맥의 언어 설정을 영어로 해서 다소 다를 수가 있다....

   밑에 보이는 Continue(계속)를 누르면 비밀번호를 물어보는 창이 있는데 비밀번호 입력 후 설치를 계속 진행한다.

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfbc92c0-e2ad-4bd6-8c30-83ee0e2be9a0/Screen_Shot_2020-02-04_at_11.16.40_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bfbc92c0-e2ad-4bd6-8c30-83ee0e2be9a0/Screen_Shot_2020-02-04_at_11.16.40_PM.png)

   - 이런 창이 나오면 JDK를 설치를 끝났다.

     자 그럼 이제 JDK가 성공적으로 잘 설치되었는지 확인해봐야 한다.

     맥에서 Terminal이나, iTerm를 실행 시킨다.

3. JDK 설치 확인 

   - Terminal을 열어 명렁어 입력 커서에 "java-version"이라고 입력한 후

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e6bbaec-2c55-45d7-ad1a-fa35c2e33edb/Screen_Shot_2020-02-04_at_11.17.42_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5e6bbaec-2c55-45d7-ad1a-fa35c2e33edb/Screen_Shot_2020-02-04_at_11.17.42_PM.png)

   - 이렇게 정상적으로 java version을 확인 성공적으로 나왔다면 "javac -version"을 입력해준다.

   ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9b66c412-15b7-4490-baf8-d32186d6cef9/Screen_Shot_2020-02-04_at_11.18.07_PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9b66c412-15b7-4490-baf8-d32186d6cef9/Screen_Shot_2020-02-04_at_11.18.07_PM.png)

   - javac -version까지 성공적으로 출력이 됬다면 JDK를 성공적으로 설치한 것이다.



