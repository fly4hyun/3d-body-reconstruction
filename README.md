# 3D Human Body Reconstruction (LVD + ICON)

> 단일 또는 4방향 이미지만으로 3D 체형 복원 및 치수 자동 측정 모델 개발
> 기간: 2022.09 – 2023.03

---

## Summary

* 단일/4-view 입력만으로 **의복 상태에서도 체형 복원** 가능한 모델 개발
* 복원 Mesh 기반으로 **부위별 신체치수 자동 산출**까지 End-to-End 구현

---

## Technical Highlights

* **SMPL 기반 LVD + ICON 결합 구조** 설계 및 구현
* `trimesh` 기반 body_measurements 라이브러리 수정으로 **치수 자동화 알고리즘 개발**
* ## Performance (10명 실측 기준)

| 항목        | 평균 절대 오차율 |
| --------- | --------- |
| 몸무게       | 8%        |
| 목둘레       | 13%       |
| 가슴둘레      | 4%        |
| 복부        | 6%        |
| 팔둘레       | 9%        |
| 엉덩이       | 3%        |
| 허벅지       | 5%        |
| **전체 평균** | **7%**    |

---

## Deployment / Output

* **KIMES 2023 전시회 실시간 시연**
* 특허 출원: *체형예측시스템 및 동작 방법* (출원번호: 10-2023-0024467)

---

## Visual Examples (to be inserted)

* 복원 결과 Mesh 렌더링 캡처
* 입력 대비 전/후 비교 이미지
* 치수 측정 결과 Overlay 시각화

> 실제 이미지는 `docs/figures/` 하위에 추가 예정

---

## Disclosure

* 연구 산출물은 전시/시연 기반 공개 범위 내에서만 제공
* 모델 가중치/데이터/세부 학습 코드는 저장소에 포함하지 않음

---

## Contact

이현희 / AI Research Engineer
[fly4hyun@naver.com](mailto:fly4hyun@naver.com)
