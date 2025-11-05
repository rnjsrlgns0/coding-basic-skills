# CLAUDE.md

이 파일은 Claude Code (claude.ai/code)가 이 저장소에서 작업할 때 필요한 가이드를 제공합니다.

## 프로젝트 규칙
### 개발 환경
- .gitignore 파일에 있는 파일 또한 당신의 작업 대상입니다. 
- **가상환경**: 프로젝트 루트의 `.venv` 디렉토리를 반드시 사용
  ```bash
  source .venv/bin/activate  # Mac/Linux
  .venv\Scripts\activate     # Windows
  ```
- **패키지 관리**: UV 사용 (pip 대신)
- **Python 버전**: 3.13

## Workflow
- Always use the `branch-manager` skill to manage branches before and after starting any work.
- Always create work plans using the `task-planner` skill.
- When work is completed, update the work plan using the `memory-bank-updater` skill.

## MCP 도구 사용 규칙
- Always use the mcp serena tools
- Always use the `mcp__serena-mcp__list_memories` tool to list available memories before using any other tool.
- When using Context7, make sure that you keep the range of output in the range 2k to 10k based on what you think is the best.
- Maintain a file named library.md to store the Library IDs that you search for and before searching make sure that you check the file and use the library ID already available. Otherwise, search for it.

## 테스트 결과 관리
### 
- 경로: `.serena/memories/test_results/phase{N}_{test_type}_test`

### 테스트 디렉토리 명명 규칙
- **Phase별 테스트**: `phase{N}_{test_type}_test/` 
  - 예시: `phase2_integration_test/`
- **워크플로우 테스트**: `{N}-step-{feature}-workflow-test-report/`
  - 예시: `5-step-ocr-workflow-test-report/`
- **기능별 테스트**: `{feature_name}_test/`
  - 예시: `api_performance_test/`

### 각 테스트 디렉토리 필수 구성
- **테스트 보고서**: `{test_name}_report.md` (상세 결과 및 분석)
- **스크린샷**: `screenshots/` 디렉토리 (UI 테스트 시각적 증거)
- **테스트 데이터**: `test_data/` 디렉토리 (필요시 입력/출력 파일)

### 테스트 보고서 필수 포함 항목
1. **테스트 실행 정보**: 일시, 환경, 테스트 대상 URL
2. **테스트 요약**: 성공/실패 항목 개수 및 전체 성공률
3. **상세 테스트 결과**: 단계별/기능별 세부 검증 내용
4. **에이전트별 참조용 분석**: Backend/Frontend/Tester별 이슈 및 개선사항
5. **정량적 성과**: 응답시간, 성능 지표, 개선율 등
6. **스크린샷 참조**: 주요 화면 캡처 및 설명
7. **종합 평가**: 점수, 등급, 배포 준비도 평가

### 에이전트별 테스트 결과 활용 방법
- **Web App Tester**: 
  - 기존 테스트 시나리오 및 성능 벤치마크 참조 필수
  - 회귀 테스트 시 이전 결과와 비교 분석
  - 새로운 테스트 시 기존 표준 양식 준수
- **Backend API Developer**: 
  - API 응답시간, 에러 처리, WebSocket 통신 안정성 결과 참조
  - 성능 개선 시 기존 벤치마크와 비교
- **Frontend UI Developer**: 
  - UI/UX 테스트, 반응형 디자인 검증 결과 참조
  - 컴포넌트 동작 및 사용자 경험 개선사항 반영
- **Technical Documentation Writer**: 
  - 테스트 문서화 표준 및 보고서 작성 가이드라인 참조
  - 모든 테스트 결과의 문서화 품질 일관성 유지

### 테스트 결과 활용 필수 원칙
1. **참조 의무화**: 새로운 테스트 수행 시 관련 기존 결과 필수 참조
2. **표준 준수**: 테스트 보고서는 정해진 양식과 필수 항목 준수
3. **품질 기준**: 이전 테스트 성과를 기준선으로 하여 동등 이상 품질 달성
4. **문서화 일관성**: 모든 테스트 결과는 동일한 품질과 상세도로 문서화
5. **스크린샷 포함**: UI 관련 테스트는 반드시 시각적 증거 포함
6. **성능 벤치마크**: 측정 가능한 지표는 정량적 데이터로 기록
