
AI Search 생성하기
===

### 기본 조건 - Microsoft Azure 테넌트 및 구독이 있어야 합니다.
> Azure 회원가입 및 간단하게 교육용 Subscription을 받는 내용은 아래를 참고해 주세요.  
> www.aaa.ccc

<br/>

AI Search는 일반 개발 언어로도 작업이 가능합니다. 즉, 여기서 하는 대부분의 작업을 프로그램 코드로 진행할 수 있습니다.
> 한국어 버전의 코드 샘플 및 참고 깃헙리포는 다음을 참고합니다.  
> https://github.com/Azure-Samples/azure-ai-search-samples-kr
---

### 1. 검색할 문서 선정
간단한 실습을 위해 문서를 선정합니다. 여기서는 해당 경로 하위에 있는 File 폴더 내 Power Apps Coding Standard 문서를 참고합니다.

### 2. AI Search 리소스 생성
Azure portal에서 AI Search를 생성합니다. 간단하게 생성하는 절차는 다음을 참고합니다.

1) portal.azure.com으로 접속 후 AI Search를 검색합니다. (한글로는 'AI 검색' 이라고 입력합니다)
![image](https://github.com/user-attachments/assets/4f8c49a1-0670-4799-b761-2b4f8870779c)

2) AI Search 리소스 진입 후 신규 리소스를 생성하기 위해 생성 버튼을 누릅니다.   
![image](https://github.com/user-attachments/assets/ddf15080-b704-4d30-98d9-fe2a22116270)

3) 리소스를 생성하기 위해서 다음과 같이 리소스 및 이름 & 위치를 입력합니다.
![image](https://github.com/user-attachments/assets/1ebd29e4-608d-4781-9a5d-ea5e9fb8fb77)
<br/>

가격 책정의 기본 값은 '표준'입니다. '기본'으로 변경하고 리소를 생성합니다.   
실습 이후에는 해당 리소스를 지울 예정이기 때문에, 실습 후 별도의 비용이 발생하지 않습니다.  
<br/>
**중요: 실습 후 리소스를 지우지 않는다면, 비용이 계속 발생할 수 있습니다.**
![image](https://github.com/user-attachments/assets/825da36a-85f4-4897-97d4-6207192b1cf1)

4) 검토 및 만들기를 클릭하여 최종 리소스를 생성합니다.
생성이 완료되면, 다음과 같은 알림창을 확인할 수 있습니다. 알림창에서 리소스로 이동하여 리소스를 확인합니다.   
![image](https://github.com/user-attachments/assets/443731e1-3e08-47f6-b165-633ba5d222e1)

### 3. 데이터 가져오기 및 벡터화 작업 진행
AI Search에 바로 데이터를 불러와 벡터작업을 할 수 있는 기능이 있습니다. 이번 시간에는 해당 기능을 이용합니다.
