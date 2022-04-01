
## docker의 컨테이너에 우분투 18.04이미지를 다운받고 ros-melodic 및 실습 패키지까지 다운받았던 과정
- 나의 경우 로컬호스트는 우분투 20.04였음. 

1) 도커 설치 및 기본 명령어들 https://www.notion.so/2-Docker-47d55c78e4ca49e780ce8051818bbea1  https://blog.naver.com/padamu1/222140838918
2) http://wiki.ros.org/melodic/Installation/Ubuntu  ros-melodic 공식 설치 링크
3) 로컬의 파일, 폴더를 컨테이너 안으로 옮겨야 해서 다음 블로그 참고!  https://jayharvey.tistory.com/9 
   절대경로 찾을 때 터미널에 $pwd 입력하자.

- 도커를 사용하여 컨테이너에서 열심히 작업한 후 이미지를 저장해놓지 않으면 다시 들어와도 변경내용이 사라지는듯?
  - 왜냐면 ros-melodic까지 깔아놓고 roscore까지 작동되는걸 확인했는데 저장 전 컨테이너에서 roscore를 실행하니 적용이 안되었기 때문. 따라서 저장 관련 다음 링크 참고.
  - https://losskatsu.github.io/it-infra/docker03/#2-%EB%B3%80%EA%B2%BD%EB%90%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0
  - 도커도 깃허브처럼 이미지를 push하는게 있는데 이건 나중에 다시 알아보자..

- 새로 저장한 도커 이미지 이름 : ros_docker
  - docker run -it ros_docker:18.04 /bin/bash 사용하여 컨테이너로 들어간다.
  
- docker를 처음 설치하면 기본적으로 rviz, gazebo등의 시각화 도구를 사용할 수 없다. 
- rviz등을 입력했을때 QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root' qt.qpa.screen: QXcbConnection: Could not connect to display  대강 이런 오류가 뜨면 도커에서 하드웨어 가속을 사용할 수 있도록 설정을 해 줘야 한다고 한다. 
- https://wooono.tistory.com/123 참고 블로그
- http://wiki.ros.org/action/login/docker/Tutorials/Hardware%20Acceleration#nvidia-docker2  공식 레퍼런스 
==> 아직 미해결




#### 삽질기록
![Screenshot from 2022-03-29 09-30-38](https://user-images.githubusercontent.com/86426437/161102733-3e346259-023d-45d6-bd08-7e30a33a6f5e.png)
![Screenshot from 2022-04-01 00-34-22](https://user-images.githubusercontent.com/86426437/161102747-5303d70d-e3ab-46b1-b81a-c749dfecdf97.png)
![Screenshot from 2022-04-01 00-44-40](https://user-images.githubusercontent.com/86426437/161102757-0e5d31dc-3ecc-427f-a8df-65698771c2e0.png)
![Screenshot from 2022-04-01 00-50-33](https://user-images.githubusercontent.com/86426437/161102766-ff7a0e66-52f4-4e0f-9807-082a308c1768.png)
![Screenshot from 2022-04-01 00-55-41](https://user-images.githubusercontent.com/86426437/161102774-57116b17-84d6-4c85-9382-ac08c1a3f5d2.png)
![Screenshot from 2022-04-01 01-05-39](https://user-images.githubusercontent.com/86426437/161102782-f90242df-126f-4b27-9ce5-ed0f93f568cd.png)
![Screenshot from 2022-04-01 01-05-48](https://user-images.githubusercontent.com/86426437/161102790-b297b2ec-137c-44e0-a269-14a405bc3943.png)

- 주된 삽질은 패키지가 빌드되지 않아서였다. 의존하는 패키지, 부족한 패키지를 무한설치 해줌. 
