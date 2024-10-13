# /24-10-11

## 프로젝트 설정

# /24-10-12

## 메시지, 국제화 소개

### 메시지
여러 화면에보이는 상품명, 가격, 수량 등, label에 있는 단어를 변경하려면 다음 화면들을 다 찾아가면서 모두 변경해야한다.
지금처럼 화면 수가 적으면 문제가 되지 않지만 화면이 수십개 이상이라면 수십개의 파일을 모두 고쳐야한다.
왜냐하면 해당 HTML 파일에 메시지가 하드코딩 되어 있기 때문이다.
이런 다양한 메시지를 한 곳에서 관리하도록 하는 기능을 메시지 기능이라 한다.

예를 들어 message.properties라는 메시지 관리용 파일을 만들고
각 HTML들은 다음과 같이 해당 데이터를 key값으로 불러서 사용하는 것이다.

addForm.html
`<label for="itemName" th:text="#{item.itemName}"></label>`

### 국제화
메시지에서 설명한 메시지파일을 각 나라별로 별도로 관리하면 서비스를 국제화 할 수 있다.

한국에서 접근한것인지 영어에서 접근한 것인지는 인식하는 방법은 HTTP 'accept-language'헤더 값을 사용하거나 
사용자가 집접 언어를 선택하도록 하고, 쿠키 등을 사용해서 처리하면 된다.

메시지와 국제화 기능을 직접 구현할 수도 있겠지만, 스프링은 기본적인 메시지와 국제화 기능을 모두 제공한다.
그리고 타임리프도 스프링이 제공하는 메시지와 국제화 기능을 편리하게 통합해서 제공한다.

## 스프링 메시지 소스 설정
스프링은 기본적인 메시지 관리 기능을 제공한다.
메시지 관리기능을 사용하려면 스프링이 제공하는 MessageSource를 스프링 빈으로 등록하면 되는데,
MessageSource는 인터페이스이다.
따라서 구현체인 ResourceBundleMessageSource를 스프링 빈으로 등록하면 된다.

### 스프링부트
스프링부트를 사용하면 스프링 부트가 MessageSource를 자동으로 스프링 빈으로 등록한다.

#### 스프링 부트 메시지 소스 설정

application.properties
springmessages.basename=messages,config.i18n.messages

#### 스프링 부트 메시지 소스 기본값
springmessages.basename=messages
MessageSource를 스프링 빈으로 등록하지 않고, 스프링 부트와 관련된 별도의 설정을 하지 않으면
messages라는 이름으로 기본 등록된다. 
따라서 messages_ko.properties, messages.properties 파일만 등록하면 자동으로 인식된다.

### 메시지 파일 만들기

- messages.properties : 기본값으로 사용(한글)
- messages_en.properties : 영어

# /24-10-13

## 스프링 메시지 소스 사용

### MessageSource 인터페이스



