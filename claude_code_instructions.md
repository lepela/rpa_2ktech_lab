# PA/PAD 교육 사이트 콘텐츠 생성 지침

## 역할
너는 Power Automate / Power Automate Desktop 교육 사이트의 콘텐츠 작성자야.
Just the Docs 테마 기반 Jekyll 사이트(docs/ 폴더)에 들어갈 마크다운 파일을 생성한다.

---

## 파일 생성 규칙

- 저장 위치: `docs/`
- 파일명: `m0-orientation.md`, `m1-overview.md` 형태
- frontmatter 필수 포함
- 스크린샷 필요 위치: `<!-- SCREENSHOT: 설명 -->` 형태로 placeholder 삽입
- 실습 단계는 번호 리스트로 명확하게 구분

---

## frontmatter 템플릿

```yaml
---
title: 제목
parent: 📘 기본과정
nav_order: 숫자
---
```

---

## 콘텐츠 톤 & 원칙

### 대상
- 코딩 경험 없는 시티즌 개발자
- HTML/CSS 개념 전무 가정
- 엑셀 함수 경험은 있을 수 있음

### 3가지 원칙
```
개념: 최소한으로 (왜 필요한지만)
구현: LLM에 위임 (어떻게는 물어봐라)
체험: 반드시 직접 (눈으로 확인해라)
```

### 어투
- 친근하고 명확하게
- "~입니다" 체
- 어려운 용어 첫 등장 시 반드시 한 줄 설명
- 겁주지 않기 — "어렵지 않습니다", "이것만 알면 됩니다"

### LLM 활용 팁
- 막히는 구간마다 LLM 활용 패턴 삽입
- 프롬프트 예시는 반드시 나쁜 예 vs 좋은 예 대비로

---

## 페이지 구조 템플릿

```
## 🎯 학습 목표
## ⏱ 예상 소요 시간
  | 구분 | 시간 |
  | 강사 설명 | N분 |
  | 실습 | N분 |
  | 버퍼 | N분 |
## 개념 설명
## 실습
  ### 준비물
  ### 단계별 가이드
  <!-- SCREENSHOT: 설명 -->
  > 💡 팁: ...
  > ⚠️ 주의: ...
## ✅ 핵심 정리
## 👉 다음 모듈
```

---

## 생성할 모듈 목록

### 📘 기본과정

| 파일명 | 제목 | nav_order |
|---|---|---|
| `m0-orientation.md` | M0. 오리엔테이션 | 1 |
| `m1-overview.md` | M1. Power Platform 개요 | 2 |
| `m2-pad-basic.md` | M2. PAD 기초 | 3 |
| `m2-lab1.md` | M2 실습 — 첫 번째 흐름 | 4 |
| `m3-web-excel.md` | M3. 웹+엑셀 자동화 | 5 |
| `m3-lab1.md` | M3 실습 — 오피넷→엑셀 | 6 |
| `m4-ui-email.md` | M4. UI+이메일 자동화 | 7 |
| `m4-lab1.md` | M4 실습 — Contoso 반복입력 | 8 |
| `m5-pa-cloud.md` | M5. PA 클라우드 흐름 맛보기 | 9 |
| `m5-lab1.md` | M5 실습 — 템플릿 흐름 | 10 |
| `m6-closing.md` | M6. 마무리 & 다음단계 | 11 |

### 🛠 팁 & 레퍼런스

| 파일명 | 제목 | nav_order |
|---|---|---|
| `t1-prompt-guide.md` | T1. LLM 프롬프트 가이드 | 1 |
| `t2-selector-guide.md` | T2. 셀렉터 정제 가이드 | 2 |
| `t3-expression-ref.md` | T3. 자주 쓰는 표현식 모음 | 3 |
| `t4-troubleshooting.md` | T4. 트러블슈팅 레퍼런스 | 4 |

---

## 모듈별 상세 지침

---

### M0. 오리엔테이션
**시간:** 15분  
**목적:** 환경 확인, 하루 흐름 안내, 심리적 준비

