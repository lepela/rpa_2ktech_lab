# RPA 2kTech Lab

Power Automate / Power Automate Desktop 교육 사이트입니다.  
코딩 경험 없는 시티즌 개발자를 위한 하루 완성 과정을 제공합니다.

## 사이트 구조

```
docs/
  intro.md              # 강의 소개 (홈)
  basic.md              # 📘 기본과정 (부모 페이지)
  tips.md               # 🛠 팁 & 레퍼런스 (부모 페이지)
  basic/
    m0-orientation.md   # M0. 오리엔테이션
    m1-overview.md      # M1. Power Platform 개요
    m2-pad-basic.md     # M2. PAD 기초
    m2-lab1.md          # M2 실습 — 첫 번째 흐름
    m3-web-excel.md     # M3. 웹+엑셀 자동화
    m3-lab1.md          # M3 실습 — 오피넷→엑셀
    m4-ui-email.md      # M4. UI+이메일 자동화
    m4-lab1.md          # M4 실습 — Contoso 반복입력
    m5-pa-cloud.md      # M5. PA 클라우드 흐름 맛보기
    m5-lab1.md          # M5 실습 — 템플릿 흐름
    m6-closing.md       # M6. 마무리 & 다음단계
  tips/
    t1-prompt-guide.md  # T1. LLM 프롬프트 가이드
    t2-selector-guide.md # T2. 셀렉터 정제 가이드
    t3-expression-ref.md # T3. 자주 쓰는 표현식 모음
    t4-troubleshooting.md # T4. 트러블슈팅 레퍼런스
```

## 로컬 실행

### 사전 요구사항

- Ruby 3.x
- Bundler (`gem install bundler`)

### 실행

```bash
bundle install
bundle exec jekyll serve
```

브라우저에서 `http://localhost:4000/rpa_2ktech_lab` 접속

## 기술 스택

- **Jekyll** — 정적 사이트 생성
- **Just the Docs** — 문서 특화 Jekyll 테마 (`remote_theme: just-the-docs/just-the-docs`)
- **GitHub Pages** — 배포

## 콘텐츠 작성 규칙

### frontmatter 템플릿

```yaml
---
layout: default
title: 제목
parent: 📘 기본과정   # 또는 🛠 팁 & 레퍼런스
nav_order: 숫자
---
```

### 페이지 구조

```
## 🎯 학습 목표
## ⏱ 예상 소요 시간
## 개념 설명
## 실습
  ### 준비물
  ### 단계별 가이드
  <!-- SCREENSHOT: 설명 -->
## ✅ 핵심 정리
## 👉 다음 모듈
```

### 스크린샷 placeholder

```html
<!-- SCREENSHOT: 설명 -->
```

실제 스크린샷 추가 시 placeholder를 이미지로 교체합니다.

## 라이선스

교육 목적으로 자유롭게 사용 가능합니다.
