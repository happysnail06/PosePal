# PosePal

<div align="center">
<h3>25th YBIGTA Conference</h3>
![KakaoTalk_20241224_010135825](https://github.com/user-attachments/assets/30ab9b7f-8bc3-4129-8665-18011013b9e4)

<em>Your Friendly Fitness Coach: Real-time Exercise Analysis and Feedback System</em>

</div>

## 목차
- [문제 정의](#문제-정의)
- [선행 연구](#선행-연구)
- [세부 목표](#세부-목표)
- [접근 방법](#접근-방법)
- [결과 및 주요 기능](#결과-및-주요-기능)
- [팀 구성](#팀-구성)

---

## 문제 정의

좋은 PT 선생님을 찾는 것은 시간과 비용 면에서 많은 어려움을 동반합니다.  
운동 자세를 스스로 분석하고 교정할 수 있는 시스템이 있다면 어떨까요?  
**PosePal**은 사용자의 운동 자세를 실시간으로 분석하고 피드백을 제공하여 개인 맞춤형 운동 코칭 경험을 제공합니다.

---

## 선행 연구

*(생략)*

---

## 세부 목표

1. 사용자의 주요 관절 움직임을 실시간으로 분석하여 운동 자세 평가.
2. 바른 자세와 틀린 자세를 분류하여 점수화 및 리포트 생성.
3. 실시간 챗봇을 통해 운동 관련 궁금증 해소 및 심화 학습 지원.

---

## 접근 방법

### 태스크

1. **운동 자세 분석**
   - MediaPipe를 활용하여 운동 자세의 33개 주요 키포인트를 추적.
   - Multivariate Time-Series 데이터를 기반으로 시간의존성을 분석.
2. **운동 자세 평가**
   - ROCKET Classifier를 사용하여 시간의존 데이터를 효과적으로 분류.
   - Peak Detection 알고리즘을 통해 운동 반복 횟수와 자세 구간 파악.
3. **피드백 및 리포트 제공**
   - GPT API를 활용하여 개인 맞춤형 피드백 리포트 생성.
   - Prompt Engineering으로 GPT를 전문 피트니스 코치로 설정.

### 데이터셋

- **AI HUB 피트니스 자세 이미지 데이터**
  - 약 200,000 클립(15초/클립)을 분석하여 3백만 장의 이미지로 변환.
  - 다양한 신체 조건과 연령대를 반영한 데이터 품질 향상.
- **커스텀 데이터**
  - MediaPipe로 처리된 Raw Image 데이터를 활용하여 학습.
  - 운동별 약 10,000 프레임 사용.

### 모델링/아키텍처

- **MediaPipe**
  - Google의 Pose Estimation 프레임워크로 BlazePose를 기반으로 높은 정확도 제공.
- **ROCKET Classifier**
  - Random 1-D Kernels와 RidgeClassifier를 조합하여 Multivariate Time-Series 데이터를 효과적으로 분류.
- **GPT API**
  - 사용자의 운동 데이터를 바탕으로 언어 기반의 개인화된 피드백 생성.
- **Streamlit**
  - 사용자가 운동 영상을 업로드하고, 리포트를 확인할 수 있는 인터페이스 제공.

---

## 결과 및 주요 기능

1. **개인 맞춤형 리포트 생성**
   - 각 운동 반복(reps)마다 자세 분석 및 점수화 결과 제공.
   - 자세 교정을 위한 상세한 코칭 내용 포함.
2. **실시간 챗봇 기능**
   - 사용자의 질문에 실시간 응답하여 운동에 대한 궁금증 해소.
3. **모델 유연성**
   - 새로운 운동 데이터를 쉽게 적용할 수 있는 아키텍처 설계.

---

## 팀 구성

| 이름       | 팀  | 역할                              |
|------------|-----|-----------------------------------|
| 김준호 (팀장) | DS  | Multivariate Time-Series Modeling, Pose Estimation Modeling |
| 김서윤      | DA  | LLM, Reports Generation, Chatbot System |
| 김성환      | DS  | Video Processing, Pose Estimation Modeling |
| 이상헌      | DE  | Fullstack                        |
| 최수현      | DS  | Multivariate Time-Series Modeling, Pose Estimation Modeling |
| 홍규원      | DA  | LLM, Reports Generation, Chatbot System |
