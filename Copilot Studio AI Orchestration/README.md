Copilot Studio AI Orchestration 실습
============
이 실습에서는 Copilot Studio의 핵심 AI 기능인 AI Orchestration을 이해합니다.
이는 일반적인 챗봇을 넘어 에이전트로 가는 역할을 하고, 한 개의 의도만 처리할 수 있었던 기본 챗복과 다르게 여러 개의 의도를 LLM이 파악하어 실행계획을 수립합니다. 

Copilot Studio AI Orchestration 설명
===
[![Copilot Studio AI Orchestration](https://img.youtube.com/vi/NV-6gXz3Xug/maxresdefault.jpg)](https://youtu.be/NV-6gXz3Xug)
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

   
기타
==
최종 실습 결과물의 에이전트는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/CopilotStudio%2BSAP/Files/SAPProductAgent_1_0_0_1_managed.zip)에 Power Platform Soultion 형태로 저장되어 있습니다.     
원하는 고객은 다운로드 후 직접 고객 테넌트에 Import 하여 사용할 수 있습니다. 사용하는 방법은 다음과 같습니다.

1) 해당 파일을 깃헙 리포에서 다운로드
2) 라이선스가 있는 테넌트 내 파워플랫폼 솔루션으로 업로드
3) 업로드 시 Connection에 대한 내용을 자신이 가지고 있는 계정으로 인증
   
<br/>

> 파워플랫폼 솔루션 Import 참고 문서는 [여기](https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/Copilot%20Studio%20AI%20Orchestration/Files/KoreaTourAgent_1_0_0_1.zip)를 참고하여 주세요.
