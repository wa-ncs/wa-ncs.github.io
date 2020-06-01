---
layout: post
title: Docker를 이용한 스프링부트 서버 띄우기
comments: true
categories: [Infra/Docker]
tags: [Docker]
author: hongbeom
userImage: /assets/user-img/hongbeom.png
---
<br>

### CentOS 7 기반의 환경에서 진행했습니다
### 로컬과 원격 환경에서 도커를 모두 설치한 상태임을 가정하고 진행하겠습니다.
<br/>

### 도커를 이용해서 스프링 부트 서버를 GCP 위에 실행시키는 작업을 해보겠습니다.
<br/>

### 프로세스는 다음과 같습니다.
#### 1. 이미지 생성
#### 2. DockerHub Push
#### 3. GCP 서버에서 Pull
#### 4. 이미지 실행
#### 5. 외부에서 접속
<br/>

## 도커 이미지 생성하기 (docker build)
### 먼저 로컬에서 도커 이미지를 생성해보겠습니다.

### 스프링 부트 기반의 Demo Project 를 생성합니다.

### 배포할 jar 파일을 생성하고 루트 디렉토리에 Dockerfile 을 작성합니다.
![dockerfile.png](/assets/post-img/docker/dockerfile.png)

### Dockerfile 을 작성하고 나면 docker build 명령어를 통해 이미지를 생성할 수 있습니다.
### 루트 디렉토리로 이동해서 명령어를 실행합니다.
```
$ docker build -t demo .
```
### -t : 이미지 이름 지정
<br/>

### docker images 명령어를 통해 빌드된 이미지 리스트를 확인할 수 있습니다.
```
$ docker iamges
```
![docker-img.png](/assets/post-img/docker/docker-img.png)

### 이미지가 생성됐으면 Docker Hub 라는 저장소에 이미지를 Push 합니다.
<br/>

## 도커 이미지 올리기 (docker push)
### DockerHub 에 회원 가입이 된 상태라는 가정 하에 진행하겠습니다.
### 먼저 도커 허브에 로그인을 합니다.
```
$ docker login
```
### 명령어를 입력하면 username 과 password 를 입력해서 로그인을 할 수 있습니다.
![docker-login.png](/assets/post-img/docker/docker-login.png)

### 그럼 이제 이미지를 태깅하고 푸쉬합니다.
```
$ docker tag demo longbeom/demo
```
### demo 라는 이미지를 [도커 허브 이름]/[태그] 했습니다.
### 이제 docker push 명령어를 통해 이미지를 푸쉬합니다.
```
$ docker push longbeom/demo
```
![docker-push.png](/assets/post-img/docker/docker-push.png)

### 정상적으로 푸쉬가 되면 도커 허브 레포지토리에 이미지가 올라간 걸 확인할 수 있습니다.

### 이제 원격 서버에 접속해서 도커 이미지를 받아보겠습니다.
<br/>

## 도커 이미지 받아오기 (docker pull)
### 원격 서버에 접속한 뒤 docker pull 명령어를 실행합니다.
```
$ docker pull longbeom/demo:latest
```
![docker-pull.png](/assets/post-img/docker/docker-pull.png)

### 이렇게 원격 서버에서 이미지를 받아왔습니다.
### 이제 이미지를 실행시켜서 스프링 부트 서버를 띄워보겠습니다.
<br/>

## 이미지 실행 (docker run)
```
$ docker run -d -p 8088:8088 longbeom/demo
```
![docker-run.png](/assets/post-img/docker/docker-run.png)
### 이미지를 실행하고 컨테이너가 올라갔는지 확인이 되면 이제 외부에서 서버에 접속해보겠습니다.
<br/>

## 외부에서 접속하기
![vm-ip.png](/assets/post-img/docker/vm-ip.png)
### 원격 서버의 IP 와 포트 번호를 이용해 접근할 수 있습니다.
<br/>

### 주소창에 서버 IP 와 포트 번호를 입력해서 스프링 부트 웹서버에 접속했습니다.
### 다음과 같은 화면이 출력되면 정상적으로 접속된 것입니다.
![connect-server.png](/assets/post-img/docker/connect-server.png)