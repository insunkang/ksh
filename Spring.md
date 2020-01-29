# 20-01-21 화

## Spring Framework

* 내부에서 객체를 관리 < LIFECYCLE >
  * 객체생성에 관여하는 기능 : 컨테이너 가 객체를 관리하는 방식 : IOC(Inversion of Control) 컨테이너
  * => 스프링의 컨셉을 이해하는데 가장 중요
* WEB , DB연동, 로그, 트랜잭션
* 스프링에서는 객체를 Bean이라고 불러요
* 스프링은 우리가 일반적으로 만드는 방식대로 클래스를 만들고 어떻게 개발하는지 방식이 정해져있다.
  * 클래스를 만드는 방식과 운영방식이 정해져있는 것.

---

# 20-01-22 수

## 스프링의 개요

### 1. 프레임 워크

> 완성된 소프트웨어가 아니라 어떤 문제를 해결하기 위해서 잘 설계된 미완의 모듈로 spring같은 경우 자바 개발자들이 공통으로 사용할만한 기능을 미리 정의해 놓은 모듈이다.

* 모듈? : 코드를 모아 놓은 라이브러리
* 해결해야 하는 문제 : 내가 개발하고 싶은 시스템 => 쇼핑몰, 예약관리시스템, 인터넷뱅킹............
* 스프링은 재사용이 가능한 모듈이며 일반적으로 프레임워크를 통해서 개발하는 시스템의 공통모듈은 프레임워크에서 제공

#### - 스프링 프레임워크의 이점

* 개발자가 처리해야하는 대부분의 작업을 프레임워크 내부에서 처리해 주므로 개발을 위한 시간과 노력을 절약가능
* 신뢰있는 프로그램을 개발할 수 있다.(정부인증 프레임워크로 대부분의 대기업들이 사용)
* 개발자간의 의사소통이 활발.
* 주어진 메뉴얼대로 개발하면된다. 즉, 프레임워크 내부에서 제공하는 모듈을 사용해서 개발하면 된다.

### 2. 스프링의 특징

* 경량시스템(포함된 라이브러리가 거의 1MB가 넘지 않기 때문에 가볍다)
* POJO(Plain Old Java Object)로 개발하기 때문에 작성하는 클래스는 작성하는 OOP의 특징을 적용하며 개발하면 됨.
* spring 프레임워크 내부에 IoC컨테이너를 포함하고 있다.(***)

#### 1) 의존성을 주입

* 시스템 내부(내가 만든 프로그램)에서 사용하는 객체를 직접 생성해서 사용하지 않고 스프링내부에 존재하는 *컨테이너*를 통해 필요한 곳에서 사용할 수 있도록 전달받아 사용한다.
  * *컨테이너*? : 스프링 내부에서 라이브러리로 존재
    * spring-beans-4.2.4.RELEASE.jar
    * spring-context-4.2.4.RELEASE.jar

#### 2) 스프링 내부의 IoC컨테이너를 통해 객체를 관리하면서 커플링을 낮출 수 있다.

#### 3) 스프링 내부에는 발생할 수 있는 다양한 모든 경웨 반응할 수 있도록 많은 컨테이너 클래스를 제공한다.

### 3. 스프링 컨테이너의 종류

> 기본설정은 모든 컨테이너는 같은 객체는 하나만 생성한다.

* *BeanFactory*  : 개발자가 객체(빈)를 요청하는 시점에 객체를 생성한다.(가장 상위의 컨테이너)
  - *ApplicationContext* : 컨테이너 객체가 생성될때 전달된 xml안에 정의된 모든 빈을 생성하고 의존성주입을 처리.
    - *WebApplicationContext* :

### 4. 의존성 주입

#### 1)  DL(Dependency Lookup)

* 컨테이너가 만든 객체를 getBean메소드를 통해 가져와서 사용하는 것

#### 2) DI(Dependency Injection)

* 

---

# 20-01-23 목

* 내가 사용하고 있는 클래스? => 의존모듈 -> ( DI ) 를 통해서 여러 객체를 관리할 것이다.

* 유지보수를 위해 요구사항이 바귄다 해서 변경되면 안되고 원활하게 추가될 수 있게 개발해야 한다.

  => OOP와 다형성을 이용해서 잘 설계해야 함. => 외부에서 객체를 관리하도록 위임

