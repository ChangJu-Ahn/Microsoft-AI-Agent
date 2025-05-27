실습 - 에이전트 로직을 위한 Topic 생성
===

### 12. 일정 생성을 위한 신규 토픽 생성
에이전트 화면으로 돌아와 상단의 **토픽**을 선택합니다. 
![image](https://github.com/user-attachments/assets/f493914f-f1fa-49fb-a22b-7cba3dbcb78f)

</br>

**새로 시작**을 누르고, 상단 트리거에 맥락을 입력합니다.   
그리고 다음과 같이 입력합니다. 이는 AI Orchestration이 해당 맥락에 맞는 질문이 들어오면 이 토픽을 실행하게 됩니다.
![image](https://github.com/user-attachments/assets/ea4856e9-f016-4fb6-a159-e8f69a879b76)

```
이 토픽은 사용자의 일정을 관리하는 토픽입니다. 사용자가 자신의 일정을 생성하거나 삭제할 수 있습니다. 이 토픽은 한 번에 한 개의 일정만 상신할 수 있습니다.
```

### 13. 신규 토픽의 Slot 채우기 기능을 위한 추가 옵션 설정
상단 세부정보의 아래 경로로 들어와 새 변수를 2개 추가합니다.
![image](https://github.com/user-attachments/assets/e15910d4-1eca-4eb7-910b-6ea2bc5b322f)

1) VarData
   - 변수 타입: String
   - 표시 이름: VarData
   - 다음으로 식별: 선택
   - 설명
       ```
        사용자 캘린더에 반영할 변수입니다. 
        날짜를 AI가 파악해서 일반적으로 사용할 수 있는 [yyyy-mm-dd] 형태로 정보를 저장합니다.
      ```
2) VarDescription
   - 변수 타입: String
   - 표시 이름: VarDescription
   - 다음으로 식별: 선택
   - 설명
        ```
        일정에 대한 제목입니다.   
        예를 들면 '가족 행사', '병원 진료', '개인 사유' 등과 같이 왜 휴가를 썼는지에 대한 사유라고 생각할 수 있습니다.
        ```

</br>

### 14. 사용자에게 질문하기 위한 추가 로직 설정
사용자가 입력을 안 했다면? 직접 AI가 물어볼 수 있는 로직을 구현합니다.   
아래와 같이 간단하게 설정하고, 일정 및 사유를 입력받는 변수를 위에서 설정한 변수로 지정합니다.
![image](https://github.com/user-attachments/assets/78d04572-e7ad-4c38-849c-766a962a6ab5)


### 15. Topic 내 자동화 프로세스 연결
노드를 추가해 아래와 같이 이전에 만들어 둔 Agent Flow를 연결합니다.
![image](https://github.com/user-attachments/assets/721e0bf3-6fdf-42fd-841d-f44147d12c2d)

</br>

그리고 이전에 입력받았던 변수를 그대로 입력 변수로 전달합니다.   
![image](https://github.com/user-attachments/assets/847f9afd-b3f6-485c-8eea-b3f9cd0c8d41)

</br>

마지막으로 **상신을 완료했습니다. ** 라는 간단한 메시지를 출력 후 저장을 눌러 마무리합니다.
![image](https://github.com/user-attachments/assets/953462c6-1f9e-4b61-97d6-940b7433c81e)

