# 신년카드 전송 애플리케이션

2인 프로젝트로 Spring boot와 MySQL을 이용하여 웹 서비스를 구현하고 카카오 API를 적용하며 AWS를 이용해 웹 배포를 하고 실제 도메인을 구입하여 적용하는 실습을 진행하기 위해 프로젝트를 진행하였다.


## 기획 의도

다가오는 설날에 메시지 카드를 작성하여 카카오톡을 통해 사람들에게 공유할 수 있는 웹 서비스를 제공하고자 한다. <br>

- 사용자는 메인 페이지에서 제공하는 카드 디자인을 보고 마음에 드는 카드를 선택하여 보내는 사람 이름과 보낼 내용을 작성한다. <br>
- 이후 보내기 버튼을 누르면 생성되는 링크를 복사 버튼을 눌러 직접 사람들에게 전달 하거나, 공유하기 버튼을 눌러 카카오톡을 통해 사람들에게 해당 링크를 공유할 수 있다. <br>
- 메시지를 수신받은 사람들은 해당 링크를 타고 들어가면 작성된 메시지카드를 확인할 수 있고, 나도 공유하기 버튼을 눌러 메인 페이지로 돌아가 메시지를 작성할 수 있다.

<p align="center">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/4f6671d4-9cd0-4715-802e-09ecffcea3af" align="center" width="30%" style=" max-width: 100%;margin: 1px; box-shadow: 3px 3px 3px gray;">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/33e55cd4-9a0b-4d93-85fd-123b6ea23654" align="center" width="30%" style=" max-width: 100%;margin: 1px; box-shadow: 3px 3px 3px gray;">
  <img src="https://github.com/bone0825/happy-card/assets/88430215/7152937d-cc74-4ba6-98b5-54c466e92a32" align="center" width="30%" style=" max-width: 100%;margin: 1px; box-shadow: 3px 3px 3px gray;">
</p>

## 기간 및 역할

2024-01-15 ~ 2024-02-06

- MySQL 서버 연결 및 ER 다이어그램 작성, 데이터베이스 구현
- write-card, read-card 백엔드 작성, read-card 프론트 구현
- 카카오 API 적용
- AWS EC2 서버 배보 및 업데이트 


## ER-Diagram

## 개발 환경

- **OS**: Windows10, AWS EC2(Linux)
- **DB**: MySQL
- **Language**: Java, HTML, CSS, Javascript
- **Framework**: Spring Boot
- **etc**: git, github, notion, intelliJ