**포함 내용:**
- 오늘 배울 것 한눈에 보기 (모듈 맵)
- 사전 준비 체크리스트
  - [ ] Microsoft 365 계정 로그인
  - [ ] Power Automate Desktop 설치
  - [ ] make.powerautomate.com 접속
  - [ ] Chrome 브라우저 + PAD 확장 설치
- 실습 환경 안내 (계정 종류, OneDrive 경로)
- "이 과정의 철학" — 개념 최소, LLM 활용, 직접 체험

**주의사항 명시:**
- Windows Home에서 클라우드 런타임 불가 안내
- 조직 정책으로 PAD 설치 막힌 경우 대응

---

### M1. Power Platform 개요
**시간:** 강사 설명 30분 + Q&A 15분  
**목적:** DPA/RPA 개념 이해, PA vs PAD 역할 구분

**포함 내용:**
1. 자동화가 왜 필요한가
   - 송장 처리 사례: 연 300시간 절감, 24/7 처리
   - "사람이 반복하는 일은 기계가 할 수 있다"
2. Power Platform 구성요소 개요
   - Power BI / Power Apps / Power Automate / Copilot Studio
   - 이 과정의 범위: Power Automate + PAD
3. PA vs PAD 비교표

| 구분 | Power Automate (PA) | Power Automate Desktop (PAD) |
|---|---|---|
| 목적 | 클라우드 서비스 간 통합 | PC 반복 작업 자동화 |
| 기술 | API / 커넥터 | UI 자동화 / RPA |
| 실행 | 클라우드 서버 | 내 PC |
| 비유 | 시스템끼리 대화 | 사람 손을 대신 |

4. 테넌트 / 환경 개념
   - 테넌트: 우리 회사 전용 MS 클라우드 공간
   - 환경: 테넌트 안의 개발/테스트/운영 구분
5. Attended vs Unattended
   - Attended: 내가 보는 앞에서 실행
   - Unattended: 혼자 알아서 실행 (서버/야간)

**핵심 메시지:**
> "PA는 시스템이 연결된 자동화, PAD는 사람 손을 대신하는 자동화"

---

### M2. PAD 기초
**시간:** 강사 설명 25분 + 미니실습 25분  
**목적:** PAD 화면 파악, 변수/제어구조 이해, 첫 흐름 실행

**포함 내용:**
1. 화면 구성 파악
   - 콘솔 / 디자이너 구조
   - 액션 패널 / 캔버스 / 변수 패널
   - 하위 흐름(서브흐름) 탭
2. 변수
   - "이름표 붙은 상자" 비유로 설명
   - 타입별 설명 (최소한으로)

| 타입 | 한 줄 설명 | 예시 |
|---|---|---|
| 텍스트 | 글자 상자 | "서울" |
| 숫자 | 숫자 상자 | 2024 |
| Boolean | 켜짐/꺼짐 | True/False |
| 리스트 | 같은 종류 묶음 | [서울, 부산, 대구] |
| 데이터테이블 | 엑셀 표 그 자체 | For Each에서 등장 |

   - Object는 언급 생략 (Day 1 범위 초과)
   - `%변수명%` 참조 방식 강조
   - **변수 패널에서 실시간 값 확인** — 눈에 보인다는 것 강조

3. 제어구조
   - If/Else: "조건에 따라 다르게"
   - For Each: "목록을 하나씩 처리"
   - Loop: "N번 반복"
   - Switch: 언급만 (복잡한 조건 분기 시)

4. 흐름제어
   - 서브흐름 개념: "큰 흐름을 역할별로 나누기"
   - Main + 서브흐름 구조 도식

5. Input / Output Parameter
   - PA에서 PAD 호출 시 데이터 전달 방식
   - "PA가 PAD를 부를 때 전달하는 값"

**미니실습 포함** (M2-Lab1로 분리)

---

### M2-Lab1. 첫 번째 흐름 만들기
**시간:** 20분  
**시나리오:** 현재 날짜+시간을 메시지 박스로 출력

**단계:**
1. 새 흐름 생성
2. `현재 날짜 및 시간 가져오기` 액션 추가
3. `메시지 표시` 액션으로 결과 출력
   - `%CurrentDateTime%` 참조
