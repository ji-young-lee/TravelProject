### Error Message

------

```java
Could not find or load main class worker.org.gradle.process.internal.worker.GradleWorkerMain
```

<img src="C:\Users\이지영\Documents\리쿠르팅\직무부트캠프\오류 해결 목록\gradle오류 사진\image-20210111230125860.png" alt="image-20210111230125860" style="zoom:67%;" />

<img src="C:\Users\이지영\Documents\리쿠르팅\직무부트캠프\오류 해결 목록\gradle오류 사진\image-20210114010030391.png" alt="image-20210114010030391" style="zoom:67%;" />

<img src="C:\Users\이지영\Documents\리쿠르팅\직무부트캠프\오류 해결 목록\gradle오류 사진\image-20210111230204718.png" alt="image-20210111230204718" style="zoom:67%;" />



#### 문제점

​	빌드는 제대로 되는데 test가 안됨. gradle 문제로 파악됨



---



#### 해결과정

1. 

   * intellij 같은 버전(2020.3.1) 로 두번이나 깔고

   * 파일도 다시 git clone  ,

   * jdk도 여러개로 바꾸다가 11.0.9 설치 후 변경

   * jdk 설정 확인 (path와 JAVA_HOME) 

   * intellij에서 structure 수정 => jdk 버전 수정

   * setting 에서 gradle 를 default에서 IntelliJ IDEA로 변경

   <img src="C:\Users\이지영\Documents\리쿠르팅\직무부트캠프\오류 해결 목록\gradle오류 사진\image-20210114012705949.png" alt="image-20210114012705949" style="zoom:50%;" />

   ​	

   ​	=> 이 경우는 junit.jar가 없다고 나오는데 junit5라서 junit jupiter로 되어있다. dependency		에서 확인 가능

   * 코멘드에서 파일 디렉토리로 들어간 후 rm -rf ./.idea 후에 다시 부팅

   * ./ gradlew test

   * ./gradlew build

   * ./gradlew clean build

2. 

   * 여기서 다시 git clone 하고 1 반복 ㅎ

   * ./gradlew --stop 후에 ./gradlew test : 다른게 돌고 있을 확률이 있기에

     역시나 안됨

3. 

   * 윈도우 버전으로 설정된 파일 다시 다운받음

   * 인텔리제이에서는 여전히 오류 코멘드(git bash)에서 ./gradlew test 실행시 성공
   * Windows Defender 예외처리
     * windows defender 보안센터 -> 바이러스 및 위협방지 ->제외 추가 또는 제거->제외 사항 추가 > 프로세스 > idea64.exe, fsnotify64.exe

4. 

   * intellij 다시 설치
   * settings 에서 옵션설정
     * editor -> general -> auto import 에서 'add unamiguos imports on the fly' , 'optimize imports on the fly' 에 체크

   

   

   ### 결론

   ---

   

   intellij를 세번 지웠다 다시 설치하니 되었다...

   그 전에는 환경변수의 사용자 변수에 intellij가 추가 안되었나 싶긴한데

   결론은 다시 설치하는것으로,,,

   