* setter인젝션은 기본생성자가 추가되어야 하고, setter메소드가 추가되어야 한다. - <property>

* di인젝션 은 - <constructor> - 기본 생성자가 없어도 ㄱㅊ & set 메소드가 없다.



### <어노테이션을 활용하기>

- 설정파일에 빈을 등록하지 않고 사용ㅎ나다.

- 설정파일에 <context:compent-scan>앨립먼트를 이용해서 컨테이너가 빈을 찾을 수 있도록 패키지를 등록

- 기본생성자를 반드시 추가해야 한다.

- 빈 생성을 위해 사용할 수 있는 어노테이션 기호

  - *component* : 일반적인 빈
  - *Service* : 비지니스로직(DAO제외)이 정의되어 있는 빈을 등록하는 경우 사용
    - 클래스의 첫 글자를 소문자로 변경한 이름을 빈을 name에 등록
    - Dice=>dice , Player=>player
    - 이름을 별도로 정의하고 싶으면  괄호를 이용해서 사용가능
  - *Repository* : DAO를 등록하는 경우 사용

- 빈의 이름을 특별한 이름으로 명시하고 싶으면 ( )안에 " " 로 정의

  ex) 빈의 이름을 myplayer - @Service( " myplayer " )

  ​															------------------- => 등록한 빈의 이름은 lookup하거나 의존성주입할때 사용한다.

---

# 20-01-28 화

* Model 1 ? => Model 2 ( Controller가 중요 )

* 개발자들이 컨트롤러 부분을 좀 더 편하게 작업하기 위해 .

* 웹사이트는 굉장히 다양하게 치고 들어온다.?(접속) => 사이트 관리가 안돼~(보안, 로그인 등등) 

  => 모든요청이 하나의 통로로 들어오게 만들어 주자!!

  => *Front Controller* 패턴

  => 결국에는 전부 스프링 기반이다~

  < Front Controller >

  * 요청 분석 기능
  * 요청에 따라 실행할 결과를 찾아서 호출
  * forward 전담
  * 한글처리
  * DB처리
  * view
  * .... 등등

* 모든 작업을 클래스 하나로 만들 수 없고 분리시켜야 하기 때문에 RequestMapping이라는 클래스를 하나 만들어서 mycommand.properties를 보고 요청. 

* 실행할 객체를 만들어서 넘겨줘야한다. (다양한 이름과 다양한 패키지) => 타입을 통일시켜줘야 함.

  * Action이라는 걸 상속.(다형성 적용)
  * 그럼 Action만 하나 넘겨주면 된다



* STS에서 JSP라이브러리 등록하기 : https://blog.naver.com/heaves1/221592072984 
* internal, external server 익스터널이 캐시를 덜 받는다.
* web프로젝트는 라이브러리가 lib에 있어야 한다.

## Spring-STS

### 1. Spring MVC 프로젝트 구성 - maven을 이용하지 않는 경우 

1. Dynamic Web Project 생성

2. 라이브러리를 lib폴더에 복사하기

   ![image-20200128133115312](images/image-20200128133115312.png)

3. DispatcherServlet을 web.xml에 등록

   => 모든 요청이 DispatcherServlet을 통해 진입하도록 설정해야 스프링이 제공하는 여러가지 기능을 적용할 수 있다.

   ( forntController패턴이 적용되어 있다.)

4. spring에서 사용할 설정파일을 작성한다.

   => 따로 등록하지 않으면 web프로젝트에서 사용할 스프링설정 파일은 파일명을 작성할 때 규칙이 있다.

   [DispatcherServlet을 등록한 서블릿명] - servlet.xml

   ex) 서블릿명 : springapp

   ​	/ WEB-INF /

   ​			+

   ​			 l_ springapp-servlet.xml

5. Controller 작성하기

   * 기본 web에서 서블릿과 같은 역할을 하는 클래스
   * 실제 처리를 담당하는 클래스

