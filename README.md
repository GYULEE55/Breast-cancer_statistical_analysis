# 유방암 환자의 임상·병리학적 요인별 생존기간 차이 통계분석

> 팀 통키즈 | 이승규, 김명선, 모지윤, 방혜원 | 2025.07

---

## 📌 프로젝트 개요

유방암 환자의 생존율은 다양한 임상·병리학적 요인에 따라 크게 달라집니다. 본 프로젝트는 SEER 실제 환자 데이터를 기반으로 논문에서 제시된 핵심 임상 변수를 선정하고, 통계적 가설 검정을 통해 요인별 생존기간 차이를 분석합니다.

---

## 🎯 수행 목표

- 유방암 환자 데이터에서 생존기간에 유의미한 영향을 미치는 임상 변수 식별
- 논문 기반 가설 설정 → 실제 데이터로 통계적 검증
- 데이터 전처리부터 통계 분석, 시각화까지 전 과정 직접 수행

---

## 📊 주요 변수

| 변수 | 설명 |
|------|------|
| **ER** | Estrogen Receptor (에스트로겐 수용체) |
| **PR** | Progesterone Receptor (프로게스테론 수용체) |
| **HER2** | Human Epidermal growth factor Receptor 2 |
| **LNR** | Lymph Node Ratio (전이 림프절 비율) |
| **T-Stage** | 원발 종양의 크기 및 침윤 정도 |
| **N-Stage** | 림프절 전이 여부 및 범위 |
| **RT** | Radiation Therapy (방사선 치료 여부) |

---

## 🔬 분석 가설 및 결과

### 가설 1 — ER/PR 상태와 LNR에 따른 생존기간 차이

> "ER/PR 모두 양성(++) 그룹과 모두 음성(--) 그룹 간에 전이 여부(LNR)에 따라 생존기간에 유의미한 차이가 있다."

**검정 방법:**
- LNR 범주에 따른 ER/PR 간 생존 개월 차이 → **ANOVA**
- LNR과 ER/PR 간 관련성 → **카이제곱 검정**

**결과:** ANOVA 검정 결과 6개 그룹의 생존기간 차이가 통계적으로 매우 유의함 **(p = 0.000\*\*\*)**

<p align="center">
  <img src="./results/hypothesis1_anova.jpg" width="700"/>
</p>

---

### 가설 2 — N-stage, T-stage, LNR 조합에 따른 생존기간 차이

> "N-stage와 T-stage에 따라, 전이율 조합 그룹의 영향을 보정한 상태에서 생존기간에 유의미한 차이가 있다."

**검정 방법:**
- 각 T/N 조합에 대해 LNR Low/Middle vs High 그룹 간 생존개월 → **독립 T검정**
- T-stage, N-stage, LNR 조합과 생존 여부 분포 → **카이제곱 검정**

**결과:** 독립 T검정 결과 T/N/LNR에 따른 생존 개월 평균 차이가 통계적으로 유의미함 **(p < 0.001\*\*\*)**

<p align="center">
  <img src="./results/hypothesis2_ttest.jpg" width="700"/>
</p>

---

### 가설 3 — 성별, 호르몬 수용체 상태, 방사선치료 여부에 따른 생존기간 차이

> "성별, ER, PR, HER2 상태와 방사선치료 유무에 따라 생존기간에 유의미한 차이가 있다."

**검정 방법:**
- 성별별 Radiation 여부 + 호르몬 수용체 상태 조합에 따른 생존 개월 → **ANOVA**
- 치료 방식과 호르몬 수용체 상태 간 관련성 → **카이제곱 검정**

**결과:** 카이제곱 검정 결과 방사선치료 여부와 호르몬 수용체 상태 간 분포 차이가 통계적으로 매우 유의함 **(χ²=2336.99, p < 0.0001\*\*\*)**

<p align="center">
  <img src="./results/hypothesis3_anova.jpg" width="700"/>
</p>

<p align="center">
  <img src="./results/hypothesis3_table.jpg" width="700"/>
</p>

---

## 🔄 데이터 플로우차트

<p align="center">
  <img src="./results/flowchart.jpg" width="500"/>
</p>

- 총 코호트: **1,048,576명** → 제외 기준 적용 후 **692,838명**
- Y Radiation: 305,328명 / N Radiation: 383,533명

---

## ⚙️ 기술 스택

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)

- **분석**: Pandas, NumPy
- **통계 검정**: Scipy (ANOVA, T-test, Chi-square)
- **시각화**: Matplotlib, Seaborn

---

## 📁 프로젝트 구조

```
📦 Breast-cancer_statistical_analysis
├── results/
│   ├── hypothesis1_anova.jpg     # 가설 1 시각화
│   ├── hypothesis2_ttest.jpg     # 가설 2 시각화
│   ├── hypothesis3_anova.jpg     # 가설 3 시각화
│   ├── hypothesis3_table.jpg     # 가설 3 통계 테이블
│   └── flowchart.jpg             # 데이터 플로우차트
├── notebooks/
│   ├── hypothesis1.ipynb
│   ├── hypothesis2.ipynb
│   └── hypothesis3.ipynb
└── README.md
```

---

## 📌 주요 인사이트

- **ER/PR 수용체 상태**와 **LNR(전이 림프절 비율)**은 생존기간에 가장 강한 영향을 미침
- T-stage와 N-stage의 조합이 높을수록 LNR High 그룹에서 생존기간이 유의미하게 짧아짐
- 방사선치료 여부는 호르몬 수용체 상태와 강하게 연관되어 있으며, 생존기간에 유의미한 영향을 미침
- 설정한 **3개 가설 모두 p < 0.001 수준에서 통계적으로 유의**함을 확인

---

## 📚 참고문헌

- SEER (Surveillance, Epidemiology, and End Results) Database
- Breast Cancer Subtypes Based on ER/PR and Her2 Expression (2021)
- The lymph node ratio as prognostic factor in node-positive breast cancer
- 외 15편 논문 기반
