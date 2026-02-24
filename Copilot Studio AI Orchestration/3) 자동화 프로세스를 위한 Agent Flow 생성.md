실습 - 자동화 프로세스를 위한 Agent Flow 생성
===

## 자동화를 위한 Agent Flow 생성
다음과 같은 경로로 들어가 신규 Flow를 생성합니다.
![image](https://github.com/user-attachments/assets/e2a8d151-1b7c-48f5-8a07-fd02c43bd478)

</br>

## Flow 내 트리거 및 액션 설정
우선, 해당 Flow를 실행하기 위한 트리거를 설정합니다. 여기서는 에이전트에서 호출하기 때문에 **에이전트가 흐름을 호출할 때**로 변경합니다.
![image](https://github.com/user-attachments/assets/88d8b8f5-8fdc-4cf4-882e-e892b17d1c99)

</br>
그리고 변수를 추가합니다. 여기서는 휴가일자, 사유 라는 두 개의 입력변수를 String type으로 생성합니다.   
<img width="2000" height="1035" alt="image" src="https://github.com/user-attachments/assets/7fed318e-5f0f-47a9-9850-3dac08d5dfac" />

</br>

## 1,400개 이상의 커넥터 연결
라이선스에 따라 사용 유뮤가 판단됩니다. 하여, 실제 필요한 방법으로 매칭해서 진행합니다.   
아래 시나리오는 M365 아웃룩 또는 Google 캘린더, 둘 다 어렵다면 임시 값을 반환하는 방법 중 **한 개를 선택**해서 진행합니다.

> [!NOTE]
> 아래 3개의 케이스 중 하나를 선택해서 진행합니다. 선택 기준은 현재 가지고 있는 라이선스를 기반으로 합니다.
> 케이스 1: 아웃룩 켈린더 연결 - [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/edit/main/Copilot%20Studio%20AI%20Orchestration/3)%20%EC%9E%90%EB%8F%99%ED%99%94%20%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EB%A5%BC%20%EC%9C%84%ED%95%9C%20Agent%20Flow%20%EC%83%9D%EC%84%B1.md#%EC%BC%80%EC%9D%B4%EC%8A%A4-1-m365%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B3%A0-%EC%9E%88%EC%96%B4-outlook%EC%9D%98-%EC%BA%98%EB%A6%B0%EB%8D%94%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8B%A4%EB%A9%B4)
> 케이스 2: 구글 캘린더 연결 - 여기
> 케이스 3: 임의 값 반환 - 여기

### 케이스 1. M365를 사용하고 있어, OutlooK의 캘린더를 사용할 수 있다면?
Power Automate는 1,400개 이상의 커넥터가 이미 만들어져 있습니다.   
또한, 고객의 레거시 API를 기반으로 만들 수 있는 **커스텀 커넥터**라는 기능도 제공합니다. 여기서는 이미 만들어진 아웃룩 커넥터를 사용합니다.
![image](https://github.com/user-attachments/assets/f9f2b66e-ce0f-45c9-a3f7-caac43d2142c)

아웃룩 커넥터 내 이벤트 생성 액션을 사용합니다. 다음과 같이 일정 ID를 입력하고, *fx* 라는 버튼을 누릅니다.
![image](https://github.com/user-attachments/assets/f3b4c636-f294-452a-a6bd-525bc357c977)

이 모드에서는 Power Fx는 물론, 이미 설정된 변수도 모두 사용할 수 있습니다. 여기서는 트리거에서 생성했던 변수 중 **사유**를 입력할 수 있도록 합니다.   
![image](https://github.com/user-attachments/assets/ff1de02b-2ea8-491e-84f0-21bc91981300)

시작/종료시간은 data type이 일반 날짜 형식이 아니라 시간까지 포함된 형식으로 입력해야 합니다.   
즉, 트리거링에서 입력변수는 텍스트로 받았지만, Power Fx를 사용해서 데이터 타입을 변경해야 합니다. 

여기서는 **Copilot으로 식 만들기** 기능을 이용해 자연어로 엑셀과 같은 Power Fx 함수를 생성합니다. 그리고 확인을 누릅니다.
![image](https://github.com/user-attachments/assets/8e3ab925-10d7-4dcb-80ff-cd0344e26368)
![image](https://github.com/user-attachments/assets/f9d4d70a-e36a-4ecc-b855-453c7119aced)

```
트리거의 텍스트 입력변수인 날짜 항목을, '2017-08-29T04:00:00'과 같이 변경해 줘
```

> **중요!** 만약 **Copilot 으로 식 만들기**가 안 보인다면? 아래 수식을 붙여넣습니다.
```
formatDateTime(triggerBody()?['text'], 'yyyy-MM-ddTHH:mm:ss')
```

위에서 입력한 값을 **종료 시간**에도 복사/붙여넣기 하고, 마지막으로 표준 시간대를 **'Seoul'**로 변경합니다.
![image](https://github.com/user-attachments/assets/c901f1bc-63ff-4259-8ea0-9238f1ff160d)

### 케이스 2. 구글 캘린더 연결



### 4. Flow 이름 변경
Agent Flow의 이름과 설명을 변경하기 위해 다음과 같은 경로로 클릭하며 넘어갑니다.   
그리고 에이전트 플로우의 이름을 **휴가 상신 자동화**로 변경합니다.
![image](https://github.com/user-attachments/assets/82aedaa9-2c12-455e-ad4d-32ebfe9cf263)

</br>

### 5. 게시 및 테스트
테스트를 위해 다음 이미지와 같이 **게시**를 진행합니다.
![image](https://github.com/user-attachments/assets/934c9775-1a2b-40fd-92ff-667f76398873)

</br>

이후, 테스트창으로 넘어와 다음과 같이 입력해 봅니다. 정상적으로 반영되었다면, 아웃룩 캘린더에서 결과를 확인할 수 있습니다.
![image](https://github.com/user-attachments/assets/e687604a-b289-452a-a0fc-9e2fcf685fb8)
![image](https://github.com/user-attachments/assets/1d49cc29-005e-475a-b057-68d4a5838308)


---
만약 테스트시 오류가 발생한다면, Power Fx 오류일 수 있습니다. 아래 코드를 디자이너 내 시간/종료 시간에 붙여넣기합니다.
![image](https://github.com/user-attachments/assets/12659dcc-f018-47b5-be93-41c14cb3a353)



