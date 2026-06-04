<div align="right">
  <a href="README.md">🇬🇧 English</a> &nbsp;|&nbsp; 🇰🇷 <strong>한국어</strong>
</div>

# juhyeon-works-with-ai

AI와 함께 일하면서 쌓은 프롬프트, 설정, 워크플로우 모음입니다. 새로운 툴을 쫓는 것이 아니라, 실제 문제를 더 빠르게 해결하기 위해 만들었습니다.

---

## 철학

저는 AI를 마법 지팡이가 아니라 힘 배수기(force multiplier)로 봅니다. 새 모델이나 프레임워크에 손을 뻗기 전에, 먼저 묻습니다: *실제 문제가 무엇이고, 이것이 맞는 도구인가?*

이 워크플로우들은 모두 실제로 겪은 마찰을 해결하면서 만들어졌고, 계속 다듬어가고 있습니다.

---

## 구성

### 💬 [`system_prompts/`](./system_prompts/)
실제로 유용하게 사용하고 있는 프롬프트 모음입니다.

| 프롬프트 | 대상 | 언어 |
|---------|------|------|
| [`coding-interview/en.md`](./system_prompts/coding-interview/en.md) | 해외 / 런던 기업 | English |
| [`coding-interview/ko.md`](./system_prompts/coding-interview/ko.md) | 한국 기업 | 한국어 |

### ⚙️ [`claude/`](./claude/)
일상적인 엔지니어링 작업을 위한 개인 Claude Code 설정입니다. 설치 방법은 [`claude/README.md`](./claude/README.md)를 참고하세요.
- 흔한 바이브 코딩 실수 방지 (Karpathy의 관찰에서 영감을 받음)
- 비즈니스 영어 프롬프트 작성 시 자연스러운 표현 코칭
- 워크플로우 개선 사항을 `agent-notes/`에 자동 기록
- Confluence, Jira, GitHub Enterprise 내부 툴 패턴

### 🗂️ [`agent-notes/`](./agent-notes/)
Claude가 자동으로 기록하는 디렉토리입니다. 직접 작성하는 노트가 아닙니다.
- `todo/` — 실행할 워크플로우 개선 아이디어
- `learnings/` — 프로젝트 간에 재사용 가능한 인사이트

---

## 소개

저는 검색(Search) 전문 ML 엔지니어 남주현입니다. 엔지니어링과 AI에 대한 생각이 궁금하시다면 [GitHub 프로필 →](https://github.com/harryjhnam)을 확인해주세요.
