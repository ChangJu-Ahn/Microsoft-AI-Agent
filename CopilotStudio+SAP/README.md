SAP AI Agent 실습 (Or any data! :)
============
이 실습에서는 AI를 활용하여 Microsoft + SAP 제품을 최적화하는 방법을 알아봅니다. 
SaaS 제품인 Copilot Studio를 활용하면, 별도의 호스팅 서버가 필요없고 연동할 수 있는 서비스(서버)만 필요합니다.
또한, Copilot Studio의 장점인 채널을 활용하면 추가 개발 없이 Teams, Web, 그리고 M365 Copilot로 바로 배포하여 사용할 수 있습니다.

여기서는 SAP와 연결하지만, Power Automate의 1,400개 커넥터 / 더 나아가서 기업 시스템과 연동 및 관리할 수 있습니다.


>원본은 아래에서 참고할 수 있고, 저는 여기에 한국 특성에 맞게 더 커스터마이징 한 내용을 담습니다.
https://techcommunity.microsoft.com/blog/sapapplications/sap--teams-integration-with-copilot-studio-and-generative-ai/4213260**
----

완성된 데모 영상 #1 (SAP AI Agent in Microsoft Teams)
===
[![Copilot Studio + SAP](https://img.youtube.com/vi/HkWA80HQHx4/maxresdefault.jpg)](https://youtu.be/HkWA80HQHx4)
> 위 썸네일을 클릭하면 영상을 볼 수 있어요! :)
----

완성된 데모 영상 #2 (SAP AI Agent in Microsoft 365 Copilot)
== 
[![Copilot Studio + SAP + M365 Copilot](https://img.youtube.com/vi/I3fVuDAATdk/maxresdefault.jpg)](https://youtu.be/I3fVuDAATdk)
> 위 썸네일을 클릭하면 영상을 볼 수 있어요! :)
----

실습 시나리오
== 

- 예: SAP AI 제품정보 Agent
  - 시나리오: Contoso의 제품 관리자는 SAP 시스템에서 제품 정보를 정기적으로 검토하고 업데이트해야 합니다.
  - 솔루션: Copilot Studio에서 제공하는 SAP와 Teams 통합을 통해 Contoso의 제품 관리자는 SAP에서 현재 제품 정보를 쉽게 얻고 적응형 카드에서 편리하게 사양을 업데이트할 수 있습니다.
    
Copilot Studio 및 Generative AI를 사용하여 SAP를 Microsoft Teams와 통합하면 생산성을 크게 향상하고 워크플로를 간소화할 수 있습니다. 여기서는 Power Platform과 SAP Odata Connector를 이용합니다.
그리고 최종 결과물은 AI Agent를 생성하고, Teams 및 M365 Copilot으로 배포하고, 제너레이티브, 사용자와 소통할 수 있는 적응형 카드(Adaptive Card)를 만들고 SAP의 데이터를 변경할 수 있습니다. 

기타
==
최종 실습 결과물의 에이전트는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/CopilotStudio%2BSAP/Files/SAPProductAgent_1_0_0_1_managed.zip)에 Power Platform Soultion 형태로 저장되어 있습니다.     
원하는 고객은 다운로드 후 직접 고객 테넌트에 Import 하여 사용할 수 있습니다. 사용하는 방법은 다음과 같습니다.

1) 해당 파일을 깃헙 리포에서 다운로드
2) 라이선스가 있는 테넌트 내 파워플랫폼 솔루션으로 업로드
3) 업로드 시 Connection에 대한 내용을 자신이 가지고 있는 계정으로 인증
   
<br/>

> 파워플랫폼 솔루션 Import 참고 문서는 [여기](https://learn.microsoft.com/ko-kr/power-apps/maker/data-platform/import-update-export-solutions)를 참고하여 주세요.
