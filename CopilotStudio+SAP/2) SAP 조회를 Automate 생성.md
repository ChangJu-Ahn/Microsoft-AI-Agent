실습 - SAP 조회를 Automate 생성
===

### 6.Power Automate & Connector 설정
1. 상단 작업 -> 작업 추가 -> 새 작업 -> 새 Power Automate 흐름을 눌러 신규 Automate flow를 생성합니다.
![image](https://github.com/user-attachments/assets/6bb1ebb4-0850-4302-83a3-8e134a028144)

2. Flow 이름을 'SAP 카테고리 기반 제품검색' 이라고 변경합니다.
![image](https://github.com/user-attachments/assets/8745c2d7-fd00-4fa8-a0d3-e802805f32f0)

3. 'Copilot에서 흐름 실행'을 누른 뒤 Input 변수를 추가합니다.<br><img width="400" alt="image" src="https://github.com/user-attachments/assets/fbc6c62a-b145-447c-be88-7badf1c6af53" />

5. 마찬가지로 'Respond to Copilot'을 누른 뒤 Output 변수를 추가합니다.<br><img width="400" alt="image" src="https://github.com/user-attachments/assets/25a7a952-e739-47f7-9018-03af23886c66" />

6. SAP Odata 작업을 추가합니다. 이때 선택할 커넥터는 'SAP Odata의 Odata 엔터티 쿼리' 입니다.
   <br><img width="400" alt="image" src="https://github.com/user-attachments/assets/9c3bf5e7-7985-4e1f-abce-59ed8f516126" />
   <br><img width="339" alt="image" src="https://github.com/user-attachments/assets/acb4128d-8037-4658-88dc-d47ee524e130" />
   <br><img width="337" alt="image" src="https://github.com/user-attachments/assets/f25c1685-1b23-4761-80bd-7adf4cc2959a" />
   <br>OData 기본 URI:
   <br>
    ```
    https://sapes5.sapdevcenter.com/sap/opu/odata/iwbep/GWSAMPLE_BASIC
    ```
7. Odata 엔터티 'Product Set'을 입력합니다. 이는 SAP Odata 표준 API입니다.
   <br><img width="335" alt="image" src="https://github.com/user-attachments/assets/44bfda9d-071c-4517-82af-29bdd222d87d" />
8. 'Show All'을 눌러 고급 매개변수에 필터를 입력합니다. 그리고 $Filter에 다음과 같은 명령어를 입력합니다.
   ![image](https://github.com/user-attachments/assets/c6a9d9c7-0ce5-4b07-a0d2-67e3ead0bad6)
   <img width="350" alt="image" src="https://github.com/user-attachments/assets/8b07ea0c-a5da-4355-ad39-77b466fdcfc0" />
   ```
   concat('Category eq ', '''', triggerBody()['text'], '''')
   ```
9. 그리고 output 변수를 설정하여 찾은 제품을 Agent에게 반환합니다.
   <br><img width="743" alt="image" src="https://github.com/user-attachments/assets/94eef669-1801-4182-879c-71c40761aedc" />
   <br><img width="743" alt="image" src="https://github.com/user-attachments/assets/9bb4578a-9b04-4e5c-ac2f-a73308972052" />

10. 만든 Flow를 테스트합니다. 이때 테스트는 수동, 그리고 입력할 input은 'Keyboards' 입니다.
    <br><img width="548" alt="image" src="https://github.com/user-attachments/assets/ad9fda42-65a6-4fcd-9cdf-cf288eb19b0d" />
    <br><img width="339" alt="image" src="https://github.com/user-attachments/assets/2f0e3389-192c-48bc-a7a5-58d72d07833b" />

11. 생성 및 테스트가 성공적으로 진행되었다면, 결과 값은 다음과 같습니다.
    <img width="633" alt="image" src="https://github.com/user-attachments/assets/ae5dac4c-c2da-405c-b179-428a6826b440" />

### 6. Copilot Studio & Power Automate 연결하기
1. 페이지 새로고침 후 다시 작업 -> 작업추가로 들어가서 방금 만든 Automate를 검색합니다. 
<img width="944" alt="image" src="https://github.com/user-attachments/assets/3b657db2-7e07-4301-830b-20dfe78c54c4" />

2. 선택 후 처음 페이지에서 AI가 이해할 수 있도록 다음 설명을 작성합니다. 그리고 작업추가 합니다.
   ```
    제품 카테고리. 이 목록에서 입력으로 선택할 수 있는 카테고리는 단 하나뿐입니다. 대소문자를 구분하며 아래와 같이 정확히 작성해야 합니다.
    Accessories;Notebooks;Laser Printers;Mice;Keyboards;Mousepads;Scanners;Speakers;Headsets;Software;PCs;Smartphones;Tablets;Servers;Projectors;MP3 Players;Camcorders
   ```
   <img width="776" alt="image" src="https://github.com/user-attachments/assets/a61acdc8-6557-4523-abfa-b8e5db58c9a6" />

3. 생성 후 다시한번 해당 작업에 들어가서 입력 / 출력할 때도 AI가 잘 이해할 수 있도록 추가 설명을 입력합니다.
   <img width="571" alt="image" src="https://github.com/user-attachments/assets/012f52f8-1f9e-4bfb-a0a1-c55c9a0de2d1" />

   [입력 설명]
   ```
    제품 카테고리. 이 목록에서 입력으로 선택할 수 있는 카테고리는 단 하나뿐입니다. 대소문자를 구분하며 아래와 같이 정확히 작성해야 합니다.
    Accessories;Notebooks;Laser Printers;Mice;Keyboards;Mousepads;Scanners;Speakers;Headsets;Software;PCs;Smartphones;Tablets;Servers;Projectors;MP3 Players;Camcorders
   ```
   [출력 설명]
   ```
   SAP에서 찾은 주어진 카테고리의 제품. 다음 정보를 포함하는 HTML 테이블로 결과를 제시합니다.
   ProductID; Name; Category; Description; Supplier; Price; Currency.
   ```

4. 저장 후 Agent를 테스트 창에서 테스트해 봅니다. 다음과 같이 테스트할 수 있습니다. Agent의 설정은 영어로 되어있지만, AI 오케스트레이션에서 임베딩처리 하여 동작하기 때문에 한글도 동작합니다.
   <br>만약 이때 Connect를 추가해야 한다고 인증창이 나온다면, Connect를 누른 뒤 다시한번 연결해 주고 새로고침 후 테스트합니다.
   ![image](https://github.com/user-attachments/assets/194cd5bd-a2f4-4b7e-a05e-670f4040b710)

   ```
   Keyboards 카테고리 제품 알려줘
   Show me Servers products in SAP
   노트북 관련한 정보
   ```
