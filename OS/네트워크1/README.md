## TCP

#### 3-way Handshake 에 대해 설명해 주세요.

#### ACK, SYN 어디에 저장하나?

#### 2-Way Handshaking 를 하지않는 이유에 대해 설명해 주세요.

#### 두 호스트가 동시에 연결을 시도하면, 연결이 가능한가요? 가능하다면 어떻게 통신 연결을 수행하나요?

#### SYN Flooding 에 대해 설명해 주세요.

#### 4-way Handshake 에 대해 설명해 주세요

#### 패킷이 4-way handshake 목적인지 어떻게 파악할 수 있을까요?

#### 빨리 끊어야 할 경우엔, (즉, 4-way Handshake를 할 여유가 없다면) 어떻게 종료할 수 있을까요?

#### 4-Way Handshake 과정에서 중간에 한쪽 네트워크가 강제로 종료된다면, 반대쪽은 이를 어떻게 인식할 수 있을까요?

#### 패킷에 담겨진 헤더 정보?

#### 연결을 끊는다고 어떤 쪽에서 보낼 때, 더 이상 정보를 보내지 않도록 통제하는 방법?

#### 왜 종료 후에 바로 끝나지 않고, TIME_WAIT 상태로 대기하는 것 일까요?

---

## HTTP

#### HTTP에 대해 설명해주세요

#### 공개키와 대칭키에 대해 설명해 주세요.

#### 왜 HTTPS Handshake 과정에서는 인증서를 사용하는 것 일까요?

#### SSL과 TLS의 차이는 무엇인가요

#### HTTP/1.1과 HTTP/2의 차이점은 무엇인가요?

#### HOL Problem

#### HTTP/1.0 vs HTTP/1.1

#### HTTP/3.0

#### HTTP 프로토콜의 특징

#### HTTPS에 대해 설명해주세요

#### 인증서를 사용하는 이유?

#### 공개키, 대칭키 장단점

#### Stateless와 Connectionless에 대해 설명해 주세요.

#### 왜 HTTP는 Stateless 구조를 채택하고 있을까요?

#### HTTP Persistence Connection

#### 왜 HTTP는 Stateless 구조를 채택하고 있을까요?

#### HTTP Persistence Connection 이 무엇인가요?

#### TCP의 keep-alive와 HTTP의 keep-alive의 차이는 무엇인가요

#### GET과 POST의 차이점은 무엇인가요?

#### 멱등성에 대해 설명해주세요.

#### HTTP Method의 멱등성에 대해 설명해 주세요.

#### GET과 POST의 차이는 무엇인가요?

#### POST와 PUT, PATCH의 차이는 무엇인가요?

#### HTTP 1.1 이후로, GET에도 Body에 데이터를 실을 수 있게 되었습니다. 그럼에도 불구하고 왜 아직도 이런 방식을 지양하는 것일까요?

#### HTTP 응답코드에 대해 설명해주세요.

#### 401 (Unauthorized) 와 403 (Forbidden)은 의미적으로 어떤 차이가 있나요?

#### 200 (ok) 와 201 (created) 의 차이에 대해 설명해 주세요.

#### pre-defined 가 안 된 status code?

#### HTTP와 HTTPS

#### HTTP 요청/응답 헤더

#### HTTP와 HTTPS 동작 과정

---

## UDP

#### TCP와 UDP의 차이점은 무엇인가요?

#### HTTP 에서 TCP를 고집하였던 이유 / HTTP/3.0에서는 왜 UDP(QUIC)를 사용하는가?

#### checksum

#### TCP / UDP 헤더 차이

#### UDP의 실시간 스트리밍 외 다른 예시

#### TCP 연결에 혼잡제어나 flow control 동작 방식

#### TCP 핸드쉐이크

#### 왜 HTTP는 TCP를 사용하나요?

#### 그렇다면, 왜 HTTP/3 에서는 UDP(QUIC) 를 사용하나요? 위에서 언급한 UDP의 문제가 해결되었나요?

#### 본인이 새로운 통신 프로토콜을 TCP나 UDP를 사용해서 구현한다고 하면, 어떤 기준으로 프로토콜을 선택하시겠어요?

#### TCP와 UDP 중 어느 프로토콜이 Checksum을 수행할까요?

#### 그렇다면, Checksum을 통해 오류를 정정할 수 있나요?

#### TCP가 신뢰성을 보장하는 방법에 대해 설명해 주세요.

#### TCP의 혼잡 제어 처리 방법에 대해 설명해 주세요.

---

## OSI 7계층

#### OSI 7계층에 대해 설명해 주세요.

#### Transport Layer 의 역할, 예시

#### TCP, UDP 헤더의 특징

#### 인터넷 4계층

#### L3 Switch / Router

#### 각각의 Header의 Packing Order

#### 3계층 프로토콜 → 왜 IP만 이야기할까?

#### ICMP

#### ARP

#### L3 Switch와 Router의 차이에 대해 설명해 주세요.

#### 각 Layer는 패킷을 어떻게 명칭하나요? 예를 들어, Transport Layer의 경우 Segment라 부릅니다.

#### 각각의 Header의 Packing Order에 대해 설명해 주세요.

---

## CORS

#### CORS(Cross Origin Resource Sharing)란

#### CORS 동작원리

#### CORS 과정

#### Socket.io와 WebSocket의 차이

#### Frame Packet Segment Datagram
