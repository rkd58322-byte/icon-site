# ICON Analysis · 베타 랜딩 페이지

ICON 베타 신청 전용 랜딩 페이지. 인스타 스토리 링크에 걸 페이지.

## 파일 구조

```
icon-site/
├── index.html        ← 메인 페이지
├── assets/
│   └── logo.png      ← ICON 로고
└── README.md         ← 이 파일
```

`index.html` 하나가 사이트 전체. CSS·JS 다 안에 들어 있어서 추가 파일 필요 없음.

---

## 1. 배포하기 (Vercel — 5분이면 됨)

가장 쉬운 방법은 **Vercel + GitHub** 조합. 둘 다 무료.

### 단계

1. **GitHub 가입** — github.com 가입
2. **새 저장소 만들기** — "New repository" → 이름: `icon-site` → Public
3. **파일 업로드** — 저장소 페이지에서 "uploading an existing file" 클릭 → `icon-site` 폴더 안의 모든 파일 드래그
4. **Vercel 가입** — vercel.com → "Continue with GitHub"
5. **프로젝트 import** — "Add New Project" → 방금 만든 저장소 선택 → "Deploy"
6. **끝.** 1~2분 후 `your-project.vercel.app` 같은 주소로 사이트 라이브

이후 GitHub에 변경사항 푸시할 때마다 Vercel이 자동 재배포.

### 도메인 붙이기 (선택)

`iconanalysis.com` 같은 도메인 사고 싶으면:

1. 가비아 / 후이즈 / Namecheap 등에서 도메인 구매 (연 1~2만원)
2. Vercel 프로젝트 → Settings → Domains → 도메인 추가
3. Vercel이 알려주는 DNS 설정대로 도메인 등록처에서 설정
4. 5~30분 후 자기 도메인으로 사이트 접속 가능

---

## 2. 신청 폼 이메일 연결하기 (필수, 2분)

지금 사이트는 진짜 신청 폼이 들어있어. "지금 신청하기" 누르면 이름·이메일·인스타·종목·영상 파일·요청사항이 너 이메일로 바로 날아오는 구조. 다만 **Web3Forms 액세스 키를 폼에 한 번 박아줘야** 작동해.

### 단계

**(1) Web3Forms 액세스 키 발급 — 회원가입 없이 1분**

1. https://web3forms.com 접속
2. 메인 페이지에서 "Get your free Access Key" 박스에 본인 이메일 입력
3. "Create Access Key" 클릭
4. 너 이메일로 액세스 키가 도착함 (32자 정도 영문/숫자 조합)

**(2) `index.html` 열기 → `YOUR_ACCESS_KEY_HERE` 검색**

다음 줄 찾기:

```html
<input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
```

**(3) `YOUR_ACCESS_KEY_HERE`를 본인 액세스 키로 교체**

예시:

```html
<input type="hidden" name="access_key" value="a1b2c3d4-1234-5678-abcd-..." />
```

**(4) GitHub에 푸시 → Vercel 자동 배포 → 끝.**

### 이게 어떻게 작동하나

- **Web3Forms** — 무료 폼 백엔드 서비스. 영상 파일까지 첨부해서 너 이메일로 forwarding 됨.
- **영상 파일 직접 업로드** — 신청자가 폼에서 영상을 직접 첨부함. 너 이메일에 첨부파일로 도착.
- **파일 크기 제한 10MB** — Web3Forms 무료 플랜 한도. 영상 폰 카메라 720p로 30~60초 정도면 거의 다 들어감. 더 크면 신청자는 인스타 DM으로 안내됨 (사이트에 안내문 박혀 있음).
- **비공개 기본** — 영상은 분석자(너)만 봄. 신청 폼에 "콘텐츠 활용 동의" 선택 옵션이 있어서, 동의한 경우에만 ICON 채널에 익명으로 활용 가능.

### 신청 받은 후 흐름

1. 너 이메일에 신청서 도착 (이름·이메일·인스타·종목·영상 첨부·요청사항 + 콘텐츠 활용 동의 여부)
2. 영상 첨부파일 다운로드 → 분석 진행
3. 8페이지 PDF 리포트 만들어서 회신 메일에 첨부 발송
4. (콘텐츠 활용 동의자만) 나중에 ICON 인스타·유튜브 콘텐츠로 익명 활용

### 폼 필드 수정하고 싶을 때

`index.html`에서 `<form id="apply-form"` 부분 찾아서 안에 있는 `<div class="form-row">` 블록 추가/삭제. 예를 들어 "현재 수영 수준" 같은 필드 추가하고 싶으면 다른 form-row 블록 복사해서 붙여넣고 수정하면 됨.

### Tally로 전환하고 싶을 때 (선택)

신청자가 늘어나서 관리 페이지·자동화·통계가 필요하면 Tally로 전환 추천. 그때는 위 form 블록 전체를 Tally 임베드 코드로 교체.

---

## 3. 인스타 스토리에 링크 거는 법

1. 사이트 주소 복사 (예: `iconanalysis.vercel.app` 또는 자기 도메인)
2. 인스타 스토리 만들기 → 스티커 → "링크" 선택 → 주소 붙여넣기
3. "맞춤 텍스트" 설정 가능 — "베타 신청하기" 같은 거 넣으면 깔끔
4. 게시

---

## 4. 수정하고 싶을 때

`index.html` 열어서 텍스트 바꾸고 GitHub에 푸시. 자동 재배포.

자주 바꾸게 될 부분:

- **인스타/유튜브 링크** — `@icon__0fficial`, `@icon_0fficial_korea` 부분 검색해서 수정
- **CTA 문구** — "지금 신청하기" 같은 문구
- **분석 영역** — 자세 효율성·추진력·부상 위험 같은 카테고리 설명

---

## 트러블슈팅

- **로고가 안 보임** → `assets/logo.png` 파일이 같이 업로드됐는지 확인
- **한글이 깨짐** → Pretendard 폰트 CDN이 차단된 환경일 수도. 대부분 문제 없음.
- **배포 후 변경 반영 안 됨** → 브라우저 캐시 문제. 시크릿 모드로 열어보면 보임.

---

## 다음 단계 아이디어

- [ ] 가격 정해지면 결제 연동 (Toss Payments / Stripe)
- [ ] `/about` 페이지 추가 (브랜드 스토리 더 깊게)
- [ ] `/guide` 페이지 추가 (자격증 가이드 컨텐츠)
- [ ] `/archive` 페이지 추가 (분석 사례 모음)
- [ ] 신청자 늘어나면 Tally 폼으로 전환

지금은 원페이지로 충분. 신청자 늘기 시작하면 그때 확장.
