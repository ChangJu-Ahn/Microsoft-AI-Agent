SSO 인증을 위한 Entra ID App Registration 설정을 진행합니다.
===

이 에이전트의 시나리오는 SSO가 적용된 로우코드 AI Agent를 코드 레벨로 통합하는 실습입니다. 

</br>

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
   


