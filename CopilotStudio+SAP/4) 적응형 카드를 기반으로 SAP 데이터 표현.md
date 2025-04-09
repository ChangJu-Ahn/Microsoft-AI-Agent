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

Copilot Studio로 다시 반환하는 값은 다음 이미지를 참고합니다. SAP에서 받아온 값 내에서 'data' 항목의 값을 추출하기 위해 빨간색 영역의 ['data']를 꼭 추가해야 합니다.   
![image](https://github.com/user-attachments/assets/59591809-6b81-4563-a0a2-a97231afe4a1)

<br/>

![image](https://github.com/user-attachments/assets/7fa72019-1e13-4293-a961-9f8595b281b8)
플로우 저장 후 혹시 켜짐 상태가 아니라면, 플로우가 동작할 수 있도록 켜짐 상태로 유지합니다.

<br/>

### 10. 토픽에서 Power Automate 호출
다음과 같이 토픽의 노드를 추가합니다. 그리고 방금 만들었던 Power Automate를 호출합니다.
![image](https://github.com/user-attachments/assets/ccab9a3e-b6dd-49f1-8b39-c68426bfaf96)

<br/>
이후 Power Automate를 호출할 입력 변수에 이전에 받아온 ProductId를 연결합니다.
![image](https://github.com/user-attachments/assets/98a2b34b-ee2e-41fc-86b6-cd93f382cbe0)

<br/>

### 11. 오류 처리 프로세스 설정(!만약 반환된 값이 없다면!)
만약 ProductID를 잘못 입력했거나, SAP에서 찾은 값이 하나도 없다면? 이럴 때 처리할 수 있는 오류 프로세스르 설정합니다.
![image](https://github.com/user-attachments/assets/724dc067-af23-4f91-af3e-5dadbe8d4e07)

<br/>

위 프로세스를 구성하기 위한 단계는 아래와 같습니다.
1) Automate를 호출한 다음 노드에 반환된 '다음과 같음' 일 때 로 설정하고 해당 값은 []으로 설정합니다. 이는 반환된 json 값이 공백임을 의미합니다.
2) 만약 공백이라면? 찾을 수 없다는 메시지를 추가합니다. 이때 사용자가 이해하기 쉽도록 조회한 변수(ProductId)를 포함하는 것이 좋습니다.
3) 다시한번 물어볼 수 있도록 **노드 추가 -> 토픽 관리 -> 단계로 이동 -> 최초 ProductId를 질문하는 단계 선택** 이 되도록 설정합니다.
   ![image](https://github.com/user-attachments/assets/f1433a81-5d96-43ca-a9ff-13164e80bc32)


### 12. Automate Output 값 기반의 구문 분석 
Automate에서는 SAP 제품정보의 상세 값을 JSON값으로 반환합니다. 이를 사용하기 위해서는 파싱처리를 해야 합니다.    
위치는 SAP에서 값을 받아온 이후 프로세스이므로, 꼭 위치를 잘 확인해야 합니다.
![image](https://github.com/user-attachments/assets/debfe927-6d88-4a9f-a07c-8368c81a1c12)


<br/>

구문 분석을 위해서 Automate에서 받아온 변수 값을 선택합니다.   
<img width="600" alt="image" src="https://github.com/user-attachments/assets/b8067634-7006-492e-945f-9b10db429dfa" />

<br/>

샘플 데이터를 얻기 위해 기존에 생성했던 Automate로 돌아가서 다음과 같이 테스트를 진행합니다.   
![image](https://github.com/user-attachments/assets/0e0af061-62b4-4cc2-bcb3-a81f629a2e73)

<br/>

이후 테스트한 샘플 값을 복사합니다. 과정은 다음과 같습니다.
![image](https://github.com/user-attachments/assets/254e7c72-d4cf-4adb-8c22-6a018a24424a)

<br/>
다시 코파일럿 스튜디오로 넘어와서 샘플 데이터에서 참고할 수 있도록 '샘플 JSON에서 스키마 가져오기'를 클릭하고 위의 샘플 결과 값을 붙여넣기합니다.

![image](https://github.com/user-attachments/assets/5553cab1-b349-4252-a1c9-0914008aadde)
<img width="710" alt="image" src="https://github.com/user-attachments/assets/31a25087-5f72-4ecc-8010-20f7cde5f97e" />

<br/>
마지막으로 이해하기 쉽도록 변수명(Product)을 변경하고 토픽을 저장합니다.
<br/>
<img width="350" alt="image" src="https://github.com/user-attachments/assets/109f993c-0c39-4667-8595-004f13ca5b9d" />

### 13. SAP 데이터를 기반으로 적응형 카드 제작
적응형 카드를 기반으로 메시지를 보내고, 응답받을 수 있습니다.  
![image](https://github.com/user-attachments/assets/952d3655-daec-4fbf-8fa6-45df29d266a6)


<br/>

[여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/CopilotStudio%2BSAP/Files/SAP%20Adaptive%20Card.json)에 저장된 Adaptive Card json 템플릿을 복사하여 붙여넣습니다.   
이때 빨간색 표시 박스를 클릭하여 '수식 편집'으로 변경해서 저장합니다.
![image](https://github.com/user-attachments/assets/5151c83f-3674-4d3c-b8c5-fa8b73238c7e)

> 위 정보는 미리 **디자인 및 값을 바인딩**한 적응형 카드 템플릿입니다.   
> 다양한 템플릿을 만들 수 있는 적응형 카드 디자이너 웹 사이트는 [여기](https://adaptivecards.io/designer/)를 참고할 수 있습니다.

<br/>

잘 마무리 했다면, 'HT-6102 제품 상세정보' 라고 입력해서 테스트를 했을 때 다음과 같이 나올 수 있습니다.
<img width="265" alt="image" src="https://github.com/user-attachments/assets/99f57cf5-8903-4fac-b8ec-ecb3351ceaa4" />

> 만약 Product ID 값 외에 아무것도 안 나온다면?   
> Power Automate에서 반환하는 값이 잘못 되어있을 수 있습니다. 꼭 이번 페이지의 9번 순서의 Automate 설정을 잘 확인하세요.

<br/>

사용자가 입력한 값을 변수로 받기위해서 **스키마 편집**을 누른 후 아래 값을 붙여넣습니다.
![image](https://github.com/user-attachments/assets/b67ea2ae-6c6b-4524-bff1-5595a205b3de)
<img width="596" alt="image" src="https://github.com/user-attachments/assets/e02a2a06-d7cc-4488-8979-e887d22f4861" />

```
kind: Record
properties:
  action: String
  actionSubmitId: String
  currencyCode: String
  description: String
  price: Number
  productName: String
```

<br/>

최종 화면은 다음과 같고, 적응형 카드에서 저장한 값들이 아래의 출력 변수에 담기는 구조가 됩니다.
<img width="763" alt="image" src="https://github.com/user-attachments/assets/4cce43ea-4b3e-4407-8ad3-f86772018567" />