6. 스프링설정파일에 컨트롤러 등록하기

   * <bean> 태그를 이용해서 5번에서 생성한 컨트롤러 등록하기
   * 요청path를 기준으로 컨트롤러를 등록할 것이므로 id속성을 쓰지 않고 name속성을 사용한다.
   * DispatcherServlet내부에서 요청path에 맞는 컨트롤러를 getBean할 수 있도록 등록

   ```xml
   [형식]
   <bean name="요청path" class="컨트롤러 클래스"/>
   
   [예제] - test.do로 TestController를 요청
   <bean name="/test.do" class="test.TestController"/>
   ```

   * 1,2,3,4번은 한번만 등록하고 5,6번은 계속 해줘야 한다. 6번은 mypropertis에 등록했던 것을 xml에등록하는 것.

### 2. Spring MVC 구성요소

> 스프링 MVC를 구축하고 웹을 실행
>
> 스프링이 제공하는 모든 기능을 잘 활용하기 위해서 스프링이 내가 작성한 자바빈을 관리할 수 있도록 작업해야 한다. => *스프링 내부의 컨테이너가 내가 작성한 빈을 생성하고 관리할 수 있도록 작업)*
>
> * 이를 위해 모든 요청을 DispatcherServlet이라는 서블릿을 통해 들어올 수 있도록 처리

#### 1.DispatcherServlet 

* 클라이언트의 모든 요청을 처리하기 위해 첫 번재로 실행되는 서블릿

#### 2. HandlerMapping

* 클라이언트가 요청한 path를 분석해서 어떤 컨트롤러를 실행해야 하는지 찾아서 DispatcherServlet으로 넘겨주는 객체

#### 3. Controller

* 클라이언트의 요청을 처리하는 객체
* DAO의 메소드를 호출하는 기능을 정의

#### 4. ModelAndView

* Controller에서 DAO의 메소드를 실행결과로 만들어진 데이터에 대한 정보나 응답할 view에 대한 정보를 갖고 있는 객체

#### 5. ViewResolver

* ModelAndView에서 저장된 view의 정보를 이용해서 실제 어떤 view를 실행해야 하는지 정보를 넘겨주는 객체

=> 컨트롤러를 기능별로 세분화 시켜놓은 것.( 중앙 집중식 관리! )

=> *스프링MVC를 구축하면 위의 클래스들이 자동으로 실행되며 일처리를 한다. 따라서 필요에 따라 ViewResolver나 handlerMapping객체를 다양하게 등록하고 사용할 수 있다.*

=> 기본 설정을 이용하는 경우 개발자는 Controller만 작성하고 설정파일이나 Annotation으로 등록하면 된다.



* WEB-INF는 외부에서 절대로 요청될 수 없는 폴더이다. 그 안에 jsp가 있으면 XX

---

# 20-01-29 수

## Maven

* <beans> 로 되있는 거는 스프링설정 파일
* STS에서 UTF-8 설정하기
  * windows-preferences-General-Workspace-Text file Encoding - UTF8
  * windows-preferences-Web-CSS,HTML,JSP Files - UTF-8
  * windows-preferences-General-Content types- text- Default encoding에 UTF-8
* 최종프로젝트 - 책 20p
* 라이브러리를 form.xml에 등록하고 사용할 것임.

## Tiles Framework

> https://mvnrepository.com/

### - 화면구성하기

1. 라이브러리를 pom.xml에 등록

2. 레이아웃이 적용되어 있는 템플릿 파일과 연결할 jsp파일들이 미리 준비되어 있어야 한다.

3. tiles 설정파일을 작성( main-tiles.xml )

   - 템플릿을 등록 : 템플릿의 각 영역을 나누고 각 영역에 기본으로 연결할 jsp파일을 설정한다.

4. 템플릿(레이아웃을 미리 설정해 놓은 파일 - mainLayout.jsp)으로 만들어 놓은 jsp파일의 각 영역이 템플릿에 등록한 영역과 일치하도록 설정

   * tiles에서 제공하는 태그를 사용한다.

     => 내부에서 tiles설정 파일에 등록한 내용과 연결하여 실행하는 작업을 처리하기 위해 tiles에서 제공하는 태그를 써서 작업해야 한다.

5. 스프링 내부에서 실행될 때 DispatcherServlet이 뷰 정보를 ViewResolver에게 전달하면 ViewResolver가 tiles프레임워크를 활용해서 뷰를 만들 수 있도록 spring설정파일에 등록

   * tiles설정 파일이 어떤 파일인지 등록
   * 만들어야 하는 view가 tiles뷰임을 등록

6. 템플릿을 활용해서 만들어질 뷰의 정보를 tiles설정 파일에 등록