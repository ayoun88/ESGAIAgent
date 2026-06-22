# 🤖 ESG Guide AI Agent
목적 : 복잡한 ESG 규제, 분석 및 계산 항목에 대한 처리에 어려움을 겪는 기업 실무자들을 위한 LangChain & RAG 파이프라인 기반 지능형 AI Agent 설계

> 📌 이 레포는 제가 담당한 **RAG 파이프라인**(Vector DB 구축, PDF 하이브리드 검색, SQLite DB 구축 및 검색) 중심으로 정리한 개인 작업 기록입니다.

## 👨‍👧‍👦 Team
<table align="center">
  <!-- 상단 팀원 이름 Table-->
  <tr>
    <th align="center">👑 이진성</th>
    <th align="center">🙍 고아연</th>
    <th align="center">🙍‍♂ 김재현</th>
    <th align="center">🙍‍♂ 박성재</th>
    <th align="center">🙍‍♂ 배준서</th>
    <th align="center">🙍 윤소정</th>
  </tr>
  
  <!-- 팀원 이미지 Table-->
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/a9befe05-0cb9-4e0c-ba1f-43b4275ce55e" width="150">    <!--이진성-->
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/35c220cf-9b00-4e9a-a3e9-0e2e3e2318b7" width="120">    <!--고아연-->
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/89342c37-c1f9-4fcf-9ef9-a9fc032a807f" width="105">    <!--김재현-->
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/21d5ac6e-c2c9-47a8-867a-7cb362f05973" width="110">    <!--박성재-->
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/e10fba61-2421-4bca-b470-506f854fa909" width="105">    <!--배준서-->
    </td>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/10778e56-ea3c-4e64-8204-3ab5a5d2df36" width="105">    <!--윤소정-->
    </td>
  </tr>

  <!-- 팀원 역할 Table-->
  <tr>
    <!--이진성-->
    <td align="center">
      Custom Tool<br>
      Router<br>
      답변 성능 평가 Tool<br>
      UI 개선
    </td>
    <!--고아연-->
    <td align="center">
      RAG PipeLine<br>
      Vector DB<br>
      PDF Hybrid Search<br>
      SQLite DB
    </td>
    <!--김재현-->
    <td align="center">
      Team BaseLineCode<br>
      WebSearchTool<br>
      etc PipeLine<br>
      MiddleWare
    </td>
    <!--박성재-->
    <td align="center">
      CustomTool<br>
      Prompt Engineering
    </td>
    <!--배준서-->
    <td align="center">
      CustomTool<br>
      Prompt Engineering
    </td>
    <!--윤소정-->
    <td align="center">
      CustomTool<br>
      Prompt Engineering
    </td>
  </tr>

  <tr>
    <td align="center">
      <a href="https://github.com/wlstjd6524"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>        <!--이진성-->
    </td>
    <td align="center">
      <a href="https://github.com/ayoun88"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>           <!--고아연-->
    </td>
    <td align="center">
      <a href="https://github.com/KJH-0596"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>          <!--김재현-->
    </td>
    <td align="center">
      <a href="https://github.com/sungjae3911-arch"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>  <!--박성재-->
    </td>
    <td align="center">
      <a href="https://github.com/jun-01111"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>         <!--배준서-->
    </td>
    <td align="center">
      <a href="https://github.com/Lucia128"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=white"/></a>          <!--윤소정-->
    </td>
  </tr>

</table>

