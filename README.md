** 기본 필수 **

---

## 07 · 한 파일로 회귀·분류 비교표 만들기
PPT 73쪽과 연결 · 권장 실습 60분 (07·08 합계)

**목표:** 숫자 예측과 클래스 예측을 각각 비교하고 결과를 파일로 남긴다.

**열 파일:** `07_project.py`. TODO만 먼저 완성합니다. 제공된 읽기·저장 코드를 다시 작성하지 않아도 됩니다.

**새 함수·옵션:** clone: 학습 전 전처리를 별도 준비(제공 코드) / Pipeline: 전처리→모델 / to_csv(index=False): 행 번호 없이 저장

**실행:** 현재 README가 있는 폴더(/01_기본필수)에서 아래 명령을 사용합니다.

```powershell
python 07_project.py
```

**출력** — 소수점 출력 자릿수·공백 표시는 환경에 따라 약간 다를 수 있습니다.

```text
분할: 12 4 4
회귀 비교 / 낮은 MAE가 좋음
 model  MAE_ms
 Dummy 253.750
Linear  17.886
분류 비교 / 높은 F1이 좋음
   model  F1
   Dummy 0.0
Logistic 0.0
저장: regression_comparison.csv, classification_comparison.csv, validation_predictions.csv
test는 학습·예측하지 않았습니다.
```

** 결과: ** 
결과 1. 회귀 모델들 중에서는 LinearRegreesion이 가장 오차가 작게(MAE_ms:17.886)에서 나왔으며,   
결과 2. 분류 모델들 중에서는 모두 F1-Score가 0으로 확인되어 해석이 불가합니다.

**완료 기준:** 회귀 2행·분류 2행·valid 4행 파일을 생성한다. 파일을 다시 실행해 같은 결과를 확인한다.

**생성되는 파일:** `regression_comparison.csv`, `classification_comparison.csv`, `validation_predictions.csv`



** 응용 **

---

## 07 · 회귀·분류 각각 세 후보 비교

PPT 73쪽과 연결 · 권장 실습 60분 (07·08 합계)

**목표:** 숫자 예측과 클래스 예측을 각각 비교하고 결과를 파일로 남긴다.

**열 파일:** `07_project.py`. TODO만 먼저 완성합니다. 제공된 읽기·저장 코드를 다시 작성하지 않아도 됩니다.

**새 함수·옵션:** 회귀 주 지표 RMSE 최소 / 분류 주 지표 F1 최대 / 동일 문제 안에서만 비교

**실행:** 현재 README가 있는 폴더에서 아래 명령을 사용합니다.

```powershell
python 07_project.py
```

**예상 출력** — 소수점 출력 자릿수·공백 표시는 환경에 따라 약간 다를 수 있습니다.

```text
회귀 / valid 20건
 model    scale  MAE_ms  RMSE_ms
 Dummy standard 541.260  658.745
Linear standard 551.797  639.996
 KNN15 standard 530.063  641.788
분류 / valid 20건
   model    scale    F1  Precision  Recall  FP  FN
   Dummy standard 0.000      0.000   0.000   0   6
Logistic standard 0.333      0.333   0.333   4   4
    KNN3 standard 0.545      0.600   0.500   2   3
저장: outputs의 비교표 2개와 validation_predictions.csv
test는 학습·변환·예측·평가하지 않았습니다.
```

** 결과: ** 
결과 1. 회귀 모델들 중에서는 비교적 KNN(K=15)가 가장 오차가 적은 선(MAE_ms:530.063, RMSE_ms:641.788)에서 나왔으며,  
결과 2. 분류 모델들 중에서는 비교적 KNN(K=3)이 가장 잘나왔습니다.(F1-Score: 0.545, Precision: 0.600, Recall: 0.500)

**완료 기준:** 각 비교표 3행과 valid 예측 120행(20건×3모델×2문제)을 저장한다.

**설명 질문:** Linear와 KNN의 회귀 RMSE 차이가 작을 때 무엇을 함께 말해야 하는가?

**생성되는 파일:** `outputs/regression_comparison.csv`, `outputs/classification_comparison.csv`, `outputs/validation_predictions.csv`

** 심화 ** 

 심화 · 구조는 체계적으로, 내용은 종전 응용 수준

심화라는 이름 때문에 고급 알고리즘·복잡한 예외처리·자동 테스트 작성으로 확장하지 않습니다. 기존 응용의 다중 입력·오류 사례·가중치·전처리 비교·K 탐색·저장 복원을 역할별로 정리합니다. **전체 TODO10곳**이며 모든 단계를 의무 수행하지 않습니다.

| 실습 | 들어갈 폴더 | 과제 |
|---|---|---|
| 01 | [실습01_선형회귀](실습01_선형회귀/README.md) | 두 계수·절편과 손계산 |
| 02 | [실습02_회귀오차](실습02_회귀오차/README.md) | 기준선 비교·큰 잔차3건 |
| 03 | [실습03_확률과오류](실습03_확률과오류/README.md) | 혼동행렬·가상 임계값2개 |
| 04 | [실습04_KNN가중치](실습04_KNN가중치/README.md) | 거리 표·가중 평균 |
| 05 | [실습05_스케일링](실습05_스케일링/README.md) | 세 스케일·중앙값 불변 |
| 06 | [실습06_K비교](실습06_K비교/README.md) | 분류F1·회귀RMSE, K 선택 |
| 07~08 | [day6_compare](day6_compare/README.md) | 모듈형 프로젝트·복원·보고서 |

각 폴더의 README부터 읽습니다. `data/`는 입력, `expected/`는 비교 자료, `outputs/`는 직접 생성 결과, `reports/`는 자신의 설명입니다. 위의 순서로 진행하되 각 실습은 독립 실행됩니다. 마지막 프로젝트도 앞 실습 결과 파일을 요구하지 않습니다.

실습01과04는 코드에 작은 입력이 있으므로 빈 data 폴더를 억지로 만들지 않았습니다. 여러 파일로 나누는 것은 책임을 분리하기 위한 것이지, 폴더 수를 늘리는 목표가 아닙니다.

**사용하지 않는 과제:** 거리 동률·과도한 K의 실패 테스트, 입력 계약 검증기, C 추가 탐색, JSON 설정 프레임워크, 그룹/시간 분할, 모델 보안 검사 구현. 제작 검수는 강사가 별도로 수행합니다.

응용·심화의 `requests.csv`는 원본과 같고, 분할 파일은 기존 소속·순서를 합친 단일 표입니다. test 입력·정답은 모델에서 사용하지 않습니다.