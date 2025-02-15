자바 공부

자바란?
   - 자바란 단순히 프로그래밍 언어를 넘어서 소프트웨어 개발 플랫폼이라고 볼 수 있다.
   - 프로그래밍 언어로서 규칙이 정해져 있고
   - 객체지향 프로그래밍을 추구하며
   - jvm이라는 실행환경이 존재하고
   - 여러 표준라이브러리, API, spring같은 프레임워크, maven gradle 같은 빌드도구 등등 다양한 생태계를 가지고 있다.
   - 이로써 자바란 컴퓨터 소프트웨어 개발 플랫폼이라고 볼 수 있다.

자바의 특징
  - 가비지컬렉터의 자동 메모리 관리 안쓰는 메모리는 자동으로 정리해줌
  - 멀티 쓰레드 사용
  - 
객체지향 프로그래밍이란?
  - OOP라고 불리우며

톰캣

  - 톰캣은 was즉 웹 어플리케이션 서버 또는 서블릿 컨테이너
  - 요청이 들어오면 요청을 분석함 예를 들어 /login이라는 요청이 들어왔다.
  - 이 요청을 처리하는 서블릿을 찾음
  - 어떻게 찾냐? 톰캣은 실행시 web.xml 또는 @WebServlet을 분석한다.
  - /login url에 맵핑 되어있는 서블릿을 찾는다.
  
  @WebServlet
  
  ![image](https://github.com/user-attachments/assets/f9d51c5a-de02-4945-98a7-6959be814dff)
  ![image](https://github.com/user-attachments/assets/7735f7d7-4248-4ab8-93ed-980b7329b8d1)
  
  request.getRequestDispatcher("/jsp/noserviceinfo.jsp").forward(request, response); 를 사용해 전달한다.
  
  web.xml 
  
  ![image](https://github.com/user-attachments/assets/0781d76e-f186-4351-87b5-1ed4360c390c)


  - 그 다음 서블릿을 실행시켜 서블릿 내에 있는 코드가 작동하며 db처리든 데이터를 가공해서 보여주든 작업을 수행한다.
  - 서블릿에 html 코드를 삽입시켜 페이지를 보여주는 형식으로 작동도 가능
  - 이게 책임과 역할도 명확하지 않고 html을 삽이하는 것도 너무 번거로우니 jsp가 등장
  - !!중요!! jsp도 서블릿이다.
  - jsp는 html 코드 내에 자바 코드를 작성하여 동적인 컨텐츠를 제공한다.
  - jsp도 내부적으로 서블릿으로 변환되어 클라이언트한테 보여진다.

  gpt가 보여준 jsp -> 서블릿 변환 결과
  
  ![image](https://github.com/user-attachments/assets/18fa919e-4c23-4ddb-b23b-bfedb79d7731)

  - 서블릿과 jsp를 동시에 사용해 서블릿은 클라이언트 요청을 처리하고 비즈니스 로직을 수행하고
  - jsp는 클라이언트한테 보여줄 화면을 구성해
  - 책임과 역할이 분명해졌다.
    
  정리 
  
  톰캣이 클라이언트한테 받은 요청 > 맵핑 된 서블릿으로 전달 > 서블릿이 요청을 처리 (비즈니스 로직) > 서블릿이 jsp에 데이터 전달 >
  jsp가 받은 데이터로 화면을 구성 이 과정에서 <%= request.getAttribute("currentTime") %></p> 이런 식으로 자바코드를 삽입해 구성 가능
         
톰캣2
  - 톰캣의 startup.bat이 어떻게 jvm도 실행하고 war파일을 실행시키는지 궁금했다.
  - 톰캣의 startup.bat에는 %JAVA_HOME%\bin\java.exe -classpath %CLASSPATH% %JAVA_OPTS% org.apache.catalina.startup.Bootstrap start 라는 코드가 들어있다.
  - java.exe: JVM을 시작하는 실행 파일
  - org.apache.catalina.startup.Bootstrap: 톰캣의 시작점이 되는 Java 클래스 라고 한다.
  - 톰캣의 startup.bat에는 jvm을 실행하고 wepapps폴더를 읽어서 Root폴더나 Root.war 파일을 실행하거나 압축을 풀고 web.xml 설정을 로드해서 서블릿을 초기화 하는 이 과정이 포함되어있었다.





