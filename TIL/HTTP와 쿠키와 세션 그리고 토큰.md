## HTTP와 쿠키 그리고 세션

### HTTP는 Hyper Text Transfer Protocol의 약자로써 인터넷에서 데이터를 주고받는 프로토콜을 뜻함

TCP 위에서 동작하지만 TCP와는 달리 무상태성 혹은 비연결성 → **쿠키나 세션을 이용하여 클라이언트의 상태를 관리**

HTTP연결은 시작과 끝은 TCP연결과 해제가 이루어져야함

### **Stateful과 Stateless는, 클라이언트와 서버간의 네트워크 통신이 어떻게 이루어지는지에 대한 개념**

**`Stateful` : 세션이 종료될 때까지, 클라이언트의 세션 정보를 저장하는 네트워크 프로토콜**

**`Stateless` : 서버가 클라이언트의 세션 상태 및 세션 정보를 저장하지 않는 네트워크 프로토콜 ( 요청에 대한 응답만 처리 )**

정리: HTTP통신은 연결, 해제가 발생하여 같은 클라리언트에서 여러번 요청해도 서버에서는 알 수 없다. 그래서 세션을 사용한다

HTTP 프로토콜 환경은 "connectionless, stateless"한 특성을 가지기 때문에 서버는 클라이언트가 누구인지 매번 확인해야합니다. 이 특성을 보완하기 위해서 쿠키와 세션을 사용하게됩니다.

**쿠키 ( Cookie )**

- 쿠키는 클라이언트(브라우저) 로컬에 저장되는 키와 값이 들어있는 작은 데이터 파일
- 사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지됨
- 쿠키는 클라이언트의 상태 정보를 로컬에 저장했다가 참조
- 클라이언트에 300개까지 쿠키저장 가능, 하나의 도메인당 20개의 값만 가질 수 있음, 하나의 쿠키값은 4KB까지 저장
- Response Header에 [Set-Cookie](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Set-Cookie) 속성을 사용하면 클라이언트에 쿠키를 만들 수 있음
- 쿠키는 사용자가 따로 요청하지 않아도 브라우저가 Request시에 Request Header를 넣어서 자동으로 서버에 전송

**세션 ( Session )**

- 세션은 쿠키를 기반하고 있지만, 사용자 정보 파일을 브라우저에 저장하는 쿠키와 달리 세션은 서버 측에서 관리
- 서버에서는 클라이언트를 구분하기 위해 세션 ID를 부여, 웹이 서버에 접속해 브라우저를 종료할 때까지 인증상태를 유지
- 물론 접속 시간에 제한을 두어 일정 시간 응답이 없다면 정보가 유지되지 않게 설정 가능
- 사용자에 대한 정보를 서버에 두기 때문에 쿠키보다 보안에 좋지만, 사용자가 많아질수록 서버 메모리를 많이 차지함
- 즉 동접자 수가 많은 웹 사이트인 경우 서버에 과부하를 주게 되므로 성능 저하의 요인
- 클라이언트가 Request를 보내면, 해당 서버의 엔진이 클라이언트에게 유일한 ID를 부여하는 데 이것이 세션 ID

1. HTTP 통신은 연결 해제가 일어난다
2. stateless 특성은 통신이 끝나면 상태를 가지고 있지 않는다
3. 그래서 쿠키랑 세션을 통해 이를 해결한다
ex) 예를 들어 쇼핑을 하는데 페이지를 이동할때마다 로그인이 풀리는걸 방지하기 위해
4. 쿠키와 세션을 사용하면 한번 로그인 했을 때 사용자에 대한 인증을 유지한다
5. 쿠키는 로컬에 저장되는 데이터 파일
6. 세션은 쿠키를 기반하고 있지만 서버측에서 관리한다
7. 세션이 보안에 더 유리하지만 쿠키가 더 빠르다
8. 세션을 사용하면 메모리 사용량이 늘어나 힘들다

**토큰 ( Token )**
서버가 각각의 클라이언트를 구별하기 위한 정보를 담은 데이터
사용자에 대한 정보를 암호화 하여 브라우저에 저장, 웹페이지 접속시 정보를 가져옴
1. 사용자가 서버에 로그인
2. 서버는 로그인 정보로 토큰 생성
3. 사용자는 브라우저에서 토큰을 받아 임시저장
4. 요청시 토큰을 같이 보내고, 서버는 확인 후 요청을 응답


**참고링크 <br/>**
https://mysterico.tistory.com/29 <br />
https://wooono.tistory.com/366 <br />
https://hahahoho5915.tistory.com/32 <br />
https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Set-Cookie <br />
https://krksap.tistory.com/1586 <br />
https://velog.io/@junghyeonsu/프론트에서-로그인을-처리하는-방법 <br />
https://defineall.tistory.com/861 <br /> 
