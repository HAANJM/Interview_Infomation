# ETC

- Cron
- 리팩토링(refactoring)
- 유니티(Unity)
- ROS(Robot Operating System)

## Cron
Cron(크론)은 소프트웨어 유틸리티로써 유닉스 계열 컴퓨터 운영 체제의 시간 기반 잡 스케줄러이다. 소프트웨어 환경을 설정하고 관리할 때 고정된 시간, 날짜 간격에 주기적으로 실행할 수 있도록 스케줄링을 도와주는 도구이다. 매일 저녁에 하루의 데이터를 정리하거나, 아침에 기본 세팅을 설정하는 부분을 스케줄링할 수 있다.

윈도우용 크론 설치 참고 : https://decdream08.tistory.com/67

크론을 설치하게 되면 폴더에 cron.tab 이라는 파일이 생기게 되고, 이 파일을 크론 표현식에 맞춰 작성하면 그에 맞추어 실행된다. 크론을 실행하기 위해서는 cmd창에서 크론이 설치된 폴더로 이동한 후, startcron.bat를 통해 실행하고 stopcron.bat로 종료할 수 있다. 혹은 윈도우의 서비스를 통해서 관리할 수 있다.

크론 표현식은 <주기 커맨드>의 형태로 구성된다. 주기의 경우 다양한 주기를 설정할 수 있고, 커맨드에서는 윈도우 배치 파일(.bat)이나 자바/파이썬 등의 파일을 실행할 수 있다.

표현식 참고 : https://zamezzz.tistory.com/197

주기 설정 참고 사이트 : http://www.cronmaker.com/;jsessionid=node0q1vadruy4kh6na1h672govdm134701.node0?0 / https://crontab.guru/

## 리팩토링(refactoring)
리팩토링은 소프트웨어 공학에서 '결과의 변경없이 코드의 구조를 재조정함'을 뜻한다. 주로 가독성을 높이고 유지보수를 편하게 하는데 목적을 둔다. 사용자가 보는 외부 화면은 그대로 두면서 내부 논리나 구조를 바꾸고 새건하는 유지보수 행위이다. 리팩토링의 잠재적인 목표는 소프트웨어의 설계, 구조 및 구현을 개선하는 동시에 소프트웨어의 기능을 보존하는 것이다. 리팩토링은 코드의 가독성을 향상시키고 복잡성을 감소시키는 효과를 가지며 일관성이 떨어지는 코드에 일관성을 부여한다. 이러한 이점은 소스 코드의 유지 보수성을 개선하고 확장성을 개선하기 위해 더 깔끔하고 표현력이 뛰어난 내부 아키텍처 또는 객체 모델을 만들 수 있게 한다. 
가독성은 팀 개발에서 매우 중요한 부분이다. 하나의 프로젝트를 완성하기 위해서는 내가 작성한 코드 뿐 아니라 팀원이 작성한 코드까지 완벽하게 알아볼 수 있어야 한다. 그리고 프로젝트를 완성한 뒤에도 서비스를 위해 코드를 꾸준히 관리하기 위해서는 코드의 가독성이 요구될 것이다.
### 그래서 언제?
1. 유사한 내용이 세 번 이상 반복될 때 리팩토링을 고려
무조건 하는 것이 아니라 상황을 고려하여 리팩토링을 결정한다.
2. 새로운 기능을 추가할 때
새로운 기능을 추가할 때 현재 코드와 충될되는 부분, 코드를 추가하기 어려운 부분이 있다면 리팩토링을 고려해야 한다. 
3. 코드리뷰를 할 때
협업하는 개발팀과 함께하는 코드리뷰는 코드의 질을 높일 수 있다. 수월하게 코드리뷰를 하기 위해 리팩토링을 통해 가독성을 향상시킬 필요가 있다.

## ROS
로봇 운영체제(ROS,Robot Operating System)는 로봇 응용 프로그램을 개발할 때 필요한 하드웨어 추상화, 하위 디바이스 제어, 일반적으로 사용되는 기능의 구현, 프로세스간의 메시지 패싱, 패키지 관리, 개발환경에 필요한 라이브러리와 다양한 개발 및 디버깅 도구를 제공한다. ROS는 로봇 응용 프로그램 개발을 위한 운영체제와 같은 로봇 플랫폼이다.

### ROS1 / ROS2 차이

<img src="./img/ros_version.png">

### Bridge_launch 노드
ssafybridge_launch.py 실행 시 4개의 노드가 자동으로 실행됨

- udp_to_pub
1. 각각의 data_type(envir_status, app_status, turtlebot_status, imu, custom_object_info)에 맞춰 퍼블리셔를 생성
2. ssafy_udp_parser 노드의 erp_udp_parser 메소드를 이용하여 해당하는 유저 ip와 포트에 맞게 udp데이터를 파싱
- sub_to_udp
- udp_to_cam
  ```
  params_cam_0 = {
      "SOCKET_TYPE": 'JPG',
      "WIDTH": 320, # image width
      "HEIGHT": 240, # image height
      "FOV": 60, # Field of view
      "localIP": "127.0.0.1",
      "localPort": 1232,
      "Block_SIZE": int(65000),
      "UnitBlock_HEIGHT": int(30),
      "X": 1.7, # meter
      "Y": 0,
      "Z": 1.2,
      "YAW": 0, # deg
      "PITCH": -5,
      "ROLL": 0
  }
  ```
  1. 주어진 params_cam_0 데이터를 utils.py의 UDP_CAM_Parser 메소드에 전달하여 카메라로 촬영하는 데이터를 수신
  2. CompressedImage를 발신하는 퍼블리셔 생성
  3. 받아오는 데이터의 바이트가 0이 아니라면 jpeg로 포맷하여 퍼블리싱
