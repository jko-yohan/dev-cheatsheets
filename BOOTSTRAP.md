# Dev Cheatsheets - 부트스트랩 가이드

> 이 문서는 새 Claude 세션에서 프로젝트 시작 시 참조하는 설계 문서입니다.
> 진입 명령어: `Dev Cheatsheets 작업 시작하자`

## 자동 실행 지시

**진입 명령어가 호출되면 사용자에게 묻지 않고 아래 작업을 즉시 자동 수행한다.**

1. 이 BOOTSTRAP.md를 읽고 현재 상태 파악
2. iCloud의 MASTER_INDEX.md, STATUS.md를 읽어 진행 현황 확인
3. 초기 세팅이 안 되어 있으면: Git 저장소 생성, 공통 파일(index.html, style.css) 개발, GitHub Pages 배포
4. 아직 개발되지 않은 치트시트 중 **우선순위가 가장 높은 것**부터 순서대로 개발 시작
5. 각 치트시트마다 아래를 자동 수행:
   - `sheets/{topic}.html` 생성 (명령어/문법/예시 코드 포함, 충실한 콘텐츠)
   - `index.html` 목록에 추가
   - `sitemap.xml`에 URL 추가
   - 커밋 & 푸시
   - iCloud MASTER_INDEX.md, STATUS.md 업데이트
6. 한 치트시트 완료 후 바로 다음으로 넘어감 (사용자 확인 불필요)
7. 모든 치트시트 완료 시 또는 세션 종료 시 최종 현황 보고

---

## 1. 프로젝트 개요

개발자들이 자주 검색하는 **치트시트(요약 레퍼런스)**를 모아놓은 정적 사이트.
각 치트시트가 독립 페이지 → SEO 키워드별 유입 극대화.

### 핵심 전략
- 치트시트 1개 = 독립 페이지 1개 = 검색 키워드 1~3개
- 하나의 GitHub 저장소, 하나의 사이트에 모든 치트시트 포함
- GitHub Pages 무료 호스팅 (운영비 0원)
- AdSense 계정: ca-pub-4754582635962628

---

## 2. 경로 규칙

| 구분 | 경로 |
|------|------|
| 로컬 루트 | `/Users/johnko/Documents/GitHub/dev-cheatsheets/` |
| iCloud 관리 | `/Users/johnko/Library/Mobile Documents/com~apple~CloudDocs/00_사업/01_피워크엔터테인먼트/02_툴개발/05_DevCheatsheets/` |
| GitHub 저장소 | `jko-yohan/dev-cheatsheets` |
| 사이트 URL | `https://jko-yohan.github.io/dev-cheatsheets/` |

---

## 3. 파일 구조

```
dev-cheatsheets/
├── index.html              # 홈페이지 (전체 치트시트 목록)
├── style.css               # 공통 스타일시트
├── sheets/
│   ├── git.html            # Git 치트시트
│   ├── css-flexbox.html    # CSS Flexbox 치트시트
│   ├── css-grid.html       # CSS Grid 치트시트
│   ├── regex.html          # Regex 치트시트
│   ├── markdown.html       # Markdown 치트시트
│   ├── html-entities.html  # HTML Entities 치트시트
│   ├── http-status.html    # HTTP Status Codes 치트시트
│   ├── bash.html           # Bash/Shell 치트시트
│   ├── python.html         # Python 치트시트
│   └── javascript.html     # JavaScript 치트시트
├── sitemap.xml             # 사이트맵 (모든 페이지 포함)
├── robots.txt              # 크롤러 허용
└── .gitignore              # Git 제외
```

---

## 4. 디자인 규칙

- 다크 테마 (DevTools Online과 동일 톤)
- 반응형 (모바일/태블릿/데스크톱)
- Google Fonts Inter + monospace (코드용)
- 영어 중심 콘텐츠
- 각 치트시트 페이지 레이아웃:
  - 상단: 제목 + 간단 설명
  - 본문: 카드형 섹션으로 명령어/문법 그룹핑
  - 각 카드: 명령어 + 설명 + 예시 코드
  - 하단: 광고 영역 + 다른 치트시트 링크
