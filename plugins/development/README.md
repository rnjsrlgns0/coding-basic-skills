# Development Plugin

웹 개발 프로젝트를 위한 종합 워크플로우 플러그인입니다.

## 🎯 목적

소프트웨어 개발 전체 라이프사이클을 지원하는 에이전트와 스킬을 제공합니다.

## 🤖 포함된 에이전트

### Backend Development
- **backend-api-developer**: 서버 로직, REST API, 데이터베이스 작업
- **code-debugger**: 버그 식별, 분석 및 해결

### Frontend Development
- **frontend-ui-developer**: UI 컴포넌트 구현, 반응형 레이아웃
- **ui-ux-designer**: 인터페이스 디자인, 사용자 플로우 평가

### Testing & QA
- **web-ui-tester**: 자동화 테스트, 성능 모니터링, UI/UX 검증

### Documentation
- **technical-documentation-writer**: 프로젝트 진행 상황 문서화

## 🛠️ 포함된 스킬

### 워크플로우 관리
- **task-planner**: 작업 계획 수립 및 서브에이전트 조율
- **branch-manager**: Git 브랜치 생성, 병합, 정리
- **memory-bank-updater**: 프로젝트 메모리 업데이트
- **project-reviewer**: 온보딩 문서 생성

## 📝 슬래시 커맨드

개발 워크플로우를 간편하게 실행할 수 있는 슬래시 커맨드를 제공합니다:

- **/plan**: task-planner 스킬을 실행하여 작업 계획 수립
- **/branch**: branch-manager 스킬을 실행하여 Git 브랜치 관리
- **/update-memory**: memory-bank-updater 스킬을 실행하여 메모리 업데이트
- **/complete**: 현재 작업을 완료하고 메모리 업데이트 및 브랜치 관리
- **/workflow**: 전체 개발 워크플로우를 통합 실행 (plan → branch → work → update-memory)

## 📋 사용 시나리오

### 웹 애플리케이션 개발
```
1. task-planner로 작업 계획 수립
2. branch-manager로 기능 브랜치 생성
3. backend-api-developer로 API 개발
4. frontend-ui-developer로 UI 구현
5. web-ui-tester로 테스트 실행
6. memory-bank-updater로 작업 내용 기록
7. branch-manager로 브랜치 병합
```

### API 서버 구축
```
1. backend-api-developer로 엔드포인트 설계
2. code-debugger로 버그 수정
3. web-ui-tester로 API 테스트
4. technical-documentation-writer로 API 문서 작성
```

### UI/UX 개선
```
1. ui-ux-designer로 디자인 분석 및 개선안 제시
2. frontend-ui-developer로 디자인 구현
3. web-ui-tester로 반응형 테스트
```

## 🔧 설정

### 플러그인 활성화
`.claude-plugin/marketplace.json`에서:
```json
{
  "plugins": [
    {
      "name": "development",
      "enabled": true
    }
  ]
}
```

### 프로필 사용
`.claude/profiles.json`에서 `development` 프로필 선택

## 📂 디렉토리 구조

```
development/
├── .claude-plugin/
│   └── marketplace.json    # 플러그인 매니페스트
├── agents/                 # 개발 에이전트
│   ├── backend-api-developer.md
│   ├── frontend-ui-developer.md
│   ├── ui-ux-designer.md
│   ├── web-ui-tester.md
│   ├── code-debugger.md
│   └── technical-documentation-writer.md
├── skills/                 # 워크플로우 스킬
│   ├── task-planner/
│   ├── branch-manager/
│   ├── memory-bank-updater/
│   └── project-reviewer/
├── commands/               # 슬래시 커맨드
│   ├── plan.md
│   ├── branch.md
│   ├── update-memory.md
│   ├── complete.md
│   └── workflow.md
└── README.md              # 이 파일
```

## 🚀 시작하기

1. 프로필을 `development`로 설정
2. `task-planner` 스킬로 작업 계획 시작
3. 필요한 에이전트를 호출하여 작업 수행
4. `branch-manager`로 브랜치 관리
5. 완료 후 `memory-bank-updater`로 기록

## 💡 팁

- 복잡한 작업은 `task-planner`로 계획 수립 후 시작
- Git 작업 전후로 항상 `branch-manager` 사용
- 작업 완료 시 `memory-bank-updater`로 컨텍스트 유지
- 디버깅 시 `code-debugger` 에이전트 적극 활용
