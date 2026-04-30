# RAG Search App

이 프로젝트는 사용자가 문서를 업로드하고, 해당 문서의 내용을 바탕으로 질문에 답변을 제공하는 **RAG(Retrieval-Augmented Generation)** 기반 검색 애플리케이션입니다.

## 🚀 주요 기능

- **다양한 포맷의 문서 업로드**: PDF, DOCX, TXT 등 다양한 형태의 문서를 지원합니다.
- **자동 텍스트 추출 및 임베딩**: 업로드된 문서에서 텍스트를 추출하고 LangChain과 OpenAI를 활용하여 임베딩 벡터로 변환합니다.
- **벡터 데이터베이스 저장**: 생성된 문서 임베딩을 Supabase (pgvector)에 안전하게 저장합니다.
- **RAG 기반 검색 및 질의응답**: 사용자의 질문에 대해 벡터 검색을 수행하여 가장 관련성 높은 문서 내용을 바탕으로 정확한 답변을 생성합니다.
- **문서 뷰어 내장**: 검색 결과의 원본 문서를 확인할 수 있는 PDF 뷰어 등을 제공합니다.

## 🛠️ 기술 스택

- **프론트엔드**: [Next.js](https://nextjs.org) (App Router), React, Tailwind CSS
- **백엔드/API**: Next.js Route Handlers
- **AI/LLM**: [OpenAI](https://openai.com), [LangChain](https://js.langchain.com)
- **데이터베이스**: [Supabase](https://supabase.com) (PostgreSQL + pgvector)
- **문서 파싱**: `pdf2json` (PDF), `mammoth` (DOCX)

## 📦 시작하기 (Getting Started)

### 1. 환경 변수 설정
프로젝트 루트 디렉토리에 `.env.local` 파일을 생성하고 다음 환경 변수들을 설정합니다.

```env
# OpenAI
OPENAI_API_KEY=your_openai_api_key

# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
```

### 2. 패키지 설치
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. 개발 서버 실행
```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어 애플리케이션을 확인할 수 있습니다.

## 📁 프로젝트 구조

- `src/app/page.tsx`: 메인 검색 및 채팅 UI
- `src/app/api/upload/route.ts`: 문서 업로드, 텍스트 추출, 청크 분할 및 임베딩 저장 API
- `src/app/api/search/route.ts`: 사용자 질문의 임베딩 생성 및 벡터 DB 검색 API
- `src/app/components/`: 업로드 모달(`UploadModal`), PDF 뷰어(`PDFViewerModal`) 등 재사용 가능한 UI 컴포넌트
