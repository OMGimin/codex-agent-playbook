# Third-party notices / 외부 자료 고지

이 저장소는 외부 프로젝트 전체를 재배포하지 않습니다. 일부 개발 스킬을 수정해 포함하고, 총괄·역할·의사결정 구성에는 외부 설계 아이디어를 참고했습니다. 아래 고정 커밋은 2026-09-25 라이선스 확인 시점이며, 과거 로컬 설치 버전을 뜻하지 않습니다.

| 원출처 | 이 저장소의 범위 | 처리 |
|---|---|---|
| obra/superpowers | systematic-debugging, test-driven-development, requesting-code-review, verification-before-completion, using-git-worktrees, finishing-a-development-branch와 해당 참조 | 수정·재작성한 파생 스킬. Jesse Vincent의 MIT 저작권 고지 보존 |
| provencher/codex-skills | work-orchestrator의 조정·위임 설계 참고 | 독립적인 로컬 재작성. 원 저장소나 CLI를 통째로 포함하지 않음. Eric Provencher의 MIT 고지 보존 |
| msitarzewski/agency-agents | work-orchestrator/references/roles.md의 역할 분리 참고 | 역할을 짧은 지시로 재작성. 원 카탈로그 전체 미포함. AgentLand Contributors의 MIT 고지 보존 |
| TorpedoD/claude-council | decision-council의 다섯 검토 관점 참고 | 가벼운 선택적 자문 절차로 재작성. 원 CLI·스크립트 미포함. TorpedoD의 MIT 고지 보존 |

새로 작성한 공통 지침, 구성·사용 설명과 예시에는 루트 [LICENSE](LICENSE)가 적용됩니다. 외부에서 가져온 부분의 권리는 각 원저작권자에게 남습니다. 개별 스킬을 복사할 때 그 폴더의 LICENSE도 포함하세요. 관련 원문 고지는 아래에 보존했습니다.

## 주요 수정

- 고정 단계별 승인·반복 확인을 동일 범위 승인 재사용으로 정리하되 명시적 안전장치 유지.
- 직접 수행 요청 우선, 명시적 하위 모델 배정, 모델 요청 수락과 런타임 확인 구분.
- 완료 주장에 유효한 근거 요구, 불필요한 동일 검증 반복 방지.
- 작업트리 생성 실패의 자동 현위치 전환과 폴더명 기반 소유권 추정 제거.
- 디버깅 참조 3개를 범용 문서로 축약. 원 프로젝트의 과거 성능 수치와 전용 스크립트 의존성 제거.
- 선택적 도구 연동은 별도 설치 항목으로 표시. 개인 경로·계정·대화 기록·플러그인 원본 미포함.

## 보존한 라이선스 전문

- [obra/superpowers](https://github.com/obra/superpowers) — [확인한 원문](https://github.com/obra/superpowers/blob/5bf4e78011075bcfc0dc295f0724994cd123ee71/LICENSE), [저장소 내 전문](LICENSES/obra--superpowers.txt)
- [provencher/codex-skills](https://github.com/provencher/codex-skills) — [확인한 원문](https://github.com/provencher/codex-skills/blob/8aa6c42b73781c905c55f8a1253a18127079ac21/LICENSE), [저장소 내 전문](LICENSES/provencher--codex-skills.txt)
- [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) — [확인한 원문](https://github.com/msitarzewski/agency-agents/blob/053ddbbf392a1688fc7043d81529f47ef2cf86c8/LICENSE), [저장소 내 전문](LICENSES/msitarzewski--agency-agents.txt)
- [TorpedoD/claude-council](https://github.com/TorpedoD/claude-council) — [확인한 원문](https://github.com/TorpedoD/claude-council/blob/f963fd62a4234735b194a916c86539d92bfb6389/LICENSE), [저장소 내 전문](LICENSES/TorpedoD--claude-council.txt)

각 원문 파일의 해시와 확인 커밋은 [출처 기록](docs/upstream-sources.json)에 있습니다. 원저자의 승인·공식 제휴를 의미하지 않습니다.
