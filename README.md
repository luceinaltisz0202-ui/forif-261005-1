# 깃허브(GitHub) 핵심 가이드

이 문서는 Git과 GitHub의 핵심 개념 및 기본 협업 워크플로우를 정리한 설명 문서입니다.

---

## 1. Git과 GitHub의 차이점

| 구분 | Git | GitHub |
| :--- | :--- | :--- |
| **개념** | 분산 버전 관리 시스템 (VCS 도구) | Git 저장소를 호스팅하는 클라우드 기반 웹 서비스 |
| **실행 위치** | 사용자의 로컬 컴퓨터 | 원격 클라우드 서버 (인터넷 필요) |
| **주요 역할** | 소스 코드의 변경 이력(버전) 추적 및 관리 | 원격 저장소 보관, 코드 공유, 팀 협업 지원 |
| **대표 기능** | `git commit`, `git branch`, `git merge`, `git log` | `Pull Request`, `Issue`, `GitHub Actions`, `Projects` |

> 💡 **비유로 이해하기**: Git이 "동영상/사진을 기록하는 카메라"라면, GitHub는 이를 공유하고 협업하는 "유튜브/인스타그램"과 같습니다.

---

## 2. 깃허브의 핵심 개념

1. **저장소 (Repository, Repo)**
   - 프로젝트의 모든 파일과 전체 커밋 기록이 저장되는 공간입니다.
   - 로컬 저장소(Local Repository)와 원격 저장소(Remote Repository)로 구분됩니다.

2. **커밋 (Commit)**
   - 코드나 파일의 변경 사항을 의미 있는 단위로 저장한 "스냅샷"입니다.
   - 각 커밋은 고유한 해시값(ID)과 작성자, 변경 내용, 커밋 메시지를 가집니다.

3. **브랜치 (Branch)**
   - 독립적인 작업을 진행하기 위해 `main` 브랜치에서 갈라져 나온 작업 공간입니다.
   - 서로 다른 기능을 독립적으로 개발하여 충돌을 방지할 수 있습니다.

4. **이슈 (Issue)**
   - 버그 제보, 기능 개발 제안, 개선 작업 목록(To-do)을 관리하고 소통하는 도구입니다.
   - 각 이슈에는 번호(예: `#2`)가 부여되어 커밋이나 PR과 연계할 수 있습니다.

5. **풀 리퀘스트 (Pull Request, PR)**
   - 내가 작성한 브랜치의 변경 사항을 다른 브랜치(예: `main`)에 반영(Merge)해 달라고 요청하는 기능입니다.
   - 코드 리뷰와 토론, 자동화 테스트(CI)를 거쳐 안정적인 코드를 병합할 수 있습니다.

---

## 3. 깃허브 협업 워크플로우 (GitHub Flow)

일반적인 협업은 다음 단계로 진행됩니다:

```text
[이슈 생성] ➔ [새 브랜치 생성] ➔ [작업 및 커밋] ➔ [원격 브랜치 푸시] ➔ [Pull Request 생성/리뷰] ➔ [Merge 및 이슈 종료]
```

### 단계별 명령어 요약

1. **최신 코드 가져오기**
   ```bash
   git checkout main
   git pull origin main
   ```

2. **기능 작업을 위한 새 브랜치 생성 및 이동**
   ```bash
   git switch -c feature/docs-github
   ```

3. **코드 작성 후 스테이징 및 커밋**
   ```bash
   git add README.md
   git commit -m "docs: 깃허브 설명 문서 추가 (closes #2)"
   ```

4. **원격 저장소로 브랜치 푸시**
   ```bash
   git push origin feature/docs-github
   ```

5. **GitHub에서 Pull Request(PR) 생성 및 리뷰 후 Merge**
   - 커밋 메시지나 PR 설명에 `closes #2` 또는 `fixes #2`를 포함하면 PR 머지 시 이슈가 자동으로 닫힙니다.

6. **로컬 main 브랜치 최신화 및 완료된 브랜치 정리**
   ```bash
   git checkout main
   git pull origin main
   git branch -d feature/docs-github
   ```

---

## 4. 자주 사용하는 필수 Git/GitHub 명령어

- `git status` : 현재 작업 폴더의 상태 확인 (수정된 파일, 스테이지 여부 등)
- `git add <파일명>` : 커밋 대상 파일 스테이징
- `git commit -m "메시지"` : 스테이징된 변경 사항 커밋
- `git log --oneline` : 커밋 이력을 한 줄씩 간략하게 확인
- `git branch` : 브랜치 목록 확인
- `git switch <브랜치명>` : 브랜치 전환
- `git push -u origin <브랜치명>` : 원격 저장소에 브랜치 푸시
- `git pull` : 원격 저장소의 최신 커밋을 현재 브랜치로 가져오기
