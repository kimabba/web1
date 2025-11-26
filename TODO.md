# 매치온 웹사이트 개선 작업 목록

## 📋 현재 상태
- 정적 HTML 랜딩 페이지 (3개 페이지)
- Tailwind CSS + Vanilla JS
- CDN 기반 라이브러리 사용

## 🎯 향후 계획
- **헤드리스 워드프레스** 방식으로 전환 예정

---

## ✅ 우선순위 작업 (현재 정적 페이지 개선)

### Phase 1: SEO & 성능 최적화 (즉시 적용 가능)

- [ ] **SEO 메타태그 추가**
  - Open Graph 태그 (Facebook, KakaoTalk 공유)
  - Twitter Card 태그
  - 상세한 description 및 keywords
  - Canonical URL 설정
  - 파일: `index.html`, `about.html`, `property-loan.html`

- [ ] **이미지 최적화**
  - lazy loading 속성 추가 (`loading="lazy"`)
  - alt 텍스트 확인 및 보완
  - 이미지가 있다면 WebP 형식 고려

- [ ] **성능 최적화**
  - Critical CSS 인라인화
  - 폰트 preload 최적화
  - 외부 스크립트 async/defer 적용

- [ ] **접근성 개선**
  - ARIA 레이블 점검
  - 폼 접근성 강화
  - 키보드 네비게이션 테스트

### Phase 2: 구조화된 데이터 & 분석

- [ ] **Structured Data (JSON-LD) 추가**
  - Organization schema
  - LocalBusiness schema
  - FinancialProduct schema
  - BreadcrumbList schema

- [ ] **Google Analytics / Tag Manager 설정**
  - 페이지뷰 추적
  - 전환 이벤트 설정 (폼 제출, 버튼 클릭)
  - 스크롤 깊이 측정

- [ ] **XML Sitemap 생성**

### Phase 3: 코드 품질 개선

- [ ] 중복 코드 제거 (헤더/푸터 분리 준비)
- [ ] 일관된 네이밍 컨벤션
- [ ] 주석 추가 (유지보수성)

---

## 🚀 헤드리스 WordPress 전환 계획 (진행 중)

### 현재 상태
- ✅ Phase 1 완료: SEO 최적화 및 성능 개선
- 🚀 Phase 2 시작: Next.js 16 프로젝트 전환

### 아키텍처 설계

**백엔드: WordPress (WPGraphQL)**
- 콘텐츠 관리 (블로그, 상품 정보, FAQ)
- Custom Post Types (대출 상품, 후기, 사례)
- ACF (Advanced Custom Fields) - 필드 관리
- WPGraphQL API

**프론트엔드: Next.js 16**
- Static Site Generation (SSG)
- Server-Side Rendering (SSR) - 동적 페이지
- Incremental Static Regeneration (ISR)
- Vercel 배포

### 구현 단계

#### Step 1: WordPress 설정
- [ ] WordPress 설치 (호스팅 선정)
- [ ] 테마 설치 (headless 용 최소 테마)
- [ ] 플러그인 설치
  - ACF Pro (커스텀 필드)
  - WPGraphQL 또는 REST API 활성화
  - Yoast SEO
  - WP Fastest Cache
- [ ] Custom Post Types 정의
  - 대출 상품 (Loan Products)
  - 고객 후기 (Testimonials)
  - FAQ
  - 블로그/뉴스

#### Step 2: 프론트엔드 개발
- [ ] Next.js 프로젝트 초기화
- [ ] Tailwind CSS 설정
- [ ] WordPress API 연동
- [ ] 페이지 구조 마이그레이션
  - 홈페이지
  - 소개 페이지
  - 상품 상세 페이지
  - 블로그 목록/상세
- [ ] 컴포넌트 구조화
  - Header
  - Footer
  - Hero Section
  - Loan Calculator
  - Product Cards
  - Contact Form

#### Step 3: 데이터 마이그레이션
- [ ] 현재 HTML 콘텐츠 → WordPress 입력
- [ ] 이미지 업로드 및 최적화
- [ ] URL 구조 정의 (SEO 유지)

#### Step 4: 배포 및 테스트
- [ ] Vercel 연동
- [ ] 환경 변수 설정
- [ ] 성능 테스트 (Lighthouse)
- [ ] SEO 테스트
- [ ] 모바일 반응형 테스트

---

## 📦 추천 기술 스택 (헤드리스 WP)

### 백엔드
- **WordPress** (6.x 최신 버전)
- **WPGraphQL** (REST API보다 유연함)
- **ACF Pro** (커스텀 필드 관리)
- **WPGraphQL for ACF** (GraphQL 쿼리)

### 프론트엔드
- **Next.js 16** (최신 버전, App Router)
- **TypeScript** (타입 안정성)
- **Tailwind CSS** (현재 사용 중)
- **SWR** 또는 **React Query** (데이터 페칭)
- **Headless UI** (접근성 좋은 컴포넌트)

### 배포
- **Vercel** (Next.js 최적화)
- **Cloudflare** (CDN, DNS)

### 모니터링
- **Google Analytics 4**
- **Vercel Analytics**
- **Sentry** (에러 추적)

