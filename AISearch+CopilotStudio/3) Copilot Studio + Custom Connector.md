실습 - Power Platform Custom Connector로 Azure AI Search를 연결하기.
===

Power Platform의 Custom Connector는 Power Platform 내 1,400개 이상의 커넥터에 내가 원하는 API가 없을 때 사용할 수 있는 기술입니다.    
여기서 얻어가야 할 중요한 포인트는 다음과 같습니다.

1) 여기서는 Azure AI Search를 Rest API 형태로 호출할 수 있도록 설정합니다.
2) Power Platform Custon Connector는 모든 형태의 Rest API를 호출할 수 있습니다.
3) 만약 다른 RAG Architecture, 자사 AI Model, 그리고 기타 고도화된 AI 시스템의 Rest API를 동일하게 연동할 수 있습니다.

<br/>

---

### 1. Custom Connector 생성.
Power Platform 전체에서 사용가능한 Custom Connector를 생성합니다.

1) make.powerapps.com 으로 이동하여, Custom Connector 항목을 찾습니다.
![image](https://github.com/user-attachments/assets/67cdc30d-1c42-4a9c-9fd5-dfec7ef0c59c)
![image](https://github.com/user-attachments/assets/d8f24246-e752-4bd5-8bf4-0ec15009d48d)

2) API를 호출하는 방식으로 간단하게 구현할 수 있습니다. 여기서는 공백인 상태에서 시작합니다.    이름은 Azure AI Search로 입력합니다.
![image](https://github.com/user-attachments/assets/82b35b24-31e4-4ba7-b374-b92af8480372)

3) 아래 Swagger를 copy하여 붙여넣기합니다. 이때 포인팅된 두 군데의 내용을 알맞게 변경합니다.    
![image](https://github.com/user-attachments/assets/c6491d91-1e5c-424b-92bd-017b2b459762)

```
swagger: '2.0'
info:
  title: Azure AI Search Connector
  description: Custom connector for Azure AI Search
  version: 1.0.0
host: {your-search-service-name}.search.windows.net
basePath: /indexes/{index-name}/docs
schemes:
  - https
consumes:
  - application/json
produces:
  - application/json
paths:
  /search:
    post:
      summary: Search documents in Azure AI Search
      operationId: SearchDocuments
      parameters:
        - name: api-version
          in: query
          required: true
          type: string
          default: 2023-07-01-Preview
        - in: body
          name: body
          required: true
          schema:
            type: object
            properties:
              search:
                type: string
                example: 성능저하
              count:
                type: boolean
                default: true
              vectorQueries:
                type: array
                items:
                  type: object
                  properties:
                    kind:
                      type: string
                      enum:
                        - text
                    text:
                      type: string
                      example: 성능저하
                    fields:
                      type: string
                      example: text_vector
              queryType:
                type: string
                enum:
                  - semantic
              semanticConfiguration:
                type: string
                example: vector-1743511685565-semantic-configuration
              captions:
                type: string
                enum:
                  - extractive
              answers:
                type: string
                example: extractive|count-3
              queryLanguage:
                type: string
                default: en-us
              select:
                type: string
                example: title,chunk
                title: ''
                default: title,chunk
              top:
                type: integer
                default: 10
      responses:
        '200':
          description: Successful response
          schema:
            type: object
securityDefinitions:
  api_key:
    type: apiKey
    in: header
    name: api-key
security:
  - api_key: []


```
4) 우측 상단에 Update Connector 누른 뒤 좌측 상단의 리스트 중 Test로 이동합니다.
![image](https://github.com/user-attachments/assets/27e0d9a1-d4c6-4896-8ad4-098795937a24)

5) New Connection을 눌러 Azure AI Search Key를 입력한 뒤 커넥션을 생성합니다.
![image](https://github.com/user-attachments/assets/e74a0433-fedb-4ffb-aad3-4005160ad8dd)

6) API를 잘 호출하는지 확인합니다.
![image](https://github.com/user-attachments/assets/3c60182c-ea77-46cc-b6e8-d2f4c61d9db0)    
![image](https://github.com/user-attachments/assets/2f3d35d1-317b-457c-a5af-f9329199452a)

7) 이번에 생성한 내용을 연결하기 위해 기존에  만들어 둔 Custom Agent에 연결된 AI Search를 삭제합니다.   혹시 이 리소스가 없다면, 여기는 skip 하도록 합니다.    
![image](https://github.com/user-attachments/assets/274f4a38-37fe-4262-acfe-e5a3b8cb6a31)

8) Copilot Studio 상단에 있는 Action 탭에서 여기서 만든 Custon Connector가 검색될 수 있도록 필터링 합니다.
![image](https://github.com/user-attachments/assets/ff36a623-2e23-42b5-9532-c906d0b5c85d)

9) 그리고 검색된 Custom Connector를 선택하고 커넥션을 생성합니다.  이전에 잘 생성해 두었다면, 기존에 만들어진 커넥션이 바로 연결됩니다.
![image](https://github.com/user-attachments/assets/cd652bf4-9dff-442d-80af-070fd3dbc672)

10) 일단 Action을 생성한 뒤 우측 상단의 **Open code editor**를 엽니다.    그리고 아래 코드를 복사 및 붙여넣기 합니다.
![image](https://github.com/user-attachments/assets/71d432cb-0ae0-485d-a425-8a58c23afbdc)


```
kind: TaskDialog
modelDisplayName: Search documents in Azure AI Search
modelDescription: This information answers Power Platform overall best practices, performance issues, and coding standard guide.
inputs:
  - kind: ManualTaskInput
    propertyName: top
    value: 10

  - kind: ManualTaskInput
    propertyName: "'api-version'"
    value: 2023-07-01-Preview

  - kind: ManualTaskInput
    propertyName: select
    value: title,chunk

  - kind: AutomaticTaskInput
    propertyName: search
    description: It's user query and question in order to get answers from this action.

outputs:
  - propertyName: Response
    description: You should summarize for users.

action:
  kind: InvokeConnectorTaskAction
  connectionReference: cr8e1_aiSearchAgent.shared_azure-20ai-20search-20v2-5f3065911619969a73-5f54bc2b3e53b56dbc.f98b6c46c88d48e68921cf2599e0aa8f
  connectionProperties:
    mode: Invoker

  operationId: SearchDocuments

outputMode: All
```

11) 저장 후 테스트 채팅 세션을 초기화 합니다.
![image](https://github.com/user-attachments/assets/785ec038-3c46-47e1-ae8c-946893e88a6a)

12) 그리고 다시한번 질문해 봅니다. 마찬가지로 답변의 이력을 가지고 있기 때문에 연속으로 질문이 가능합니다.
![image](https://github.com/user-attachments/assets/f4cc6188-2ce5-4ae8-92ad-92dd5deb06a5)

13) 간단히 만들어진 Azure AI Search + Custom Agent를 다양한 채널로 즉시 배포할 수 있습니다.
![image](https://github.com/user-attachments/assets/35c8a73f-71f5-4a32-ab25-8a2d228df02d)

<br/>

> 이렇게 만들어진 Custom Agent는 다양한 채널에서 서비스가 가능합니다.    
> 이런 아키텍처라면, Azure AI Search 뿐 아니라 다양한 API & 엔드포인트를 연결한 에이전트를 생성할 수 있습니다.    
> 이렇게 만들어진 에이전트는 다양한 디자인을 포함할 수 있으며, 실제 예시는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/tree/main/AdaptiveCardSamples#%EC%8B%A4%EC%A0%9C-%ED%99%94%EB%A9%B4%EC%9D%84-%EA%B8%B0%EB%B0%98%EC%9C%BC%EB%A1%9C-%ED%95%9C-%EC%BC%80%EC%9D%B4%EC%8A%A4-%EC%98%88%EC%8B%9C) 를 참고하여 주세요.
