# Paper Notes — 논문 정리 블로그

Quarto + GitHub Pages 기반의 인공지능 논문 리뷰 블로그 템플릿입니다.
수식(KaTeX), 코드 실행, Mermaid 도식을 기본 지원합니다.

## 폴더 구조

```
paper-blog/
├── _quarto.yml        # 사이트 전체 설정 (제목, 메뉴, 테마)
├── index.qmd          # 홈 (글 목록 자동 생성)
├── about.qmd          # 소개 페이지
├── styles.css         # 커스텀 스타일
├── posts/             # ← 여기에 논문 리뷰 글을 추가
│   └── 2026-07-15-attention-is-all-you-need.qmd
└── .github/workflows/
    └── publish.yml    # push 하면 자동 배포
```

## 처음 한 번만: 로컬 셋업

1. **Quarto 설치** — https://quarto.org/docs/get-started/ 에서 OS에 맞게 설치
2. (선택) Python 코드를 실제로 실행하려면: `pip install jupyter`
3. 로컬 미리보기:

   ```bash
   quarto preview
   ```

   브라우저가 열리고, 파일을 저장할 때마다 실시간으로 반영됩니다.

## 새 글 쓰기

`posts/` 폴더에 `.qmd` 파일을 하나 추가하면 홈 목록에 자동으로 뜹니다.
파일 맨 위 YAML 헤더의 `title`, `date`, `categories` 만 채우면 끝.

기존 예시 글(`posts/2026-07-15-...qmd`)을 복사해서 시작하는 걸 추천합니다.
그 글 안에 수식·코드·Mermaid·콜아웃 사용법이 실제 예시로 다 들어있습니다.

## GitHub Pages 배포 (한 번만 설정)

1. GitHub에 새 repo 생성 (예: `paper-blog`)
2. `_quarto.yml` 과 `about.qmd` 안의 `USERNAME` 을 본인 GitHub 아이디로 바꾸기
3. 코드 업로드:

   ```bash
   git init
   git add .
   git commit -m "first post"
   git branch -M main
   git remote add origin https://github.com/USERNAME/paper-blog.git
   git push -u origin main
   ```

4. GitHub repo → **Settings → Pages → Build and deployment → Source** 를
   **GitHub Actions** 로 설정
5. 끝. 이후 `git push` 할 때마다 자동으로 빌드·배포됩니다.
   주소는 `https://USERNAME.github.io/paper-blog` 입니다.

## 자주 쓰는 문법 요약

| 기능 | 문법 |
|------|------|
| 인라인 수식 | `$E = mc^2$` |
| 블록 수식 | `$$ ... $$` |
| 코드(표시만) | ```` ```{python} ```` + `#| eval: false` |
| 코드(실행) | ```` ```{python} ```` + `#| eval: true` |
| 도식 | ```` ```{mermaid} ```` |
| 콜아웃 | `::: {.callout-note}` ... `:::` |
| 각주 | `본문[^1]` ... `[^1]: 내용` |
