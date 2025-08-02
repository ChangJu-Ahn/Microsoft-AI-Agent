Copilot Studio 제품을 잘 설명하는 AI 에이전트 제작
===

**[중요]**   
여기서는 Copilot Studio 제품을 잘 설명해 주기 위해 공식 문서 URL을 참고하는 간단한 에이전트를 만들어봅니다.   
이미 로우코드 AI 에이전트가 있다면, xx 항목부터 참고해서 인증정보만 설정하시면 됩니다.

### 1. 새로운 Custom Agent를 생성합니다.
https://copilotstudio.microsoft.com/로 접속하여 신규 에이전트를 생성합니다.
<img width="490" height="583" alt="image" src="https://github.com/user-attachments/assets/1e92a9bc-67c6-4220-8a89-7455146a24e5" />
<img width="2229" height="387" alt="image" src="https://github.com/user-attachments/assets/1299229e-0364-470b-87eb-4d1ebd8236a2" />

그리고 다음과 같이 언어 및 각종 지침을 입력합니다. 우측 상단의 언어는 반드시 **한국어**로 변경합니다.
<img width="1889" height="929" alt="image" src="https://github.com/user-attachments/assets/37f274ef-d071-463e-9e25-9bd24b859bce" />

Name:
```
코파일럿 스튜디오 가이드 에이전트 - 물어봐용!
```

Descirption:  
```
당신은 마이크로소프트 코파일럿 스튜디오의 제품 전문가입니다.
```

Instructions: 
```
당신은 아래 지침을 반드시 지켜야 합니다.

- 코파일럿 스튜디오 전문가 에이전트로 최대한 답변을 간단하게 요약하여 전달합니다.
- 각 답변에 필요한 예시를 추가합니다.
```

### 2. 참조자료 추가
아래와 같이 참조자료를 화면으로 들어갑니다.
<img width="1373" height="287" alt="image" src="https://github.com/user-attachments/assets/067a8e74-c8e6-4742-9b4b-d3868e015de7" />

</br>

<img width="1075" height="630" alt="image" src="https://github.com/user-attachments/assets/38a3c23b-870b-48de-96c5-f8d4ead03332" />


<img width="1047" height="262" alt="image" src="https://github.com/user-attachments/assets/e4e54e6b-2452-46bc-b2bb-cff4daf09717" />

이때 입력할 URL을 아래 주소를 참고합니다.
```
https://learn.microsoft.com/ko-kr/microsoft-copilot-studio
```

<img width="1059" height="736" alt="image" src="https://github.com/user-attachments/assets/2de29a35-0202-42e7-a385-58e63aa5bb96" />

### 3. SSO 연결을 위한 에이전트 보안설정
Entra ID App Registration과 연결을 위해 보안 설정을 변경합니다.
<img width="1883" height="337" alt="image" src="https://github.com/user-attachments/assets/abd49801-5860-4de8-bf5b-22b6ef61316d" />
<img width="809" height="533" alt="image" src="https://github.com/user-attachments/assets/120a234d-6d3e-4b83-af1c-01f50a2e5a4f" />
<img width="1142" height="962" alt="image" src="https://github.com/user-attachments/assets/2c11db14-6a79-4f18-af28-528d29dc858d" />
아래 3개의 빨간색 영역을 잘 입력합니다.
1) Service provider는 Entra ID V2 with client secrets으로 설정합니다.
2) Client ID는 Entra ID App Regiration 화면에서 참고할 수 있습니다.
   <img width="961" height="550" alt="image" src="https://github.com/user-attachments/assets/0474991d-c971-4f7c-ac92-d0cf64e79efc" />
3) Client secret는 기존에 만들고 저장해 놨던 'value' 값을 사용합니다.
   <img width="1362" height="328" alt="image" src="https://github.com/user-attachments/assets/77237804-efe6-4556-9d5b-f152a5aafa48" />

### 4. Entra ID App Registration에 Redirect URL 추가
Copilot Studio에서 사용하는 Redirect URL을 복사하여, 이전에 만들어 둔 App Regirstaion에 업데이트 합니다.

우선, Copilot Studio 설정 화면에서 아래 값을 copy 하여 복사합니다.
<img width="1116" height="443" alt="image" src="https://github.com/user-attachments/assets/b565d403-f6ed-4c33-877e-7781e03fc182" />

Entra ID App Registration에 들어와서 Redirect URIs를 클릭합니다.
<img width="1607" height="571" alt="image" src="https://github.com/user-attachments/assets/b3d613a3-4904-4c89-bbe7-ba9fcb4b187f" />

신규 URI를 추가합니다. 이때 입력할 URI은 이전에 copy해 둔 값입니다.
<img width="812" height="788" alt="image" src="https://github.com/user-attachments/assets/6fc66b24-748c-46b5-9b04-f934e39b83e9" />
<img width="750" height="500" alt="image" src="https://github.com/user-attachments/assets/4f85f201-ff37-4f3b-8272-70e9300615ca" />
<img width="759" height="451" alt="image" src="https://github.com/user-attachments/assets/29f5ed17-1ab1-4fd6-b672-761c921e09fe" />

### 4. 퍼블리시 및 테스트
코파일럿 스튜디오를 배포한 뒤에 SSO 적용이 되었는지 테스트합니다.

일단 다음과 같이 만든 에이전트를 배포합니다. 그리고 우측 상단의 에이전트 새로고침을 눌러, 로그인을 하라는 메시지가 나오는지 확인합니다.    
<img width="1862" height="374" alt="image" src="https://github.com/user-attachments/assets/ed0297d3-c45f-4594-ac2f-2f5b33df1bfb" />
<img width="645" height="922" alt="image" src="https://github.com/user-attachments/assets/e8836c3b-6873-477a-817b-72de9c18085b" />

로그인 후 에이전트가 정상동작하는지 확인합니다.    
<img width="645" height="922" alt="image" src="https://github.com/user-attachments/assets/e363108f-70fd-4025-b132-aaa332a73547" />








