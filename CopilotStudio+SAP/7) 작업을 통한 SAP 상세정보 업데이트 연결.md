실습 - 이미 만들어 둔 SAP 품목 상세정보 Automate를 재활용 하는 방법
===
SAP Automate를 기준으로 SAP 품목 상세정보를 조회할 수 있는 프로세스가 있습니다.   
이를 다시 응용하기 위해 Action에 추가하고, 사용자가 원할 경우 품목을 직접 입력해서 바로 상세정보를 볼 수 있도록 합니다.

1. Agent의 작업 신규 생성.
다시 Copilot Studio 화면으로 돌아옵니다. 그리고 상단의 **작업**을 선택하고, **작업 추가**를 누릅니다.
![image](https://github.com/user-attachments/assets/3ac5b5a6-56a7-4c96-a83e-37cc89738a66)

2. Automate를 검색해서 작업을 생성합니다.
![image](https://github.com/user-attachments/assets/14285319-5e27-46e4-b15a-65dc8152a799)

3. 우측 상단의 코드 편집기를 열고 아래 빨간색 테두리 영역의 GUID를 복사해 둡니다.
![image](https://github.com/user-attachments/assets/5815c813-f07c-4ae7-a761-fc0becb4f090)
![image](https://github.com/user-attachments/assets/34145dae-070b-4e07-ac34-f5da3223dd1c)

4. [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/CopilotStudio%2BSAP/Files/SAP%20%ED%92%88%EB%AA%A9%20%EC%83%81%EC%84%B8%EC%A1%B0%ED%9A%8C.yml)의 내용을 복사합니다.
**그리고 FlowId란에 위에서 복사해 둔 GUID 값으로 변경** 후 코드 편집기에 붙여넣습니다. 그리고 작업 추가를 완료합니다.
![image](https://github.com/user-attachments/assets/32179a38-b8c8-4503-a57c-74281ad440cf)
![image](https://github.com/user-attachments/assets/43b3d993-df1f-4b21-8edb-699589e39dd7)

5. 최종 작업은 다음과 같습니다.
![image](https://github.com/user-attachments/assets/e7a263ff-137a-40dd-85ea-051c4a2b6d94)
