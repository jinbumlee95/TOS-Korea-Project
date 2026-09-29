# 대한민국 서비스 약관 저장소

대한민국 온라인 서비스의 이용약관과 정책을 Git 저장소로 관리합니다. 각 약관은 Markdown 파일이고, 각 개정은 해당 버전의 날짜를 가진 Git commit입니다.

[legalize-kr](https://legalize.kr) (대한민국 법령 Git 저장소)의 방식을 따릅니다.

> 이 저장소는 **비영리** 목적으로, 공개된 약관의 **저장과 버전 간 비교**만을 위해 운영됩니다. 수록된 약관·정책 문서의 **모든 권리는 해당 기업에 있습니다.** 자세한 내용은 [권리 고지 및 이용 조건](#권리-고지-및-이용-조건)을 참고하세요.

## 빠른 시작

```bash
git clone https://github.com/jinbumlee95/TOS-Korea-Project.git
cd TOS-Korea-Project

# 쿠팡 이용 약관 현재 내용 보기
cat coupang/쿠팡이용약관.md

# 쿠팡 이용 약관 개정 이력 보기
git log -- coupang/쿠팡이용약관.md

# 직전 개정에서 바뀐 내용 보기
git log -p -1 -- coupang/쿠팡이용약관.md

# 회사 하나의 전체 약관 변경 이력 (시간순)
git log -- tving/

# 특정 날짜의 약관 상태
git log --before="2025-01-01" -1 -- coupang/쿠팡이용약관.md

# 전체 약관에서 특정 단어 검색
grep -r "개인정보" .
```

Windows에서 한글 파일명이 깨져 보이면 `git config core.quotepath false`를 설정하세요.

## 구조

```
{회사}/
  {약관명(띄어쓰기 제거)}.md

{게임사}/
  {게임}/
    {약관명(띄어쓰기 제거)}.md
    {약관명(띄어쓰기 제거)}({플랫폼}).md
```

회사·게임 디렉토리는 영문 소문자를 사용합니다 (`coupang`, `naver`, `kakao`, `tving`, `kt`, `krafton/pubg`, `nexon/mabinogimobile`, `riotgames/leagueoflegends` 등). 파일명은 회사가 게시한 약관 제목에서 띄어쓰기를 제거하여 사용합니다. Windows에서 쓸 수 없는 문자(`:` 등)도 제거합니다.

게임사는 게임별로 약관이 따로 있으므로 `{게임사}/{게임}/` 아래에 둡니다. 같은 약관이 플랫폼(Steam, PlayStation 등)별로 따로 게시되면 `{약관명}({플랫폼}).md`로 구분합니다. 플랫폼 구분이 없는 약관은 괄호 없이 저장합니다.

### 쿠팡 (`coupang/`)

| 파일 | 약관 | 출처 |
|------|------|------|
| `쿠팡이용약관.md` | 쿠팡 이용 약관 | https://www.coupang.com/np/policies/terms |
| `상품평및상품문의운영원칙.md` | 상품평 및 상품문의 운영원칙 | https://www.coupang.com/np/policies/product |
| `청소년보호정책.md` | 청소년 보호 정책 | https://www.coupang.com/np/policies/youth |
| `판매이용약관.md` | 판매이용 약관 | https://www.coupang.com/np/policies/seller |
| `멤버십서비스이용약관.md` | 멤버십 서비스 이용 약관 | https://www.coupang.com/np/policies/loyalty |
| `쿠팡서비스이용정책.md` | 쿠팡 서비스 이용 정책 | https://www.coupang.com/np/policies/service |
| `AI이용정책.md` | AI 이용 정책 | https://www.coupang.com/np/policies/ai-policy |
| `취약점공개정책.md` | 취약점 공개 정책 | https://www.coupang.com/np/policies/vdp |
| `쿠팡이츠서비스이용기준.md` | 쿠팡이츠 서비스 이용 기준 | https://web.coupangeats.com/versioned-doc/CUSTOMER_EATS_TNC |
| `쿠팡플레이서비스이용기준.md` | 쿠팡플레이 서비스 이용 기준 | https://web.coupangstreaming.com/tnc/index.html |

### TVING (`tving/`)

| 파일 | 약관 | 출처 |
|------|------|------|
| `TVING이용약관.md` | TVING 이용약관 | https://www.tving.com/policy/terms |
| `유료이용약관.md` | 유료이용약관 | https://www.tving.com/policy/pay-terms |
| `포인트이용약관.md` | 포인트 이용약관 | https://www.tving.com/policy/point-terms |
| `E-mail무단수집거부.md` | E-mail 무단수집거부 | https://www.tving.com/policy/email |
| `법적고지.md` | 법적고지 | https://www.tving.com/policy/legal |
| `개인정보처리방침.md` | 개인정보처리방침 | https://www.tving.com/policy/privacy |
| `청소년보호정책.md` | 청소년 보호정책 | https://www.tving.com/policy/youth |

### 크래프톤 PUBG: BATTLEGROUNDS (`krafton/pubg/`)

출처는 모두 `https://pubg.com/ko/clause/{약관}/{플랫폼}/latest` 형식입니다.

| 파일 | 약관 | 플랫폼 |
|------|------|--------|
| `서비스이용약관(Steam).md` | 서비스 이용약관 | Steam |
| `서비스이용약관(EpicGames).md` | 서비스 이용약관 | Epic Games |
| `서비스이용약관(PlayStation).md` | 서비스 이용약관 | PlayStation |
| `서비스이용약관(Xbox).md` | 서비스 이용약관 | Xbox |
| `서비스이용약관(KraftonID웹사이트).md` | 서비스 이용약관 | Krafton ID & 웹사이트 |
| `운영정책(Steam).md` | 운영정책 | Steam |
| `운영정책(EpicGames).md` | 운영정책 | Epic Games |
| `운영정책(PlayStation).md` | 운영정책 | PlayStation |
| `운영정책(Xbox).md` | 운영정책 | Xbox |
| `개인정보처리방침.md` | 개인정보 처리방침 | (구분 없음) |
| `PUBGBattlegrounds모드정책(Steam).md` | PUBG: Battlegrounds 모드 정책 | Steam |
| `PUBGBattlegrounds모드정책(EpicGames).md` | PUBG: Battlegrounds 모드 정책 | Epic Games |

### 넥슨 마비노기 모바일 (`nexon/mabinogimobile/`)

| 파일 | 약관 | 출처 |
|------|------|------|
| `게임운영정책.md` | 마비노기 모바일 게임 운영정책 | https://mabinogimobile.nexon.com/Support/Policy/2753857 |
| `이벤트규약.md` | 마비노기 모바일 이벤트 규약 | https://mabinogimobile.nexon.com/Support/Policy/2726702 |
| `공식홈페이지운영정책.md` | 마비노기 모바일 공식 홈페이지 운영정책 | https://mabinogimobile.nexon.com/Support/Policy/2753118 |
| `크리에이터즈운영정책.md` | 크리에이터즈 운영정책 | https://mabinogimobile.nexon.com/Support/Policy/2755803 |

마비노기 모바일은 게시글 하나를 고쳐 쓰는 방식이라 사이트에 과거 본문이 없습니다. 현행본만 수록하며, 버전일자는 본문 부칙의 가장 최근 시행일입니다.

### KT (`kt/`)

| 파일 | 약관 | 출처 |
|------|------|------|
| `전기통신서비스이용기본약관.md` | 전기통신서비스 이용기본약관 | https://corp.kt.com/html/etc/agreement_01.html |
| `KT회원이용약관.md` | KT 회원 이용약관 | https://corp.kt.com/html/etc/agreement_02.html |
| `위치정보사업이용약관.md` | 위치정보사업 이용약관 | https://corp.kt.com/html/etc/agreement_07.html |
| `위치기반서비스이용약관.md` | 위치기반서비스 이용약관 | https://corp.kt.com/html/etc/agreement_07.html |
| `법적고지.md` | 법적고지 | https://corp.kt.com/html/etc/legal.html |
| `청소년보호정책.md` | 청소년보호정책 | https://corp.kt.com/html/etc/agreement_05.html |
| `신용정보조회동의서.md` | 신용정보조회 동의서 | https://corp.kt.com/html/etc/agreement_06.html |
| `개인정보처리방침.md` | 개인정보 처리방침 | https://inside.kt.com/html/privacycenter/privacy102.html |
| `아동을위한개인정보처리방침.md` | 아동을 위한 개인정보 처리방침 | https://inside.kt.com/html/privacycenter/privacy103.html |

- 버전일자는 일반 약관은 사이트 게시일, 위치정보·개인정보 약관은 시행일입니다.
- 과거 본문이 HTML로 제공되는 개인정보 처리방침은 2024-12-19부터 모든 버전을 수록했습니다. 그 이전 개인정보 처리방침과 위치정보 약관의 과거 버전, 개인/기업 상품 이용약관은 PDF로만 제공되어 아직 수록하지 않았습니다.
- 위치정보 약관 페이지의 신구조문 대비표·비교표는 약관 본문이 아니므로 제외했습니다. 별표는 포함합니다.

### 라이엇게임즈 (`riotgames/`)

[라이엇 게임즈 법률 문서](https://legal.kr.riotgames.com/) 사이트의 문서 전체입니다. 회사 공통 문서(서비스 약관, 개인정보 처리방침, 계정운영 정책, 가입·환불·미성년자·게스트 계정 등 동의서)는 `riotgames/` 바로 아래에, 게임·서비스별 문서는 아래 폴더에 둡니다. 파일명에서는 게임·서비스 이름 접두어를 뺍니다.

| 폴더 | 게임·서비스 | 문서 |
|------|-------------|------|
| `leagueoflegends/` | 리그 오브 레전드 | 운영정책, 가상재화정책, 소환사의규율, 계약관련필수고지사항 |
| `valorant/` | 발로란트 | 운영정책, 가상재화정책, 계약관련필수고지사항, My Card 동의서 |
| `wildrift/` | 리그 오브 레전드: 와일드 리프트 | 운영정책, 가상재화정책, 계약관련필수고지사항 |
| `legendsofruneterra/` | 레전드 오브 룬테라 | 운영정책, 가상재화정책, 계약관련필수고지사항 |
| `2xko/` | 2XKO | 운영정책, 가상재화정책, 계약관련필수고지사항 |
| `riftbound/` | 리프트바운드 | PC방 파트너 스토어 서비스약관·개인정보처리방침·개인정보 연계·이용 동의 |
| `pcbang/` | 프리미엄 PC방 | 서비스약관, 개인정보처리방침, 계약관련필수고지사항, 동의서류 |

- 버전일자는 사이트 버전 목록에 표시되는 게시일입니다. 운영정책처럼 게시 후 일정 기간 뒤에 시행되는 문서는 `시행일자`가 따로 적혀 있습니다.
- 과거 버전은 사이트가 제공하는 모든 버전을 수록했습니다 (예: 리그 오브 레전드 운영정책 2012년부터 20개, 개인정보 처리방침 2011년부터 32개).
- 게시일이 없는 동의서류는 수집일자로 커밋했습니다.

### 네이버 (`naver/`)

| 파일 | 약관 | 버전 수 | 출처 |
|------|------|---------|------|
| `네이버이용약관.md` | 네이버 이용약관 | 11 (2006~) | https://policy.naver.com/policy/service.html |
| `네이버유료서비스이용약관.md` | 네이버 유료서비스 이용약관 | 19 (2008~) | https://policy.naver.com/policy/service_paid.html |
| `네이버위치기반서비스이용약관.md` | 네이버 위치기반서비스 이용약관 | 8 (2010~) | https://policy.naver.com/policy/service_location.html |
| `네이버게시물운영정책.md` | 네이버 게시물 운영정책 | 1 | https://policy.naver.com/policy/service_group.html |
| `네이버계정운영정책.md` | 네이버 계정 운영정책 | 1 | https://policy.naver.com/policy/service_group2.html |
| `네이버개인정보처리방침.md` | 네이버 개인정보 처리방침 | 79 (2006~) | https://policy.naver.com/policy/privacy.html |
| `네이버청소년보호정책.md` | 네이버 청소년보호정책 | 1 | https://policy.naver.com/policy/youthpolicy.html |
| `네이버스팸메일정책.md` | 네이버 스팸메일정책 | 1 | https://policy.naver.com/policy/spamcheck.html |
| `네이버책임의한계와법적고지.md` | 네이버 책임의 한계와 법적고지 | 1 | https://policy.naver.com/policy/disclaimer.html |
| `네이버검색결과수집에대한정책.md` | 네이버 검색결과 수집에 대한 정책 | 1 | https://policy.naver.com/policy/search_policy.html |

- 과거 버전은 각 페이지의 "이전 ○○ 보기" 링크를 끝까지 따라가 모았습니다.
- 버전일자는 다음 순서로 정했습니다.
  1. 새 버전 페이지의 "이전 보기" 링크에 적힌 적용 시작일
  2. 페이지의 시행일자
  3. 그 버전이 대체한 이전 페이지 이름의 교체일
  4. 본문의 "…부터 적용" 문구
- 개인정보 처리방침의 가장 오래된 두 버전(Ver.1.7, 1.8)은 날짜 단서가 없어 수록하지 않았습니다.
- 이메일주소 무단수집 거부 페이지는 본문 없이 공지사항으로 넘어가서 제외했습니다.
- 정보보호 인증·SOC 인증 페이지는 약관이 아니라 제외했습니다.
- 날짜가 없는 청소년보호정책·법적고지·검색결과 수집 정책은 수집일자로 커밋했습니다.

### 카카오 (`kakao/`)

| 파일 | 약관 | 버전 수 | 출처 |
|------|------|---------|------|
| `카카오계정약관.md` | 카카오계정 약관 | 11 (2019~) | https://www.kakao.com/policy/terms?type=a&lang=ko |
| `카카오통합서비스약관.md` | 카카오 통합서비스약관 | 12 (2019~) | https://www.kakao.com/policy/terms?type=ts&lang=ko |
| `카카오서비스약관.md` | 카카오 서비스 약관 | 18 (2019~) | https://www.kakao.com/policy/kakaoTerms?type=s&version=simple&lang=ko |
| `카카오위치정보이용약관.md` | 카카오 위치정보 이용약관 | 12 (2019~) | https://www.kakao.com/policy/location?lang=ko |
| `카카오개인정보처리방침.md` | 카카오 개인정보 처리방침 | 73 (2024~) | https://www.kakao.com/policy/privacy?type=p&lang=ko |
| `카카오운영정책.md` | 카카오 운영정책 | 1 | https://www.kakao.com/policy/oppolicy?lang=ko |
| `카카오청소년보호정책.md` | 카카오 청소년보호정책 | 1 | https://www.kakao.com/policy/safeguard?lang=ko |
| `카카오권리침해신고안내.md` | 카카오 권리침해신고안내 | 1 | https://www.kakao.com/policy/right?lang=ko |

- **과거 버전:**
  - 약관은 각 페이지의 "변경 전 ○○ 보기" 링크를 끝까지 따라가 모았습니다.
  - 개인정보 처리방침은 과거 버전 목록 페이지를 따라 모았습니다. 사이트가 ver.94(2024-02-01)부터만 제공합니다.
- **버전일자:** 각 페이지의 시행일자입니다.
- **날짜 없는 문서:** 운영정책·청소년보호정책·권리침해신고안내는 버전 정보와 날짜가 없어 수집일자로 커밋했습니다.

## 메타데이터 (YAML Frontmatter)

```yaml
---
제목: 쿠팡 이용 약관
회사: 쿠팡
버전일자: 2026-09-04
시행일자: 2026-09-03
출처: https://www.coupang.com/np/policies/terms
수집일자: 2026-09-28
---
```

| 필드 | 설명 |
|------|------|
| `게임`, `플랫폼` | 게임사 약관에만 있음. 플랫폼 구분이 없는 약관은 `플랫폼` 생략 |
| `버전일자` | 사이트의 버전 목록("다른 버전 보기", "이전 버전 보기", 날짜 선택)에 표시된 날짜. 버전 목록이 없으면 본문에 적힌 게시일, 그것도 없으면 `null` |
| `시행일자` | 본문(부칙 등)에 명시된 시행일. 본문에 없거나 버전일자와 60일 이상 차이 나면 생략 |
| `출처` | 수집한 원문 페이지 |
| `수집일자` | 수집한 날짜 |

## 커밋

약관 커밋은 버전일자(정오, KST)를 Git author/committer date로 사용합니다. 커밋 메시지 형식:

```
쿠팡: 쿠팡 이용 약관 (개정)

원문: https://www.coupang.com/np/policies/terms

버전일자: 2026-09-04
시행일자: 2026-09-03
회사: 쿠팡
수집일자: 2026-09-28
```

개정 구분:
- `최초 수록`: 저장소에 처음 추가된 버전 (회사가 공개한 가장 오래된 버전이며, 실제 제정본이 아닐 수 있음)
- `개정`: 직전 버전과 본문이 다름
- `버전 갱신, 본문 동일`: 새 버전이 게시되었으나 본문은 같음 (파일 변경이 없으면 빈 커밋으로 기록)

같은 날짜에 여러 커밋이 있으면 순서를 지키기 위해 12:00:00, 12:00:01, … 처럼 초 단위를 늘립니다. 사이트 목록에 같은 날짜가 두 번 나오는 경우(예: TVING 이용약관 2020-01-30) 목록에서 아래에 있는 것을 먼저, 위에 있는 것을 "같은 날짜의 두 번째 버전"으로 커밋합니다.

버전 정보가 없는 약관은 본문의 게시일(TVING E-mail 무단수집거부: 2010-04-06)로, 그것도 없으면(쿠팡 AI 이용 정책·취약점 공개 정책, TVING 법적고지·청소년 보호정책) 수집일자로 커밋합니다.

### 커밋이 쌓이는 순서

커밋은 **회사 단위로** 추가됩니다. 새 회사를 수록할 때는 그 회사의 과거 버전을 날짜순으로 기존 히스토리 위에 쌓고, 이미 수록된 회사를 다시 수집했을 때는 새로 나온 버전만 쌓습니다. 기존 커밋은 다시 쓰지 않으므로(force-push 없음) 커밋 해시가 바뀌지 않습니다.

그래서 회사 안에서는 커밋이 시간순이지만, 저장소 전체로 보면 회사가 추가된 순서대로 묶여 있습니다. 예를 들어 전체 `git log`에서는 나중에 수록한 회사의 2010년 커밋이 먼저 수록한 회사의 2026년 커밋보다 위에 나옵니다.

- 이력을 볼 때는 `git log -- {회사}/` 또는 `git log -- {회사}/{약관}.md`처럼 **경로를 지정**하세요. 이렇게 보면 항상 시간순입니다.
- 경로 없이 저장소 전체에 `--since`를 쓰면 git이 오래된 커밋에서 탐색을 일찍 멈춰 일부 커밋이 빠질 수 있습니다. 날짜로 거를 때도 경로를 지정하세요.
- 파일을 바꾸지 않은 빈 커밋(`버전 갱신, 본문 동일`)은 경로를 지정한 `git log`에 나오지 않습니다. 모두 보려면 `git log --grep="TVING:"`처럼 커밋 메시지로 찾으세요.

## 권리 고지 및 이용 조건

### 운영 목적

- 이 저장소는 **영리를 목적으로 하지 않습니다.** 광고, 판매, 유료 제공, 상업적 서비스에 쓰지 않습니다.
- 목적은 두 가지뿐입니다.
  - **저장:** 각 기업이 공개한 약관·정책이 언제 어떻게 바뀌었는지 기록으로 남깁니다.
  - **비교 제공:** 버전 간 차이를 누구나 확인할 수 있게 합니다.

### 권리 귀속

- 수록된 모든 이용약관, 운영정책, 개인정보 처리방침 등 약관·정책 문서의 **저작권과 그 밖의 모든 권리는 해당 문서를 작성·게시한 각 기업에 있습니다.**
- 저장소 관리자는 수록 문서에 대해 어떠한 권리도 주장하지 않습니다.
- 저장소 안의 다른 요소(README, 폴더 구조, 메타데이터, 커밋 메시지 등)에 어떤 조건이 붙더라도, 수록 문서에 대한 권리나 이용 허락으로 해석되지 않습니다.
- 회사명, 서비스명, 상표는 각 기업의 것입니다. 이 저장소는 어떤 기업과도 제휴하거나 승인받지 않았습니다.

### 정본과 정확성

- 효력을 가지는 **정본은 각 기업의 공식 페이지에 게시된 문서**입니다. 문서마다 frontmatter의 `출처`에 원문 주소를 적어 두었습니다.
- 이 저장소의 문서는 공개 페이지를 수집해 Markdown으로 변환한 사본입니다.
  - 제목(`#`), 장(`##`), 조 또는 번호 절(`###`) 외의 서식은 단순화했습니다.
  - 변환 과정에서 서식이나 내용이 원문과 다를 수 있습니다.
  - 버전일자·시행일자는 수집 시점에 사이트에 표시된 정보를 바탕으로 정했습니다.
- 이 저장소의 내용은 **법적 판단이나 권리 행사의 근거로 쓸 수 없습니다.** 계약 관계와 효력은 반드시 각 기업의 공식 문서로 확인하세요.

### 수집 방식

- 로그인 없이 누구나 볼 수 있게 공개된 페이지만 수집했습니다.
- 페이지당 한 번씩, 서버에 부담을 주지 않는 수준으로 요청했습니다.

### 이용 조건

- 이 저장소를 열람하고 비교하는 것은 **비영리·참고 목적**으로만 해 주세요.
- 수록 문서를 복제·배포하거나 그 밖의 방법으로 이용하려면 해당 기업의 권리와 조건을 따라야 합니다.

### 삭제 요청

- 권리자인 기업이 수록 중단이나 삭제를 요청하면 **지체 없이 해당 문서를 삭제**합니다.
- 요청은 이 저장소의 [GitHub Issues](https://github.com/jinbumlee95/TOS-Korea-Project/issues)로 보내 주세요.