4. 실행 → 변수 패널에서 값 확인
5. 확장: 텍스트 변수 추가해서 메시지 커스텀

**LLM 팁 삽입:**
```
날짜 형식을 바꾸고 싶다면?
→ LLM에게: "PAD에서 CurrentDateTime을 yyyy년 MM월 dd일 형식으로 바꾸는 표현식"
```

---

### M3. 웹+엑셀 자동화
**시간:** 강사 설명 20분 + 실습 70분  
**목적:** 웹 데이터 추출 → 엑셀 기록 체인 완주

**포함 내용:**
1. 브라우저 자동화 개요
   - PAD 지원 브라우저 (Chrome/Edge)
   - Chrome 확장 설치 확인
2. **셀렉터 — 핵심 개념 (최소한으로)**

   > HTML이 뭔지 몰라도 됩니다. 이것만 알면 됩니다:
   > 브라우저의 모든 요소에는 "주소"가 있습니다.
   > id: 페이지에서 단 하나뿐인 고유 주소
   > class: 비슷한 요소들이 공유하는 주소

3. PAD 자동캡처의 한계
   - 자동캡처로 잡히는 셀렉터 예시
   - 왜 불안정한가: 값이 바뀌거나 구조가 바뀌면 깨짐
   - **설계된 실패:** 자동캡처 그대로 실행 → 깨지는 것 확인

4. 셀렉터 정제 방법
   ```
   ① PAD 자동캡처로 일단 잡기
   ② 실행 → 깨지는 것 확인
   ③ Ctrl+Shift+C → 원하는 요소 클릭
   ④ 코드 확인 후 Ctrl+C (Copy selector 선택)
   ⑤ LLM에 붙여넣기:
      "이 코드에서 PAD 웹자동화에 쓸 최적의 CSS 셀렉터 찾아줘"
   ⑥ 나온 셀렉터를 PAD에 직접 입력 → 테스트
   ```
   <!-- SCREENSHOT: Ctrl+Shift+C 인스펙터 화면, Copy selector 위치 -->

5. 엑셀 자동화 개요
   - 실행/저장/종료
   - 데이터 읽기 (셀/범위/전체)
   - 데이터 쓰기

**실습:** M3-Lab1로 분리

---

### M3-Lab1. 오피넷 유가 → 엑셀 기록
**시간:** 45분  
**시나리오:** 오피넷에서 현재 유가 조회 → 날짜+가격 엑셀 누적 기록

**서브흐름 구조 (첫 번째 적용):**
```
Main
  ├── GetFuelPrice (오피넷 스크래핑)
  └── WriteToExcel (엑셀 기록)
```

**단계:**
1. 새 흐름 생성 + 서브흐름 2개 추가
2. GetFuelPrice 서브흐름
   - Chrome 시작: `https://www.opinet.co.kr`
   - 웹 페이지 요소 추출
   - **자동캡처 시도 → 셀렉터 확인**
   - CSS 셀렉터로 교체: `#oilcon1 .oil_info dl:first-child dd span.text-3`
   <!-- SCREENSHOT: 오피넷 유가 요소 선택 화면 -->
3. WriteToExcel 서브흐름
   - Excel 시작 (새 파일)
   - 현재 날짜 가져오기
   - 워크시트에 쓰기 (날짜, 유가)
   - 저장 후 종료
4. Main에서 두 서브흐름 순서대로 호출
5. 실행 → 엑셀 파일 확인

**수강생 직접 해볼 것:**
- 지역평균 가격도 같은 패턴으로 추가
- 셀렉터: `#sido_price1 span.text-3`

> 💡 **LLM 활용 팁**
> 셀렉터를 직접 찾고 싶다면:
> 1. F12 → Elements 탭에서 원하는 요소 찾기
> 2. 우클릭 → Copy → Copy selector
> 3. LLM에게: "이 CSS 셀렉터를 PAD 웹자동화에 최적화해줘: [붙여넣기]"

---

### M4. UI+이메일 자동화
**시간:** 강사 설명 20분 + 실습 70분  
**목적:** 데스크톱 앱 UI 자동화 + 완료 후 이메일 발송 연결

