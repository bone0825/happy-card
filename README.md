# 신년카드 전송 애플리케이션

2인 프로젝트로 Spring boot와 MySQL을 이용하여 웹 서비스를 구현하고 카카오 API를 적용하며 AWS를 이용해 웹 배포를 하고 실제 도메인을 구입하여 적용하는 실습을 진행하기 위해 프로젝트를 진행하였다.


## 기획 의도

다가오는 설날에 메시지 카드를 작성하여 카카오톡을 통해 사람들에게 공유할 수 있는 웹 서비스를 제공하고자 한다. <br>

- 사용자는 메인 페이지에서 제공하는 카드 디자인을 보고 마음에 드는 카드를 선택하여 보내는 사람 이름과 보낼 내용을 작성한다. <br>
- 이후 보내기 버튼을 누르면 생성되는 링크를 복사 버튼을 눌러 직접 사람들에게 전달 하거나, 공유하기 버튼을 눌러 카카오톡을 통해 사람들에게 해당 링크를 공유할 수 있다. <br>
- 메시지를 수신받은 사람들은 해당 링크를 타고 들어가면 작성된 메시지카드를 확인할 수 있고, 나도 공유하기 버튼을 눌러 메인 페이지로 돌아가 메시지를 작성할 수 있다.

<p align="center">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/4f6671d4-9cd0-4715-802e-09ecffcea3af" align="center" width="30%" style=" box-shadow: 3px 3px 3px gray;">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/33e55cd4-9a0b-4d93-85fd-123b6ea23654" align="center" width="30%" style=" box-shadow: 3px 3px 3px gray;">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/7152937d-cc74-4ba6-98b5-54c466e92a32" align="center" width="30%" style=" box-shadow: 3px 3px 3px gray;">
</p>

## 기간 및 역할

2024-01-15 ~ 2024-02-06

- MySQL 서버 연결 및 ER 다이어그램 작성, 데이터베이스 구현
- write-card, read-card 백엔드 작성, read-card 프론트 구현
- 카카오 API 적용
- AWS EC2 서버 배보 및 업데이트 


## ER-Diagram
<p align="center">
<img src ="https://github.com/bone0825/happy-card/assets/88430215/62aa33a9-f82e-45c9-a19b-3151bee62bfb" align="center">
</p>

서비스 할 카드에 대한 정보를 담기 위해 **card**테이블을 작성하였다. 작성된 카드에 대한 정보를 담기 위해 **write_card**테이블을 작성하였다. <br>

**write_card**에서 어떤 카드에서 내용이 작성되었는가에 대한 정보를 담기 위해 card_id를 **card**테이블로부터 FK로 받아와 저장하였다.

## 개발 회고

> #### 카드 이미지 생성 AI

 카드로 사용될 이미지를 생성하기 위해 우리는 AI를 생성하여 카드를 만들었다. 한국 정서에 맞는 적당한 이미지를 생성하기 위해 다양한 키워드를 삽입해 보았지만, 우리가 원하는 이미지를 찾는 것은 쉽지 않았고 여러 사이트에서 제공되는 다양한 생성 AI를 사용해 보았고 그 중 가장 적절하다고 생각되는 몇 개의 이미지를 가져와 사용하였다.
<br>
<br>

> #### Spring Boot 실습

현업에서 자주 사용된다는 Spring Boot에 대한 공부를 병행하며 실습을 진행하였다. MVC 패턴과 각종 데이터 엔티티의 처리를 위해 dto 클래스를 관리 하였다. 다만, 책과 강의 간의 차이가 있어 이번 실습에서는 Lombok을 사용하지 않았다. 추후 리팩토링할 때 Lombok을 사용하고, vo 클래스를 작성하며 mapping을 추가적으로 이용해 보고자 한다.
<br>
<br>

> #### 카카오 API

카카오 메시지 API를 이용하여 공유하는 기능을 구현하였다. 공식 문서를 참고하였지만, REST 방법과 JavaScript방법 중 어느것을 선택해야 하는지 잘 몰랐다. 그래서 youtube에 나와있는 JavaScript를 이용한 API 사용법을 참고하여 작성하였으며 실제 적용하기 위해 도메인을 잘 설정해 줘야 한다는 것을 알 수 있었다.
<br>
<br>

> #### AWS EC2 실습 

책을 바탕으로 실습을 진행하였고, git에서 코드를 가져와 EC2에 적용하고 nohup를 통해 실시간으로 서버가 돌아갈 수 있게 하였다. 첫 배포는 어렵지 않았으나 코드를 업데이트 하는 과정에서 어려움이 있었다. 기존 8080포트가 사용되고 있거나, git pull은 성공적으로 했지만 변경된 코드가 제대로 적용되지 않았거나 하는 문제가 있었다. <br>

그래서 새로 적용 할 때에는 **기존 nohup.out 파일을 지우고 8080포트를 닫은 상태**에서 `./gradlew clean build -x test`를 진행하여 SNAPSHOT.jar을 생성한 다음 nohup를 생성하는 방식으로 진행해야 함을 느낄 수 있었다.
<br>
<br>

> #### git을 이용한 협업

사실상 이번 프로젝트 실습에서 가장 어지러웠던 부분이다.<br>
이전의 git은 단순히 내가 작성한 코드를 나의 Repository에 올려 보관하고, 업데이트 하는 용도로만 사용하였다.<br>
하지만 이번 협업에서는 하나의 Repository에 각 기능에 맞게 branch를 따로 나누고 이를 develop에 merge 시키는 방법을 채용하였다. 거기에 더불어 나는 팀장의 레파지토리를 fork로 떠와 내 레파지 토리에서 작업한 내용을 다시 팀장의 레파지토리에 올리는 방법을 이용하다 보니 merge할 때 여러 버전 문제가 생기는 것을 확인하였다.

이는 나의 git 사용 법이 아직 미숙하기 때문에 일어난 일이고 항상 작업할 때는 pull도 잘 활용해야 한다는 것을 느꼈다. 또한 merge 시킬 때 충돌이 나지 않게 하기 위해 팀원끼리 코딩 규칙을 절 정해야 하며 정해진 규칙을 잘 따라야한다는 것을 느꼈다.
<br>
<br>

## 개발 환경

- **OS**: Windows10, AWS EC2(Linux)
- **DB**: MySQL
- **Language**: Java, HTML, CSS, Javascript
- **Framework**: Spring Boot
- **etc**: git, github, notion, intelliJ
