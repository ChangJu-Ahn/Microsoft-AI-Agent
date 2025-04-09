실습 - Agent에서 SAP 값 변경하기
===

지금까지 Agent를 생성하고 SAP의 값을 적응형카드로 표현하는 것을 진행했습니다.
이번에는 이러한 기능을 가지고 SAP 데이터를 직접 변경해 보고자 합니다. 


---
### 1. SAP 데이터 변경을 위한 Power Automate 생성 
make.powerautomate.com 으로 접속하여, 이 전에 만들었던 'SAP 품목 상세 조회'를 다른이름으로 저장합니다.   
여기서는 'SAP 품목 정보 변경'으로 입력합니다.
![image](https://github.com/user-attachments/assets/3de0db11-a5b5-42f6-b1f1-bbbde9378d2f)

<br/>

복사된 Flow는 꺼져있을 수 있으므로 아래와 같이 설정을 통해 켜도록 합니다.
![image](https://github.com/user-attachments/assets/51a13e46-d503-46d2-bdce-046e3a93be25)

<br/>

편집 화면에 들어와서 아래 항목을 삭제하고, 'Odata 엔티티 업데이트'을 선택합니다.
![image](https://github.com/user-attachments/assets/ab57b03f-acea-474f-b64b-b5287a9b6e28)
![image](https://github.com/user-attachments/assets/f929f304-0847-4f9f-888c-7ec6707ea7bd)

<br/>

엔티티 이름을 'ProductSet'으로 설정하고, 필수 검색 조건인 ProductId에 Agent에서 전달받은 Input 변수를 입력합니다.  
![image](https://github.com/user-attachments/assets/df871720-7892-4e48-a5d2-8333abff98b4)

<br/>

고급 매개변수에서 Agent와 연동해서 값을 변경하고자 하는 컬럼을 선택합니다.
![image](https://github.com/user-attachments/assets/19227dbd-1352-4578-b297-95806996492c)

<br/>
추가한 파라미터의 값을 Agent에서 받아올 수 있도록 입력 변수를 아래와 같이 설정합니다.   
이때 **Price의 경우는 숫자 타입**으로 지정합니다.
![image](https://github.com/user-attachments/assets/87dae1a1-d1c3-4dc5-a41c-2e33c59adcf3)
