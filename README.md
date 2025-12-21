## TasteBox Frontend

### 📚 프로젝트 개요

TasteBox Frontend는 React + TypeScript 기반의 영화·TV 콘텐츠 추천 서비스 사용자 화면입니다.
TasteBox Backend에서 제공하는 API와 연동하여 인증, 콘텐츠 탐색, 개인화 기능을 제공합니다.
​
--- 
### ✨ 주요 기능
- Google / Kakao 소셜 로그인 연동

- 영화·TV 콘텐츠 목록 및 상세 조회

- 영화·TV 콘텐츠 장르 설정 및 프로필 설정

- 사용자 맞춤 추천 및 컬렉션 보드 영역

- 공통 레이아웃·헤더·푸터 등 재사용 가능한 UI 컴포넌트

- 로딩/에러 상태 표시 및 사용자 피드백 처리

- 콘텐츠 추가 기능 및 토스트 추가 알림 기능

- 컬렉션 제목· 설명 및 썸네일 설정 기능​

- 컬렉션 수정 및 삭제 기능

---

## 🛠 기술 스택
- 언어 & 프레임워크: React, TypeScript

- 번들러: Vite

- 라우팅: React Router

- 상태 관리: Zustand

- 스타일링: styled-components

- 빌드 & 배포: GitHub Actions, AWS S3/CloudFront

- 코드 품질: Biome, Prettier, Husky, lint-staged, commitlint
​
---

## 🧱 아키텍처: Feature-Sliced Design (FSD)
TasteBox Frontend는 Feature-Sliced Design(FSD) 아키텍처를 기반으로 폴더 구조를 설계했습니다.

```​
src/
├── app/        # 애플리케이션 엔트리, 전역 Provider, 라우팅 설정
├── pages/      # 라우트 단위 페이지 컴포넌트
├── widgets/    # 페이지를 구성하는 큰 단위 UI 블록
├── features/   # 개별 기능(로그인, 검색, 필터 등)
├── entities/   # 핵심 도메인 모델(사용자, 콘텐츠 등)
├── shared/     # 공통 컴포넌트, 라이브러리, 유틸리티
└── ...
```

상위 레이어(app, pages, widgets)는 하위 레이어(features, entities, shared)에만 의존하도록 설계하여 결합도를 낮춥니다.

widgets/ 내부는 common, contents, user 등 도메인/역할별 슬라이스로 구성되며, 여러 features와 entities를 조합해 실제 화면에 가까운 UI 블록을 만듭니다.
​

## ⚙️ 환경변수 설정
.env 파일은 저장소에 커밋하지 않으며, .env.example을 복사하여 사용합니다.
프로젝트 설정에 맞게 실제 키 이름을 조정해서 사용하세요.
​
# API 서버
VITE_API_URL=                 # 백엔드 API base URL

# OAuth
```
# MySQL 환경변수
MYSQL_DATABASE=
MYSQL_HOST=
MYSQL_PORT=
MYSQL_USERNAME=
MYSQL_PASSWORD=
MYSQL_SYNCHRONIZE=

# Redis 환경변수
REDIS_HOST=
REDIS_PORT=
REDIS_PASSWORD=
REDIS_REFRESH_EXPIRE_SECONDS=

# Google API
GOOGLE_API_KEY=

# JWT
JWT_SECRET=
JWT_EXPIRES_IN=

# Refresh JWT
REFRESH_JWT_SECRET=
REFRESH_JWT_EXPIRES_IN=

# Google OAuth
GOOGLE_CLIENT_ID=
GOOGLE_SECRET=
GOOGLE_CALLBACK_URL=

# Kakao OAuth
KAKAO_CLIENT_ID=
KAKAO_CALLBACK_URL=
```
---

## 🚀 설치 및 실행
#### 1. 레포지토리 클론
git clone https://github.com/StepUp2025/TasteBox-Frontend.git
cd tastebox-frontend

#### 2. 의존성 설치
npm install

#### 3. 환경변수 파일 생성
cp .env.example .env
.env 파일에 실제 값 입력

#### 4. 개발 서버 실행
npm run dev
로컬 개발 서버는 Vite 기본 포트(예: http://localhost:5173)에서 실행됩니다.
​
---

### 🧑‍💻 협업 및 개발 환경 가이드
- **코드 포맷팅/린팅**
npm run format으로 전체 코드 자동 정렬(기존 작업 중인 파일도 포함)
마크다운 파일은 Prettier로, 나머지는 Biome으로 포맷팅

- **커밋 컨벤션**
커밋 메시지는 팀 규칙을 따라 작성 (commitlint 자동 체크)

- **브랜치 네이밍**
feat/, fix/, chore/ 등 prefix 사용

- **VSCode 확장**
Biome 확장 설치
.vscode/settings.json 참고
