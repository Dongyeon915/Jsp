
프로젝트 설정
jdk,이클립스,tomcat 준비

jdk -> 환경변수 설정 (위치를 알아야한다)

-----------------------------------------------------
JSP - 자바 서버페이지 (html) 표현에 적합함

아파치 - HTTP 웹 서버 소프트웨어다.

톰캣 - 웹 애플리케이션 서버이다. 
톰캣은 웹 서버와 연동하여 실행할 수 있는 자바 환경을 제공하여 자바서버 페이지와 자바 서블릿이 실행할 수 있는 환경을 제공하고 있다

jsp코드는 톰캣이 처리후 브라우저로 출력

웹서버의역활
jsp는 시작점이없다 클라이언트 요청으로 반응하는것
-------------------------------------------------------------
프로젝트 폴더구조
src 자바코드 위치
webContent (나머지 웹자원 html,css,js등) 무언가를 만들때는 이곳에 위치
webinf 외부 라이브러리 사용
---------------------------------------------------------------------------------
서버 실행시
*항상 실행할 프로젝트는 하나의 프로젝트로만 설정해줘야한다*
run on as 는 프로젝트 *전체*를 연결되어있는 tomcat을 통해 실행하는것
톰캣 내부 java코드는 tomcat이 처리하여 결과만을 웹브라우저에 출력해준다.
------------------------------------------------------------------------
톰캣실행시 http://localhost:8080/myjsp/ 주소는 webContent 최상위 주소와 동일 이러한 경로를 context path라 칭함
tomcat은 기본적으로 8080포트를 실행한다.
-------------------------------------------------------------------------

http는 request/response로 이루어져있다.
------------------------------------------------------

정적서비스 html,css,js => 요청시마다 항상 동일한 결과를 응답하는것 

동적서비스 jsp,asp,php,react
--------------------------------------------------------

jsp는 javaee를 통해 배포 설정자를 xml형식으로 제공한다 (이름,값) 이를 통해서 페이지 단위 조절이 가능하다.
ex) <welcom-file>index.html<welcom-file>
--------------------------------------------------------------------

외부 라이브러리 사용시 WEB-INF -> lib 폴더 사용

--------------------------------------------
jsp사용법

스크립트안에서 지정된 변수는 service()호출후 초기화작업이 이루어짐
<% %> 자바 코드사용가능 / 연산,처리 기능 정의 / 서버에서처리
String str = ""; 포문등


<%= %> 표현식 : 값을 출력
str 출력용


객체 값을유지한다 멤버변수로 
<%! %> 선언문(멤버필드,멤버 메서드 정의) 처리연산 사용불가 / 거의사용하지않음
String str = "";
 
-------------------------------
jsp 라이프 사이클

클라이언트 페이지 요청 -> tomcat 내부 jsp -> .java파일로 생성 -> 서버에서 처리 class컴파일 -> 서버의메모리 jspService()실행 -> 클라이언트 응답

두번째 같은 파일을 요청할때는 바로 jspService()함수를 호출 또다시 객체를 생성하지 않는다.

서버 메모리에서는 jspDestroy()함수를 실행하는데 실행 기준은 기존 jsp파일이나 자바에 변경이 있으면 실행된다. 이후 객체를 삭제하고 다시 메모리에 올리게된다.


jspInit(),jspDestroy()는 직접 객체를 삭제하고 메모리에 올리는 역활을 하는것이 아닌 삭제전 후에 행동을 오버라이딩을 통해 정의하는 역활을 수행한다.

---------------------------------------------------------------------------------------
jsp파일은 결국 자바 코드로 변환된다 선언문에 작성된 코드는 멤버 변수로 변경
---------------------------------------------------------------------------------------
jsp는 클라이언트 요청을 http request.으로 정보를 확인할수있다.