**포함 내용:**
1. UI 자동화 개요
   - 브라우저 자동화와 구조는 동일
   - 차이점: 데스크톱 앱의 요소를 잡음
   - UI 요소 캡처 방식 (Ctrl+클릭)
   - 선택기 직접 수정 방법
2. 마우스/키보드 액션
   - 텍스트 입력 / 버튼 클릭 / 드롭다운 선택
3. PAD Outlook 액션
   - Office 365 Outlook 연결 참조
   - 이메일 보내기 액션
   - **동적 콘텐츠:** `%변수명%` 으로 본문에 변수 삽입
   - PA의 동적 콘텐츠와 같은 개념임을 명시

**실습:** M4-Lab1로 분리

---

### M4-Lab1. Contoso 반복입력 + 메일 발송
**시간:** 45분  
**시나리오:** 엑셀 데이터를 읽어 Contoso Invoicing 앱에 반복 입력 → 완료 후 메일 발송

**서브흐름 구조:**
```
Main
  ├── ReadInvoiceData (엑셀 읽기)
  ├── FillInvoiceApp (Contoso 반복 입력)
  └── SendCompletionMail (완료 메일)
```

**준비물:**
- Contoso Invoicing 앱 설치 완료
- 실습용 엑셀 파일 (Date/Account/Contact/Amount 컬럼)

**단계:**
1. ReadInvoiceData 서브흐름
   - Excel 시작 → 전체 데이터 읽기 → DataTable 변수 저장
2. FillInvoiceApp 서브흐름
   - Contoso 앱 실행
   - For Each로 DataTable 반복
     - 새 항목 추가 버튼 클릭
     - 각 필드에 변수 입력
     <!-- SCREENSHOT: Contoso 앱 UI 요소 캡처 화면 -->
3. SendCompletionMail 서브흐름
   - Outlook 연결 참조 확인
   - 이메일 보내기 액션
   - 본문에 처리 건수 변수 삽입: `%처리건수%건 입력 완료`
4. Main에서 순서대로 호출

> ⚠️ **UI 요소 캡처 주의**
> 자동캡처 후 선택기가 너무 구체적으로 잡히면
> 텍스트 편집기로 직접 수정하세요.
> 모르겠으면 LLM에게 물어보세요.

---

### M5. PA 클라우드 흐름 맛보기
**시간:** 강사 설명 10분 + HOL 20분  
**목적:** PA의 존재감 체험, Day 2 기대감 형성

**포함 내용:**
1. PA 클라우드 흐름 3종
   - 인스턴트 / 자동화 / 예약
2. 커넥터 개념
   - "PA와 외부 서비스를 연결하는 다리"
   - 표준 vs 프리미엄 (라이선스 주의)
3. "PAD와 PA는 이렇게 연결됩니다" — 전체 그림

**HOL (짧게, 성공 경험 위주):**
- 템플릿으로 이메일→Teams 채널 전달 흐름 (10분)
- 예약 흐름으로 자동 메일 발송 (10분)

> 💡 "PAD에서 %변수%로 값을 넣은 것처럼
>    PA에서도 동적 콘텐츠로 값을 넣습니다.
>    같은 개념, 다른 모양입니다."

**핵심 메시지:**
> "오늘은 PAD를 배웠습니다.
>  내일(Day 2)은 이걸 더 똑똑하게 만드는 법을 배웁니다."

---

### M6. 마무리 & 다음단계
**시간:** 30분  
**목적:** 복습, Q&A, 다음 단계 안내

**포함 내용:**
- 오늘 배운 것 한눈에 정리
- 혼자 해볼 수 있는 것들 (숙제 아님, 권장)
- 다음 단계 안내
  - Day 2: Copilot Studio
  - Day 3: 실전 프로젝트 (HR 채용 시스템)
  - PL-900 시험 경로
  - MS Learn 링크
  - 커뮤니티 링크

---

### T1. LLM 프롬프트 가이드
**목적:** PAD 작업 시 LLM을 효과적으로 활용하는 법

