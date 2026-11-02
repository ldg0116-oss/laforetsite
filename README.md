# 라포레(la Forêt) 홈페이지

제주 도남동 유아 한국무용·발레 학원 **라포레무브먼트** 공식 홈페이지 코드.

## 현재 운영 상태
- **배포 주소**: https://laforet-jeju.netlify.app
- **GitHub 저장소**: https://github.com/ldg0116-oss/laforetsite
- **호스팅**: Netlify (GitHub 연동 → `main` 브랜치에 push하면 자동 배포)
- 사이트는 `index.html` **한 파일**로 구성 (로고는 코드에 내장, 빌드 불필요)

## Claude Code로 관리하는 방법
이 폴더를 GitHub 저장소와 연결하면, 수정 후 push만 하면 자동으로 사이트에 반영됩니다.

처음 한 번만 (이 폴더에서):
```
git init
git remote add origin https://github.com/ldg0116-oss/laforetsite.git
git fetch origin
git reset --hard origin/main
```

이후 수정할 때마다:
```
git add .
git commit -m "수정 내용"
git push origin main        # → Netlify가 자동 배포
```

## 연동된 외부 서비스
- **인스타 갤러리**: Behold 위젯(feed-id `by4LOxMtqBqnBc8oSZgR`) — 인스타 @laforet_movement 에 올리면 홈페이지 갤러리 자동 갱신
- **카톡 문의**: https://pf.kakao.com/_xcpPWX
- **인스타**: https://www.instagram.com/laforet_movement

## 아직 채워야 할 것 (index.html 안의 【 】 자리)
- 대표자명 / 사업자등록번호 / 통신판매업신고번호
- 스마트스토어 URL (굿즈) — 현재 '준비중'
- 쿠팡 파트너스 링크 (추천 용품)
- 네이버 예약 URL
- 유튜브·블로그 URL, 개인정보처리방침 링크
- 무료체험 폼 실제 발송 연결 (Formspree 등)
- 네이버 서치어드바이저 / 구글 서치콘솔 소유확인 코드 (`<meta>` 자리)

## 기본 정보
- 상호: 라포레무브먼트 (la Forêt)
- 주소: 제주시 복지로3길 2-1 2층 (도남동 703-2)
- 전화: 0507-1386-6878
- 운영: 매일 ~22:00