- 검색/필터 기능 (JS로 카드 필터링)
- 인쇄 친화적 CSS (`@media print`)
- AdSense 스크립트를 `<head>`에 포함:
```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-4754582635962628" crossorigin="anonymous"></script>
```
- 광고 영역: 페이지 상단 1개 + 하단 1개

---

## 5. SEO 규칙

### 각 페이지별
- `<title>`: "{주제} Cheat Sheet - Quick Reference for Developers"
- `<meta name="description">`: 키워드 포함 설명 (150자 이내)
- `<link rel="canonical">`: 정규 URL
- Open Graph 메타태그
- 구조화된 데이터 (JSON-LD): Article 또는 TechArticle 스키마

### sitemap.xml
- 모든 치트시트 페이지를 개별 URL로 등록
- 새 치트시트 추가 시 sitemap에도 추가

---

## 6. 치트시트 후보 목록 (우선순위순)

| 순위 | 주제 | 파일명 | 타겟 키워드 | 예상 월 검색량 |
|------|------|--------|------------|---------------|
| 1 | Git Commands | git.html | git cheat sheet | 500,000+ |
| 2 | CSS Flexbox | css-flexbox.html | flexbox cheat sheet | 300,000+ |
| 3 | Regex | regex.html | regex cheat sheet | 250,000+ |
| 4 | Markdown | markdown.html | markdown cheat sheet | 200,000+ |
| 5 | HTTP Status Codes | http-status.html | http status codes | 200,000+ |
| 6 | CSS Grid | css-grid.html | css grid cheat sheet | 150,000+ |
| 7 | Bash/Shell | bash.html | bash cheat sheet | 150,000+ |
| 8 | JavaScript | javascript.html | javascript cheat sheet | 150,000+ |
| 9 | Python | python.html | python cheat sheet | 150,000+ |
| 10 | HTML Entities | html-entities.html | html entities list | 100,000+ |
| 11 | SQL | sql.html | sql cheat sheet | 200,000+ |
| 12 | Docker | docker.html | docker cheat sheet | 100,000+ |
| 13 | Vim | vim.html | vim cheat sheet | 100,000+ |
| 14 | Keyboard Shortcuts (VS Code) | vscode.html | vscode shortcuts | 100,000+ |
| 15 | npm/yarn | npm.html | npm commands | 80,000+ |

---

## 7. 개발 절차

### 7.1 초기 세팅 (1회)
1. `git init` → `git branch -m main`
2. `gh repo create dev-cheatsheets --public --description "Developer cheat sheets - Quick reference for Git, CSS, Regex, and more"`
3. `git remote add origin https://github.com/jko-yohan/dev-cheatsheets.git`
4. 공통 파일 생성: `index.html`, `style.css`, `sitemap.xml`, `robots.txt`, `.gitignore`
5. 커밋 & 푸시
6. GitHub Pages 활성화

### 7.2 치트시트 추가 (반복)
1. `sheets/{topic}.html` 생성
2. `index.html` 목록에 추가
3. `sitemap.xml`에 URL 추가
4. 커밋 & 푸시
5. Search Console에서 색인 생성 요청

### 7.3 Search Console
- URL 검사 → 각 치트시트 페이지 색인 생성 요청
- Sitemaps → `sitemap.xml` 제출

---

## 8. 문서 동기화 규칙

Git 내 문서 변경 시 → iCloud 관리 경로에도 동일 파일 복사.
MASTER_INDEX.md, STATUS.md는 iCloud에만 존재하며 변경사항 발생 시 함께 업데이트.

---

## 9. 참고

이 프로젝트는 DevTools Online, SEO Tool Sites와 **완전히 독립**적입니다.
경로, 파일, 설정을 절대 혼용하지 마세요.
AdSense 계정(ca-pub-4754582635962628)만 공유합니다.
