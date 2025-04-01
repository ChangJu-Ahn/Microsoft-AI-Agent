실습 - AI Search Index 간단하게 생성하기
===

### 기본 조건 - Microsoft Azure 테넌트 및 구독이 있어야 합니다.
> Azure 회원가입 및 간단하게 교육용 Subscription을 받는 내용은 아래를 참고해 주세요.  
> www.aaa.ccc

<br/>

AI Search는 일반 개발 언어로도 작업이 가능합니다. 즉, 여기서 하는 모든 작업을 프로그램 코드로도 진행할 수 있습니다.    
이미 AI Search를 기반으로 RAG Architecture를 구성할 수 있는 유저라면, 간단하게 보고 넘기는 것을 추천합니다.
> 한국어 버전의 코드 샘플 및 참고 깃헙리포는 다음을 참고합니다.  
> https://github.com/Azure-Samples/azure-ai-search-samples-kr
<br/>

---

### 1. 검색할 문서 선정
간단한 실습을 위해 문서를 선정합니다. 여기서는 해당 경로 하위에 있는 File 폴더 내 Power Apps Coding Standard 문서를 참고합니다.
<br/>

---

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
<br/>

---

### 3. 파일 원본을 Azure Blob Storage에 저장하기
파일을 Blob Storage에 저장합니다. 이는 향후 AI Search의 인덱스를 각종 문서 기반으로 만들 때도 동일한 패턴이 사용될 수 있습니다.

1) portal.azure.com 에서 스토리지 계정을 클릭합니다.
![image](https://github.com/user-attachments/assets/45f528c5-2113-45bf-9859-6847381a9633)

2) Blob Storage를 신규로 생성합니다.
![image](https://github.com/user-attachments/assets/7974a3ec-9e75-4797-afde-9a6953a59119)

3) 아래 내용을 참고해서 리소스를 생성합니다. 이때 **기존에 만든 리소스 그룹에 함께 포함**시켜둡니다. 이는 실습 후 리소스를 삭제하는 데 중요한 역할을 합니다.
![image](https://github.com/user-attachments/assets/0af08aa5-14b4-4dad-9640-f54d70cbc25e)

4) 검토 후 만들기를 실행합니다. 이후 만들어진 Blob Storage 리소스로 이동합니다.
이후 파일을 저장할 수 있는 컨테이너를 신규로 생성합니다.
![image](https://github.com/user-attachments/assets/95b02615-1bc1-461c-9a35-8281fc07d892)
<img width="295" alt="image" src="https://github.com/user-attachments/assets/d57fe152-940d-4d43-bb10-42bc75b8c6a2" />

5) 이렇게 만들어진 컨테이너에 파일을 업로드합니다.   
![image](https://github.com/user-attachments/assets/ed8fc236-cd34-49d9-b273-dfd26b615b4e)

6) 파일이 업로드된 최종 모습입니다.
![image](https://github.com/user-attachments/assets/31747b2a-e39e-45e9-8596-99b31a829258)

<br/>

---

### 4. 데이터 가져오기 및 벡터화 작업 진행
AI Search에 바로 데이터를 불러와 벡터작업을 할 수 있는 기능이 있습니다. 이번 시간에는 해당 기능을 이용합니다.

1) 상단 데이터 가져오기 및 벡터화를 클릭합니다.
![image](https://github.com/user-attachments/assets/bfaad821-d6a2-465e-8761-a9cb67ac2868)

2) 데이터 연결설정에서 Azure Blob Storage를 선택합니다.
![image](https://github.com/user-attachments/assets/c0d03c44-4e9b-42a3-b488-66f142da2d9e)

3) 위에서 만든 Blob Storage 및 컨테이너를 선택합니다.
![image](https://github.com/user-attachments/assets/eb7e8bb9-67c5-40d1-ae74-1e8aec62e850)

4) 다음은 값에 대한 벡터화(임베딩)을 위한 리소스를 설정합니다. 아직 Azure OpenAI 임베딩 모델이 없다면, 아래를 참고하여 Azure OpenAI 리소스를 생성합니다.
![image](https://github.com/user-attachments/assets/cf0a8849-0119-45cb-8e3e-6182152eb42f)   
![image](https://github.com/user-attachments/assets/416873fe-0ef1-4043-bf01-c29ab589c5a4)

5) 생성한 Azure OpenAI 리소스로 이동합니다. 이후 정보를 벡터화 하기 위한 모델을 생성합니다.   
![image](https://github.com/user-attachments/assets/28cdb45e-c753-4b9d-9c0e-03e56dc9b8ce)

6) 이후 정보를 벡터화하기 위한 모델을 생성합니다.
![image](https://github.com/user-attachments/assets/510dc281-11aa-4ab7-b601-956e3722d484)
![image](https://github.com/user-attachments/assets/3ed77f80-e950-489d-a750-9bb2db081477)

7) 최종 Deployment 후 리소스가 잘 생성되었는지 확인합니다.
![image](https://github.com/user-attachments/assets/d0f13ebf-c76d-4831-aa95-27b44aa5c842)

8) 이후 다시 AI Search 화면으로 돌아와 위에서 생성한 임베딩 모델을 선택 후 다음으로 이동합니다.
![image](https://github.com/user-attachments/assets/6bdacd5a-a5f5-46a4-a5cb-ccfad128a22e)

9) 이후 '이미지 벡터화', '고급 설정'은 기본으로 두고 최종 리소스를 생성합니다.
이미지 벡터와도 위와 같은 패턴으로 이미지에 대한 값을 벡터화해서 저장하는 걸 의미하고, re-raking 기능은 조금 더 정확한 값을 반환할 때 사용하는 고급 기능입니다.
> AI Search는 다양한 고급 검색 기능을 제공합니다. 상세 기능은 아래 영상을 참고하세요.    
> https://www.youtube.com/watch?v=Xwx1DJ0OqCk

10) AI Search Index를 생성하기 위해 최종 '만들기' 버튼을 클릭합니다.
![image](https://github.com/user-attachments/assets/e6a62648-3dbf-43b1-a7b8-9ada070357ad)

<br/>

---

### 5. 생성한 AI Search 테스트 해 보기
위에서 문서 기반으로 간단히 벡터검색을 구성한 인덱스를 테스트합니다.

1) 작업이 완료되면, 인덱스 탭에 생성된 인덱스를 확인할 수 있습니다.
![image](https://github.com/user-attachments/assets/c0896ea1-b858-4252-857a-8668b1804cb0)

2) 원하는 검색어를 입력하고 검색을 눌러 결과가 나오는지 확인합니다.
![image](https://github.com/user-attachments/assets/ba6d6d60-7ea8-4578-9b92-9170129f16f6)

<br/>

---