---

## 🎯 헤드리스 WP의 장단점

### ✅ 장점
1. **콘텐츠 관리 용이**: 비개발자도 WordPress 관리자 페이지에서 수정 가능
2. **빠른 개발**: WordPress의 풍부한 플러그인 생태계 활용
3. **SEO 친화적**: WordPress의 강력한 SEO 플러그인 활용
4. **확장성**: 커스텀 포스트 타입으로 다양한 콘텐츠 관리
5. **성능**: Next.js SSG로 정적 생성 → 빠른 로딩
6. **보안**: 프론트엔드와 백엔드 분리로 WordPress 관리자 노출 최소화

### ⚠️ 고려사항
1. **복잡도 증가**: 프론트엔드 + 백엔드 관리 필요
2. **호스팅 비용**: WordPress 서버 별도 필요
3. **캐싱 전략**: ISR, CDN 설정 필요
4. **개발 시간**: 초기 설정에 시간 투자 필요
5. **미리보기 기능**: 콘텐츠 미리보기 구현 필요

---

## 💡 대안 방안

### Option 1: 헤드리스 CMS (WordPress 대신)
- **Strapi** (오픈소스, 자체 호스팅)
- **Contentful** (SaaS, 무료 티어)
- **Sanity** (개발자 친화적)
- **Payload CMS** (Next.js 기반)

### Option 2: 완전 정적 (마크다운 기반)
- **Next.js + MDX** (블로그만 필요한 경우)
- **Astro** (콘텐츠 중심 사이트)

### Option 3: 하이브리드
- 랜딩/마케팅 페이지: 정적 (빠른 성능)
- 블로그/콘텐츠: 헤드리스 WP (관리 편의성)

---

## 🚦 추천 접근 방법

### 단기 (1-2주)
1. ✅ 현재 HTML 페이지 SEO/성능 최적화
2. ✅ Google Analytics 설치
3. ✅ 콘텐츠 정리 및 문서화

### 중기 (1-2개월)
1. WordPress 설치 및 설정
2. Next.js 프로젝트 초기화
3. 주요 페이지 마이그레이션 (홈, 소개)
4. API 연동 테스트

### 장기 (3개월+)
1. 전체 페이지 마이그레이션
2. 블로그 시스템 구축
3. 관리자 교육
4. 운영 프로세스 확립

---

---

## 🎯 Next.js 16 마이그레이션 로드맵

### Phase 1: 프로젝트 초기화 (1-2일)

- [ ] **Next.js 16 프로젝트 생성**
  ```bash
  npx create-next-app@latest match-on-nextjs --typescript --tailwind --app
  ```

- [ ] **기본 설정**
  - [ ] Tailwind CSS 커스텀 설정 (현재 디자인 시스템 적용)
  - [ ] 폴더 구조 설정
  - [ ] ESLint/Prettier 설정
  - [ ] 환경 변수 설정

- [ ] **외부 라이브러리 설치**
  - [ ] Swiper (슬라이더)
  - [ ] Chart.js (차트)
  - [ ] Framer Motion (애니메이션 - Particles.js 대체)
  - [ ] React Hook Form (폼 관리)

### Phase 2: 공통 컴포넌트 (2-3일)

- [ ] **레이아웃 컴포넌트**
  - [ ] `Header.tsx` - 네비게이션, 로고
  - [ ] `Footer.tsx` - 푸터 정보, 링크
  - [ ] `Layout.tsx` - 전체 레이아웃 래퍼

- [ ] **UI 컴포넌트**
  - [ ] `Button.tsx` - 재사용 가능한 버튼
  - [ ] `Card.tsx` - 상품 카드
  - [ ] `Badge.tsx` - 배지 컴포넌트
  - [ ] `Input.tsx` - 폼 입력 필드

### Phase 3: 페이지 마이그레이션 (3-4일)

- [ ] **홈페이지** (`app/page.tsx`)
  - [ ] Hero Section (롤링 텍스트 애니메이션)
  - [ ] 대출 신청 폼
  - [ ] 프로세스 섹션
  - [ ] 통계 섹션 (CountUp 애니메이션)
  - [ ] 상품 비교표
  - [ ] FAQ 섹션
  - [ ] CTA 섹션
  - [ ] 모바일 스티키 바

- [ ] **소개 페이지** (`app/about/page.tsx`)
  - [ ] Hero Section
  - [ ] 회사 소개
  - [ ] 비전/미션
  - [ ] 팀 소개 (있다면)

- [ ] **부동산담보대출 페이지** (`app/property-loan/page.tsx`)
  - [ ] Hero Section
  - [ ] 상품 유형별 탭
  - [ ] 상품 리스트
  - [ ] 신청 폼

### Phase 4: 기능 컴포넌트 (2-3일)

- [ ] **대출 계산기** (`components/LoanCalculator.tsx`)
  - [ ] 입력 폼 (대출 금액, 기간)
  - [ ] 실시간 계산 로직
  - [ ] 결과 표시

- [ ] **상품 비교표** (`components/ProductComparison.tsx`)
  - [ ] 테이블 레이아웃
  - [ ] 모바일 최적화 (3줄 레이아웃)
  - [ ] 필터 기능

