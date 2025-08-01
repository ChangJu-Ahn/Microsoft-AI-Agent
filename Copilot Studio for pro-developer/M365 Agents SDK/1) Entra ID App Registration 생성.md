SSO 인증을 위한 Entra ID App Registration 설정을 진행합니다.
===

이 에이전트의 시나리오는 SSO가 적용된 로우코드 AI Agent를 코드 레벨로 통합하는 실습입니다. 

### 1. Entra ID App Registraion 등록
https://portal.azure.com에 접속하여, Entra ID -> App Registrations을 들어갑니다.
<img width="509" height="978" alt="image" src="https://github.com/user-attachments/assets/20cdfb0b-c183-4388-a97a-d85a3061dfd6" />

### 2. SSO 인증을 위한 '신규 App Registration'을 생성합니다. 
<img width="778" height="675" alt="image" src="https://github.com/user-attachments/assets/100d07f1-3598-4deb-918f-38630952b541" />
<img width="1155" height="1050" alt="image" src="https://github.com/user-attachments/assets/a134b6df-14ef-4d2d-ad86-00625ee5a7ab" />

이때 필요한 설정은 다음을 참고합니다.
1) Name: App Registration 이름을 입력합니다.
2) Account Type: 가장 첫 번째인 'Single tenant'를 선택합니다. 이미지의 빨간색 테두리를 참고하세요.
3) Redirect URL: SPA(Single-Page Application)을 선택한 후 서비스를 하고자 하는 URL을 입력합니다.
   > 아래 이미지는 깃헙 코스페이스에서 서비스합니다. 하여, 해당 URL을 직접 입력한 경우입니다.
   > 샘플 코드를 fork하여 로컬에 다운로드 받는다면, http://localhost:5173/ 을 입력하셔야 합니다.
   
### 3. 권한을 부여할 수 있는 API Permissions을 설정합니다.
다음과 같은 순서로 접근 후 API Permission을 설정합니다.
<img width="1947" height="1197" alt="image" src="https://github.com/user-attachments/assets/56050ef4-5fd7-401b-b915-d2721a79aca5" />
> 만약 Permission을 검색했는데, Power Platform API이 안 나온다면? [여기](https://learn.microsoft.com/en-us/power-platform/admin/programmability-authentication-v2?tabs=powershell#step-2-configure-api-permissions)를 참고하세요.

</br>

이후 다음과 같이 **Copilot Studio**를 검색해 아래 이미지의 권한을 선택하고 완료합니다.
<img width="1445" height="1117" alt="image" src="https://github.com/user-attachments/assets/94d95164-b044-4a21-8898-c74f6dd01d17" />

### 4. 설정한 권한을 다음과 같이 승인합니다.
<img width="1384" height="963" alt="image" src="https://github.com/user-attachments/assets/42cda5dd-da31-445c-97d5-d18f61d1fc48" />

### 5. 인증을 위한 secret을 생성합니다.
<img width="1903" height="1131" alt="image" src="https://github.com/user-attachments/assets/fbe9fa54-9db6-4a06-b3d5-eaed1d7a2584" />

</br>

그리고 아래 정보는 사용해야 하므로, 별도 공간(예: 메모장)에 기록해 둡니다.
<img width="1362" height="328" alt="image" src="https://github.com/user-attachments/assets/8a50eace-8b92-43d8-ab1d-b8ce54d96041" />

---

Entra ID 관련한 설정은 완료했습니다! :) 이제는 로우코드 AI 에이전트를 만들어볼까요?