- udp_to_laser

ssafy_bridge 패키지에는 존재하나 실행되지 않는 노드

cam_viewer

- sub1의 perception 노드와 비슷한 역할을 진행
- 시뮬레이터의 터틀봇이 촬영하는 이미지 데이터를 실시간으로 전송하여 외부의 창을 통해 송출하는 역할
- 존재하나 launch.py에 포함되지 않아 실행되지는 않는다

ssafy_udp_parser

- ssafy_bridge 패키지의 노드들이 기능을 위해 필요한 클래스를 포함
    - erp_udp_parser
 
```
      def __init__(self,publisher,ip,port,data_type):
    
    				# udp_to_pub 에서 실행할 때 받아온 매개변수 세팅
            self.ip=ip # UDP 데이터를 수신할 IP 주소
            self.port=port # UDP 데이터를 수신할 포트 번호
            self.publisher=publisher # 데이터를 발행하는 데 사용되는 객체
            self.data_type=data_type # 수신된 데이터의 유형을 지정하는 문자열
    				
            self.is_sender_port=False # 송신 정보 포트
    			
    				# UDP 통신에 필요한 socket 객체 생성
            self.sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    
    				# 수신할 ip주소와 port 번호를 튜플로 생성합니다
            recv_address = (self.ip,self.port)
    				# 튜플로 생성한 ip주소와 port번호를 소켓에 바인딩합니다
            self.sock.bind(recv_address)
    				# 데이터의 최대 크기 설정, 65535바이트
            self.data_size=65535 
    				# 파싱한 데이터를 받기 위한 빈 배열을 초기화
            self.parsed_data=[]
    
    				# UDP 데이터를 비동기적으로 처리하기 위한 스레드 생성
    				# recv_udp_data 메소드가 이 스레드의 작업대상
            thread = threading.Thread(target=self.recv_udp_data)
    				# 스레드를 데몬 쓰레드로 설정
    				# 데몬 쓰레드 : 백그라운드에서 작동
            thread.daemon = True 
    				# 쓰레드를 시작하여 UPD 데이터를 비동기적으로 수신
            thread.start()
```
```
      def recv_udp_data(self):
        while True : # 무한반복
    				# 수신한 UDP 데이터를
    				# raw_data : 수신한 데이터
    				# sender : 송신자의 정보(주소 및 포트)
            raw_data, sender = self.sock.recvfrom(self.data_size)
            
    				# raw_data에 저장된 UDP 데이터를 처리하기 위해 data_parsing 메서드를 호출
    				# data_parsing : 주어진 데이터를 파싱하고 처리
    				self.data_parsing(raw_data)
            
    				# is_sender_port 의 값이 False일 때만 실행
    				# 초기에 False로 지정하고 아래의 코드 블럭이 실행되면 True로 변하기 때문에
    				# 송신 포트 정보를 처음 수신했을때만 실행되는 코드이다
            if self.is_sender_port == False :
                self.is_sender_port= True # True로 설정하여 송신 포트 정보를 한번만 저장하도록 한다
                self.sender_port=sender[1] # 송신자 정보 sender에서 포트 번호(sender[1])를 추출하여 저장
    
    				# 처음 수신한 데이터의 송신 포트 정보를 저장
    				# 나중에 데이터를 보낼 때 적절한 포트로 데이터를 전송할 수 있다
```
```
      파싱되기 전의 바이너리 형태의 raw_data

        b'#Turtlebot$ \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x83\x9a>\xb6\x00\x00\x00\x00\x00\x00\x00\x00\x00ta\x16\xc1dt\xf6\xc0\x80\\\xc4:\x08\xa7\xb4B\x00\x00\x00\r\n'
        b'#Enviroment$\x06\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x01\x0b\t\x01\r\x00\r\n'
        b'#hand_control_pub$\xf0\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\r\n'
        b'#Appliances$\x11\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\x02\r\n'

      data_parsing 메소드
      
      if self.data_type=='turtlebot_status': # data_type에 따라 실행할 코드블럭 분리
          # print(raw_data)
          header=raw_data[0:11].decode() # raw_data의 11번째 항목까지 decode하여 header로 설정
          data_length=struct.unpack('i',raw_data[11:15])
          if header == '#Turtlebot$' and data_length[0] ==32:
              msg=TurtlebotStatus()
      				# struct.unpack 하단 추가 설명
      				# 각 데이터에 맞는 값을 가져와 msg에 넣어주는 과정
              ego_status_data=struct.unpack('2f',raw_data[15+12:15+8+12])
              battery_charge_status=struct.unpack('B',raw_data[15+8+12:15+8+12+1])[0]
              battery_percentage=struct.unpack('f',raw_data[15+8+12+1:15+8+12+1+4])[0]
              msg.twist.linear.x=ego_status_data[0]
              msg.twist.angular.z=ego_status_data[1]
              msg.power_supply_status=battery_charge_status
              msg.battery_percentage=battery_percentage
      
              x,y,z,heading=struct.unpack('4f',raw_data[15+8+12+1+4:15+8+12+1+4+16])
              msg.twist.angular.x=x
              msg.twist.angular.y=y
              msg.twist.linear.z=heading
      
              hand_status=struct.unpack('???',raw_data[56:59])
              msg.can_use_hand=hand_status[0]
              msg.can_put=hand_status[1]
              msg.can_lift=hand_status[2]
      
      				# msg 퍼블리시
              self.publisher.publish(msg)
```
