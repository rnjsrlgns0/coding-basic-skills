# 플러그인 구조 개선 마이그레이션 가이드

## 📋 개요

`coding-basic-skills` 프로젝트가 **v2.0.0**으로 업그레이드되었습니다. 이제 개발(development)과 데이터 사이언스(data-science) 플러그인이 명확히 분리되어 더 나은 관리와 사용성을 제공합니다.

## 🎯 변경 사항

### 버전 정보
- **이전 버전**: v1.0.0 (단일 플러그인 구조)
- **새 버전**: v2.0.0 (모듈식 플러그인 구조)

### 주요 개선 사항

#### 1. 플러그인 분리
```
BEFORE:
├── agents/                 # 모든 에이전트 혼재
├── Skills/                 # 개발 스킬만
└── scientific-skills/      # DS 스킬 (별도)

AFTER:
├── plugins/
│   ├── development/        # 개발 플러그인
│   │   ├── agents/         # 개발 에이전트 6개
│   │   └── skills/         # 워크플로우 스킬 4개
│   └── data-science/       # DS 플러그인
│       ├── agents/         # DS 에이전트 6개
│       └── scientific-skills/  # 과학 스킬 50개
```

#### 2. 새로운 파일

**설정 파일**:
- `.claude/profiles.json`: 프로필 관리 (development/data-science/full)
- `plugins/*/README.md`: 각 플러그인별 상세 가이드

**매니페스트**:
- `plugins/development/.claude-plugin/marketplace.json`: 개발 플러그인 정의
- `plugins/data-science/.claude-plugin/marketplace.json`: DS 플러그인 정의
- `.claude-plugin/marketplace.json`: 루트 매니페스트 (업데이트)

**문서**:
- `CLAUDE.md`: 플러그인 관리 섹션 추가
- `MIGRATION.md`: 이 파일

#### 3. 하위 호환성

기존 코드/스크립트가 깨지지 않도록 symlink 생성:
- `agents` → `plugins/development/agents`
- `Skills` → `plugins/development/skills`

## 🔧 사용 방법

### 플러그인 프로필 선택

`.claude/profiles.json`에서 활성 프로필 변경:

```json
{
  "active_profile": "development"  // 또는 "data-science", "full"
}
```

### 개별 플러그인 제어

`.claude-plugin/marketplace.json`에서 플러그인별 활성화/비활성화:

```json
{
  "plugins": [
    {
      "name": "development",
      "enabled": true    // false로 변경하여 비활성화
    },
    {
      "name": "data-science",
      "enabled": false   // true로 변경하여 활성화
    }
  ]
}
```

## 📊 플러그인 비교

### Development Plugin

**포함 내용**:
- 에이전트 6개: backend-api-developer, frontend-ui-developer, ui-ux-designer, web-ui-tester, code-debugger, technical-documentation-writer
- 스킬 4개: task-planner, branch-manager, memory-bank-updater, project-reviewer

**사용 사례**:
- 웹 애플리케이션 개발
- API 서버 구축
- UI/UX 작업
- 코드 디버깅 및 테스트

### Data Science Plugin

**포함 내용**:
- 에이전트 6개: data-scientist, data-cleaning-specialist, data-visualization-specialist, feature-engineering-specialist, ml-modeling-specialist, model-evaluation-specialist
- 스킬 50개: aeon, matplotlib, scikit-learn, pytorch-lightning, 생물정보학 DB 등

**사용 사례**:
- 데이터 분석 및 EDA
- 머신러닝 모델 개발
- 데이터 시각화
- 생물정보학 연구
- 과학 문헌 조사

## 🎨 프로필별 추천 사용 시나리오

### development 프로필
```bash
# 웹 개발 프로젝트
task-planner → backend-api-developer → frontend-ui-developer → web-ui-tester
```

### data-science 프로필
```bash
# ML 파이프라인
data-cleaning-specialist → data-visualization-specialist →
feature-engineering-specialist → ml-modeling-specialist →
model-evaluation-specialist
```

### full 프로필
```bash
# ML 기반 웹 앱
task-planner → backend-api-developer (API) →
ml-modeling-specialist (모델) →
frontend-ui-developer (대시보드) →
web-ui-tester (테스트)
```

## ⚠️ 주의사항

### 하위 호환성
- 기존 `agents/`, `Skills/` 경로는 symlink로 유지됩니다
- 기존 코드는 수정 없이 작동합니다
- 단, 새로운 프로젝트는 `plugins/` 구조 권장

### Git Submodule
- `scientific-skills`는 여전히 git submodule입니다
- `plugins/data-science/scientific-skills`는 이를 가리키는 symlink입니다
- submodule 업데이트: `git submodule update --remote`

### 권장 사항
1. 프로젝트 시작 시 적절한 프로필 선택
2. 복잡한 작업은 `task-planner` 스킬 사용
3. 작업 완료 후 `memory-bank-updater` 실행
4. Git 작업 시 `branch-manager` 활용

## 📚 추가 문서

- `plugins/development/README.md`: 개발 플러그인 상세 가이드
- `plugins/data-science/README.md`: DS 플러그인 상세 가이드
- `CLAUDE.md`: 프로젝트 전체 규칙 및 플러그인 관리

## 🚀 다음 단계

1. **프로필 선택**: `.claude/profiles.json`에서 프로젝트에 맞는 프로필 설정
2. **README 확인**: 각 플러그인의 README.md 읽기
3. **테스트**: 선택한 프로필로 간단한 작업 수행
4. **피드백**: 문제 발견 시 이슈 등록

## 📝 변경 이력

### v2.0.0 (2024-11-24)
- ✅ 플러그인 구조를 development/data-science로 분리
- ✅ 프로필 시스템 도입
- ✅ 각 플러그인별 README 추가
- ✅ 하위 호환성 symlink 생성
- ✅ CLAUDE.md에 플러그인 관리 섹션 추가

### v1.0.0 (초기 버전)
- 단일 플러그인 구조
- 기본 워크플로우 스킬
- 개발 에이전트
- scientific-skills 서브모듈

---

**문의**: rnjsrlgns0@gmail.com
**프로젝트**: coding-basic-skills
**라이선스**: 프로젝트 루트의 LICENSE 파일 참조
