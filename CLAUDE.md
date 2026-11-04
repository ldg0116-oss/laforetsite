# 라포레(la Forêt) 홈페이지 — Claude Code 작업 가이드

제주 도남동 **한국무용 스튜디오** **라포레무브먼트**의 단일 페이지 홍보 사이트(유아·초등·성인·예비전공/콩쿨). 사이트 표기는 '학원'·'전문교육기관'이 아니라 **'한국무용 스튜디오'**. 주 타깃은 30~40대 엄마. 발레 관련 내용은 넣지 않음. 목적은 무료체험 문의 유도, 굿즈 안내, 홍보.

## 구조·배포
- 정적 사이트: `index.html`(본문) + `privacy.html`(개인정보처리방침). 빌드 도구 없음.
- 이미지: `logo.png`(헤더용), `logo-light.png`(어두운 배경용), `og-image.jpg`(카톡·SNS 공유 썸네일 1200×630), `favicon.png`, `apple-touch-icon.png`. SEO: `robots.txt`, `sitemap.xml`.
- 첫 화면은 **three.js 3D 마을**(`index.html` 하단 `<script type="module">`, three@0.160.0을 jsDelivr CDN import map으로 로드). 건물·나무·캐릭터는 전부 코드로 만든 기본 도형(둥근 박스·구·원뿔)이라 별도 3D 파일 없음.
  - 캐릭터 함수: `kidHanbok(옵션)`(한복+한삼 리본, 초급반), `kidFan`(부채, 무대에서 회전·개인레슨 카드), `kidStar`(트로피, 예비전공/콩쿨반), `adult`(진도북춤 북, 성인반), `kidPencil`(왕연필 릴레이, 광장 둘레를 달림), `kidWitch`(마녀+호박등). 공통 얼굴 `face()`, 팔 `arm()`.
  - 카드 그림 키(`data-kid`): hanbok·star·adult·fan·pencil·friends.
  - `og-image.jpg`는 이 3D 마을을 렌더링한 장면 + 문구(2026-11-04).
  - 건물은 `buildWorld()` 안 `place(g, {id, name, sub, desc, color, ly})`: 나무집=about, 연습실=programs, 무대=gallery, 바우처 센터=voucher, 굿즈샵=shop, 카톡 우체통=contact. 누르면 카메라가 다가가고 대화창에 설명 + '자세히 보기' 버튼.
  - 아래 섹션의 캐릭터 그림(`img.kidimg[data-kid]`)은 페이지가 열릴 때 같은 3D 캐릭터를 렌더링해서 채움(`renderPortraits`).
  - 3D가 9초 안에 안 뜨면 `.fallback`으로 글자만 보이는 화면 전환.
- 2D 그림 버전(이전 시안)은 저장소에 없음(로컬 임시 백업만).
- 배포: GitHub `ldg0116-oss/laforetsite` `main`에 push → Netlify 자동 배포. 수정 후 `git add . && git commit && git push origin main`.
- 대표 주소: **https://laforetmovement.netlify.app** (무료 Netlify 주소, 예전 laforet-jeju.netlify.app에서 이름 변경). canonical·og:url·og:image·JSON-LD·robots·sitemap 모두 이 주소. 주소가 바뀌면 전부 일괄 치환.
- 폰트: Pretendard(전체, jsDelivr CDN).
- 섹션 순서: hero(3D 마을) → about → programs → voucher → gallery → voice(hidden) → shop → gear(hidden) → contact → footer. 모바일은 하단 플로팅 '카톡 문의' 버튼(첫 화면 지나면 나타남).

