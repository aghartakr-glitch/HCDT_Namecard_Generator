# N-FUD 2026 명함 생성기

N-FUD 2026 로고 가이드(261019) 명함 10종·5색으로 앞·뒷면을 만들고 벡터 PDF/SVG로 저장하는 웹페이지입니다.
서버가 필요 없는 정적 페이지(파일 3개 폴더)라서 GitHub Pages에 그대로 올리면 됩니다.

## 폴더 구성

| 파일 | 설명 |
|---|---|
| `index.html` | 페이지 전체 (로고·도형 벡터 데이터 포함) |
| `lib/` | PDF·글꼴 처리용 라이브러리 3개. 인터넷 CDN 없이 동작하도록 같이 넣었습니다 |
| `.nojekyll` | GitHub가 파일을 가공하지 않게 하는 빈 파일. 지우지 마세요 |

## 배포 방법 A: 웹 화면만으로 (명령어 없음, 가장 쉬움)

1. GitHub에서 오른쪽 위 `+` → `New repository`.
2. Repository name에 `nfud-namecard`처럼 영문 소문자로 입력, `Public` 선택 → `Create repository`.
3. 새 저장소 화면에서 `uploading an existing file` 링크 클릭.
4. 이 폴더 안의 `index.html`, `lib` 폴더, `.nojekyll` 파일을 창에 끌어 놓기.
   - `.nojekyll`은 맥/윈도우에서 숨김 파일이라 안 보일 수 있습니다. 안 보이면 건너뛰어도 동작합니다.
5. 아래 `Commit changes` 클릭.
6. 저장소 `Settings` → 왼쪽 `Pages` → `Build and deployment`의 Source를 `Deploy from a branch`, Branch를 `main` / `/ (root)`로 고르고 `Save`.
7. 1~2분 뒤 같은 화면 위쪽에 `https://내아이디.github.io/nfud-namecard/` 주소가 나타납니다.

## 배포 방법 B: git 명령어 (터미널)

폴더 안에서 한 줄씩 실행합니다. `내아이디`는 본인 GitHub 아이디로 바꿉니다.
(GitHub에서 같은 이름의 빈 저장소를 먼저 만들어 두어야 합니다.)

```
git init
git add .
git commit -m "명함 생성기 첫 배포"
git branch -M main
git remote add origin https://github.com/내아이디/nfud-namecard.git
git push -u origin main
```

그다음 방법 A의 6번(Pages 설정)을 하면 됩니다.

| 명령어 | 하는 일 |
|---|---|
| `git init` | 이 폴더를 git 저장소로 만듭니다 |
| `git add .` | 폴더 안 모든 파일을 올릴 목록에 담습니다 |
| `git commit -m "..."` | 목록을 하나의 저장 기록으로 묶습니다 |
| `git branch -M main` | 기본 가지 이름을 main으로 맞춥니다 |
| `git remote add origin 주소` | 올릴 GitHub 저장소 주소를 등록합니다 |
| `git push -u origin main` | 실제로 GitHub에 올립니다 |

## 수정 후 다시 올리기

`index.html`을 바꾼 뒤 아래 세 줄을 실행하면 1~2분 안에 사이트에 반영됩니다.

```
git add .
git commit -m "수정 내용 메모"
git push
```

## 사용 시 알아둘 점

- 앞면과 뒷면에서 디자인 10종과 단색을 각각 고릅니다. 앞 5번 + 뒤 2번처럼 섞어 쓸 수 있습니다.
- 색상은 보라, 시안, 오렌지, 그린, 옐로 5가지이며 앞면과 뒷면이 각각 따로 정해집니다.
- 단색은 흰 바탕 또는 5색 바탕을 고를 수 있습니다. 색 바탕에서는 로고·글자 색이 읽히도록 자동으로 바뀝니다(보라 바탕은 흰색).
- 로고는 모든 앞면에서 같은 크기로 카드 정중앙에 놓입니다.
- 한글 이름과 영문 이름 사이에 연결 기호(없음, 대시, 플러스, 바)를 고를 수 있고, 간격은 가이드의 최소·최대 범위(13.0~19.6) 안에서 조절됩니다. 한글 두 글자 이름은 가이드처럼 글자 사이가 벌어집니다.
- 글꼴은 `index.html` 안에 들어 있어 별도 설정이 없습니다. 영문은 Helvetica Neue LT Std(Roman, Bold), 한글은 Spoqa Han Sans Neo Bold입니다. 같은 파일을 `fonts/`에도 넣어 두었습니다.
- Spoqa Han Sans Neo는 SIL Open Font License 1.1로 배포되는 글꼴입니다(`fonts/SpoqaHanSansNeo-LICENSE.txt`). 한글은 현대 한글 2,574자가 들어 있으며, 없는 글자를 입력하면 경고가 뜨고 내보내기가 막힙니다.
- 사이트 언어(한/EN)는 오른쪽 위 버튼으로 바꾸며, 선택은 브라우저에 기억됩니다.
- 로고·UNIST 워드마크·도형·Helvetica 글꼴은 학과/학교와 글꼴 제작사의 자산입니다. 저장소를 Public으로 공개하면 누구나 이 파일들을 내려받을 수 있으니, 라이선스 범위가 걱정되면 `Private` 저장소로 바꾸세요. (Private 저장소의 Pages는 GitHub 요금제에 따라 제한이 있습니다.)
