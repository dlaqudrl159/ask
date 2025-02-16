# 자바 공부

# 자바란?
   - 자바란 단순히 프로그래밍 언어를 넘어서 소프트웨어 개발 플랫폼이라고 볼 수 있다.
   - 프로그래밍 언어로서 규칙이 정해져 있고
   - 객체지향 프로그래밍을 추구하며
   - jvm이라는 실행환경이 존재하고
   - 여러 표준라이브러리, API, spring같은 프레임워크, maven gradle 같은 빌드도구 등등 다양한 생태계를 가지고 있다.
   - 이로써 자바란 컴퓨터 소프트웨어 개발 플랫폼이라고 볼 수 있다.

# 자바의 특징
  - 가비지컬렉터의 자동 메모리 관리 안쓰는 메모리는 자동으로 정리해줌
  - 멀티 쓰레드 사용
  - 
# 객체지향 프로그래밍이란?
  - OOP라고 불리우며 모든 데이터를 객체로 취급해 객체끼리의 상호작용을 통해 프로그래을 만드는 기법
  - 상속 다형성 캡슐화 추상화 4개의 특징을 가짐
  ## 캡슐화
  - 객체의 속성과 행위를 하나로 묶고 외부로 드러나지 않게 하는 것
  - 예를들면 금액의 10%를 할인해야 한다 하자
  - 객체에서 price라는 금액을 받아와서 0.9 를 곱한다면 가능하지만 이건 캡슐화의 진정한 의미가 아님 만약 다른 곳에서도 10%할인을 해야한다면 거기서도 0.9를 곱해야 하는 코드의 중복이 발생
  - 그러므로 객체안에 금액을 10%할인하는 메소드를 만들고 다른곳에서 객체에게(10%할인 메소드를 가지고 있는 객체 price도 가지고 있지) 요청 하기만 한다면 가능
  - 캡슐화는 코드의 중복을 없애주며 동작 방식을 외부에서 알 필요가 없다는 것이 장점(10%할인 메소드를 쓰기만 하면 되니깐)
    
  ## 추상화
  - 객체의 공통된 속성과 기능을 뽑아내서 정의하는것
  - 예를 들어 여러객체들의 가져야할 공통된 기능을 추상클래스나 인터페이스로 정의하고 하위 클래스는 기능을 가져다 쓰기만 하면 됨
  - exception 클래스를 만든다 해보자 exception은 errorcode 나 errorMessage가 있을 것 이다.
  - 하위 커스텀된 exception 클래스는 errorcode, errorMessage 필드를 따로 만들 필요가 없으며, 이 것을 정의하는 기능을 따로 만들 필요가 없다 생성자만 만들어서 매개변수로 넣어주기만 하면 되니깐
  - 이로 인해 코드의 중복이 줄어든다
  - 또 추상화된 클래스를 사용하면 이 클래스가 어떤 역할을 하는지 직관적으로 이해가 가능함
    
  ## 다형성
   - 부모 타입의 참조 변수가 자식 타입의 객체에 참조가 가능한 것
   ![image](https://github.com/user-attachments/assets/7f9a097d-42e2-4f8d-9360-680f79814919)

  - 예를들어 asia나 afreeca의 시간대를 보여준다 해보자;
  - earth라는 부모클래스가 있고 new asia(); new afreeca(); 라는 자식 클래스가 존재한다.
  - earth는 showTime()이라는 추상메서드가 존재하고 하위 클래스는 각 지역별로 시간대를 나타내도록 showTime() 메서드를 구현했다.
  - 이런 형변환이 가능함으로써 새로운 자식 클래스(예를 들면 유럽) 같은 걸 추가해도 Earth를 상속받기만 하면 되니 확장성이 용이하며 showTime() 이라는 공통메서드를 활용해 코드의 재사용성이 올라간다.
    
   ![image](https://github.com/user-attachments/assets/81d67593-0a1a-4c34-a356-eb65ded7f9ee)

  - 결국 객체지향 프로그래밍은 유연한 설계를 목적으로 하는 것
  - 다형성은 부모타입의 객체가 자식타입을 참조함으로써 형변환을 통해 유연한 코드를 짤 수 있고
  - 상속은 부모로부터 물려받아 코드의 재사용성이 증가하며 정해진 규격을 만들 수 있다
  - 추상화는 공통된 속성 기능을 뽑아내 불필요한 세부 사항을 감출 수 있다.
# 톰캣

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
         
# 톰캣2
  - 톰캣의 startup.bat이 어떻게 jvm도 실행하고 war파일을 실행시키는지 궁금했다.
  - 톰캣의 startup.bat에는 %JAVA_HOME%\bin\java.exe -classpath %CLASSPATH% %JAVA_OPTS% org.apache.catalina.startup.Bootstrap start 라는 코드가 들어있다.
  - java.exe: JVM을 시작하는 실행 파일
  - org.apache.catalina.startup.Bootstrap: 톰캣의 시작점이 되는 Java 클래스 라고 한다.
  - 톰캣의 startup.bat에는 jvm을 실행하고 wepapps폴더를 읽어서 Root폴더나 Root.war 파일을 실행하거나 압축을 풀고 web.xml 설정을 로드해서 서블릿을 초기화 하는 이 과정이 포함되어있었다.





