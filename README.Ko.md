# Incident Management System  
### 멀티테넌트 기반 실시간 사고 보고 및 고급 분석 플랫폼

본 프로젝트는 다음 기술 스택을 기반으로 구축된 클라우드 기반 Incident Management System입니다.

- AWS RDS (MySQL)
- ASP.NET Core MVC
- Angular
- AWS Infrastructure

본 플랫폼은 조직 단위로 사고를 실시간으로 보고·분류·추적·분석할 수 있도록 설계되었습니다.

저는 전체 시스템 아키텍처 설계에 참여하였으며,  
**End-to-End Analytics Dashboard 설계 및 구현을 단독으로 담당하였습니다.**

---

## 📌 시스템 개요

본 시스템은 다음과 같은 목적을 갖습니다:

- 실시간 사고 등록 (예: COVID, 총기 사건, 독감, 위협 사례 등)
- 계층형 IssueType 기반 사고 분류
- Role 기반 접근 제어 (RBAC)
- 사고 발생 즉시 관계자 알림
- 사고 처리 상태 및 이력 추적
- 다차원 분석 대시보드 제공

각 Incident는 다음 흐름을 따릅니다:

1. IssueType 계층 구조에 따라 분류
2. 조직 및 역할(Role)에 따라 관리
3. 상태 변경을 통해 라이프사이클 추적
4. 분석용 집계 데이터에 반영

---

## 🏗 아키텍처

### Infrastructure
- AWS RDS (MySQL)
- orgId 기반 멀티테넌트 구조
- 클라우드 배포 환경

### Backend
- ASP.NET Core MVC
- RESTful API 계층
- Role 기반 권한 관리
- Incident 라이프사이클 관리

### Frontend
- Angular
- Role 기반 UI 제어
- 인터랙티브 대시보드
- 지도(Map) 기반 시각화

---

## 🧩 핵심 도메인 모델

주요 엔티티:

- Organization (멀티테넌트 루트)
- User / Role / UserType
- Incident (핵심 엔티티)
- IssueType (계층형 분류 구조)
- Site / Location
- SelfReport

지원 기능:

- Parent-Child 구조의 IssueType 계층 모델
- 다중 역할 기반 관리 체계
- 조직 단위 데이터 분리
- 상태 기반 사고 추적

---

# 📊 프로덕션 분석 대시보드 (단독 담당 영역)

Analytics 계층은 제가 단독으로 설계 및 구현하였습니다.

### 데이터 흐름

```
MySQL (Analytics Views)
        ↓
ASP.NET Core REST API
        ↓
Angular Dashboard
        ↓
인터랙티브 그래프 & 지도 시각화
```

---

## 🔎 분석 기능

### 1️⃣ Issue Type별 사고 분석
- 기간 필터링
- IssueType 집계
- Bar + Donut 차트 시각화
- 총 사고 건수 표시

**목적:** 주요 사고 유형 및 추세 변화 파악

---

### 2️⃣ Location별 사고 분석
- Site 단위 집계
- IssueType + 기간 필터링
- 위치별 분포 비교

**목적:** 고위험 지역 및 사고 집중 구역 분석

---

### 3️⃣ Reporter 기반 분석
- 신고자 단위 집계
- 행동 패턴 분석
- Role 기반 필터링 적용

**목적:** 신고 패턴 및 시스템 신호 분석

---

### 4️⃣ Risk / Threat 수준 분석
- 위협 단계 (Low / Medium / High) 분류
- 시간대별 분포 분석
- 위험도 추세 시각화

**목적:** 위협 수준 상승 패턴 모니터링

---

### 5️⃣ 사고 추세 분석
- 월별 / 분기별 집계
- 상태별 필터링 (New / In Progress / Closed)
- 장기 추세 분석

**목적:** 운영 부하 및 처리 속도 평가

---

### 6️⃣ 공간 분석 (Map 기반 시각화)
- 인터랙티브 지도
- 사고 클러스터 표시
- Top 10 피해 Site
- 지역별 사고 분포 분석

**목적:** 공간 기반 위험 모니터링 및 자원 배치 지원

---

# 🛠 DB 기반 분석 설계

모든 분석은 최적화된 MySQL View를 기반으로 구성되었습니다.

적용 전략:

- GROUP BY 기반 집계
- 날짜 컬럼 인덱스 활용
- 조건부 집계(Conditional Aggregation)
- orgId 기반 데이터 분리
- 사전 집계(View) 구조 설계

설계 목표:

- API 연산 부담 최소화
- 대시보드 응답 속도 개선
- 다차원 필터링 지원
- 확장성 유지

---

# 🔐 Role 기반 분석 제어

Analytics 계층에서는 다음을 보장합니다:

- 조직 단위 데이터 격리
- Role 기반 접근 통제
- 민감 사고 유형 필터링
- 신고자 가시성 제어

데이터 필터링은 UI가 아닌 쿼리 레벨에서 적용됩니다.

---

# 🎯 나의 기여

### 시스템 레벨 참여
- 도메인 모델 설계 참여
- Incident / IssueType 스키마 설계 기여
- RBAC 구조 설계 협업

### 단독 담당 (Analytics 계층)
- 분석 데이터 모델 설계
- DB Analytics View 설계 및 구현
- REST Analytics API 구현
- Angular Dashboard 구현
- 필터링 및 Drill-down 로직 구현
- Map 기반 시각화 통합
- Analytics 구조 유지보수 및 확장

---

# 🚀 기술적 특징

- 멀티테넌트 SaaS 아키텍처
- 계층형 IssueType 모델
- 실시간 사고 운영 관리
- DB 중심 집계 최적화 전략
- 공간 기반 시각화
- Role 기반 데이터 노출 제어
- End-to-End Analytics 파이프라인 설계

---

# 📈 프로젝트 효과

본 시스템은 조직이 다음을 가능하게 합니다:

- 긴급 사고의 신속한 보고
- 실시간 위험 분포 모니터링
- 처리 워크플로우 추적
- 과거 사고 트렌드 분석
- 데이터 기반 의사결정 지원

Analytics Dashboard는 운영 데이터를 **의사결정 가능한 인사이트**로 변환합니다.
