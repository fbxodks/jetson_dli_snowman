# jetson_dli_snowman

``` bash ```

## jetsonnano 설명
<img width="341" alt="산인지 사진" src="https://github.com/user-attachments/assets/672157bf-d31a-4bb6-b349-41d23cd8ccaf">


![image](https://github.com/user-attachments/assets/402426fd-2d12-49c2-90df-da9111d3cdcf)

## 11/7 잿슨 나노 설치 과정
1.sd 카드 포멧터 다운 및 포멧팅


2. jetack 링크로 다운로드
<사진>
![image](https://github.com/user-attachments/assets/b0c9e79b-654e-4843-b68b-200f917684cf)


3. 발레나 에처 다운해서 이미지 굽기
![image](https://github.com/user-attachments/assets/14639b00-69c0-4ff1-9d3f-b63ad21ad82c)


4 - 1 SD카드 Jetson에 주의하여 꽂기

4 - 2 언어 한글로 설정

4 - 3 싱글보드 컴퓨터 만들고 와이파이 설정

4 - 4 Terminal로 들어간 후 한글 설정을 위해 명령어 입력

![image](https://github.com/user-attachments/assets/306b7943-6d94-4bda-8239-472f4ff2ec15)

## 11/14 카메라 설치 방법

1. 터미널 명령어 창을 열어서 명령어 입력
dli@dli-desktop:~$ sudo apt install python3-pip
![image](https://github.com/user-attachments/assets/e84e6f99-c829-4d35-9a27-0cbaf708e80d)


컴퓨터가 다음과 같이 물어보면 do you want to continue ? Y  Y라고 답한다.
![image](https://github.com/user-attachments/assets/58110532-d471-4e10-af3d-b6d1955a2b3b)

 다음 명령어 실행 - dli@dli-desktop:~$  sudo -H pip3 install -U jetson-stats
![image](https://github.com/user-attachments/assets/06c5a172-b366-42ec-a9e1-83229547630e)

에러가 나올시에 다음 명령어 입력 후 jetson-stats-4.2.3가 써진걸 확인
sudo apt-get upgrade, sudo apt-get update해준다.
![image](https://github.com/user-attachments/assets/12584daa-8d56-4652-829c-96207ef536a3)

확인후에 reboot를 진행하여 카메라를 설치한다.

2. 온도가 높을시에 쿨링팬 설치
![image](https://github.com/user-attachments/assets/84b4d553-a47b-4153-929b-02688b59d931)

터미널을 열고 명령어를 쳐본다.
sudo sh -c 'echo 128 > /sys/devices/pwm-fan/target_pwm'
![image](https://github.com/user-attachments/assets/6022b9a2-d81f-49f9-95b7-dd65cf2b6f6b)

해당 명령어 입력시 온도가 감소하는 것을 확인 할 수 있다.


3. 젯슨이 카메라를 인식하는지 다음 명령어를 통하여 확인한다.

dli@dli-desktop:~$  ls /dev/vi*

crw-rw----+ 1 root video 81, 0  1월  7 18:29 /dev/video0 - 아 창이 뜨면 확인 완료 되었다는 뜻
![image](https://github.com/user-attachments/assets/0f6159b0-4077-4313-bf29-04b5e31adb15)

다음 명령어
dli@dli-desktop:~$ git clone https://github.com/jetsonhacks/USB-Camera.git
![image](https://github.com/user-attachments/assets/23288863-5e64-48e1-b474-933ea5a25538)

*주의* CSI일시에 USB말고 CSI를 검색하여 명령어 가져오기

명령어 차례로 입력



dli@dli-desktop:~$ cd USB-Camera

dli@dli-desktop:~/USB-Camra$ ls

dli@dli-desktop:~/USB-Camera$ python3 usb-camera-gst.py 

dli@dli-desktop:~/USB-Camera$  python3 face-detect-usb.py




다음과 같이 카메라가 얼굴을 인식하는지 확인
![image](https://github.com/user-attachments/assets/39740e04-6bb8-4318-ad4f-574d14d62913)

## 11/21 헤드리스 모드 설정 및 claasification


헤드리스 모드란?


헤드리스 모드 jetson nano에 대한 이미지 검색결과 Headless mode 인 경우 Jetson은 모니터나 키보드가 필요하지 않습니다.
gui가 없이 젯슨의 화면은 검정색이 됩니다. (이를 '헤드리스' 모드라고 함). 

#추가설명
![image](https://github.com/user-attachments/assets/18eca900-9251-4ccd-8cb4-c08511e84978)

도커설치 방법

다음 코드를 순서대로 터미널에서 진행


<img width="690" alt="도커 사진1" src="https://github.com/user-attachments/assets/cf5e6646-efe7-45c0-b221-72903cf53251">

<img width="898" alt="도커 사진 2" src="https://github.com/user-attachments/assets/49d5b9bf-3b8b-4da6-972f-0f5bf01a1033">

<img width="935" alt="도커 사진 3" src="https://github.com/user-attachments/assets/a65ff9f0-4f78-4e0b-b6ac-c3e2ce382763">

<img width="977" alt="도커 사진 4" src="https://github.com/user-attachments/assets/f763b587-bf6a-46a0-b4eb-22404198c6b8">

*도커를 설치하는 이유는 classfication을 진행할 때 메모리가 부족할 수 있기 때문에 여유 저장공간을 만들기 위함이다.*

도커 설치후 주피터 접속하여 thumb up 샘플 30개 thumb down 샘플 30개 만들고 epoch 10으로 해서 학습시키기

![KakaoTalk_20241127_153504469_01](https://github.com/user-attachments/assets/e2255b4a-8e66-401f-b199-0ad48c54ea02)

![KakaoTalk_20241127_153504469_03](https://github.com/user-attachments/assets/4880e169-da9a-4186-a97a-5d4d2330b087)




이미지를 학습 시킨 후 카메라에 손을 가져다 대어 up으로 인식하는지, down으로 인식하는지 실행해본다. 


다음과 같이 젯슨을 학습시켜 이미지 분류 시스템을 만들 수 있다.










