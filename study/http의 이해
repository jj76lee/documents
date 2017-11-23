HTTP의 이해
---

* http 0.9
  * UA(user agent) - request -> <- response - O (origin)
  * 기존 프로토콜과 비교하자면 상태가 없고 한번 보내고 받아서 (GET 요청) 끝 : 단순함
* http 1.0
  * header 와 메소드 추가

* HTTP 메시지 구조 
  * Start Line <cr> Header <cr> Blank Line <cr> Body
  * 아르파넷 : 핵전쟁이후에도 살아남기, 평문기반 : 사람이 손으로 써도 가능

* Request 의 header
  * accept : 나(UA - 클라이언트) 이거 받을수 있어
  * Connection: keep-alive connection 닫지 말고 (이거는 http 1.1 부터 default)
  * Content : Body를 의미, Content-Type : body의 데이터 종류
  * If -* : cache control 에 사용함
  * User Agent: 현재에는 서버측에서 이 정보값을 활용해 response를 보내기 때문에 잘 정의해야 한다 (예 whale 은 safari이며서 chrome이고 ,  ...)
   * Cache-control : 서버쪽 cache 컨트롤 요청. 예) 클라이언트 캐싱하지마

 * Response 의 header
   * Access-Control-Allow-Origin : 크로스도메인 허용여부
   * Cache-control : UA쪽 cache 컨트롤 요청. 예) 클라이언트 캐싱하지마
   * Etag: 리소스 ID - 콘텐츠의 해싱값, 우선수위가 IF-이거보다 높다.
   * Location : 리소스가 새롭게 생성될때,
   * Content-Length: 필수 항목 이거 잘못 적어주면 브라우저 행걸린다.
 
 * Response Code : 몇개 필요하지
   * 201 Created - 중요해
   * 1xx (조건부 응답)
     * 101 Switching Protocols - 다른 프로토콜로 전환 (https)
   * 2xx (성공)
   * 3xx (리다이렉션 완료)
     * 301(영구적), 302(일적) : post 요청을 get으로 바꿀수 있다. (브라우저가)
     * 308(영구적), 307(일시적) : post 요청을 get으로 바꾸지 않고 post로 보냄 
   * 4xx (요청 오류) - 너 잘못
   * 5xx (서버 오류) - 내 잘못
   
 * Content Type
   * 예) text/plain;charset=utf-8, application/json, image/jpeg
   * Primary Object Type / specific subtype (mime 타입 - 이메일 첨부 스펙)
   * 카테고리 : text, applicatoin,  / 실제 파일 종류
 
 * Http Methods
   * GET: idempotent: ok, safe: ok
   * POST: idempotent: x, safe: x - 리소스 대체이다 (수정 아니야)
     * Body는 default URL 인코딩되어서 보내진다. (query 파트 같다)
     * 바이너리라 큰 파일은: multipart/form-data 로 전송 (boundary 라고 키를 준)
   * PUT: idempotent: ok, safe: x  
     * 200 (ok) or 201 (리소스가 없어서 생성된 경우)
   * DELETE: idempotent: ok, safe: x
     * 202 (accepted - 배치처리나 지연된 응)
   * PATCH: 일부 수정, range, 이어받기
   * OPTIONS: 특정 URL의 옵션을 알려달라
   * HEAD: GET의 헤더만 줘, 
   * TRACE: 내 요청이 서버에 갈때 프록시들을 알려줘
   * HTML 은 GET, POST 두개만 지원 
   * Properties
     * Idempotent - 멱등성, 여러번 요청해도 한번 요청과 같다. PUT, DELETE 
     * Safe - read-only 
     

* Conditional Get : 
   * Cache Control 헤더: 브라우저 측에서 캐
     * no-cache: 캐슁하지 마
     * max-age: 델타까지만 가지고 있어라 (과거 expire인데 이건 절대 시간) 
     * no-store: 절대 저장하지 마라
   * Last-Modified : 가장 최근 변경일시, UTC 스트링 
   * ETag: 컨텐츠 해
     * 강한ETag: 이거 바꼈으면 변경이 있어 
     * 약한ETag: 리소스가 의미있는 수준의 변화가 없다면 바꾸지 않을수 있다

 * State Management : 상태 저장
   * 쿠키 (가장 많이 써) : 
     * HTTP 헤더의 한 항목이다
     * 응답으로 (response)에 Set-Cookie:  value를 준다
       * NAME=value; 쿠키이름
       * expires=Date; 완료일자
       * domain=Domain; 해당 도메인에만 쿠키를 사용한다.
       * secure ; https가 아니면 저장 안한다
       * session 쿠키 : 브라우저 종료후 사라짐 (expires를 안쓰는 경우)
       * persistent cookie: domain 지정여부에 따라 동작이 다름
     * 
   * Fat URL: URL 상태 저장 - 요즘 안써
   * IP추적
   * Authentication: Http의 인증 매커니즘 사용
 
 * HTTPS - 보안
  * 서버인증/클라이언트인증/무결성/암호화
  * 1. 서버 인증 : 서버에게서 인증이 무결해를 응답받음
  * 2. 클라이언트인증: 클라이언트가 랜덤 키 전달, 복호화 시킨 뒤 대칭키(=세션 키)로 사용함
  * 3. 대칭키(세션키)로 암호화 
 * HTTP 인증
   * Basic Authentication - Base64로 인증
   * Digest Authentication - 이것도 MD32 같은거 써
   * 이런거 말고 제대로 하는건 OAuth1, OAuth2(default가 https)
 
 * HTTP/2
    * HTTP/1.1보다 빠르다
    * header compression : header 정형화 되어 있으므로, diff만 전송
    * Multiplexed Streams : 
    * Server Push
    * Stream Priority
  
 * 비대칭 암호화
   * public key 로는 암호화(encryption)만 가능
   * private key 로 복호화(decryption)만 가능

* exmaple.com: 테스트용  
     ```bash
 $ nc www.exmple.com 80
 GET / HTTP/1.1
 Host: example.com
 
 $ nc www.example.com 80
 OPTIONS / HTTP/1.1
 Host:example.com
 
 
 $ nc -l 8080
 
```
    
   