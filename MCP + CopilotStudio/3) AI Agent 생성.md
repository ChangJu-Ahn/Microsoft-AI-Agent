![image](https://github.com/user-attachments/assets/4d0f96fe-8d6c-4025-b16f-13e25df7b9df)실습 - Copilot Studio 기반의 AI Agent 생성
===

Copilot Studio에서 AI Agent를 생성한 후 설정한 MCP를 연결해 봅니다.

---

### 1. Copilot Studio Agent 생성
[여기](https://copilotstudio.preview.microsoft.com/)를 접속하여, 좌측 **Create** 항목에서 에이전트를 신규로 생성합니다.
![image](https://github.com/user-attachments/assets/6ee6cb33-71d5-4237-a3b5-a95ff3e14ba0)

이후 우측 상단에 설정 제외(Skip to Configure)를 누른 후 다음과 같이 간단하게 이름을 입력한 에이전트를 생성합니다.
![image](https://github.com/user-attachments/assets/f75e5ba9-6b73-4c91-9956-4f7000f02408)


### 2. AI Agent 내 MCP 설정
에이전트가 생성되었다면, 상단의 Tool을 선택합니다.
![image](https://github.com/user-attachments/assets/1371e0c8-a691-43ac-bf81-06502a505307)

이후 **도구 추가**를 누른 후 **Model Context Protocol**을 선택합니다.
![image](https://github.com/user-attachments/assets/c30c8533-07fa-41d7-bc7c-995be41c7c3d)


### 3. MCP 선택 후 커넥션 생성
위에서 검색된 MCP 중 직접 설정한 MCP를 선택합니다.
이후, 다음과 같은 화면에서 커넥션이 없다면 생성 후 **Add to Agent**를 선택 후 마무리합니다.
![image](https://github.com/user-attachments/assets/55dd4dcf-9943-4225-bb52-52d174d6a3f4)

### 4. Copilot Studio Tool에 추가된 MCP 확인
추가된 MCP가 이상이 없다면, 다음과 같이 상세정보 보기를 했을 때 MCP에서 사용이 가능한 Tool이 검색됩니다.
![image](https://github.com/user-attachments/assets/d3480f59-4398-4b7e-bfa4-18276b4b8bc2)

### 4-1. 커넥션이 필요하다면? 다음과 같이 추가 설정
만약 테스트를 할 때 다음과 같이 커넥션 안내가 발생한다면?
![image](https://github.com/user-attachments/assets/5ac4d885-04e1-4acf-99be-a3f42788f429)

위 빨간색 테투리를 선택하고, 커넥션을 생성 & 연결합니다. 정상적으로 연결되었을 때는 빨간색 영역이 **Conencted**로 변경됩니다.
![image](https://github.com/user-attachments/assets/97cfec26-dc6e-418f-a72e-67fc942126b6)

### 5. MCP가 연결된 Copilot Studio AI Agent 테스트
다음과 같이 Activity를 추적할 수 있는 기능을 켠 뒤에 새로고침을 실행합니다.
![image](https://github.com/user-attachments/assets/483fc510-7e6e-4ad1-af75-b6234aa49e86)

이후 원하는 프롬프트를 입력하여 결과가 잘 나오는지 확인합니다.
```
마이크로소프트 로고를 배경으로 너무나 사랑스러운 강아지 이미지를 생성해 줘
```
![image](https://github.com/user-attachments/assets/94e23ad3-59e3-4454-b976-da7a4d48e063)


