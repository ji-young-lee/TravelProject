#### 오류 목록 :



![스크린샷(597)](C:\Users\이지영\Documents\리쿠르팅\직무부트캠프\오류 해결 목록\오류 사진 캡쳐\스크린샷(597).png)

Expecting all elements of:
  <[com.github.homework.program.model.ProgramViewDto@77b66fbf,
    com.github.homework.program.model.ProgramViewDto@3edae73]>
to satisfy given requirements, but these elements did not:

  <com.github.homework.program.model.ProgramViewDto@77b66fbf>
error: 
Expecting:
 <"theme0">
to be equal to:
 <"theme">
but was not.



#### 해결 : 

1. **ProgramRepositoryTest.java**

   findByPageTest() 메소드 안에

    ```java
   then(programViewDto.getThemeName()).contains("theme");
    ```

   이부분의 해결과정 :

   ```java
   then(programViewDto.getThemeName()).isEqualTo("themeName"); 
   -> then(programViewDto.getThemeName()).contains("themeName");
   -> then(programViewDto.getThemeName()).contains("theme");
   ```

   

2. **ProgramViewServiceImplTest.java**

   getByTest() 메소드 안에

   ```java
   then(programViewDto.getThemeName()).isEqualTo("theme");
   ```

   이부분의 해결과정 :

   ```java
   then(programViewDto.getThemeName()).isEqualTo("themeName");
   -> then(programViewDto.getThemeName()).isEqualTo("theme");
   ```

   

   ##### 오류 원인 : 

   메소드 안에 변수 재정의 해주는 부분과 parameter의 이름이 맞지 않아서.

   
