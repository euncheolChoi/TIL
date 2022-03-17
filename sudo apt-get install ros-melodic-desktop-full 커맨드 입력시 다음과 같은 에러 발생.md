### 우분투에서 ros 설치 과정 중 생긴 문제와 해결

### 환경
- 우분투 18.04 + ros melodic

### 문제 1)
- sudo apt-get install ros-melodic-desktop-full 커맨드 입력시 다음과 같은 에러 발생
E: /var/lib/dpkg/lock-frontend 잠금 파일을 얻을 수 없습니다 - open (11: 자원이 일시적으로 사용 불가능함)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

- 이에 대한 일반적인 해결책으로 먼저, 다음을 시도해 볼 것.
  - sudo rm /var/lib/apt/lists/lock
  - sudo rm /var/lib/apt/lists/lock
  - sudo rm /var/lib/dpkg/lock*
보통은 이 경우에서 해결이 되지만, 다음과 같은 오류 메시지와 함께 해결이 되지 않을 경우,

### 문제 2) 위의 해결책을 시도한 뒤 apt-get을 재시도했을때.
- sudo apt-get install ros-melodic-desktop-full 커맨드 입력시 다음과 같은 에러 발생한다면
E: dpkg가 중단되었습니다. 수동으로 'sudo dpkg --configure -a' 명령을 실행해 문제점을 바로잡으십시오.

  - 먼저 sudo dpkg --configure -a 커맨드를 입력한다.
  - 이때 다시 오류 메시지로 다음과 같이 특정 패키지를 설정할 때 오류가 생긴다면
    - binfmt-support (2.1.8-2) 설정하는 중입니다 ...
  - ps aux | grep -i dpkg 입력후 실행중인 dpkg 프로세스를 sudo kill -9 process_id 커맨드로 죽이고
  - 다시 sudo dpkg --configure -a 를 시도한다.