- [ ] **문의 폼** (`components/ContactForm.tsx`)
  - [ ] React Hook Form 통합
  - [ ] 유효성 검사
  - [ ] API 연동 준비

### Phase 5: WordPress 설정 (2-3일)

- [ ] **WordPress 설치**
  - [ ] 호스팅 선택 (Cloudways, WP Engine, 또는 로컬)
  - [ ] WordPress 최신 버전 설치
  - [ ] 관리자 계정 설정

- [ ] **필수 플러그인 설치**
  - [ ] WPGraphQL
  - [ ] WPGraphQL for ACF
  - [ ] ACF Pro
  - [ ] Yoast SEO
  - [ ] WP Fastest Cache

- [ ] **Custom Post Types 생성**
  - [ ] 대출 상품 (loan_product)
    - 필드: 제품명, 최저금리, 최대한도, 특징, 이미지
  - [ ] 고객 후기 (testimonial)
    - 필드: 고객명, 내용, 평점, 날짜
  - [ ] FAQ
    - 필드: 질문, 답변, 카테고리
  - [ ] 블로그 포스트 (기본 post 타입 사용)

### Phase 6: Next.js + WordPress 연동 (3-4일)

- [ ] **GraphQL 클라이언트 설정**
  - [ ] Apollo Client 또는 urql 설치
  - [ ] GraphQL 엔드포인트 설정
  - [ ] 인증 설정 (필요 시)

- [ ] **데이터 페칭 구현**
  - [ ] 홈페이지 데이터 가져오기
  - [ ] 상품 목록 가져오기
  - [ ] 블로그 목록/상세 페이지
  - [ ] FAQ 데이터

- [ ] **이미지 최적화**
  - [ ] Next.js Image 컴포넌트 사용
  - [ ] WordPress 이미지 URL 처리
  - [ ] Lazy loading 구현

### Phase 7: 콘텐츠 마이그레이션 (1-2일)

- [ ] **현재 HTML 콘텐츠 → WordPress 입력**
  - [ ] 대출 상품 5개 입력
  - [ ] 회사 소개 내용
  - [ ] FAQ 입력

- [ ] **이미지 업로드**
  - [ ] 필요한 이미지 수집
  - [ ] WordPress 미디어 라이브러리 업로드
  - [ ] OG 이미지 생성

### Phase 8: 배포 및 최적화 (2-3일)

- [ ] **Vercel 배포**
  - [ ] GitHub 연동
  - [ ] 환경 변수 설정 (WordPress API URL)
  - [ ] 도메인 연결

- [ ] **성능 최적화**
  - [ ] Lighthouse 테스트 (목표: 90+ 점수)
  - [ ] Core Web Vitals 확인
  - [ ] 이미지 최적화 재점검
  - [ ] 번들 사이즈 최적화

- [ ] **SEO 검증**
  - [ ] 메타태그 확인
  - [ ] Sitemap 생성 (next-sitemap)
  - [ ] robots.txt 설정
  - [ ] Google Search Console 등록

- [ ] **테스트**
  - [ ] 모바일 반응형 테스트
  - [ ] 브라우저 호환성 테스트
  - [ ] 폼 제출 테스트
  - [ ] API 연동 테스트

### Phase 9: 문서화 및 인수인계 (1일)

- [ ] **개발 문서 작성**
  - [ ] 프로젝트 구조 설명
  - [ ] 환경 설정 가이드
  - [ ] 배포 가이드

- [ ] **WordPress 관리 가이드**
  - [ ] 콘텐츠 작성 방법
  - [ ] 상품 추가/수정 방법
  - [ ] 이미지 업로드 가이드
  - [ ] FAQ 관리 방법

---

## 📅 예상 소요 시간

| Phase | 작업 | 예상 시간 |
|-------|------|-----------|
| 1 | Next.js 프로젝트 초기화 | 1-2일 |
| 2 | 공통 컴포넌트 | 2-3일 |
| 3 | 페이지 마이그레이션 | 3-4일 |
| 4 | 기능 컴포넌트 | 2-3일 |
| 5 | WordPress 설정 | 2-3일 |
| 6 | API 연동 | 3-4일 |
| 7 | 콘텐츠 마이그레이션 | 1-2일 |
| 8 | 배포 및 최적화 | 2-3일 |
| 9 | 문서화 | 1일 |
| **총계** | | **17-25일** |

---

## 🚀 바로 시작 가능한 첫 단계

**지금 바로 실행:**
```bash
# 1. Next.js 16 프로젝트 생성
npx create-next-app@latest match-on-nextjs --typescript --tailwind --app

# 2. 프로젝트 이동
cd match-on-nextjs

# 3. 개발 서버 실행
npm run dev
```

**다음 작업:**
1. Tailwind 커스텀 설정 (KINFA 디자인 시스템 적용)
2. 폴더 구조 설정
3. Header/Footer 컴포넌트 생성

---

## 📞 시작하시겠습니까?

**Next.js 16 프로젝트를 지금 바로 생성하시겠습니까?**
