# 📂 AI 생성 블로그 스팸 탐지 데이터셋 구조 안내

본 `dataset` 폴더에는 프로젝트 파이프라인 전 과정(수집 ➡️ 결합 ➡️ 전처리)에서 생성된 총 8개의 데이터셋 파일이 보관되어 있습니다. 

주피터 노트북 코드(`데마_최종_통합_파이프라인_고도화.ipynb`)는 아래의 **[3. Processed 데이터셋]**을 자동으로 불러와서 사용합니다. 누구나 처음부터 데이터 구조를 파악하고 재현할 수 있도록 기초 원본(Raw) 파일부터 최종 전처리 파일까지 모두 포함하였습니다.

---

## 1. [Raw] 기초 원본 데이터셋 (3개)
가장 기본이 되는 순수 크롤링 및 생성 원본 파일들입니다.
* `human_dataset_master.csv`: 실제 인간이 작성한 맛집/리뷰 블로그 원본 데이터
* `ai_dataset_master.csv`: 챗GPT에게 일반적인 프롬프트로 생성하게 한 **GPT형 AI(v1)** 글 원본
* `ai_dataset_v2.csv`: 건조체, 단문 위주로 인간을 모방하도록 프롬프트를 조작하여 생성한 **인간형 위장 AI(v2)** 글 원본

## 2. [Mixed] 실험용 결합 원본 데이터셋 (2개)
각 실험(Experiment)의 목적에 맞게 Human 데이터와 AI 데이터를 비율에 맞춰 섞어둔 파일입니다. (전처리 전 단계)
* `dataset_exp2_human_vs_ai_v2.csv`: Human + AI_v2 결합 (EXP2 인간형 위장 탐지용)
* `dataset_exp3_human_vs_mixed_ai.csv`: Human + AI_v1 + AI_v2 결합 (EXP3 실제 인터넷 생태계 혼합용)

## 3. [Processed] 모델 학습용 전처리 완료 데이터셋 (3개) 🌟
**실제 머신러닝 모델(XGBoost)에 들어가기 직전, 불용어 제거 및 KoNLPy 형태소 피처 추출이 모두 완료된 최종 파일입니다.** 코드를 실행하면 이 파일들을 로드합니다.
* `ml_dataset_processed.csv`: **EXP1** (Human vs AI_v1) 모델 학습 및 평가용
* `ml_dataset_exp2_processed.csv`: **EXP2** (Human vs AI_v2) 모델 학습 및 평가용
* `ml_dataset_exp3_processed.csv`: **EXP3 & AI_vs_AI** (혼합 탐지 및 AI 문체 진화 분석) 모델 학습 및 평가용

---
**💡 팁:** 깃허브 클론 후 `데마_최종_통합_파이프라인_고도화.ipynb` 코드를 실행하실 때, 이 폴더의 위치를 옮기거나 파일명을 변경하지 마세요. 코드가 상대 경로(`./dataset/...`)를 통해 자동으로 데이터를 불러옵니다.
