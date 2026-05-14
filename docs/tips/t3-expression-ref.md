---
layout: default
title: T3. 자주 쓰는 표현식 모음
parent: 🛠 팁 & 레퍼런스
nav_order: 3
---

# T3. 자주 쓰는 표현식 모음

PAD 실습 중 자주 필요한 표현식을 카테고리별로 정리합니다.  
필요한 표현식을 복사해서 바로 쓰세요.

---

## 날짜/시간 포맷

### 이럴 때 씁니다
날짜를 특정 형식의 텍스트로 변환할 때

| 원하는 형식 | 표현식 | 결과 예시 |
|-----------|--------|----------|
| 기본 텍스트 | `%CurrentDateTime%` | `1/15/2024 10:30:00 AM` |
| 날짜만 (슬래시) | `%FormatDateTime(CurrentDateTime, 'MM/dd/yyyy')%` | `01/15/2024` |
| 날짜만 (하이픈) | `%FormatDateTime(CurrentDateTime, 'yyyy-MM-dd')%` | `2024-01-15` |
| 한국식 날짜 | `%FormatDateTime(CurrentDateTime, 'yyyy년 MM월 dd일')%` | `2024년 01월 15일` |
| 시간 포함 | `%FormatDateTime(CurrentDateTime, 'yyyy-MM-dd HH:mm:ss')%` | `2024-01-15 10:30:00` |
| 파일명용 | `%FormatDateTime(CurrentDateTime, 'yyyyMMdd_HHmmss')%` | `20240115_103000` |

---

## 텍스트 처리

### 텍스트 자르기

| 이럴 때 씁니다 | 표현식 | 예시 |
|--------------|--------|------|
| 앞에서 N글자 | `%Substring(MyText, 0, N)%` | `Substring("안녕하세요", 0, 2)` → `안녕` |
| 뒤에서 N글자 | `%Substring(MyText, Length(MyText)-N, N)%` | 마지막 3글자 |
| 특정 위치부터 | `%Substring(MyText, 시작위치, 길이)%` | 3번째부터 4글자 |

### 텍스트 합치기

```
%텍스트1 + 텍스트2%
%"이름: " + 이름변수%
%FormatDateTime(CurrentDateTime, 'yyyy-MM-dd') + "_보고서"%
```

### 텍스트 포함 여부 확인

| 이럴 때 씁니다 | 표현식 | 결과 |
|--------------|--------|------|
| 특정 단어 포함 여부 | `%Contains(MyText, '검색어')%` | True/False |
| 특정 텍스트로 시작 | `%StartsWith(MyText, '시작텍스트')%` | True/False |
| 특정 텍스트로 끝남 | `%EndsWith(MyText, '끝텍스트')%` | True/False |

### 대소문자 변환

```
%ToUpper(MyText)%    → 대문자
%ToLower(MyText)%    → 소문자
```

### 공백 제거

```
%Trim(MyText)%       → 앞뒤 공백 제거
```

---

## 숫자 계산

| 이럴 때 씁니다 | 표현식 |
|--------------|--------|
| 기본 사칙연산 | `%숫자1 + 숫자2%`, `%숫자1 - 숫자2%`, `%숫자1 * 숫자2%`, `%숫자1 / 숫자2%` |
| 나머지 | `%숫자1 Mod 숫자2%` |
| 반올림 | `%Round(숫자, 소수점자리수)%` |
| 절대값 | `%Abs(숫자)%` |
| 텍스트 → 숫자 | `%ToDecimal(텍스트변수)%` |
| 숫자 → 텍스트 | `%ToString(숫자변수)%` |

---

## 조건 표현식

### If 조건에서 자주 쓰는 패턴

| 상황 | 조건식 |
|------|--------|
| 변수가 비어있는지 | `%MyText = ""` 또는 `%MyText IS EMPTY%` |
| 변수가 특정 값인지 | `%MyText = "원하는값"%` |
| 숫자 비교 | `%MyNumber > 100%` |
| 파일 존재 여부 | **[파일 있는지 확인]** 액션 사용 |
| 리스트가 비어있는지 | `%MyList.Count = 0%` |

---

## 리스트/데이터테이블

### 리스트 다루기

| 이럴 때 씁니다 | 방법 |
|--------------|------|
| 리스트 항목 수 | `%MyList.Count%` |
| N번째 항목 가져오기 | `%MyList[N]%` (0부터 시작) |
| 리스트에 항목 추가 | **[리스트에 항목 추가]** 액션 |

### DataTable 다루기

| 이럴 때 씁니다 | 표현식 |
|--------------|--------|
| 행 수 | `%MyTable.RowsCount%` |
| 열 수 | `%MyTable.ColumnsCount%` |
| 특정 열 값 (열 이름으로) | `%CurrentRow['열이름']%` |
| 특정 열 값 (열 번호로) | `%CurrentRow[0]%` (0부터 시작) |

---

## 파일/폴더 경로

| 이럴 때 씁니다 | 표현식 |
|--------------|--------|
| 현재 사용자 데스크톱 | `%SpecialFolderPath(SpecialFolder.Desktop)%` |
| 현재 사용자 Documents | `%SpecialFolderPath(SpecialFolder.Documents)%` |
| 경로 합치기 | `%FolderPath + "\\" + FileName%` |

{: .note }
> 모르는 표현식은 LLM에게 물어보세요.  
> "PAD에서 [원하는 기능] 표현식 알려줘"라고 하면 바로 나옵니다.
