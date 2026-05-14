---
layout: default
title: M4 실습 — Contoso 반복입력
parent: 📘 기본과정
nav_order: 8
---

# M4 실습 — Contoso 반복입력 + 메일 발송

## 🎯 학습 목표

- 엑셀 데이터를 읽어 데스크톱 앱에 반복 입력하는 흐름을 완주합니다.
- For Each 루프와 DataTable을 함께 사용하는 패턴을 익힙니다.
- 완료 후 처리 결과를 이메일로 발송합니다.

## ⏱ 예상 소요 시간

| 구분 | 시간 |
|------|------|
| 실습 | 50분 |
| 확장 실습 | 10분 |

---

## 준비물

- Contoso Invoicing 앱 설치 완료
- 실습용 엑셀 파일 (`invoice_data.xlsx`) — 강사 배포
- Outlook 계정 연결 상태

### 실습 엑셀 파일 구조

| A (Date) | B (Account) | C (Contact) | D (Amount) |
|----------|------------|------------|-----------|
| 2024-01-15 | Contoso Ltd | John Smith | 1500 |
| 2024-01-15 | Fabrikam | Jane Doe | 2300 |
| ... | ... | ... | ... |

---

## 서브흐름 구조

```
Main
  ├── ReadInvoiceData    (엑셀 읽기)
  ├── FillInvoiceApp     (Contoso 반복 입력)
  └── SendCompletionMail (완료 메일)
```

---

## 단계별 가이드

### 1단계. 새 흐름 + 서브흐름 3개 생성

1. 새 흐름 생성: `M4_Contoso_반복입력`
2. 서브흐름 추가: `ReadInvoiceData`, `FillInvoiceApp`, `SendCompletionMail`

---

### 2단계. ReadInvoiceData 서브흐름

**ReadInvoiceData 탭에서 작성합니다.**

#### 2-1. Excel 파일 열기
1. **[Excel] > [Excel 시작]** 추가
2. 설정:
   - **Excel 시작:** 다음 문서 열기
   - **문서 경로:** 실습 파일 경로 입력 (예: `C:\Users\[사용자명]\Desktop\invoice_data.xlsx`)
   - **저장 변수:** `ExcelInstance`

#### 2-2. 전체 데이터 읽기
1. **[Excel] > [Excel 워크시트에서 읽기]** 추가
2. 설정:
   - **Excel 인스턴스:** `%ExcelInstance%`
   - **검색:** 워크시트에서 사용 가능한 모든 값
   - **첫 번째 행이 열 이름을 포함:** ✅ 체크
   - **저장 변수:** `InvoiceData` (데이터테이블)

#### 2-3. Excel 닫기
1. **[Excel] > [Excel 닫기]** 추가
2. **Excel 인스턴스:** `%ExcelInstance%`

<!-- SCREENSHOT: ReadInvoiceData 서브흐름 완성 — Excel 시작/읽기/닫기 3개 액션 -->

---

### 3단계. FillInvoiceApp 서브흐름

**FillInvoiceApp 탭에서 작성합니다.**

#### 3-1. 처리 건수 초기화
1. **[변수] > [변수 설정]** 추가
2. **변수:** `처리건수` / **값:** `0`

#### 3-2. Contoso 앱 실행
1. **[시스템] > [응용 프로그램 실행]** 추가
2. **응용 프로그램 경로:** Contoso Invoicing 실행 파일 경로 입력

<!-- SCREENSHOT: Contoso Invoicing 앱 메인 화면 -->

#### 3-3. For Each 반복 입력
1. **[루프] > [For each]** 추가
2. 설정:
   - **반복할 값:** `%InvoiceData%`
   - **저장 변수:** `CurrentRow`

For Each 블록 안에 다음 액션들을 추가합니다:

**새 항목 추가 버튼 클릭:**
```
[UI 자동화] > [창에서 UI 요소 클릭]
→ Contoso 앱의 [+ New Invoice] 버튼 캡처
```

**Date 필드 입력:**
```
[UI 자동화] > [창에서 텍스트 필드 채우기]
→ Date 필드 캡처
→ 텍스트: %CurrentRow['Date']%
```

**Account 필드 입력:**
```
텍스트: %CurrentRow['Account']%
```

**Contact 필드 입력:**
```
텍스트: %CurrentRow['Contact']%
```

**Amount 필드 입력:**
```
텍스트: %CurrentRow['Amount']%
```

**저장 버튼 클릭:**
```
[UI 자동화] > [창에서 UI 요소 클릭]
→ [Save] 버튼 캡처
```

**처리 건수 증가:**
```
[변수] > [변수 증가]
→ 변수: 처리건수 / 증가값: 1
```

<!-- SCREENSHOT: Contoso 앱 UI 요소 캡처 화면 — Date/Account/Contact/Amount 필드 강조 -->

{: .warning }
> **UI 요소 캡처 주의:**  
> 자동캡처 후 선택기가 너무 구체적으로 잡히면 텍스트 편집기에서 직접 수정하세요.  
> 모르겠으면 LLM에게 물어보세요.

---

### 4단계. SendCompletionMail 서브흐름

**SendCompletionMail 탭에서 작성합니다.**

1. **[이메일] > [Outlook을 통해 이메일 메시지 보내기]** 추가
2. 설정:
   - **받는 사람:** 본인 이메일 주소
   - **제목:** `Contoso 입력 완료 알림`
   - **본문:**
     ```
     안녕하세요.
     
     Contoso Invoicing 데이터 입력이 완료되었습니다.
     
     처리 건수: %처리건수%건
     처리 일시: %CurrentDateTime%
     
     감사합니다.
     ```

{: .note }
> `%CurrentDateTime%`을 쓰려면 SendCompletionMail 서브흐름 앞에  
> **[현재 날짜 및 시간 가져오기]** 액션을 추가해야 합니다.

---

### 5단계. Main에서 순서대로 호출

**Main 탭에서 작성합니다.**

```
1. 서브흐름 실행 → ReadInvoiceData
2. 서브흐름 실행 → FillInvoiceApp
3. 서브흐름 실행 → SendCompletionMail
```

---

### 6단계. 실행 및 확인

1. **[▶ 실행]** 클릭
2. Contoso 앱이 자동으로 열리고 데이터가 입력되는 것 확인
3. 완료 후 Outlook에서 완료 메일 수신 확인

---

## 💡 LLM 활용 팁

DataTable에서 특정 열의 값을 가져오는 방법이 헷갈리면:

```
PAD에서 For Each로 DataTable을 반복할 때
'Account'라는 열 이름으로 값을 가져오는 표현식 알려줘
```

---

## ✅ 핵심 정리

- 엑셀 DataTable + For Each = 반복 입력 자동화의 기본 패턴
- `%CurrentRow['열이름']%`으로 DataTable 각 행의 값을 참조
- 완료 후 이메일 발송까지 하나의 흐름으로 연결

## 👉 다음 모듈

[M5. PA 클라우드 흐름 맛보기](./m5-pa-cloud.md)  
PAD에서 벗어나 클라우드에서 실행되는 PA 흐름을 맛봅니다.
