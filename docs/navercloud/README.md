# 네이버 클라우드 플랫폼 ([`navercloud/`](../../navercloud/))

[네이버 클라우드 플랫폼 정책](https://www.ncloud.com/policy/terms/svc) 페이지의 서비스 이용약관, 서비스 수준 협약(SLA), 개인정보처리방침 전체입니다.

## 수집 방식

- **공개 API:** 사이트가 쓰는 공개 API로 문서 목록과 판 이력을 받았습니다.
  - 문서 목록: `/api/provisions/categories/{TERMS|SLA|INFOU}?countryCode=KR`
  - 판 정보: `/api/provisions/{코드}-{분류}-KR-{판}`
- **본문:** 판마다 원문 PDF를 받아 텍스트로 바꿨습니다.
- **판 이력:** 사이트의 "이전 버전" 버튼과 같은 정보이며, 1판부터 현행판까지 모두 수록했습니다.
- **버전일자:** API의 적용일(`applyYmd`)입니다.
- **판마다 남긴 값:** frontmatter에 판 번호(`판`)와 원문 PDF 주소(`원문PDF`)를 적었습니다.
- **본문 변환:** PDF에서 뽑은 글자를 **그대로** 두었습니다. 바꾼 것은 세 가지뿐입니다.
  - PDF 폭 때문에 끊긴 줄을 이어 붙임
  - 장·조 제목 표시
  - 쪽 번호(`1 / 15` 형식) 줄 제거

  모든 판에서 공백을 뺀 글자가 PDF와 일치하는지 대조했습니다. 다만 표는 행 단위 텍스트로 풀려 있어서, 정확한 표 모양은 원문 PDF로 확인하세요.

## 네이버 클라우드 플랫폼 회신 (2026년 9월)

수록 방식에 대해 네이버 클라우드 플랫폼에 문의했고, 다음과 같이 회신받았습니다.

> 1. 안타깝지만 이전 버전의 서비스 이용 약관은 제공하지 않습니다. 현재 버전만 제공합니다.
> 2. 서비스 이용 약관은 홈페이지에서 PDF로 다운로드가 가능하고 고객님께서 보관하셔도 됩니다.
> 3. 서비스 이용 약관 변경시에는 홈페이지 공지사항을 통해 안내 드리고 있습니다.
> 4. 서비스 이용 약관에 대해서는 API는 제공하지 않습니다. 홈페이지에서 직접 확인 및 다운로드를 부탁드립니다.
> 5. 공개된 약관으로서 이용을 하셔도 문제는 없으나 수정을 하시거나 약관에 대한 잘못된 정보를 제공하는 부분은 없으셔야 합니다.

이 회신에 따라 다음과 같이 운영합니다.

- **5번 (수정·잘못된 정보 금지):** 본문은 PDF의 글자를 바꾸지 않고, 판마다 원문 PDF 주소를 남깁니다. 아래 사이트 데이터 오류로 다른 문서가 연결된 판은 이력에서 뺐습니다.
- **1·4번:** 회신과 달리 약관 페이지에는 "이전 버전" 버튼이 있고, 페이지가 쓰는 공개 API로 과거 판을 조회할 수 있습니다. 이 저장소의 과거 판은 이렇게 공개된 페이지·API에서 받은 것이며, 공식 제공 API를 쓴 것은 아닙니다.

## 사이트 데이터 오류로 제외한 판

API가 가리키는 PDF가 해당 문서가 아닌 판은 이력에서 뺐습니다. 원문 PDF를 직접 확인해 판단했습니다.

| 판 | 제외 사유 |
|----|-----------|
| 서비스 이용약관 9판 (2017-04-13) | '네이버 클라우드 BIZ 개인정보처리방침' PDF가 연결되어 있음 |
| ARC eye 서비스 이용약관 2판 (적용일 없음) | 'ARC eye 매핑 장비 대여 서비스 이용 안내' PDF가 연결되어 있음 (`privacy/ARCeye매핑장비대여서비스이용안내.md`와 같은 문서) |
| Ncloud Kubernetes Security 서비스 이용약관 1판 (2026-08-18) | Web Security Checker 이용약관 4판과 같은 PDF가 연결되어 있음. 이 판이 유일한 판이라 문서 자체를 수록하지 않음. 회사 확인(2026년 10월): Ncloud Kubernetes Service의 중복 및 잘못된 노출, 수정 예정 |
| Web Security Checker 서비스 이용약관 1판 (2017-08-30) | System Security Checker 이용약관 1판과 같은 PDF가 연결되어 있음. 회사 확인(2026년 10월): 잘못된 업로드, 제거 예정 |

### 오류 제보와 회신 (2026년 10월)

위 표의 Web Security Checker·Ncloud Kubernetes Security 건을 네이버 클라우드 플랫폼에 제보했고, 다음과 같이 회신받았습니다.

> 1. Web Security Checker 최초 이용약관이 System Security Checker 노출이 되는 상황
>    - 잘못된 업로드가 확인되어 해당 약관은 제거가 될 예정입니다.
> 2. Ncloud Kubernetes Security 이용약관
>    - Ncloud Kubernetes Service 의 중복 및 잘못된 노출로 확인되어 수정예정입니다.

- 두 건 모두 사이트 데이터 오류로 확인되었으므로, 이 저장소에서 해당 판을 뺀 처리를 유지합니다.
- 회신 시점에는 사이트 수정이 끝나지 않았습니다. 수정이 반영되면 다시 수집해 이 표와 수록 문서를 갱신합니다.

## 그 밖의 참고

- **같은 이름의 두 문서:** "Simple & Easy Notification Service 서비스 이용약관"은 사이트에 문서 코드 두 개(`NOTIF` 6판, `SENST` 7판)로 따로 있습니다. 6판까지 내용이 같습니다. 파일명 뒤에 코드를 붙여 구분했습니다.
- **판마다 바뀐 이름:** 문서 이름이 판마다 바뀐 경우(예: 서비스 이용약관 1판은 "서비스 이용약관")에는 최신판의 이름을 파일명으로 씁니다. 판별 이름은 frontmatter의 `제목`에 있습니다.
- **날짜 없는 문서:** 적용일이 없는 문서(ARC eye 매핑 장비 대여 안내, ARC eye 개인정보 수집 동의서)는 수집일자로 커밋했습니다. ARC eye 개인정보 수집 동의서는 적용일 없는 판이 둘이라 최신판만 수록했습니다.
- **판 번호·적용일은 그대로인데 본문이 바뀐 판:** CLOVA Chatbot 서비스 이용약관 7판은 사이트 판 목록의 적용일이 2024-10-29(`apply_ymd`)입니다. 그런데 2026-09-29에 받은 PDF의 부칙은 "본 약관은 2026 년 9 월 17 일부터 적용됩니다"이고, PDF 파일명의 타임스탬프는 2026-08-31입니다. 새 판을 추가하지 않고 7판의 PDF를 새 개정본으로 바꾼 것으로 보입니다. 2024-10-29 당시 7판 PDF는 받아 둔 적이 없어 무엇이 바뀌었는지는 확인할 수 없습니다.
  - 수록은 사이트 판 목록을 따라 버전일자 2024-10-29로 두었습니다. 본문 시행일(2026-09-17)은 버전일자와 60일 넘게 차이 나므로 `시행일자` 규칙에 따라 적지 않았습니다.
  - 이 문서의 2024-10-29 버전 본문은 실제로는 2026-09-17 적용본일 수 있습니다. 사업자 제보·회신은 아직 없습니다.

### 서비스 이용약관 (`terms/`)

52개 문서

| 파일 | 문서 | 판 수 |
|------|------|-------|
| `AiTEMS서비스이용약관.md` | AiTEMS 서비스 이용약관 | 1 (2021-11-25) |
| `AI·NaverAPI서비스이용약관.md` | AI·Naver API 서비스 이용약관 | 5 (2019~) |
| `APIGateWay서비스이용약관.md` | API GateWay 서비스 이용약관 | 2 (2017~) |
| `AppSecurityChecker서비스이용약관.md` | App Security Checker 서비스 이용약관 | 3 (2017~) |
| `ARCbrain서비스이용약관.md` | ARC brain 서비스 이용약관 | 1 (2024-10-17) |
| `ARCeye서비스이용약관.md` | ARC eye 서비스 이용약관 | 2 (2024~) |
| `CertificateManager서비스이용약관.md` | Certificate Manager 서비스 이용약관 | 1 (2025-11-20) |
| `CloudDataBox서비스이용약관.md` | Cloud Data Box 서비스 이용약관 | 1 (2022-02-17) |
| `CloudFunctions서비스이용약관.md` | Cloud Functions 서비스 이용약관 | 3 (2018~) |
| `CloudSecurityWatcher서비스이용약관.md` | Cloud Security Watcher 서비스이용약관 | 1 (2024-03-21) |
| `CLOVAAiCall서비스이용약관.md` | CLOVA AiCall 서비스 이용약관  | 3 (2020~) |
| `CLOVAChatbot서비스이용약관.md` | CLOVA Chatbot 서비스 이용약관 | 7 (2018~) |
| `CLOVADubbing서비스이용약관.md` | CLOVA Dubbing 서비스 이용약관  | 2 (2020~) |
| `CLOVAGreenEye서비스이용약관.md` | CLOVA GreenEye 서비스 이용약관 | 1 (2022-12-15) |
| `CLOVAOCR서비스이용약관.md` | CLOVA OCR 서비스 이용약관 | 4 (2019~) |
| `CLOVASpeech서비스이용약관.md` | CLOVA Speech 서비스 이용약관  | 1 (2020-11-18) |
| `CLOVAStudio서비스이용약관.md` | CLOVA Studio 서비스 이용약관 | 1 (2025-07-17) |
| `DataCatalog서비스이용약관.md` | Data Catalog 서비스 이용약관 | 1 (2022-12-16) |
| `Datafence서비스이용약관.md` | Datafence 서비스 이용약관 | 1 (2024-10-17) |
| `DataFlow서비스이용약관.md` | Data Flow 서비스 이용약관 | 1 (2023-11-23) |
| `DataForest서비스이용약관.md` | Data Forest 서비스 이용약관 | 1 (2021-05-27) |
| `DataStream서비스이용약관.md` | Data Stream 서비스 이용약관 | 1 (2025-09-18) |
| `DataTeleporter서비스이용약관.md` | Data Teleporter 서비스 이용약관 | 2 (2018~) |
| `DB&ServerAccessControl서비스이용약관.md` | DB & Server Access Control 서비스 이용약관 | 1 (2025-07-17) |
| `FileSafer서비스이용약관.md` | File Safer 서비스 이용약관 | 3 (2017~) |
| `GDPRDPA.md` | GDPR DPA | 2 (2021~) |
| `GeoLocation서비스이용약관.md` | GeoLocation 서비스 이용약관 | 3 (2017~) |
| `GlobalCDN서비스이용약관.md` | Global CDN 서비스 이용약관 | 1 (2026-01-22) |
| `GlobalEdge서비스이용약관.md` | Global Edge 서비스 이용약관 | 1 (2026-01-22) |
| `IPsecVPNRental서비스이용약관.md` | IPsec VPN Rental 서비스 이용약관 | 1 (2025-04-17) |
| `Maps서비스이용약관.md` | Maps 서비스 이용약관 | 1 (2025-03-20) |
| `MediaIntelligence서비스이용약관.md` | Media Intelligence 서비스 이용약관 | 2 (2025~) |
| `MLexpertPlatform서비스이용약관.md` | ML expert Platform 서비스 이용약관 | 1 (2025-08-25) |
| `NcloudChat서비스이용약관.md` | Ncloud Chat 서비스 이용약관 | 1 (2022-04-21) |
| `NcloudKubernetesService서비스이용약관.md` | Ncloud Kubernetes Service 서비스 이용약관 | 2 (2019~) |
| `NCLUE서비스이용약관.md` | NCLUE 서비스 이용약관  | 1 (2024-10-17) |
| `NIMORO서비스이용약관.md` | NIMORO 서비스 이용약관 | 1 (2024-11-21) |
| `PapagoTranslation서비스이용약관.md` | Papago Translation 서비스 이용약관 | 1 (2026-01-22) |
| `RAG서비스이용약관.md` | RAG 서비스 이용약관 | 1 (2025-07-17) |
| `RealUserAnalytics(RUA)서비스이용약관.md` | Real User Analytics(RUA) 서비스 이용약관 | 2 (2017~) |
| `SecurityMonitoring서비스이용약관.md` | Security Monitoring 서비스 이용약관 | 5 (2017~) |
| `Simple&EasyNotificationService서비스이용약관(NOTIF).md` | Simple & Easy Notification Service 서비스 이용약관 | 6 (2017~) |
| `Simple&EasyNotificationService서비스이용약관(SENST).md` | Simple & Easy Notification Service 서비스 이용약관 | 7 (2017~) |
| `SourceBand서비스이용약관.md` | SourceBand 서비스 이용약관 | 1 (2023-05-25) |
| `SystemSecurityChecker서비스이용약관.md` | System Security Checker 서비스 이용약관 | 4 (2017~) |
| `WebSecurityChecker서비스이용약관.md` | Web Security Checker 서비스 이용약관 | 3 (2017~) |
| `WebshellBehaviorDetector서비스이용약관.md` | Webshell Behavior Detector 서비스 이용약관  | 1 (2020-11-18) |
| `개인정보수집및이용에대한안내.md` | 개인정보 수집 및 이용에 대한 안내 | 15 (2019~) |
| `네이버웍스이용약관.md` | 네이버웍스 이용약관 | 1 (2024-06-04) |
| `네이버클라우드플랫폼서비스이용약관.md` | 네이버 클라우드 플랫폼 서비스 이용약관 | 23 (2013~) |
| `위치기반서비스이용약관.md` | 위치기반서비스 이용약관 | 9 (2019~) |
| `제3자제공솔루션이용약관.md` | 제3자 제공 솔루션 이용 약관 | 4 (2018~) |

### 서비스 수준 협약(SLA) (`sla/`)

77개 문서

| 파일 | 문서 | 판 수 |
|------|------|-------|
| `AiTEMS서비스수준협약.md` | AiTEMS 서비스 수준 협약 | 1 (2021-11-25) |
| `APIGateway서비스수준협약.md` | API Gateway 서비스 수준 협약 | 1 (2019-12-30) |
| `AppSafer서비스수준협약.md` | App Safer 서비스 수준 협약 | 1 (2019-12-30) |
| `ARCeye서비스수준협약.md` | ARC eye 서비스 수준 협약 | 1 (2022-10-20) |
| `Backup서비스수준협약.md` | Backup 서비스 수준 협약 | 1 (2019-12-30) |
| `BlockStorage서비스수준협약.md` | Block Storage 서비스 수준 협약 | 1 (2025-02-20) |
| `CAPTCHA서비스수준협약.md` | CAPTCHA 서비스 수준 협약 | 1 (2019-12-30) |
| `CloudConnect서비스수준협약.md` | Cloud Connect 서비스 수준 협약 | 1 (2019-12-30) |
| `CloudDataStreamingService서비스수준협약.md` | Cloud Data Streaming Service 서비스 수준 협약 | 1 (2020-09-17) |
| `CloudDBforCache서비스수준협약.md` | Cloud DB for Cache 서비스 수준 협약 | 1 (2025-06-19) |
| `CloudDBforMongoDB서비스수준협약.md` | Cloud DB for MongoDB 서비스 수준 협약 | 1 (2023-11-23) |
| `CloudDBforMSSQL서비스수준협약.md` | Cloud DB for MSSQL 서비스 수준 협약 | 1 (2023-11-23) |
| `CloudDBforMySQL서비스수준협약.md` | Cloud DB for MySQL 서비스 수준 협약 | 1 (2023-11-23) |
| `CloudDBforPostgreSQL서비스수준협약.md` | Cloud DB for PostgreSQL 서비스 수준 협약 | 1 (2023-11-23) |
| `CloudDBServerless서비스수준협약.md` | Cloud DB Serverless 서비스 수준 협약 | 1 (2026-05-14) |
| `CloudFunctions서비스수준협약.md` | Cloud Functions 서비스 수준 협약 | 1 (2019-12-30) |
| `CloudHadoop서비스수준협약.md` | Cloud Hadoop 서비스 수준 협약 | 1 (2019-12-30) |
| `CloudSearch서비스수준협약.md` | Cloud Search 서비스 수준 협약 | 1 (2019-12-30) |
| `CLOVAAiCall서비스수준협약.md` | CLOVA AiCall 서비스 수준 협약  | 1 (2020-11-18) |
| `CLOVAChatbot서비스수준협약.md` | CLOVA Chatbot 서비스 수준 협약 | 2 (2019~) |
| `CLOVADubbing서비스수준협약.md` | CLOVA Dubbing 서비스 수준 협약 | 2 (2020~) |
| `CLOVAFaceRecognition서비스수준협약.md` | CLOVA Face Recognition 서비스 수준 협약 | 2 (2019~) |
| `CLOVAFaceSign서비스수준협약.md` | CLOVA FaceSign 서비스 수준 협약 | 1 (2021-07-22) |
| `CLOVAOCR서비스수준협약.md` | CLOVA OCR 서비스 수준 협약 | 2 (2020~) |
| `CLOVASpeechRecognition서비스수준협약.md` | CLOVA Speech Recognition 서비스 수준 협약 | 2 (2019~) |
| `CLOVASpeechSynthesis서비스수준협약.md` | CLOVA Speech Synthesis 서비스 수준 협약 | 2 (2019~) |
| `CLOVASpeech서비스수준협약.md` | CLOVA Speech 서비스 수준 협약  | 1 (2020-11-18) |
| `DataCatalog서비스수준협약.md` | Data Catalog 서비스 수준 협약 | 1 (2022-12-16) |
| `DataFlow서비스수준협약.md` |  Data Flow 서비스 수준 협약 | 1 (2023-11-23) |
| `DataForest서비스수준협약.md` | Data Forest 서비스 수준 협약 | 1 (2021-05-27) |
| `DataQuery서비스수준협약.md` | Data Query 서비스 수준 협약 | 1 (2024-06-20) |
| `DataStream서비스수준협약.md` | Data Stream 서비스 수준 협약 | 1 (2025-09-18) |
| `EffectiveLogSearch&Analytics서비스수준협약.md` | Effective Log Search & Analytics 서비스 수준 협약 | 1 (2019-12-30) |
| `FileSafer서비스수준협약.md` | File Safer 서비스 수준 협약 | 1 (2019-12-30) |
| `FileStorage서비스수준협약.md` | File Storage 서비스 수준 협약 | 1 (2019-12-30) |
| `Game서비스수준협약.md` | Game 서비스 수준 협약 | 1 (2021-01-21) |
| `GeoLocation서비스수준협약.md` | GeoLocation 서비스 수준 협약 | 1 (2019-12-30) |
| `GlobalCDN서비스수준협약.md` | Global CDN 서비스 수준 협약 | 1 (2019-12-30) |
| `GlobalEdge서비스수준협약.md` | Global Edge 서비스 수준 협약 | 1 (2022-11-29) |
| `GlobalRouteManager서비스수준협약.md` | Global Route Manager 서비스 수준 협약 | 1 (2019-12-30) |
| `HEaaNHomomorphicAnalytics서비스수준협약.md` | HEaaN Homomorphic Analytics 서비스 수준 협약 | 1 (2021-09-16) |
| `ImageOptimizer서비스수준협약.md` | Image Optimizer 서비스 수준 협약 | 1 (2019-12-30) |
| `IPsecVPN서비스수준협약.md` | IPsec VPN 서비스 수준 협약 | 1 (2019-12-30) |
| `KeyManagementService서비스수준협약.md` | Key Management Service 서비스 수준 협약 | 1 (2019-12-30) |
| `LiveStation서비스수준협약.md` | Live Station 서비스 수준 협약 | 1 (2019-12-30) |
| `LoadBalancer서비스수준협약.md` | Load Balancer 서비스 수준 협약 | 1 (2019-12-30) |
| `Maps서비스수준협약.md` | Maps 서비스 수준 협약 | 1 (2019-12-30) |
| `MediaConnectCenter서비스수준협약.md` | Media Connect Center 서비스 수준 협약 | 1 (2021-11-25) |
| `MediaIntelligence서비스수준협약.md` | Media Intelligence 서비스 수준 협약 | 1 (2025-11-20) |
| `NAS서비스수준협약.md` | NAS 서비스 수준 협약 | 1 (2019-12-30) |
| `NATGateway서비스수준협약.md` | NAT Gateway 서비스 수준 협약 | 1 (2019-12-30) |
| `NcloudChat서비스수준협약.md` | Ncloud Chat 서비스 수준 협약 | 1 (2022-04-21) |
| `NcloudKubernetesService서비스수준협약.md` | Ncloud Kubernetes Service 서비스 수준 협약 | 1 (2023-11-23) |
| `NcloudPoseEstimation서비스수준협약.md` | Ncloud Pose Estimation 서비스 수준 협약 | 1 (2019-12-30) |
| `ObjectDetection서비스수준협약.md` | Object Detection 서비스 수준 협약 | 1 (2019-12-30) |
| `ObjectStorage서비스수준협약.md` | Object Storage 서비스 수준 협약 | 2 (2019~) |
| `PapagoTranslation서비스수준협약.md` | Papago Translation 서비스 수준 협약 | 2 (2019~) |
| `PinpointCloud서비스수준협약.md` | Pinpoint Cloud 서비스 수준 협약 | 1 (2020-07-16) |
| `PrivateCA서비스수준협약.md` | Private CA 서비스 수준 협약 | 1 (2020-09-01) |
| `RealUserAnalytics서비스수준협약.md` | Real User Analytics 서비스 수준 협약 | 1 (2019-12-30) |
| `SearchEngineService서비스수준협약.md` | Search Engine Service 서비스 수준 협약 | 2 (2019~) |
| `SecureZoneFirewall서비스수준협약.md` | Secure Zone Firewall 서비스 수준 협약 | 1 (2019-12-30) |
| `SecurityMonitoring서비스수준협약.md` | Security Monitoring 서비스 수준 협약 | 2 (2019~) |
| `Server서비스수준협약.md` | Server 서비스 수준 협약 | 1 (2025-02-20) |
| `Simple&EasyNotificationService서비스수준협약.md` | Simple & Easy Notification Service 서비스 수준 협약 | 1 (2025-03-20) |
| `SourceBand서비스수준협약.md` | SourceBand 서비스 수준 협약 | 1 (2023-05-25) |
| `SourceBuild서비스수준협약.md` | Source Build 서비스 수준 협약 | 1 (2019-12-30) |
| `SourceCommit서비스수준협약.md` | Source Commit 서비스 수준 협약 | 1 (2019-12-30) |
| `SourcePipeline서비스수준협약.md` | Source Pipeline 서비스 수준 협약 | 1 (2019-12-30) |
| `SSLVPN서비스수준협약.md` | SSL VPN 서비스 수준 협약 | 1 (2019-12-30) |
| `VMwareonNcloud서비스수준협약.md` | VMware on Ncloud 서비스 수준 협약 | 1 (2019-12-30) |
| `VODStation서비스수준협약.md` | VOD Station 서비스 수준 협약 | 1 (2020-02-12) |
| `VODTranscoder서비스수준협약.md` | VOD Transcoder 서비스 수준 협약 | 1 (2019-12-30) |
| `WebServiceMonitoringSystem서비스수준협약.md` | Web Service Monitoring System 서비스 수준 협약 | 1 (2019-12-30) |
| `WebshellBehaviorDetector서비스수준협약.md` | Webshell Behavior Detector 서비스 수준 협약 | 1 (2020-11-18) |
| `WORKBOX서비스수준협약.md` | WORKBOX 서비스 수준 협약 | 1 (2019-12-30) |
| `서비스수준협약(SLA)적용기준.md` | 서비스 수준 협약(SLA) 적용 기준 | 1 (2020-10-15) |

### 개인정보처리방침 (`privacy/`)

3개 문서

| 파일 | 문서 | 판 수 |
|------|------|-------|
| `ARCeye개인정보수집동의서.md` | ARC eye 개인정보 수집 동의서 | 1 (날짜 없음) |
| `ARCeye매핑장비대여서비스이용안내.md` | ARC eye 매핑 장비 대여 서비스 이용 안내 | 1 (날짜 없음) |
| `개인정보처리방침.md` | 개인정보처리방침 | 53 (2013~) |
