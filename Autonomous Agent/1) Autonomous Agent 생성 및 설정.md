실습 - Autonomous Agent 생성
===

1) [여기](https://copilotstudio.preview.microsoft.com) URL을 통해 접속 후 좌측에 있는 **만들기**를 누릅니다.
![image](https://github.com/user-attachments/assets/27577404-175d-4646-9caa-72be7e07b94d)
    > https://copilotstudio.preview.microsoft.com/

<br/>

2) 자연어로도 에이전트를 만들 수 있지만, 여기서는 수동으로 생성합니다. 좌측 상단의 **새 에이전트**를 누릅니다.   
   그리고 **구성으로 건너뛰기**를 누릅니다.
   ![image](https://github.com/user-attachments/assets/faf6c82c-b25a-4d08-86eb-fb410f23a1fa)

   > 25/4/18일 기준, Copilot Studio의 AI Orchestration은 영어만 지원합니다. 하여, 여기서는 영어로 테스트합니다.
   
<br/>

3)  화면이 변경되면 아래 내용을 참고하여 **이름, 그리고 언어**를 변경하고 에이전트를 생성합니다.   
Autonomous Agent에서 중요한 AI Orchestion 기능은 25/4/18일 기준 영어만 지원합니다. 빠른 시일내에 한국어로도 지원할 예정입니다. 
   ![image](https://github.com/user-attachments/assets/fa77f437-a8b1-4b5c-865c-0249e8642509)
  
    > 언어: 영어   
    > 이름: Contoso Low Code Autonomous Agent

<br/>

4) 설명, 일반 지침, 그리고 오케스트레이션 기능을 활성화 합니다. 다음은 초기 화면으로 순서대로 작업을 진행합니다.
   ![image](https://github.com/user-attachments/assets/d54a0a6f-b01d-436a-8438-65cc82ec7595)   

  - (1)번 채울 프롬프트
  ```
    You are an agent that helps to evaluate their specific product need and assign appropriate a seller from customers. 
    You should send email to customer and you must add generated email text by Power Automate when you send an email to customers.
  ```

  - (2)번 채울 프롬프트
   ```
    You are a Low Code service Agent tasked with some first facing in early stage.
    
    You should follow the steps below without missing any. Once all actions are completed your work is finished.
    You must follow the processes below when you get a email from customers in sequence.
    
    1. Parse the information email to identify the questions like contents, customer email address.
    2. Extract a Product by reffering to email contents using Action.
    3. Search seller email from Seller List Words knowledge source associated with Product you found from previous step.
    4. Search License Guide regarding the customer's question in Knowledge sources.
    5. Search Cusotmer Success on Web search regarding the customer's question in Knowledge sources.
    6. Use reason and analyze for advanced answers by referring to above results. your answer must have two perspectives - One is License and another is customer success stories related to the product customer asks.
    7. Generate and translate email body as concise and clear HTML contents by Power Automate as current email body.
    8. Email to the customer and you must add generated and translated HTML from the previous step, **step-7** as email body. Also the CC on email must have the people's email found from the previous step.
    
    **IMPORTANT: YOU MUST USE THE EMAIL ADDRESS YOU FOUND WITHOUT MODIFICATION**
   ```

  - (3) 기능을 클릭을 통해 활성화 합니다.

<br/>

5) 다음은 설정이 완성된 모습입니다.

    ![image](https://github.com/user-attachments/assets/6fd01d79-7221-4ba6-9b7f-49010c4b561f)

---
짝짝짝. 에이전트를 잘 생성했습니다. 다음은 Autonomous Agent의 핵심인 트리거를 확인하러 가 봅시다.
