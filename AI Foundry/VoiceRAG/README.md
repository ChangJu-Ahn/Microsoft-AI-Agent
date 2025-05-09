VoiceRAG: An Application Pattern for RAG + Voice Using Azure AI Search and the GPT-4o Realtime API for Audio
===

> 이 데모는 아래 Microsoft Azure-Sample 깃헙리포를 참고했습니다.   
> https://github.com/Azure-Samples/aisearch-openai-rag-audio

---

이번 데모는 Voice RAG 패턴의 에이전트입니다.   
여기서는 영어, 그리고 한글로 직접 에이전트에게 질문하며, 시나리오는 다음과 같습니다.

1) Power Automate, Logic Apps, Azure Data Factory(in Microsoft Fabric)에는 다양한 SAP 커넥터를 제공합니다.
2) 여기서는 위 도구를 통해서 SAP의 품목정보를 Azure Blob Storage에 엑셀 파일 형태로 저장합니다.
3) Azure Blob Storage에 엑셀이 저장될 때 Azure OpenAI를 통해 Embedding 처리 후 Azure AI Search에 저장합니다.
4) 이후 Agent 앱에서 GPT-4o Realtim API for Audio를 사용하여 Azure AI Search의 값을 참고해 대답합니다.

<br/>

> SAP를 정말 연동할 수 있냐고요? SAP 연결하는 게 어렵지 않냐고요?   
> 어렵지 않아요. [여기](<https://github.com/ChangJu-Ahn/Microsoft-AI-Agent/blob/main/CopilotStudio%2BSAP/2)%20SAP%20%EC%A1%B0%ED%9A%8C%EB%A5%BC%20Automate%20%EC%83%9D%EC%84%B1.md>)를 참고해 보세요.


---
완성된 데모 영상
===
[![Voice RAG with SAP](https://img.youtube.com/vi/1P3M3tcRr6U/maxresdefault.jpg)](https://youtu.be/1P3M3tcRr6U)
> 위 썸네일을 클릭하면 영상을 볼 수 있어요! :)

데모 제작 가이드 - Comming Soon..
===
