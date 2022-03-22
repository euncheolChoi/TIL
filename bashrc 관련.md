### 3/22 다연프 ROS 토픽 주고받는 예제 따라하던 중
- rosrun test talker.py 와 rosrun test listener.py 를 입력하니 [rospack] Error: package 'test' not found 에러가 발생.
  - 이유 : 만든 package를 build하기 위해서 catkin_make를 실행한 다음에, 수정된 사항을 적용해주기 위해  $ source ~/catkin_ws/devel/setup.bash를 입력해야 해야 했기 때문.
  - source는 bashrc 관련 명령어
  - 하지만 터미널을 닫고 다시 $ rosrun test talker.py 를 실행하면 같은 오류가 뜬다. 즉 매번 $ source ~/catkin_ws/devel/setup.bash 를 입력해야 한다. 
    - 따라서 이런 수고를 덜기 위해 $ gedit ~/.bashrc 로 .bashrc 파일을 열고 그리고 나서 파일 맨 아래에 $source ~/catkin_ws/devel/setup.bash 를 저장해준다.
    - 한 번만 해주면 다음부터는 자동으로 적용되니 catkin_make 후에 $ source ~/catkin_ws/devel/setup.bash를 다시 입력할 필요가 없다. 
