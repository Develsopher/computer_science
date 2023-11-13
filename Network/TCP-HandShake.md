# 🤝 TCP 3 & 4 Way HandShake
---
## 1. 　3 & 4 Way HandShake 란?
- ### 클라이언트와 서버가 연결성립 및 연결해제를 하기위해 거치는 과정

---

## 2. 　TCP의 연결 성립  
### `3 way handshake`  
- #### TCP는 신뢰성을 위해, 논리적인 접속을 성립시키기 위한 3단계의 과정을 거친다
![](https://velog.velcdn.com/images/k-minsik/post/c2a651c4-714d-489e-9ae4-878042661b6d/image.png)

### 1. SYN : 클라이언트가 서버에게 자신의 ISN을 담은 SYN 패킷을 보낸다  
### 2. SYN + ACK : SYN을 수신한 서버는 서버의 ISN을 담은 SYN과 ACK(client SYN + 1)을 응답한다
### 3. ACK : 서버의 응답을 받은 클아이언트가 ACK(server SYN + 1)을 응답한다  

- #### 위 세 단계를 거쳐 클라이언트와 서버의 연결이 성립된다

> LISTEN : 서버는 CLOSED 상태에서 서버가 열린 상태 즉 LISTEN 상태여야 클라이언트의 요청을 받을 수 있다.
> ISN : TCP 기반 데이터 통신에서 각각의 새 연결에 할당된 고유한 32bits Sequence num  
> SYN : synchronization의 약자, 연결 요청 플래그  
> ACK : acknowledgement의 약자, 응답 플래그

---

## 3. 　TCP의 연결 해제  
### 4 way handshake
- #### 모든 통신이 끝났다면 연결을 해제하기 위해 4단계의 과정을 거친다
![](https://velog.velcdn.com/images/k-minsik/post/65a4918f-7341-4b1c-bf76-50ce439e2dce/image.png)


### 1. 클라이언트가 서버에게 FIN 세그먼트를 보내고 FIN_WAIT_1 상태로 서버의 응답을 기다린다
### 2. FIN을 수신한 서버가 ACK 세그먼트를 응답하고 CLOSE_WAIT 상태가 된다.
### 　　 ACK를 받은 클라이언트는 FIN_WAIT_2 상태가 된다
### 3. 서버는 LAST_ACK 상태가 되었다가, 데이터를 모두 보낸 후 FIN 세그먼트를 보낸다
### 4. FIN을 수신한 클라이언트가 ACK를 서버에게 응답하고 TIME_WAIT의 상태로 남은 데이터를
### 　　기다리다가 Closed가 된다. 그리고 서버는 ACK를 수신한 즉시 Closed가 된다

위 네 단계를 거쳐 클라이언트와 서버의 연결이 해제된다
> TIME_WAIT : 지연 패킷 등이 발생했을 때 데이터 무결성을 위해 패킷을 기다리는 시간. 2*MSL(최대 패킷 수명)

---

> 이미지 출처 : https://www.inflearn.com/course/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EB%A9%B4%EC%A0%91-cs-%ED%8A%B9%EA%B0%95#