**포함 내용:**
1. 나쁜 프롬프트 vs 좋은 프롬프트

| ❌ 나쁜 예 | ✅ 좋은 예 |
|---|---|
| "전화번호 표현식 알려줘" | "PAD에서 핸드폰번호 형식(010-XXXX-XXXX) 유효성 검사하는 표현식" |
| "날짜 바꾸는 방법" | "PAD에서 CurrentDateTime을 yyyy-MM-dd 텍스트로 변환하는 표현식" |
| "조건문 예시" | "PAD에서 텍스트 변수가 비어있는지 확인하는 If 조건 작성법" |
| "셀렉터 찾아줘" | "이 HTML 코드에서 PAD 웹자동화에 쓸 최적의 CSS 셀렉터 찾아줘: [코드]" |

2. 좋은 프롬프트 법칙
   ```
   도구 명시 (PAD / PA)
   + 변수 타입 명시
   + 원하는 결과 명시
   = 쓸만한 답변
   ```

---

### T2. 셀렉터 정제 가이드
**목적:** 웹 자동화에서 셀렉터가 깨질 때 대처법

**포함 내용:**
1. PAD 자동캡처가 불안정한 이유
2. id vs class — 한 줄 설명
3. 단계별 정제 절차 (M3 내용 레퍼런스로 상세화)
4. 자주 쓰는 안정적인 셀렉터 패턴
5. LLM 활용 셀렉터 최적화

---

### T3. 자주 쓰는 표현식 모음
**목적:** 실습 중 자주 필요한 표현식 빠른 참조

**포함 내용 (카테고리별):**
- 날짜/시간 포맷
- 텍스트 처리 (자르기/합치기/찾기)
- 숫자 계산
- 조건 표현식
- 각 표현식마다 "이럴 때 씁니다" 한 줄 설명

---

### T4. 트러블슈팅 레퍼런스
**목적:** 자주 발생하는 오류 빠른 해결

**포함 내용:**
- PAD 설치 오류
- 브라우저 확장 연결 안 됨
- 셀렉터 요소를 찾을 수 없음
- Excel 파일 잠김 오류
- Outlook 커넥터 인증 오류
- 흐름 실행 중 예상치 못한 종료

---

## 참조 지식베이스

### 공식 문서
- PAD 액션 전체 레퍼런스:
  https://learn.microsoft.com/ko-kr/power-automate/desktop-flows/actions-reference
- PAD 셀렉터 가이드:
  https://learn.microsoft.com/ko-kr/power-automate/desktop-flows/build-custom-selectors
- PA 커넥터 레퍼런스:
  https://learn.microsoft.com/ko-kr/connectors/connector-reference/
- PAD 변수 타입:
  https://learn.microsoft.com/ko-kr/power-automate/desktop-flows/variable-data-types

### 실습 관련
- Automation in a Day 공식 학습 경로:
  https://learn.microsoft.com/ko-kr/training/paths/pad-get-started/
- Contoso Invoicing 앱:
  https://github.com/microsoft/PowerAutomateDesktop-Samples

### 참조 사이트
- easycopilotlab (구조/설계 참조):
  https://microsoft.github.io/easycopilotlab/

### 커뮤니티
- Power Automate 커뮤니티:
  https://powerusers.microsoft.com/t5/Microsoft-Power-Automate/ct-p/MPACommunity
- PAD 커뮤니티:
  https://powerusers.microsoft.com/t5/Power-Automate-Desktop/bd-p/MPADesktop

---

## Claude Code 작업 지시

위 지침을 기반으로 아래 순서로 파일을 생성하라:

1. `docs/basic/` 폴더에 M0~M6 파일 생성
2. `docs/tips/` 폴더에 T1~T4 파일 생성
3. 각 파일은 페이지 구조 템플릿을 따를 것
4. 스크린샷 필요 위치는 반드시 placeholder 삽입
5. 실습 단계는 번호 리스트로 명확하게
6. LLM 활용 팁은 각 모듈에서 최소 1회 이상 삽입
7. 모든 파일 생성 후 `_config.yml` nav 구조 확인
