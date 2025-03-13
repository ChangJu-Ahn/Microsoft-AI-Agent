SAP AI Agent 실습 (Or any data! :)
============
이 실습에서는 AI를 활용하여 Microsoft + SAP 제품을 최적화하는 방법을 알아봅니다. 
SaaS 제품인 Copilot Studio를 활용하면, 별도의 호스팅 서버가 필요없고 연동할 수 있는 서비스(서버)만 필요합니다.
또한, Copilot Studio의 장점인 채널을 활용하면 추가 개발 없이 Teams, Web, 그리고 M365 Copilot로 바로 배포하여 사용할 수 있습니다.

여기서는 SAP와 연결하지만, Power Automate의 1,400개 커넥터 / 더 나아가서 기업 시스템과 연동 및 관리할 수 있습니다.


>원본은 아래에서 참고할 수 있고, 저는 여기에 한국 특성에 맞게 더 커스터마이징 한 내용을 담습니다.
https://techcommunity.microsoft.com/blog/sapapplications/sap--teams-integration-with-copilot-studio-and-generative-ai/4213260**
----

완성된 데모 영상 #1 (SAP AI Agent in Microsoft Teams)
===
동영상 위치(with 자막 및 설명 필요)

----

완성된 데모 영상 #2 (SAP AI Agent in Microsoft 365 Copilot)
== 
동영상 위치(with 자막 및 설명 필요)

----

실습 시나리오
== 

- 예: SAP AI 제품정보 Agent
  - 시나리오: Contoso의 제품 관리자는 SAP 시스템에서 제품 정보를 정기적으로 검토하고 업데이트해야 합니다.
  - 솔루션: Copilot Studio에서 제공하는 SAP와 Teams 통합을 통해 Contoso의 제품 관리자는 SAP에서 현재 제품 정보를 쉽게 얻고 적응형 카드에서 편리하게 사양을 업데이트할 수 있습니다.
    
Copilot Studio 및 Generative AI를 사용하여 SAP를 Microsoft Teams와 통합하면 생산성을 크게 향상하고 워크플로를 간소화할 수 있습니다. 여기서는 Power Platform과 SAP Odata Connector를 이용합니다.
그리고 최종 결과물은 AI Agent를 생성하고, Teams 및 M365 Copilot으로 배포하고, 제너레이티브, 사용자와 소통할 수 있는 적응형 카드(Adaptive Card)를 만들고 SAP의 데이터를 변경할 수 있습니다. 

----

실습
===
### 1. 솔루션 개요
Copilot Studio, Power Automate Flow 및 SAP OData Connector 세 가지 주요 구성 요소로 구성하고, Microsoft Teams & Microsoft 365 Copilot으로 배포합니다. 다음 도식화는 구성 요소의 작동방법을 보여 줍니다.<br> <img width="500" alt="image" src="https://github.com/user-attachments/assets/c981bfd2-f23d-4b21-8a5c-e063787cf6fa" />

### 2. 사전 요구사항
Agent 구축을 시작하기 전에 Power Platform 및 SAP 시스템에 대한 액세스 권한이 있는지 확인해야 합니다. 회사에서 사용할 수 있는 라이선스 및 SAP 시스템을 활용하거나 Power Platform 및 공개 SAP 데모 시스템에 대한 평가판 라이선스를 사용할 수 있습니다. 다음 링크는 이러한 리소스가 아직 없는 경우 이러한 리소스를 얻는 방법을 안내합니다.

### 3. Power Platform 액세스 요청 및 라이선스
만약 Power Platform 라이선스가 없다면, 여기서 평가판 라이선스를 신청합니다.<br>https://learn.microsoft.com/en-us/power-apps/maker/signup-for-powerapps

### 4. SAP 시스템 액세스
만약 SAP 시스템이 없다면, 여기서 SAP Gateway 데모 시스템 ES5를 요청합니다.<br>https://developers.sap.com/tutorials/gateway-demo-signup.html

### 5. Copilot Studio를 통한 AI Agent 생성
1. Copilot Studio 내에 있는 코파일럿을 활용하여 에이전트를 생성합니다. 이때 참고해야 할 프롬프트는 다음과 같습니다.
   <img width="1123" alt="image" src="https://github.com/user-attachments/assets/9e353d9f-de0d-452d-a133-07d969d2043b" />
   ```
   SAP 제품정보 에이전트를 만들고 싶어. 
   이 에이전트의 목적은 사용할 수 있는 제품정보를 SAP 시스템을 통해 사용자에게 제공을 목적으로 해. 
   에이전트가 답변할 때는 HTML 테이블 형태로 출력할 수 있어야 해.
   ```
2. AI가 제안한 내용을 확인한 후, 에이전트 이름이 마음에 든다면 '예'라고 입력합니다.<br>그리고 프롬프트를 기반으로 제안된 Agent의 언어를 한국어 -> 영어로 변경합니다.
   <br>(= 25년 3월 기준, AI 오케스트레이션 기능이 영어만 지원함)
   ![image](https://github.com/user-attachments/assets/fe82ff69-b6a4-480c-b41e-905df19ecc98)


4. AI 오케스트레이션 기능을 사용하기 위해 기능을 활성화 한 뒤 저장합니다.
   경로는 선택된 에이전트를 기준으로 설정 -> 생성형 AI -> 생성형(프리뷰) 입니다.
![image](https://github.com/user-attachments/assets/f1e51344-f76c-4fdd-bee4-f3b3d721b901)

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
   
### 7. 완성된 AI Agent를 Microsoft Teams, 혹은 Microsoft 365 Copilot에 배포합니다. 
1. 우선 만들어진 Agent를 게시합니다. 게시는 우측 상단에 있습니다. <br><img width="500" alt="image" src="https://github.com/user-attachments/assets/a72b7506-2445-4f94-9cb2-37ba7c8e6336" />

3. 이후 채널에서 Teams & Microsoft 365에 배포합니다.
![image](https://github.com/user-attachments/assets/2e69b3b6-0e13-4028-a5c1-d1a263f360c0)
![image](https://github.com/user-attachments/assets/6716081e-a6e0-4f72-9645-9de148672de0)

4. 벌써 완료했습니다. 참 쉽죠? Copilot Studio + SAP를 결합하여 카테고리 기준의 데이터를 팀즈에서 조회할 수 있습니다.
![image](https://github.com/user-attachments/assets/b32a1099-ca95-48bf-b87b-6f6ab01a9bde)

5. 마찬가지로 위에서 Microsoft 365 Copilot으로 배포하면, Copilot Agent로도 사용할 수 있습니다. <br><img width="949" alt="image" src="https://github.com/user-attachments/assets/fa19308c-389f-4653-84f4-285cf0d45285" />


Advanced AI Agent by Copilot Studio
<br>(+ Topic Logic & Adaptive Card & Sharing Variables)
===
Comming Soon...
   



