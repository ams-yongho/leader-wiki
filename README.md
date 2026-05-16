# leader-wiki

리더회의 회의록을 누적해 LLM이 관리하는 위키로 회사 진행 상태를 추적합니다.
구현 패턴은 Andrej Karpathy의 [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 아이디어를 따릅니다.

## 구조

- `raw/` — 원본 회의록 (사람이 넣음, LLM은 읽기만)
- `wiki/` — LLM이 작성·유지하는 위키 페이지
- `AGENTS.md` — 운영 스키마 (정본)
- `CLAUDE.md` — Claude Code 진입점 (`AGENTS.md`로 위임)

## 사용법

1. `raw/`에 새 회의록을 넣습니다. 권장 파일명: `YYYY-MM-DD-주제.md`
2. Claude Code(또는 다른 LLM 에이전트)에서 **"방금 넣은 소스 ingest해줘"** 라고 요청합니다.
3. `wiki/`에서 결과를 확인합니다. `wiki/index.md`로 시작하면 전체 카탈로그를 볼 수 있습니다.

질의는 **"지난달 A 프로젝트 결정사항 뭐였지?"** 처럼 자연어로 하세요. LLM이 `wiki/`를 탐색해 답합니다.

주기적으로 **"lint해줘"** 를 호출하면 위키의 모순·고아 페이지·누락된 cross-reference 등을 점검합니다.

## 옵션: Obsidian

`wiki/` 디렉토리를 Obsidian Vault로 열면 그래프 뷰와 `[[wikilink]]` 네비게이션을 쓸 수 있습니다. 필수는 아닙니다.

## 더 알아보기

운영 규칙·컨벤션 전체는 [AGENTS.md](AGENTS.md) 참고.
