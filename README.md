# docker-container

# 취약점 요약 (CVE-2012-1823)
- 취약점명: PHP-CGI Argument Injection (인자 주입을 통한 원격 코드 실행)
- 영향받는 버전: PHP 5.4.2 이전 버전 또는 5.3.12 버전

# 발생 원인 및 원리:
- PHP에는 웹 서버(Apache 등)와 외부 프로그램 간의 상호 작용을 가능하게 하는 표준 프로토콜인 CGI 모드가 존재한다.
- 해당 취약점은 PHP 내부 코드인 sapi/cgi/cgi_main.c 파일에 존재하는 php-cgi 로직에서 발생한다.
- 사용자가 URL 쿼리 스트링을 통해 입력한 값을 처리할 때, -s, -d와 같은 명령줄 매개변수를 필터링하거나 검증하지 않고 실 행 환경으로 넘겨버리는 결함이 존재한다.

# 환경 구성

- git clone 후, docker compose up -d 명령어를 통해 테스트 환경을 실행하였으나, ‘! php The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8)’라는 메시지가 떴다.
- 따라서 AWS의 EC2를 통해 우분투 서버를 생성하여 진행하였다.
- 인스턴스를 생성하고 실행 환경을 구성한 후, docker compose up -d 명령어를 사용하였더니, 다음과 같이 접속이 가능하였다.
- 
