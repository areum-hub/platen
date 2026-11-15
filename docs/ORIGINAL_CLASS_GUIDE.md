# PLATEN 원본 수업 안내 (참고 자료)

> 아래 내용은 [dandacompany/platen](https://github.com/dandacompany/platen)의 원본 수업용 README에서 가져온 안내를 기록용으로 보존한 것입니다.
> `fork`, PR 형식, 강사 병합, `memo.dante-labs.com` 배포 안내는 **원본 수업 저장소를 대상으로 한 설명**이며, [areum-hub/platen](https://github.com/areum-hub/platen)의 Focus Timer 개발 기록이나 배포 절차를 설명하는 내용은 아닙니다.
> 이 개인 fork의 기능·실행 방법은 [메인 README](../README.md)를 참고하세요.

---

## 이 저장소는 수업용입니다

국민대학교 경영대학원 「AI에이전트실무」 7주차 실습 저장소입니다. 수강생이 이 저장소를 **fork** 하고, 자기 해석으로 **기능 하나**를 더해 **Pull Request** 를 보냅니다. 강사가 검토·병합하면 Actions 가 돌아 운영 사이트가 바뀝니다. 수업이 끝나도 저장소는 열려 있습니다.

### 하는 법 (요약)

1. fork 와 clone — 두 줄은 손으로
   ```bash
   gh repo fork dandacompany/platen --clone
   cd platen
   ```
2. 이 폴더에서 개발용 Hermes 프로필(쌤)을 띄운다
   ```bash
   hermes -p dev
   ```
3. 나머지는 쌤에게 자연어로. 브랜치 → 기능 하나 → 브라우저로 **내가** 확인 → 커밋 → 푸시 → PR
4. PR 제목은 `[01분반] 이름: 기능` 형식. 본문은 템플릿이 열린다

자세한 절차와 프롬프트는 수업 전용관의 7주차 실습 가이드에 있습니다.

### 규칙

- **한 PR 에 기능 하나.** 작게. 큰 아이디어는 PR 두 개로 나눈다.
- `index.html` **한 파일**을 유지한다. 외부 라이브러리·빌드 도구를 넣지 않는다 (Google Fonts 는 예외).
- 기존 기능이 그대로 되어야 한다: 타이핑과 자모 조합, 램프 슬라이더 세 개, 램프 켜고 끄기, 자동 타이핑, 리셋, 타자 소리.
- 토큰·API 키·개인 이메일을 넣지 않는다. PR check 가 걸러내지만 사람이 먼저 본다.
- 병합 여부는 강사가 정한다. 수업 중에는 5~8건만 라이브로 병합하고 나머지는 수업 뒤에 병합한다.

### 기능 메뉴

고르거나, 자기 해석으로 새로 정해도 됩니다. 쌤과 brainstorming 으로 범위를 좁힌 뒤 시작하세요.

| 크기 | 예 |
| --- | --- |
| 작게 (15~30분) | 타자 소리 켜고 끄기 버튼 · 3,000자 제한을 실제로 막기 · 종이 색 고르기 · 램프 색(따뜻함/차가움) · 글꼴 고르기 · 자동 타이핑 문구를 내 글로 · 지금 시각 도장 찍기 버튼 · 커서 깜빡임 |
| 중간 (30~45분) | 새로고침해도 글이 남게 저장(localStorage) · `.txt` 로 내보내기 · 제목 줄 · 노트 여러 개와 목록 · 단어 수와 읽는 시간 · 밝은 종이/어두운 종이 전환 |
| 자기 해석 | 완전히 다른 입력 경험. 단, 기존 타이핑과 램프는 남긴다 |

### 로컬에서 열기

`index.html` 을 브라우저로 열면 됩니다. 서버가 필요하면:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

### 내 fork 를 원본 최신으로 맞추기

다른 사람의 PR 이 먼저 병합되면 내 브랜치가 낡습니다. 쌤에게 "upstream 최신으로 맞춰 줘" 라고 하면 아래를 합니다.

```bash
git fetch upstream
git rebase upstream/main
```

충돌이 나면 쌤과 같이 봅니다. 작업 중인 변경이 있으면 `git stash` 로 잠깐 치웠다가 `git stash pop` 으로 되돌립니다. rebase 로 역사가 바뀐 브랜치를 다시 올릴 때는 `git push --force-with-lease origin <내 브랜치>` 입니다 (내 브랜치에만).

## 배포

`main` 에 병합되면 `.github/workflows/deploy.yml` 이 저장소 루트를 GitHub Pages 에 올립니다. 1~2분 뒤 https://memo.dante-labs.com 이 바뀝니다. PR 이 열리면 `.github/workflows/pr-check.yml` 이 `index.html` 존재·형식·비밀값 패턴을 검사합니다.

## 출처와 라이선스

모바일 프로토타입(Gemini 생성, "Platen — Paper & Ink (Night-lamp UI)")을 데스크탑 브라우저용으로 다듬었습니다. 기기 프레임과 화면 키보드를 걷어내고 종이·램프·소리·물리 키보드만 남겼습니다. MIT License.
