실습 - 적응형 카드를 기반으로 SAP 데이터 표현
===

이제 Microsoft Teams 내에서 SAP 데이터를 동적으로 표시하는 적응형 카드를 만들어 보겠습니다. 
이섹션에서는 토픽을 만들고 구성합니다. 

1) 적절한 트리거 구문을 사용하여 토픽을 활성화합니다. 
2) 토픽 내에서 호출 흐름을 생성합니다.
3) SAP OData Connector의 다양한 엔터티를 활용합니다.
4) 제품을 찾을 수 없는 경우와 같은 특수 상황을 처리합니다.
5) JSON 데이터를 구문 분석하고 토픽 변수에 값을 할당합니다.
6) 적응형 카드를 설계하고 구현합니다.
7) 작업과 토픽의 차이점을 이해합니다.
  
이러한 기술을 습득하면 Copilot의 기능과 상호 작용성이 향상되어 사용자에게 SAP 데이터와 상호 작용하는 보다 직관적이고 효율적인 방법을 제공합니다.

---
### 8. SAP Prodct Data 토픽 생성 

다음과 같이 '새로 시작' 버튼을 통해 빈 토픽을 생성합니다.

<img width="428" alt="image" src="https://github.com/user-attachments/assets/73ad69f1-5ea9-4719-90b7-9e3fe3edc1ed" />
<br/>
<br/>
<br/>
그리고 AI 에이전트가 이해할 수 있도록, 다음 지침을 입력합니다.

```
This tool can handle queries like these:

SAP product update.
Update SAP product.
Update SAP product data.
Edit product information in SAP.
Edit SAP product data.
Show SAP product details.
Edit SAP product information.
```

<img width="630" alt="image" src="https://github.com/user-attachments/assets/e287bf6c-cae0-409c-bcc1-005b258abf0c" />
<br/>
<br/>
<br/>
그리고 토픽 이름을 **SAP Product Data**로 하여 저장합니다.
<img width="922" alt="image" src="https://github.com/user-attachments/assets/16b964ae-6549-4c41-9cff-06b1370a36c0" />

<br/>
<br/>
<br/>

이후 설명란에 다음 내용을 입력합니다.
![image](https://github.com/user-attachments/assets/a28e12a5-c88c-4109-85ca-bda2894c1c58)
```
Show and update information about a product in the SAP system.
```
<br/>
<br/>
<br/>

토픽 안에서 변수를 처리할 수 있도록 신규 생성합니다. 그리고 저장합니다.
<img width="778" alt="image" src="https://github.com/user-attachments/assets/f802cf4d-1624-4bf6-9dda-0b351c938313" />
<img width="357" alt="image" src="https://github.com/user-attachments/assets/d2c068ac-30ea-4335-91ea-6ae15c0510df" />

<br/>
<br/>
<br/>

그리고 만약 사용자가 품목을 직접 말하지 않았다면, 다시한번 물어볼 수 있는 노드를 추가합니다. 
이때 사용자의 응답은 꼭 ProductId 라는 변수에 저장해야 합니다. 
<br/><br/>
이는 다음과 같은 예시에서 사용될 수 있습니다.

> "HT-2000 품목정보 알려줘" 라고 한다면, 발화 안에 품목정보가 있기 때문에 질문 노드는 자동으로 채워지며 다음 프로세스를 진행

> "품목정보 알고싶어" 라고 한다면, 발화 안에 품목정보가 없으니 이번 노드를 통해 사용자에게 품목정보를 물어보는 프로세스를 진행

<img width="308" alt="image" src="https://github.com/user-attachments/assets/4b324ed6-37aa-497d-b6af-2563e11b5edc" />

<br/>
<br/>
<br/>

그리고 다음과 같은 메시지 노드를 추가하여, 사용자에게 어떤 정보를 검색하고 있는지를 공유해 줍니다.
<img width="326" alt="image" src="https://github.com/user-attachments/assets/c72f856d-3bd0-4a2b-8584-f2e61b102a48" />
<br/>
<br/>

### 9. SAP 제품 상세조회를 위한 Power Automate Flow 생성
make.powerautomate.com 으로 이동합니다. 이후 내 흐름에서 이전에 만들어 준 Automate를 다른이름으로 저장합니다.  이때 저장할 이름은 'SAP 품목 상세 조회'로 저장합니다.
![image](https://github.com/user-attachments/assets/c4a8eba3-10b6-46a8-b55a-6b19b242aa17)

<br/>

![image](https://github.com/user-attachments/assets/809735f5-3f80-4906-aaff-5e440dc76d83)
플로우 상세화면으로 진입해서 SAP를 호출하는 필터 조건을 Category에서 ProductId로 변경합니다.   이는 Agent가 파라미터를 알아서 파싱 후 SAP를 다시한번 조회할 때 사용됩니다.

> 참고: "Read Odata Entity"를 사용하지 않는 이유는?   
> ProductID가 잘못된 경우 Read Entity가 오류를 발생시키는 반면 Query는 간단히 "[]"를 반환하여 예외를 쉽게 처리할 수 있습니다. 

<br/>

![image](https://github.com/user-attachments/assets/7fa72019-1e13-4293-a961-9f8595b281b8)
플로우 저장 후 혹시 켜짐 상태가 아니라면, 플로우가 동작할 수 있도록 켜짐 상태로 유지합니다.



