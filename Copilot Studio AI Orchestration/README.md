Copilot Studio AI Orchestration 실습
============
이 실습에서는 Copilot Studio의 핵심 AI 기능인 AI Orchestration을 이해합니다.
이는 일반적인 챗봇을 넘어 에이전트로 가는 역할을 하고, 한 개의 의도만 처리할 수 있었던 기본 챗복과 다르게 여러 개의 의도를 LLM이 파악하어 실행계획을 수립합니다.    

자세한 설명은 아래 링크에서도 다시한번 참고할 수 있어요! 😎

https://microsoft.github.io/mwkorea/copilot/CPSAIorchestration/

</br>

Copilot Studio AI Orchestration 설명
===
[![Copilot Studio AI Orchestration](https://img.youtube.com/vi/zkLu6C7wp54/maxresdefault.jpg)](https://youtu.be/zkLu6C7wp54)
> 위 썸네일을 클릭하면 영상을 볼 수 있어요! :)
----


실습 시나리오
== 

- 예: 여행의 모든 것 - 트리바이저
  - 시나리오: Gen AI를 기반으로 여행지를 추천하고, 날씨를 확인, 그리고 스케줄까지 관리하는 에이전트
  - 역할:
    1) 여행 사이트 URL을 기반으로 여행지 추천
    2) 실시간 날씨 데이터를 API 기반으로 오늘, 내일의 일기예보를 공유
    3) 캘린더의 휴가 일정을 자연어로 상신

</br>
   
기타 - 1)
==
최종 실습 결과물의 에이전트는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/tree/main/Copilot%20Studio%20AI%20Orchestration/Files)에 Power Platform Soultion 형태로 저장되어 있습니다.     
원하는 고객은 다운로드 후 직접 고객 테넌트에 Import 하여 사용할 수 있습니다. 사용하는 방법은 다음과 같습니다.

1) 해당 파일을 깃헙 리포에서 다운로드
2) 라이선스가 있는 테넌트 내 파워플랫폼 솔루션으로 업로드
3) 업로드 시 Connection에 대한 내용을 자신이 가지고 있는 계정으로 인증
   
<br/>

> 파워플랫폼 솔루션 Import 참고 문서는 [여기](https://learn.microsoft.com/ko-kr/power-apps/maker/data-platform/import-update-export-solutions)를 참고하여 주세요.
>

</br>

기타 - 2)
==
Copilot Studio에서는 다음과 같은 다양한 에이전트를 통합하여 **멀티 에이전트** 기능을 제공합니다.   
이 기능 또한, AI Orchestraion의 핵심 기능이 서로 간의 에이전트를 조율하는 역할을 담당합니다.

또한,  Copilot Studio의 에이전트 뿐 아니라, Microsoft Fabric, Azure AI Foundry, 그리고 M365 Agents SDK와도 통합되어 운영됩니다.

![image](https://github.com/user-attachments/assets/da2aee81-9449-4183-b4f8-aed6ffbe895a)
![image](https://github.com/user-attachments/assets/293725c2-c401-46ef-8e32-6b951792f946)
![image](https://github.com/user-attachments/assets/a3bff054-184f-4254-b2b7-0b3789d41888)
