---
layout: default
title: C++ Memory Management & Optimization
---

# ⚙️ C++ Memory Management & Optimization
> **Summary:** 홍정모의 따배씨 강의와 펄어비스 기술 블로그를 참고하여, 게임 엔진에서의 효율적인 메모리 관리 기법을 연구한 기록입니다.

---

## 1. 스마트 포인터와 소유권 (Smart Pointers)
### 📝 학습 내용 (Today I Learned)
- **Raw Pointer**의 위험성(메모리 누수, 댕글링 포인터)을 해결하기 위해 C++11부터 도입됨.
- `std::unique_ptr`: 독점 소유권. 복사 불가능, 이동만 가능. 오버헤드가 거의 없음.
- `std::shared_ptr`: 공유 소유권. Reference Counting 비용 발생.

### 💡 Insight: 엔진에서의 적용
- 게임 오브젝트 컴포넌트 시스템에서는 부모가 자식을 `unique_ptr`로 관리하는 것이 명확할 것 같다.
- 렌더링 파이프라인에서 텍스처 리소스를 공유할 때는 `shared_ptr`가 유용하겠지만, 순환 참조(Circular Reference)를 조심해야 한다.

---

## 2. 가상 함수(Virtual Function)의 비용
*(여기에 공부한 내용을 자유롭게 추가해보세요)*
