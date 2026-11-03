# 일본·제주 단체 여행 플래너

배포 주소: https://trip.dsoom.com

2026년 12월~2027년 1월, 일본 4개 지역과 제주의 일정·항공 후보·숙소·예산·식당을 비교하는 한국어 정적 웹 프로그램입니다.

## 구성

- `index.html`: 화면, 스타일, 여행 데이터, 계산 및 공유 기능
- `assets/`: 웹 표시용으로 최적화한 공식 숙소·식당 이미지
- `SOURCES.md`: 사진 및 메뉴 정보 출처
- `.nojekyll`: GitHub Pages에서 정적 파일을 그대로 제공하기 위한 빈 파일

별도 설치, 빌드, API 키, 서버 데이터베이스가 필요하지 않습니다.

## 로컬 실행

`index.html`을 브라우저로 열거나, 이 폴더에서 Python이 설치되어 있다면 아래 명령으로 실행하세요.

```sh
python -m http.server 8000
```

브라우저에서 `http://localhost:8000`을 엽니다. 공유 링크 기능은 배포된 HTTPS 사이트에서 사용하는 것을 권장합니다. 등록 예산은 브라우저의 localStorage에 저장되며, 공유 버튼으로 날짜·인원·지역·예산을 URL에 담습니다. 여러 사람이 함께 수정하는 서버 저장 기능은 없습니다.

## GitHub에 업로드 및 GitHub Pages 게시

1. GitHub에서 저장소를 만들고 이 폴더의 **내용물**을 저장소 최상위에 올립니다. `index.html`과 `assets` 폴더의 상대 위치를 유지하세요.
2. 저장소의 Settings → Pages에서 게시 방식을 `Deploy from a branch`로 설정합니다.
3. 업로드한 브랜치(예: `main`)와 `/(root)`를 선택하고 저장합니다.
4. 배포가 끝나면 GitHub가 표시하는 Pages URL로 접속합니다.

저장소의 공개 여부와 이용 요금제에 따라 Pages 사용 가능 여부가 다를 수 있습니다.

공식 안내: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## japan.dsoom.com 연결

이 패키지는 현재 Sites 서비스의 도메인 연결과 별개입니다. GitHub Pages 배포 성공 후, Pages의 Custom domain에 `japan.dsoom.com`을 등록하고 DNS의 `japan` CNAME을 **본인의 `<GitHub사용자명>.github.io`**로 변경해야 합니다. 프로젝트 저장소 이름은 DNS 대상에 넣지 않습니다. HTTPS 인증서가 준비되면 HTTPS 사용을 켭니다.

현재 `japan.dsoom.com`의 CNAME은 `custom-domains.chatgpt.site`이므로 그대로 두면 GitHub Pages로 연결되지 않습니다. 이 패키지에는 잘못된 도메인 연결을 방지하기 위해 CNAME 파일을 넣지 않았습니다. 도메인 변경은 패키지 전달 과정에서 적용하지 않았습니다. GitHub에 설정할 도메인의 소유권 검증을 권장합니다.

공식 안내: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

## 내용 수정

`index.html`에서 아래 이름을 검색하면 관련 데이터를 찾을 수 있습니다.

- `data`: 지역별 일정
- `flights`: 항공편 후보와 참고 시간
- `hotels`, `economyHotels`: 호텔 후보와 공식 링크
- `cityPriceDefaults`: 항공·숙소 계획용 예상 단가
- `photoSets`: 호텔 사진 경로
- `nearbyFood`: 식당·메뉴·가격·이미지·출처

## 데이터와 사진 사용 시 유의사항

항공편 시간은 공개 운항표 참고값이며 선택 날짜의 운항·10인 좌석을 실시간 조회하지 않습니다. 숙박 가격과 추천 가격은 **임의의 계획용 예상 단가**입니다. 식당 가격은 2026-11-03 확인한 공식 메뉴의 참고 가격이며, 지점·계절·매장/포장 여부에 따라 달라집니다.

이미지는 실제 호텔·식당의 공식 공개 자료입니다. 사진 저작권은 원 권리자에게 있으며, 이 패키지는 제3자 사진의 재배포 또는 상업적 이용 허가를 제공하지 않습니다. 공개 저장소에 올리기 전 사용 권한을 확인하거나 직접 사용 가능한 사진으로 교체하세요. 도쿄 호텔 사진 2개는 공식 사이트 URL을 직접 불러오므로 제공처 정책에 따라 표시되지 않을 수 있습니다. 삿포로 식당 사진은 메뉴 사진이 아닌 공식 매장 사진입니다.

현재 공개된 앱의 파일을 전달하는 패키지이며, 기능을 여러 차례 확장하면서 CSS와 스크립트가 한 파일에 누적되어 있습니다. 프레임워크 프로젝트로 재구성한 버전은 아닙니다.
