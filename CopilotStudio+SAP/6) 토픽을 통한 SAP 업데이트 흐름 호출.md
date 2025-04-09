실습 - Agent의 토픽을 통해 Automate를 호출하여 SAP 정보 변경
===
마지막으로 직접 데이터를 호출하는 Automate를 Agent와 연결합니다.

1. Copilot Topic을 업데이트하여 업데이트 흐름을 호출
다시 Copilot Studio 화면으로 돌아옵니다. 그리고 이전에 만들었던 노드의 마지막에 방금 만든 Automate를 추가합니다.
![image](https://github.com/user-attachments/assets/95a78b1f-88b1-4ba3-beba-f9ffbb6572ec)

2. 적응형카드에서 출력변수로 받은 값을 Automate의 입력변수와 맵핑합니다.
![image](https://github.com/user-attachments/assets/c04e88a4-f057-4b43-8511-243b02a305ab)

3. 상단에 **변수** 탭에서 필요한 변수를 활성화합니다.
![image](https://github.com/user-attachments/assets/68d0c60f-fdd5-4b6f-a629-7b3be0375699)

4. 마지막 노드를 추가해서 Autoamte에서 반환한 값을 사용자에게 메시지로 전달합니다.
![image](https://github.com/user-attachments/assets/4869e4eb-95c9-40bf-9a11-c7be67853a33)

5. 그리고 저장을 눌러 토픽과 업데이트 프로세스의 연결을 마무리 합니다.
![image](https://github.com/user-attachments/assets/3ac65e17-c34f-4292-a607-ee87c846b605)

