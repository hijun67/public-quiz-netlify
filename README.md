# 공공퀴즈픽

## 내 컴퓨터에서 실행
1. Node.js 18+ 설치
2. `node scripts/collect.mjs` (이벤트 수집, AI 정답은 키가 있을 때만)
3. `node scripts/build.mjs` (상세 페이지·sitemap 생성)
4. `npx serve public` 로 확인

## Netlify 배포
- GitHub에 저장소를 올리고 Netlify에서 **Add new site → Import an existing project**로 연결합니다.
- 저장소 루트에 포함된 `netlify.toml`이 빌드 명령(`npm run build`), 게시 폴더(`public`), Node.js 버전(18)을 설정합니다.
- Netlify의 환경 변수에 `SITE_URL`을 직접 설정할 필요는 없습니다. 빌드 스크립트는 Netlify가 제공하는 배포 주소를 사용해 sitemap과 `robots.txt`를 생성합니다.
- `ANTHROPIC_API_KEY`는 정답 분석을 포함한 이벤트 수집 작업을 별도로 실행할 때만 필요합니다. Netlify 빌드 자체는 이 키 없이 진행됩니다.
- 이벤트 수집과 자동 갱신은 Netlify 배포만으로 예약되지 않습니다. 갱신하려면 별도 스케줄 작업으로 `npm run update`를 실행하고 변경 내용을 저장소에 반영해야 합니다.

## 수집 대상 늘리기
`sources.json`에 기관의 실제 이벤트 게시판 주소를 추가하세요.
