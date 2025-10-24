# 3D Human Body Reconstruction (LVD + ICON)

단일 또는 4방향 사진만으로 3D 체형을 복원하고 부위별 치수를 자동 측정하는 모델을 개발한 프로젝트입니다.  
의복 상태에서도 형태 복원이 가능한 LVD(Learned Vertex Descent)와 ICON 모델을 결합하고, 복원된 Mesh 기반으로 실측 치수에 근접한 자동 계측까지 수행하도록 전체 파이프라인을 구현했습니다.  
(기간: 2022.09 – 2023.03)

---

## What I built
- SMPL 기반 **LVD + ICON 결합 구조 구현** 및 튜닝
- `trimesh` 기반 **자동 치수 측정 알고리즘 개발(body_measurements 수정)**
- 단일/4-view 입력 대응 파이프라인 및 결과 Mesh/Visualization 출력 구현

---

## Performance
10명 실측 기준 평균 절대 오차율 **7%**
| 지표 | 오차율 |
|------|--------|
| 몸무게 | 8% |
| 목둘레 | 13% |
| 가슴둘레 | 4% |
| 복부 | 6% |
| 팔둘레 | 9% |
| 엉덩이 | 3% |
| 허벅지 | 5% |

---

## Deployment / Outcome
- **KIMES 2023**(국제의료기기·병원설비 전시회) 시연 진행
- 특허 출원 — *체형예측시스템 및 체형예측시스템의 동작 방법*  
  (출원번호: 10-2023-0024467)

---

## Disclosure
- 연구용 모델/데이터/가중치는 저장소에 포함하지 않음
- 본 레포는 포트폴리오용으로 **결과 요약 및 구조 설명만 공개**

---

## Contact
이현희 · AI Research Engineer  
fly4hyun@naver.com
