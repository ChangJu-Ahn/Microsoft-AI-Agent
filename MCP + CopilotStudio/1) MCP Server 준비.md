실습 - MCP Server 준비
===

사용할 MCP Server를 준비하는 단계입니다.
여기서는 Smithery 라는 MCP 공유 사이트에서 한 개를 특정하여 사용합니다.

---

### 1. Smithery 회원가입 및 MCP Server 검색
[여기](https://smithery.ai/)에서 회원가입을 진행합니다.  
그리고 아래 이미지와 같이 Gen AI 기반의 MCP Server를 선택합니다.

![image](https://github.com/user-attachments/assets/d43e82ef-2ab7-4c1b-878c-8d3e33620411)

</br>

### 2. MCP Server 설정
외부에서 해당 MCP를 접속할 수 있도록 URL을 생성합니다.
![image](https://github.com/user-attachments/assets/531b839e-d87c-40e9-9b75-dc5acd9c2a50)

</br>

이후 생성된 링크를 복사합니다. 여기에는 접속을 위한 Key 정보가 포함되어 있습니다.  
(= 아래 이미지에서는 모자이크 처리된 부분입니다)
![image](https://github.com/user-attachments/assets/dde4c6c2-62cf-4c00-9122-3893a5704658)


</br>

기타(= MCP Server 테스트를 위한 방법)
===
위와 같이 준비가 되어 있다면, MCP Inspector 라는 Tool로 테스트가 되어야 합니다.
**MCP Inspector**는 MCP 서버를 테스트하기 쉽게 테스트하기 위한 도구입니다. 자세한 내용은 [여기](https://github.com/modelcontextprotocol/inspector) 에서 참고할 수 있습니다.   
(= 개발자용 도구이며, 아래 캡쳐는 Visual Studio Code에서 Node.js기반으로 진행한 내용입니다)

### 1. MCP Insprctor 실행
Visual Studio Code를 실행한 후, 터미널 창에서 다음 명령어를 실행합니다.

```
npx @modelcontextprotocol/inspector
```

![image](https://github.com/user-attachments/assets/5e6f2dc9-6175-45b0-a0fb-01f94451026b)


### 2. MCP Inspector URL 실행
정상 동작 후 세션 토큰까지 발급된 링크를 클릭합니다. (클릭은 컨트롤 + 마우스 좌클릭)
![image](https://github.com/user-attachments/assets/fb28fb30-9822-4710-885f-6e5ebe8f178f)

### 3. 테스트를 위한 MCP Server 정보 입력
MCP Inspector Tool은 모든 MCP Server를 테스트할 수 있도록 설계되어 있다. 여기서는 위 내용 중 **(2)항에서 복사한 URL**을 입력하고 **Connect**를 클릭합니다.
![image](https://github.com/user-attachments/assets/e300ac85-25d8-4b92-9ced-7e0321c870cd)

### 4. Tool 반환 및 MCP Server 동작 테스트
MCP Server가 정상적으로 동작한다면, 다음과 같이 **Tool** 이라는 버튼이 활성화됩니다.
![image](https://github.com/user-attachments/assets/a23ea5a9-7da8-4c1c-9627-f77a253c9a81)

이후에는 해당 MCP Server가 가지고 있는 Tool List를 볼 수 있고, 테스트를 하게되면 다음과 같은 결과를 확인할 수 있습니다.
![image](https://github.com/user-attachments/assets/44c69b30-b587-4c07-9161-3f3faee0c843)
![image](https://github.com/user-attachments/assets/b71c4c80-d25e-4e97-b8ee-c7979d8bdb80)


