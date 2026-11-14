# SONG MATCH

청소년 뮤지션의 음악을 탐색하고, 간단한 음악 취향 설문을 통해 어울리는 곡을 추천하는 정적 웹사이트입니다.

## 바로 보기

- [SONG MATCH GitHub Pages](https://22styoon.github.io/SONG_MATCH/)
- [소리지음 YouTube](https://www.youtube.com/@sorizieum)

## 주요 기능

- 6개의 음악 취향 질문
- 선택지를 클릭하면 다음 질문으로 자동 이동
- 이전 질문으로 돌아가 답변을 수정하는 기능
- 11곡 전체를 대상으로 한 추천 결과
- 추천 결과의 곡 정보와 YouTube 바로 듣기 링크
- YouTube 썸네일을 활용한 결과 카드와 곡 목록
- 질문 전환, 결과 등장, 파티클 버스트 애니메이션
- 모바일 화면 대응

## 기술 스택

- HTML5
- CSS3
- Vanilla JavaScript
- GitHub Pages

별도의 빌드 도구나 서버가 필요하지 않습니다.

## 파일 구조

```text
SONG MATCH/
├─ index.html                       # 페이지 구조와 콘텐츠
├─ style.css                        # 레이아웃, 색상, 반응형 스타일, 애니메이션
├─ script.js                        # 설문 진행, 점수 계산, 추천 결과 처리
├─ concept.txt                      # 기획 메모
├─ youth_song_market_catalog.md     # 추천 곡 카탈로그와 출처
└─ .github/workflows/
   └─ deploy-pages.yml              # GitHub Pages 자동 배포 설정
```

## 로컬에서 실행하기

### 방법 1. 파일로 열기

`index.html`을 브라우저에서 직접 열면 됩니다.

### 방법 2. 로컬 서버 사용

```bash
python -m http.server 8000
```

브라우저에서 다음 주소를 엽니다.

```text
http://localhost:8000
```

## 추천 로직

설문 선택지에는 각 곡과 연결되는 결과 키가 들어 있습니다.

```html
<button class="answer" data-result="dayz">
  <span>A</span>해 질 무렵, 창문을 열어둔 방
</button>
```

JavaScript는 선택된 `data-result` 값을 누적하고, 가장 많이 선택된 곡을 최종 추천합니다. 동점인 경우에는 후보 중 하나를 선택해 결과를 완성합니다.

곡 정보와 YouTube 주소는 [youth_song_market_catalog.md](./youth_song_market_catalog.md)와 [script.js](./script.js)에서 관리합니다.

## 색상 시스템

기본 색상 변수는 [style.css](./style.css)의 `:root`에서 관리합니다.

```css
:root {
  --ink: #1e1e23;
  --cream: #f5f0e6;
  --yellow: #ed6d01;
  --blue: #8ab8f8;
  --pink: #f2a7c6;
}
```

선택 버튼에 마우스를 올리면 `#1e1e23` 색상이 적용됩니다.

## 콘텐츠 수정 방법

1. 질문과 선택지는 [index.html](./index.html)에서 수정합니다.
2. 추천 점수와 결과 데이터는 [script.js](./script.js)에서 수정합니다.
3. 곡 목록, 출처, YouTube 링크는 [youth_song_market_catalog.md](./youth_song_market_catalog.md)에서 확인합니다.
4. 디자인과 애니메이션은 [style.css](./style.css)에서 수정합니다.

## 배포

`master` 브랜치에 변경 사항을 push하면 GitHub Actions가 사이트를 자동으로 배포합니다.

```bash
git add .
git commit -m "Update SONG MATCH"
git push origin master
```

배포가 완료되면 [GitHub Pages 주소](https://22styoon.github.io/SONG_MATCH/)에서 변경 내용을 확인할 수 있습니다.

## 출처

추천 대상은 시립청소년음악센터 소리지음의 청소년 뮤지션 곡입니다.

- [소리지음 YouTube 채널](https://www.youtube.com/@sorizieum/videos)
- [소리모음 음악 아카이브](https://youth-music-archive.uniquegourd.chatgpt.site/archive#archive)
