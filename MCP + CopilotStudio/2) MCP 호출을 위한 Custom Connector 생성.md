실습 - MCP 호출을 위한 Custom Connector 생성
===

준비가 다 된 MCP Server를 연결하기 위한 사전준비 작업입니다.
여기서는 로우코드 내 Custom Connector 라는 기능을 이용합니다.

---

### 1. Custom Connector 템플릿 생성
[여기](https://make.preview.powerautomate.com/) 사이트로 접속하여, 사용자 지정 커넥터를 선택합니다. 
![image](https://github.com/user-attachments/assets/fa0d015f-110f-425a-8f14-11d2eca4cf6f)

만약, 사용자 지정 커넥터가 좌측 메뉴에서 보이지 않는다면? 다음과 같은 방법을 사용할 수 있습니다.
![image](https://github.com/user-attachments/assets/6f640ee4-b7fa-429f-b4ad-a6cd532ed708)

다음과 같이 이름을 지정하여 커스텀 커넥터 형태를 생성합니다.
![image](https://github.com/user-attachments/assets/e723da8e-2bbe-4d38-bb4b-778d2fcfd88f)


### 2. 기준정보 채우기
[여기](https://learn.microsoft.com/ko-kr/microsoft-copilot-studio/agent-extend-action-mcp#mcp-server-schema-examples) 소스코드를 copy 해와서 메모장에 붙여넣습니다.
최신 버전의 소스코드는 위를 참고할 수 있고, 만약 동일한 MCP Server를 사용한다면 아래 내용 중 default의 value인 **<Your Key>** 부분만 변경합니다.
여기서 Key는 이전에 복사해 둔 Smithery URL에서 참고할 수 있습니다.

```
swagger: '2.0'
info:
  title: Smithery MCP for gen-image
  description: >-
    Smithery 기반의 MCP를 호출하는 예제입니다. Smithery 기반의 MCP를 호출하는 예제입니다. Smithery 기반의
    MCP를 호출하는 예제입니다. Smithery 기반의 MCP를 호출하는 예제입니다.
  version: '1.0'
host: server.smithery.ai
basePath: /@falahgs/flux-imagegen-mcp-server/mcp
schemes:
  - https
consumes: []
produces: []
paths:
  /:
    post:
      summary: Smithery MCP for gen-image
      x-ms-agentic-protocol: mcp-streamable-1.0
      operationId: InvokeServer
      responses:
        '200':
          description: Success
      parameters:
        - name: api_key
          in: query
          required: true
          type: string
          default: <Your Key>
          x-ms-visibility: internal
definitions: {}
parameters: {}
responses: {}
securityDefinitions: {}
tags: []
security: []
```

### 3. Swagger 기반의 Custom Connector 생성
위에서 만들어 진 Swagger를 기반으로 복사/붙여넣기를 통해 커스텀 커넥터를 생성합니다.
![image](https://github.com/user-attachments/assets/6c1700e9-175e-40ec-a2ee-410d20866b5a)


### 4. Custom Connector 업데이트
저장 후 이상이 없다면, 커넥터 업데이트 후 작업을 마무리합니다.
![image](https://github.com/user-attachments/assets/6586095c-8ebf-47cd-977e-df4a5cf496d8)

