# 3D Body Reconstruction from a Single Image

> 단일(또는 4방향) 사진만으로 3D 체형 복원 및 부위별 치수 측정
> 기간: 2022.09 – 2023.03 | Repo: github.com/fly4hyun/3d-body-reconstruction

---

## Summary

* **LVD(SMPL 기반) × ICON(implicit normal 기반) 결합**으로 단일 이미지에서도 체형과 의복 디테일을 동시에 복원
* `trimesh` 기반 **자동 신체 치수 측정 알고리즘** 구현 → 실측 대비 **평균 오차율 7%** (10명 기준)
* **KIMES 2023** 부스 시연 및 **특허 출원** 완료 (출원번호: 10-2023-0024467)

---

## Model Overview

### Why LVD + ICON

* **LVD (Learned Vertex Descent)**: 마른/비만 등 **체형 형상 복원**에 강점 (SMPL 기반 파라메트릭 바디)
* **ICON (Implicit Clothed humans Obtained from Normals)**: **의복 주름·얼굴 등 디테일 복원**에 강점
* **결합 전략**: ICON의 포즈/형상 추정부 일부를 **LVD 결과로 대체**하여, 체형 일치도를 높이면서 ICON의 디테일 장점을 유지

### Trade-off / Observation

* LVD로 체형을 안정화하면 **ICON 단독 대비 체형 반영성** 확실히 개선
* 다만 LVD 결과가 이미지와 불일치할 때, ICON 단계에서 해당 부분을 **지워버리는 현상** 관찰 → 후처리 및 안정화 규칙 적용

---

## Pipeline

1. **입력**: 단일 이미지(또는 전·후·좌·우 4방향)
2. **체형 복원 (LVD)**: SMPL 파라미터 추정 → 체형 형상 안정화
3. **디테일 복원 (ICON)**: Normals 기반 implicit surface로 의복/주름/세부 윤곽 보강
4. **치수 산출 (Measurements)**: `trimesh` 기반 **body_measurements** 모듈 수정 → 키/몸무게(평균 밀도 가정) 및 부위별 둘레 계산
5. **출력**: 3D 메쉬(GLB/OBJ) + 부위별 치수 JSON

---

## My Contribution

* **LVD×ICON 결합 아키텍처** 설계/구현 (ICON의 포즈/형상 추정 일부를 LVD로 대체)
* `trimesh` **body_measurements 라이브러리 수정** 및 자동 치수 측정 파이프라인 개발
* **평가 설계**: 8~10명 대상 전/후/좌/우 촬영 및 **실측-예측 비교**
* **오류 분석**: 4방향 입력 시 **거북목/팔 각도 등 자세 불일치**로 단일 이미지 대비 오차 증가 현상 규명
* **데모/전시 기획**: **KIMES 2023** 실시간 시연 준비 및 운영
* **지식재산화**: ‘체형예측시스템 및 체형예측시스템의 동작 방법’ **특허 출원**

---

## Quantitative Evaluation (10명 기준)

| Metric      | Avg Error |
| ----------- | --------: |
| **Overall** |    **7%** |
| Body weight |        8% |
| Neck        |       13% |
| Chest       |        4% |
| Abdomen     |        6% |
| Arm         |        9% |
| Hip         |        3% |
| Thigh       |        5% |

> 참고: 4방향 입력의 경우 자세 불일치(거북목, 팔 각도 등)로 단일 이미지 대비 오차 증가 경향

---

## Demo & Exhibition

* **KIMES 2023**(국제의료기기·병원설비 전시회) 현장 시연 및 설명 진행

---

## Patent

* **특허명**: 체형예측시스템 및 체형예측시스템의 동작 방법
* **출원번호**: 10-2023-0024467
* **출원일**: 2023.02.23

---

## Image Assets (README에 삽입용)

> 아래 파일명으로 저장 후 README에 삽입하세요. (한 장으로 구성 권장)

1. **논문/모델 개념 이미지 콜라주**
   `assets/lvd_icon_papers.jpg`  — LVD/ICON 논문 대표 도식 요약

2. **입·출력 샘플 (단일 이미지 → 3D)**
   `assets/sample_inout_single.jpg`  — 입력 사진, LVD 결과, ICON 결과, LVD+ICON 결과 비교

3. **ICON vs LVD+ICON 비교**
   `assets/icon_vs_lvdicon.jpg` — ICON 단독 결과 대비 체형 반영성 개선 사례

4. **KIMES 2023 현장 사진**
   `assets/kimes2023_demo.jpg` — 부스/시연 장면

> 예시 삽입 마크다운
>
> ```markdown
> ![LVD & ICON Papers](assets/lvd_icon_papers.jpg)
> ![Single Image → 3D Outputs](assets/sample_inout_single.jpg)
> ![ICON vs LVD+ICON](assets/icon_vs_lvdicon.jpg)
> ![KIMES 2023 Demo](assets/kimes2023_demo.jpg)
> ```

---

## Notes on Disclosure

본 프로젝트는 **데모/전시 목적**으로, 일부 학습/전처리 파이프라인과 내부 측정 데이터는 비공개입니다.
요청 시 구조/원리/지표 수준으로 설명 가능합니다.
