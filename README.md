<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:0b3d2e,50:1b7f4b,100:5ec46a&height=230&section=header&text=SIM%20MINJI&fontSize=72&fontColor=ffffff&fontAlignY=36&animation=fadeIn&desc=AI%20Engineer%20%7C%20NLP%20%C2%B7%20LLM&descSize=22&descAlignY=58&descColor=d8f3dc)

### 심민지 · AI Engineer

NLP · LLM 응용 · 아주대학교 비즈니스애널리틱스 석사과정

<a href="mailto:mjmj752002@naver.com"><img src="https://img.shields.io/badge/Email-03C75A?style=flat-square&logo=naver&logoColor=white"/></a>
<a href="https://velog.io/@newspaper"><img src="https://img.shields.io/badge/Velog-20C997?style=flat-square&logo=velog&logoColor=white"/></a>
<a href="https://github.com/newspap2r"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/></a>
<a href="https://solved.ac/newspap2r"><img src="https://img.shields.io/badge/solved.ac-newspap2r-17a1ff?style=flat-square&logo=baekjoon&logoColor=white"/></a>

</div>

<br>

## 데이터를 모으는 데서 끝내지 않고, 모델이 실제로 쓰이도록 *평가와 배포까지* 확인하는 AI 엔지니어.

유튜브 댓글 339만 건을 모아 다국어 감성 모델을 직접 비교해 골랐고, 공공조달 데이터 14,313건은 대시보드로 만들어 Streamlit Cloud에 배포했습니다. 분석 결과는 제1저자 논문으로 한국전자거래학회지에 실렸습니다.

바쁘시다면 아래 숫자와 대표작 세 개만 보셔도 됩니다.

<br>

## 숫자로 먼저 보는 저

<div align="center">

| 339만 건 | 0.632 | 14,313 건 | 1 편 | 29 회 |
|:---:|:---:|:---:|:---:|:---:|
| 수집한 유튜브 댓글 | 감성 모델 macro-F1 | 공공조달 납품요구 | 제1저자 논문 | 주간 발간물 |
| 다국어 감성 · 토픽 파이프라인 | 골드셋 600건 직접 라벨링 | Streamlit Cloud 배포 | 한국전자거래학회지 · 학회 발표 3회 | 공공기관 수집 · 분석 자동화 |

</div>

<br>

## 대표작

### 01 · AI 슬롭 다국어 유튜브 댓글 분석 파이프라인

연구 프로젝트 · 2026.01 ~ 07 · `수집` `감성분석` `토픽모델링` `모델 평가`

댓글 339만 건을 모아 언어별로 나누고, 감성 모델을 골드셋으로 비교해 고른 파이프라인. 정제 후 161만 건을 분석했습니다.

AI 생성 영상(슬롭) 채널과 일반 채널의 댓글이 어떻게 다른지 보려 했는데, 한국어 비중이 2% 미만이라 준비해 둔 한국어 감정 모델을 쓸 수 없었습니다. 스페인어 · 포르투갈어 · 영어 · 아랍어 네 언어에서 각 150건씩 600건을 직접 블라인드 라벨링해 골드셋을 만들고, XLM-R과 mBERT를 같은 기준으로 비교했습니다. XLM-R이 macro-F1 0.632로 mBERT의 0.448보다 높았고, 언어 간 편차는 0.018이었습니다. 토픽은 다국어 SBERT 임베딩에 UMAP · KMeans · c-TF-IDF를 붙여 뽑고 NPMI · TU로 평가했으며, 채널 하나를 빼고 다시 돌리는 LOCO로 결과가 특정 채널에 기대지 않는지 확인했습니다.

맡은 일
- YouTube Data API 쿼터 관리와 체크포인트 재개 수집기 작성 (영상 23,756 · 쇼츠 16,159)
- fast-langdetect + langid 언어 식별, 골드셋 600건 라벨링과 감성 모델 선정
- 임베딩 3종 · 번역 대조 · HDBSCAN을 포함한 토픽 파이프라인 비교와 최종안 확정
- LLM 다중 모델로 토픽 라벨 검증, RunPod GPU 운영

### 02 · 공공조달 수요 분석 대시보드

(주)청우씨엔티 × 아주대 산학협력 · 2026.07 ~ 08 · `수집기 자작` `LDA · BERTopic` `RFM` `배포 · 이관`

