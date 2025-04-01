실습 - Copilot Studio의 AI Search Connector로 연동하기
===

AI Search 의 결과를 Copilot Studio로 바로 연결합니다.
이 아키텍처는 AI Search에서 받은 검색결과를 Copilot Studio의 GPT를 활용해 요약해 답변합니다.

<br/>

---


### 1. Copilot Studio를 통한 Custom Agent를 생성
간단하게 Agent를 생성하고 AI Search를 연결합니다.

1) [Copilot Studio](https://copilotstudio.microsoft.com/)로 접속하여 좌측 에이전트를 클릭합니다.   
![image](https://github.com/user-attachments/assets/0048fcd0-da73-4ba4-8543-eeb5925e1b18)

2) New Agent를 클릭한 뒤, 우측 상단의 Skip to configure를 클릭합니다.
![image](https://github.com/user-attachments/assets/a1bb61eb-ac68-4c9d-91f4-b490bef43dd0)
![image](https://github.com/user-attachments/assets/47866562-ca69-4138-9093-c4dac5d25e0a)

3) Agent의 이름을 입력하고 creat를 눌러 Custom Agent를 생성합니다.
여기서는 AI Search Agent라는 이름으로 만듭니다.
![image](https://github.com/user-attachments/assets/0508af21-ef9b-464a-9047-3c605c5971fa)

4) 에이전트가 생성되면 화면에서 지식(Knowledge) 탭으로 들어갑니다.
![image](https://github.com/user-attachments/assets/a6b0d53e-e14e-491c-a33f-71b0ad1f47ab)

5) Add Knowledge(지식 추가)를 누른 뒤 Advanced 항목에서 Azure AI Search를 클릭합니다.
![image](https://github.com/user-attachments/assets/5f001f1f-7497-4d7b-8f7f-122f3fda98df)

6) Azure AI Search를 연결하기 위한 설명을 입력합니다.    이때 입력한 설명은 Custom Agent이 사용자의 의도를 파악해서 AI Search Connector를 실행하는 기준이 됩니다.
   하여, 현재 Azure AI Search에서 제공하는 정보에 대한 자세한 내용을 적어주는 것을 추천합니다. 여기서는 기본 값으로 입력합니다.
![image](https://github.com/user-attachments/assets/790707d4-8830-4132-8c42-20ca67bff4d3)

7) Azure AI Search를 연결할 때 필요한 엔드포인트 및 액세스 키를 입력합니다.    다양한 인증 방식이 있지만, 여기서는 가장 기본인 Access Key 기준으로 연결합니다.
      
   a. Authentication type: Access Key    
   b. Azure AI Search Endpoint URL: AI Search 리소스 -> overview 항목 중 우측 상단의 URL 값    
   c. Azure AI Search Admin Key: AI Search 리소스 -> 설정 -> 키 -> 관리자 키 관리 -> 기존 관리자 키의 값    

![image](https://github.com/user-attachments/assets/a2ca9824-18eb-4d29-8062-9c857ad01370)
![image](https://github.com/user-attachments/assets/4fdcf87f-87fd-4592-8195-b68b04eb614e)
![image](https://github.com/user-attachments/assets/5dedc178-2f40-440a-b22d-5f74652942dc)

8) 생성 후 다음과 같이 정상 체크가 표시됨을 확인한 후 Next 
![image](https://github.com/user-attachments/assets/ee992a72-3175-4126-8c71-bd09289dc297)

9) 선택한 Azure AI Search 리소스에서 원하는 Index를 선택한 후 마무리
![image](https://github.com/user-attachments/assets/e32f68f7-8c81-4b71-b16b-d98266f28c8b)

10) Knowledge 탭에 Azure AI Search가 잘 저장되었는지 확인 후 테스트
![image](https://github.com/user-attachments/assets/32e0d4f2-533d-4235-9f83-f635b95747eb)
![image](https://github.com/user-attachments/assets/79c12251-432a-4989-a0ea-b0ab5ef2d4cd)

11) 기본적으로 Copilot Studio에서는 대화 이력을 이어가기 때문에 추가 질문도 쉽게 가능.
![image](https://github.com/user-attachments/assets/fde1ad54-3063-453e-8e79-7e595257534a)

12) 간단히 만들어진 Azure AI Search + Custom Agent를 다양한 채널로 즉시 배포
![image](https://github.com/user-attachments/assets/fa0be857-67b5-4a7c-a64d-35a48691f922)

<br/>

> 이렇게 만들어진 Custom Agent는 다양한 채널에서 서비스가 가능합니다.    
> 이런 아키텍처라면, Azure AI Search 뿐 아니라 다양한 API & 엔드포인트를 연결한 에이전트를 생성할 수 있습니다.    
> 이렇게 만들어진 에이전트는 다양한 디자인을 포함할 수 있으며, 실제 예시는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/tree/main/AdaptiveCardSamples#%EC%8B%A4%EC%A0%9C-%ED%99%94%EB%A9%B4%EC%9D%84-%EA%B8%B0%EB%B0%98%EC%9C%BC%EB%A1%9C-%ED%95%9C-%EC%BC%80%EC%9D%B4%EC%8A%A4-%EC%98%88%EC%8B%9C) 를 참고하여 주세요.

