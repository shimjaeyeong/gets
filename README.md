# Gets

## 프로젝트 개요

### 1. 패션 플랫폼

### 2. 구현 예정 사항

#### Android application

- 홈
    - 스타일 추천
    - 미리 보기
- 카테고리
    - 종류별 탐색
    - 상세 검색
    - 제품 정보
    - 제품 리뷰
- 옷장
    - 내 옷 종류별 표시
    - 좋아요 선택 옷 종류별 표시
- 코디
    - 사용자 정의 코디
- 설정
    - 계정 설정
    - 정보 수정
- 계정
    - 로그인
    - 회원 가입
    - 상세 정보 입력

#### Data server

- 제품
- 사용자 정보

#### Web application

- android 및 서버 개발 이후 진행

### 3. 개발 진행 사항

#### 주요 개발 일정

|항목                           |시작      |종료      |진행 |
|------------------------------|----------|----------|-----|
|제공 서비스 선별/확립            |2021/04/05|2021/04/09|완료|
|API 구현                        |2021/04/09|2021/04/23|완료|
|기본 레이아웃 설계               |2021/04/16|2021/04/23|완료|
|중간 보고 준비                   |2021/04/23|2021/04/30|완료|
|중간 보고                        |2021/04/30|2021/04/30|완료|
|중간 보고 피드백 관련 회의        |2021/04/30|2021/05/07|완료|
|안드로이드 레이아웃 설계          |2021/05/07|2021/05/21|완료|
|의류 데이터 수집                |2021/05/14|2021/05/28|진행|
|데이터 서버 설계               |2021/05/14|2021/05/21|완료|
|데이터베이스 설계                |2021/05/14|2021/05/24|완료|
|안드로이드 기능 구현              |2021/05/21|2021/06/18|진행|
|최종 발표 PPT & 보고서 작성       |2021/06/11|2021/06/18|완료|
|최종 발표                        |2021/06/18|2021/06/18|완료|

## 프로젝트 실행

### 1. 요구 사항

#### Android application

- Android >= 7

#### Data server

- Node.js >= 14
- MySQL Community Server >= 8

### 2. 설치 방법

#### Android application

- 요구 사항을 만족하는 emulator

#### Data server

##### 필요 프로그램 설치

- Node.js
- MySQL Community Server

##### node.js 모듈 설치

```text
npm install
```

##### 데이터베이스 설정

```mysql
create database gets;
use gets;
create table user
(
    email         VARCHAR(64) PRIMARY KEY,
    pw            VARCHAR(32)  NOT NULL,
    name          NVARCHAR(16) NOT NULL,
    phone         VARCHAR(16),
    birthday      DATE,
    address       NVARCHAR(128),
    addressDetail NVARCHAR(128),
    gender        CHAR(1),
    height        INT,
    weight        INT,
    topSize       INT,
    bottomSize    INT,
    style         INT,
    fit           INT
);

create table product
(
  id       INT PRIMARY KEY AUTO_INCREMENT,
  name     NVARCHAR(128) NOT NULL,
  brand    NVARCHAR(128) NOT NULL,
  code     NVARCHAR(64),
  gender   INT           NOT NULL,
  type     INT           NOT NULL,
  detail   INT           NOT NULL,
  color    INT           NOT NULL,
  fit      INT           NOT NULL,
  season   INT           NOT NULL,
  fiber    INT           NOT NULL,
  age      INT           NOT NULL,
  style    INT           NOT NULL,
  price    INT           NOT NULL,
  image1ID VARCHAR(32)   NOT NULL,
  image2ID VARCHAR(32) DEFAULT NULL,
  image3ID VARCHAR(32) DEFAULT NULL
);

create table review
(
    id        INT PRIMARY KEY AUTO_INCREMENT,
    userEmail VARCHAR(64),
    productID INT           NOT NULL,
    star      INT           NOT NULL,
    contents  VARCHAR(2048) NOT NULL,
    date      DATE          NOT NULL DEFAULT (current_date),
    image1ID  INT           NOT NULL,
    image2ID  INT                    DEFAULT NULL,
    image3ID  INT                    DEFAULT NULL,
    FOREIGN KEY (userEmail) REFERENCES user (email) ON UPDATE CASCADE ON DELETE SET NULL,
    FOREIGN KEY (productID) REFERENCES product (id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

##### 서버 실행

server 파일에서

```text
node ./bin/www
```

##### 서버 접속

메인페이지:
[http://localhost:3000](http://localhost:3000)  
API:
[http://localhost:3000/api](http://localhost:3000/api)

## 최종리포트

### 최종발표PPT

![plan1](./data/plan/1.png)


### 최종결과보고서