## 디자인 원칙
- 컨셉: **"숲속 장난감 마을 라포레"** — 레퍼런스 kodeclubs.com(3D 장난감 세상 가상 투어)의 방식을 따르되 모델·코드는 전부 직접 제작(그 사이트 자산 복제 금지). 물 위 섬, 둥근 블록 건물, 부드러운 그림자, 흰 말풍선 대화창(분홍 이름표 + '다음 ›').
- 2D 굵은 외곽선 스타일은 "조잡하다"는 피드백으로 폐기(2026-11-04). 아래 섹션은 테두리 없는 흰 카드 + 부드러운 그림자 + 큰 둥근 모서리, 연한 파스텔 배경(스카이·크림·라벤더). 포인트색 분홍 `#ff5c8a`, 제목 브랜드 초록 `#0e4e33`.
- 아이는 실제 사진 대신 3D 캐릭터로 표현(인스타 영상 속 장면 기반, 아이 얼굴 노출 방지). 새 캐릭터도 같은 비율(큰 머리, 점 눈, 볼터치)로.
- **초록 배경 금지** 유지(초록은 나무·포인트에만). 브랜드색 `#0e4e33`, `#eea51b`.
- 로고는 사용자가 준 원본 기반 파일만 사용(새 로고 제작 금지).

## 외부 연동
- 인스타 갤러리: Behold 위젯 `feed-id="by4LOxMtqBqnBc8oSZgR"` (@laforet_movement에 올리면 자동 갱신)
- 문의·무료체험 신청: 카톡으로 일원화 (신청 폼·네이버 예약 없음). 채팅 `https://pf.kakao.com/_xcpPWX/chat`(신청 버튼·플로팅 버튼), 채널 홈 `https://pf.kakao.com/_xcpPWX`(채널 추가 버튼·푸터)
- 인스타: https://www.instagram.com/laforet_movement

## 운영 규칙
- 대표 강사 이름은 게시하지 않음. 개인정보 보호책임자는 '대표 + 연락처'.
- 유튜브·블로그 링크 없음.
- 기본 정보: 상호 라포레무브먼트(la Forêt) / 사업자등록번호 785-07-02807 / 제주시 복지로3길 2-1 하람빌딩 2층(도남동 703-2) / 사이트 전화 0507-1386-6878 (인스타엔 010-2776-6877, 사이트엔 0507만) / 매일 ~22:00
- **한국무용 전문교육기관 — 발레·엄마와 함께 반 없음**(사이트에 쓰지 말 것). 반 구성은 공식 시간표 기준(2026-11 사용자 제공):
  - 초급반(유아·초등): 월 17:10–18:00 · 목 16:30–17:20 · 토 14:30–15:20
  - 예비전공반(콩쿨반): 월 15:30–17:00 · 토 15:30–17:00 (2027 콩쿨 참가자 모집 중, 유아·초등, 초보자 가능)
  - 성인반: 화 19:00–20:00 · 목 18:30–19:30 (9~11월 진도북춤 작품 과정, 주 1회/2회 선택)
  - 개인 및 소그룹 레슨: 화·수·금·일, 시간 협의
  - 시간표가 바뀌면 `#programs`의 카드 `.when` 줄과 `.week` 시간표를 함께 수정.

## 남은 할 일
- 스마트스토어 URL (굿즈는 현재 '준비중'; 판매 전 통신판매업 신고 확인)
- 쿠팡 파트너스: `#gear`의 `hidden` 제거 + 【쿠팡 파트너스 링크】 교체 (공시 문구 유지)
- 실제 학부모 후기로 교체 후 `#voice`의 `hidden` 제거
- 네이버 서치어드바이저·구글 서치콘솔 소유확인 `<meta>` 코드
- SmartPlace 홈페이지 주소를 laforetmovement.netlify.app으로 등록 + 서치어드바이저·서치콘솔 등록 + sitemap 제출
- (나중에) laforetmovement.com 구매 시: Netlify에 커스텀 도메인 연결(A `@`→`75.2.60.5`, CNAME `www`→`laforetmovement.netlify.app`, 대표 도메인은 apex) → 사이트 주소 일괄 치환 → SmartPlace·서치콘솔 주소 변경

## 작업 방식
- 사용자는 짧고 실행 중심의 한국어 답변을 선호. 묻기보다 바로 수정하고 결과를 한두 줄로 보고.
- 수정은 부분 수정(Edit) 위주로.
- push 전 로컬에서 브라우저로 한 번 확인.