나라장터 납품요구 14,313건을 수집 · 분석해 Streamlit Cloud에 배포하고, 비개발자가 이어받을 수 있게 인수인계서까지 넘긴 대시보드. [저장소 보기](https://github.com/newspap2r/cwcnt-dashboard)

유해가스 정화장비를 만드는 회사가 어느 기관에 무엇을 얼마나 팔 수 있을지 알고 싶어 했습니다. 공개 API로는 닿지 않는 구간이 있어 수집 스크립트를 직접 만들고 표본 대조로 일치율 99.4%를 확인했습니다. 품목명은 Kiwi로 명사를 뽑아 LDA의 K를 10부터 25까지 c_v로 비교해 18로 정했고, 13개 그룹으로 다시 묶었습니다. 기관 5,952곳은 RFM으로 나눠 상위 1,110곳이 매출의 75.7%를 차지한다는 것을 보여 줬습니다. 결과는 Plotly 3탭 앱으로 만들어 배포했고, 주간 발표 6회를 거쳐 종합보고서와 인수인계서로 마무리했습니다.

맡은 일
- 2013 ~ 2024 납품요구 수집기 작성과 검증
- Kiwi + LDA(K=18) · BERTopic(ko-sroberta, 63토픽) 품목 분류, 13그룹 수동 라벨
- RFM 세분화, 3D프린터 잠재 고객 분석
- Streamlit + Plotly 앱 개발 · Streamlit Cloud 배포 · 인수인계서 v1.0

### 03 · 딥페이크 영상 탐지

공모전 · 2026.01 · `ViT 파인튜닝` `추론 파이프라인`

영상에서 프레임을 뽑아 ViT를 파인튜닝하고, Flip TTA로 추론까지 묶은 딥러닝 파이프라인.

학습 데이터 구성부터 모델 학습, 추론 코드까지 혼자 끝까지 만들었습니다. 프레임 샘플링 간격과 테스트 시 증강을 바꿔 가며 점수 변화를 확인했습니다.

맡은 일
- 프레임 샘플링과 데이터셋 구성
- Hugging Face ViT 파인튜닝
- Flip TTA 추론 파이프라인

<br>

## 프로젝트

| 프로젝트 | 분류 · 기간 | 한 줄 |
|---|---|---|
| 소상공인 금융정책 체감도 진단 | 소상공인시장진흥공단 연구보고서 · 2025 ~ 2026.06 | 전화 상담 STT 23.5만 건과 커뮤니티 6,510건을 KR-FinBert 감성분석과 LDA · BERTopic 그리드서치로 분석해 정책 공지 전후를 비교했습니다. |
| 소상공인 현장 목소리 주간 발간 | 소상공인시장진흥공단 · 2026.06 ~ | 네이버 카페 · 국민신문고 · 소상공인24 약 62,000건을 매주 모으고, 차트 생성부터 HWP · PDF 변환까지 자동화해 29회 이상 발간했습니다. |
| 자동차 사후관리 커뮤니티 분석 | 2026 | 보배드림 · 네이버카페 · 빅카인즈 3.2만 건을 크롤링하고 토픽모델 4종을 비교해 BERT-LDA 하이브리드(coherence 0.597)를 골랐습니다. |
| Function Calling AI 에이전트 실습 | TypeScript · `@agentica/core` · OpenAI | 도구 호출과 스키마 정의로 움직이는 LLM 에이전트 구조를 구현해 봤습니다. |
| 독립서적 추천 시스템 「인디깅」 | 국립중앙도서관 데이터 활용 공모전 · 2024 · 4인 팀 | 독립서적 2,935권을 크롤링하고 설문 74명을 바탕으로 Weighted Jaccard 콘텐츠 기반 추천을 만들었습니다. |

다음으로 만들 것 · 도서 검색 RAG 시스템 (bge-m3 + BM25 하이브리드 검색 · 리랭커 · RAGAS 평가 · FastAPI)

<br>

## 경력 · 활동

| 기간 | 내용 | |
|---|---|:-:|
| 2026.06 ~ | 소상공인시장진흥공단 · 「2026 비정형 데이터 기반 정책현안 분석」 연구참여자<br>주간 수집 · 분석 · HWP/PDF 자동 생성 파이프라인 운영 | `운영` |
| 2026.07 ~ 08 | (주)청우씨엔티 × 아주대 산학협력 · 공공조달 수요 분석 대시보드<br>기획 · 모델링 · 배포 · 이관 | `배포` |
| 2025.09 ~ | 아주대학교 대학원 조교 · 3학기<br>크롤링 수업 강의, R · Python 실습 과제와 퀴즈 출제, 교안 · 영상 제작 | `강의` |
| 2026.01 ~ 02 | MCE 현장실습 · 8주<br>데이터센터 냉각 기술 영문 뉴스 수집 · 트렌드 분석 | |
| 2025 ~ 2026 | 소상공인시장진흥공단 · 금융정책 체감도 진단 연구참여자<br>STT 상담 데이터 NLP 분석 | |
| 2024.09 ~ | 경기대 ICL Lab 학부연구생<br>텍스트 마이닝 · 정보검색 연구 보조 | |

### 논문 · 발표

- 「AI 영상의 의인화 수준과 품질이 시청자 반응에 미치는 영향」 · 심민지 · 강주영 · 한국전자거래학회지 · 제1저자
  유튜브 댓글 LDA · 감성분석으로 AI 생성 영상의 의인화 역설을 실증했습니다.
- 학회 발표 3회 · 한국인터넷전자상거래학회 추계(2025) · 이브릿지 추계(2025) · 홍콩 학술교류 영어 발표(2026.02)

<br>

## 학력 · 자격

- 아주대학교 대학원 비즈니스애널리틱스학과 석사과정 · 2025.09 ~ 2027.06 예정
- 경기대학교 문헌정보학과 학사 · GPA 4.07 / 4.5 · 성적장학금 3회
- SQLD 국가공인 SQL 개발자 · 2024.04 · 영구 자격

<br>

## 도구

<div align="center">

**ML**

<img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/> <img src="https://img.shields.io/badge/Hugging%20Face%20Transformers-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black"/> <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/> <img src="https://img.shields.io/badge/Sentence--Transformers-0E7C7B?style=for-the-badge"/> <img src="https://img.shields.io/badge/BERTopic%20%7C%20LDA-5C2D91?style=for-the-badge"/>

**LLM**

<img src="https://img.shields.io/badge/OpenAI%20API-412991?style=for-the-badge&logo=openai&logoColor=white"/> <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white"/> <img src="https://img.shields.io/badge/FAISS-0467DF?style=for-the-badge&logo=meta&logoColor=white"/> <img src="https://img.shields.io/badge/Agentica-000000?style=for-the-badge&logo=typescript&logoColor=white"/> <img src="https://img.shields.io/badge/Claude%20Code-D97757?style=for-the-badge&logo=anthropic&logoColor=white"/>

**Data**

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/> <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/> <img src="https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=selenium&logoColor=white"/> <img src="https://img.shields.io/badge/Kiwi%20%7C%20KoNLPy-2E8B57?style=for-the-badge"/> <img src="https://img.shields.io/badge/YouTube%20Data%20API-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/> <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/> <img src="https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white"/>

**Serving · Work**

<img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white"/> <img src="https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white"/> <img src="https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white"/> <img src="https://img.shields.io/badge/RunPod%20GPU-673AB7?style=for-the-badge"/> <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/> <img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white"/>

**VCS**

<img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/> <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>

</div>

<br>

## 알고리즘 · GitHub

<div align="center">

[![Solved.ac](http://mazassumnida.wtf/api/v2/generate_badge?boj=newspap2r)](https://solved.ac/newspap2r)

<img height="165" src="https://github-readme-stats.vercel.app/api?username=newspap2r&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=3fb950&icon_color=3fb950"/>
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=newspap2r&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=3fb950&hide=html,css"/>

<img src="https://github-readme-streak-stats.herokuapp.com?user=newspap2r&theme=tokyonight&hide_border=true&background=0d1117&ring=3fb950&fire=3fb950&currStreakLabel=3fb950"/>

</div>

<br>

<div align="center">

### 함께 만들 AI 서비스가 있다면

mjmj752002@naver.com

![footer](https://capsule-render.vercel.app/api?type=waving&color=0:5ec46a,50:1b7f4b,100:0b3d2e&height=120&section=footer)

</div>
