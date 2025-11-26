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

## 🚀 헤드리스 WordPress 전환 계획

### 아키텍처 설계

**백엔드: WordPress (REST API)**
- 콘텐츠 관리 (블로그, 상품 정보, FAQ)
- Custom Post Types (대출 상품, 후기, 사례)
- ACF (Advanced Custom Fields) - 필드 관리
- WP REST API 또는 WPGraphQL

**프론트엔드: Next.js (추천) 또는 React**
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
- **Next.js 14+** (App Router)
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

## 📞 다음 단계

**지금 바로 시작할 수 있는 작업:**
1. SEO 메타태그 추가 (30분)
2. 이미지 lazy loading (15분)
3. Google Analytics 설정 (20분)

**어떤 작업부터 시작하시겠습니까?**
