# scp(Secure Copy Protocol)로 파일 옮기기

**구문 : # scp [옵션] [파일명 1] [파일명 2] [원격지_id]@[원격지_ip]:[받는 위치]**

scp 

- Secure Copy Protocol을 사용하여 파일을 복사하는 명령어

-i C:\Users\SSAFY\.ssh\K9A702T.pem 

- **`-i` :** 사용할 개인 키 파일을 지정하는 옵션
- **`C:\Users\SSAFY\.ssh\K9A702T.pem` :** 우리 팀 키 파일의 경로를 지정한다
- 개인 키는 SSH 연결을 안전하게 설정하는 데 사용

C:\MEETHARE\MeetHare-Location-Recommend\src\main\resources\application-secret.yml 

- 복사하려는 로컬 파일의 경로

[ubuntu@IP](mailto:ubuntu@IP):/home/ubuntu/odsayapi/MeetHare-Location-Recommend/src/main/resources

- ubuntu : 원격 서버에 로그인할 사용자 이름
- **`ec2 Ip주소` :** 원격 서버의 IP 주소
- **`/home/ubuntu/odsayapi/MeetHare-Location-Recommend/src/main/resources`** : 원격 서버에서 파일을 저장할 경로

따라서 이 명령어는 로컬 시스템의 **`application-secret.yml`** 파일을 **`C:\MEETHARE\MeetHare-Location-Recommend\src\main\resources\application-secret.yml`** 경로에서 원격 서버의 **`/home/ubuntu/odsayapi/MeetHare-Location-Recommend/src/main/resources`** 경로로 복사하게 됩니다.