## 📺 Presentation
[발표자료](https://github.com/user-attachments/files/26978271/LLM.Project.1.pptx)

## 📂 ReadME Index
[📄 Executive Summary](#executive-summary) <br>
[⏱️ Project Duration & 🔧 Tech Stack](#projectduration-techstack) <br>
[🏗️ System Architecture](#system-architecture) <br>
[📱 Demo & UI](#demo-ui) <br>
[🛠️ Core Pipelines & Implementation](#core-pipelines) <br>
[🚀 Troubleshooting & Optimization](#troubleshooting) <br>
[📈 Retrospective & Future Work](#retrospective)

<a id="executive-summary"></a>

## 📄 Executive Summary
### 📌 Background
글로벌 ESG 공시 의무화로 기업이 추적해야 할 가이드라인과 배출계수 데이터가 빠르게 늘고 있습니다. 수만 개에 달하는 계수를 수작업으로 계산하면서 발생하는 오류와 업무 지연이 핵심 페인포인트입니다.

### 🎯 Objective
전체 에이전트는 가이드라인 검색·수치 계산·법령 검색·컴플라이언스 진단까지 수행하는 LangChain/LangGraph 기반 멀티 툴 에이전트입니다. 저는 이 중 **에이전트가 정확한 근거를 가지고 답변하도록 만드는 RAG 파이프라인** — PDF/CSV 데이터의 적재(Indexing)부터 검색(Retrieval)까지 — 를 담당했습니다.

<a id="projectduration-techstack"></a>

## ⏱️ Project Duration & 🔧 Tech Stack
### ⏱️ Project Duration
2026.04.06 ~ 2026.04.17

### 🔧 Tech Stack
| Category | Tech Stack |
| :--- | :--- |
| Language & Environment | Python 3.11, uv |
| Framework & Orchestration | LangChain, LangGraph |
| LLM Model | Upstage Solar-Pro |
| **Database & Storage** | **ChromaDB (Vector)**, **SQLite (RDB)**, **AWS S3** |
| **Data Pipeline & NLP** | **BM25**, **DocTR (OCR)**, **KoNLPy** |
| Tools & API | Tavily API, OpenDartReader |
| Monitoring & UI | LangSmith, Gradio |

<a id="system-architecture"></a>

## 🏗️ System Architecture
<img width="8192" height="5488" alt="Image" src="https://github.com/user-attachments/assets/17734813-7f81-4873-9ebe-5a90cf9b9e32" />

내부 지식(RAG)과 외부 실시간 정보(Web Search)를 결합한 하이브리드 에이전트입니다. PDF 가이드라인과 CSV 배출계수 데이터를 각각 Vector DB / RDB로 구조화하고, ReAct 에이전트가 호출하는 `search_pdf` / `search_csv` 도구까지가 제 작업 범위입니다.

### 🏆 Key Contributions
| Category | Details |
| :--- | :--- |
| **Role** | RAG Pipeline — Vector DB 구축, PDF 하이브리드 검색, SQLite DB 구축 및 검색 |
| **Core Pipelines** | 구조 보존 PDF 파싱·계층형 청킹, BM25+ChromaDB 하이브리드 검색, Text-to-SQL Self-Healing |
| **Data Engineering** | AWS S3 기반 Vector/RDB 동기화, 파일명 메타데이터 자동 추출, 임베딩 캐싱 |

<a id="demo-ui"></a>

## 📱 Demo & UI
<img width="1493" height="875" alt="Image" src="https://github.com/user-attachments/assets/3f2072de-00ec-48aa-bad2-5f9a1e9017fc" /> <br> <br>
<img width="1492" height="179" alt="Image" src="https://github.com/user-attachments/assets/4289a11a-bc8a-4359-af08-347ae422724e" />

<a id="core-pipelines"></a>

## 🛠️ Core Pipelines & Implementation

1. **구조 보존 PDF 파싱 & 계층형 청킹** (`pdf_parser.py`, `pdf_chunker.py`)
   - 폰트 크기 기반 헤딩(H1~H3) 감지와 다단 컬럼 재정렬로 보고서의 읽기 순서를 복원하고, 표는 마크다운+자연어 요약으로 이중 청킹해 수치 검색과 의미 검색을 모두 지원했습니다.
   - 스캔 페이지는 DocTR OCR로 자동 전환하고, Parent(~2400자)-Child(~600자) 구조로 검색 정밀도와 LLM 문맥 제공을 동시에 확보했습니다.

2. **하이브리드 검색 & Self-Healing SQL** (`search_pdf.py`, `search_csv.py`)
   - KoNLPy 형태소 분석 기반 BM25와 ChromaDB를 0.5:0.5로 앙상블하고, 메타데이터 필터를 4단계로 점진 완화하는 폴백 검색을 구현했습니다.
   - LangGraph 기반 Text-to-SQL 파이프라인에 에러 발생 시 최대 2회 자가 재시도 로직을 구축하고, 데이터 대분류에 따라 의미가 달라지는 칼럼 구조를 프롬프트에 명시해 정답률을 높였습니다.

3. **클라우드 동기화 인덱싱 파이프라인** (`ingest.py`, `ingest_csv.py`)
   - 파일명에서 연도/기업명/문서 카테고리를 자동 추출하는 메타데이터 파서와 `CacheBackedEmbeddings`로 임베딩 비용을 절감했습니다.
   - 완성된 Vector DB(ChromaDB+BM25 캐시)와 SQLite DB를 AWS S3에 동기화해, GitHub 용량 제한 없이 팀 전체가 공유할 수 있는 구조로 설계했습니다.

<a id="troubleshooting"></a>

## 🚀 Troubleshooting & Optimization

### 1. 대기업 ESG 데이터 통합의 한계
**문제** : 4개 대기업 데이터를 표준 스키마로 통합하려 했으나, JS 기반 페이지의 크롤링 실패와 4천 행 규모의 수작업 정제 부담으로 어려움을 겪었습니다.
**해결 및 인사이트** : 무리한 통합보다 단일 기업(SK이노베이션) 데이터를 정제해 RAG로 우선 검증하는 방향으로 전환했고, 이미 보고서에 있는 값을 정확히 추출하는 것이 통합보다 더 중요한 과제임을 확인했습니다.

---

### 2. SQL 생성 오류로 인한 오답
**문제** : 동일 연료(LNG/천연가스)도 데이터 대분류에 따라 칼럼 의미가 반전되거나 표기가 달라, SQL이 잘못된 행을 가져오거나 도구 호출 자체를 건너뛰었습니다.
**해결 및 인사이트** : 프롬프트에 `REPLACE`/`UNION ALL` 규칙을 명시하고 SQL 도구를 강제로 우선 실행하도록 변경해 의도에 맞는 값을 정확히 가져오도록 해결했습니다. 같은 키워드도 데이터 분류 체계에 따라 의미가 달라질 수 있다는 점을 프롬프트로 풀어내야 했습니다.

---

### 3. PDF 표 인식 실패로 인한 할루시네이션
**문제** : 표 형태 수치를 단순 텍스트로 변환해 저장하는 방식이 의미를 유실시켜, 실제 값과 다른 답변이나 "데이터 없음" 오답이 발생했습니다.
**해결 및 인사이트** : DocTR OCR과 계층형(Parent-Child) 청킹, 표 이중 청킹(마크다운+자연어 요약)을 도입해 구조를 보존했습니다. 검색을 잘하는 것보다 문서를 구조적으로 잘 읽는 것이 선행되어야 한다는 것을 체감했습니다.

<a id="retrospective"></a>

## 📈 Retrospective & Future Work
### 📌 회고
간단한 RAG는 쉽게 동작했지만, 실제 보고서형 PDF에서는 구조와 문맥을 동시에 지키는 것이 성능을 좌우한다는 것을 절실히 느꼈습니다. AWS S3, Java/Poppler 같은 인프라를 처음 구축하며 어려움도 많았지만, 팀원들과 동일한 개발 환경을 유지하는 협업의 중요성을 배웠습니다.

### 📗 향후계획
- 중단했던 대기업 ESG 데이터 표준화를 이어서 공개 데이터셋 형태로 정리해보고 싶습니다.
- `Unstructured.io` 등 멀티모달 문서 파싱 모델을 PDFPlumber + DocTR 조합과 비교해보고 싶습니다.
- 현재의 로컬 ChromaDB + S3 구조와 Pinecone 같은 매니지드 Vector DB의 비용·성능을 비교해보고 싶습니다.

---

🔗 [팀 작업레포](https://github.com/wlstjd6524/LangchainRag_01) · [Notion](https://www.notion.so/ESG-Tool-23d6325e11938098aa97e22ed903393b)