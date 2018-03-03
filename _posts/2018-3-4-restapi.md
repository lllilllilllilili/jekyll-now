
---
layout: post
title: Rest Api
---
# Rest Api
Rest api 란 웹을 활용한 기술이다.
특징으로는 6가지가 존재하는데, 
Uniform Interface, Stateless, Cacheable, Self-descriptiveness, Client-Server, 계층적구조가 특징이다.
1. Uniform Interface
URL로 지정해서 접근할수있는 기술이다.
2. Stateless
이 상태에서는 서버에서 관리가 필요하지 않기때문에, 단순하고 사용자의 요청에만 응답한다.
3. Cacheable
Http 기반이기 때문에 웹에서 사용하는 기존의 기능을 구현할 수 있다.
4. Self-descriptiveness
Api만 보고도 쉽게 이해할 수 있다.
5. Client - Server
클라이언와 서버가 나눠져서 효율적으로 개발할 수 있다.
6. 계층적구조
여러 계층을 형성할 수 있어서 중간 계층을 통해 개발 가능 

#  Rest api 디자인 가이드
get, post, put, delete로 표현해야 한다.
```
POST : URL 요청 리소스 생성
GET : 리소스 조회, 정보를 가져온다
PUT : 수정
DELETE : 삭제

```

#  HTTP 응답상태코드

200 : 클라이언트 정상수행

201 : 클라이언트가 만드는것을 요청하고 그것을 수행할 경우

400 : 클라이언트 요청이 부적절할때

401 : 클라이언트가 인증하지 않고 암호화된 리소스를 요청할때

403 : 클라이언트가 인증여부와 관련없이 리소스를 요청할때

405 : 클라이언트가 리소스에 사용불가능한 소스를 요청했을때 

301, 500 : 클라이언트가 리소스 URL 변경되는것을 요청했을때/ 서버문제  

# Reference
[REST API 제대로 알고 사용하기](http://meetup.toast.com/posts/92)