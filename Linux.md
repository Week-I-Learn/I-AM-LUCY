# Linux
첫 회사에서 리눅스 환경에서 많은 시간을 보내며 내적 친밀감을 쌓았었는데 최근에 관심이 사라지면서 관계가 어색해진거 같다.<br />
예전에 적었던 문서를 한번 정독하면서 리눅스를 잊지 않기 위한 시간을 보냈다

**What is Linux?**
- Linux는 오픈소스 운영체제(OS)입니다. 모든 Linux 기반 OS에는 하드웨어 리소스를 관리하는 Linux 커널과 OS의 나머지를 구성하는 일련의 소프트웨어 패키지가 포함되어 있습니다.

**What is OS?**
- 운영 체제(Operating System, OS)는 CPU, 메모리, 스토리지 처럼 시스템의 하드웨어와 리소스를 직접 관리하는 소프트웨어입니다.

**What is a command line?**
- command line 통해서 컴퓨터에 직접 액세스할 수 있습니다. 사용자는 command line에서 그래픽 사용자 인터페이스(GUI)가 요청할 수 없는 하드웨어 작업을 수행하도록 소프트웨어에 요청

[리눅스 명령어 모음 ](https://www.notion.so/b832fc6793fc47e681415f258bea0c5b)

**useradd {옵션} {아이디}**
- `c`: 설명 입력
- `d`: 홈 디렉터리 지정
- `e`: 계정 만료일 지정
- `f`: 계정 유효일 지정
- `g`: 로그인 그룹 지정
- `m`: 홈 디렉터리 자동 생성
- `M`: 홈 디렉터리 자동 생성 금지
- `p`: 패스워드 지정
- `s`: Shell 지정
- `u`: UID 지정

**계정 정보 확인 방법**
- cat /etc/passwd | grep [계정명]

**사용자 계정 비밀번호 설정**
- passwd [옵션] [계정명] : 비밀번호 없는 상태로 생성이 되면 비밀번호를 지정

**사용자 계정 정보 변경**
- usermod [옵션] [계정명] : 계정에 설정을 변경할 때 사용하는 명령어
- usermod -u 600 usert1 명령어로 실행 후 <- 계정의 UID를 600으로 변경
- cat /etc/passwd | grep usert1 으로 확인

**사용자 계정 삭제**
- userdel [옵션] [계정명]
- userdel -rf usert1 명령어로 강제 계정 삭제 후 <- 강제 계정 삭제
- cat /etc/passwd | grep usert1 < - 검색 결과 확인

참고: [https://rootblog.tistory.com/2](https://rootblog.tistory.com/2)<br />

**What is awk?**
- 파일로부터 레코드(record)를 선택하고, 선택된 레코드에 포함된 값을 조작하거나 데이터화      하는 것을 목적으로 사용하는 프로그램 입니다.

참고: [https://recipes4dev.tistory.com/171](https://recipes4dev.tistory.com/171)
<br />
**Linux 컨테이너란?**
- Linux 컨테이너는 실행에 필요한 모든 파일을 포함하여 전체 런타임 환경에서 애플리케이션을 패키지화 하고 분리하는 기술입니다.

<br />
**Linux 컨테이너를 사용해야 하는 이유**
- Linux 컨테이너를 활용하면 담당 영역을 분리하여 충돌을 줄일 수 있습니다.
- 개발자는 애플리케이션에 집중할 수 있고 운영팀은 인프라에 주력할 수 있습니다.
