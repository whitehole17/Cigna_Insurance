# Cigna Global — RAG 프로젝트 보험사 개요

> SKN24 3차 프로젝트 · 4팀 · 담당: 김은우
> 마지막 수정: 2026-03-31

---

## 1. Cigna 개요

**The Cigna Group**은 1792년 필라델피아에서 설립된 미국계 글로벌 헬스케어 기업으로, 현재 미국 코네티컷주 블루밍턴에 본사를 두고 있다. 국내(미국) 건강보험 사업(Cigna Healthcare)과 약국 혜택 관리 사업(Express Scripts)을 양대 축으로 운영하며, 이 중 **Cigna Global**은 해외 거주 외국인(Expat)을 위한 국제 민간 의료보험 사업 부문이다.

Cigna Global은 **200개국 이상**에서 서비스를 제공하며, **165만 개** 이상의 병원·의원·의사 네트워크를 보유하고 있다. 개인·가족 플랜(Global Health Options)은 Silver / Gold / Platinum 3단계로 구성되며, 기업 단체 플랜은 별도 법인([Cigna Global Health Benefits](https://www.cignaglobalhealth.com))에서 운영한다.

> 출처: [Cigna Global — International Health Plans](https://www.cignaglobal.com/international-health-plans)

---

## 2. 전세계 회원 수

| 구분 | 수치 | 기준 시점 | 비고 |
|------|------|---------|------|
| **The Cigna Group 전체 고객 관계 수** | **1억 8,840만 명** | 2025년 12월 31일 | Express Scripts 약국 고객 포함 |
| **Cigna Global 국제 Expat 회원 수** | **약 70만 명** | — | 제3자 브로커 인용 수치, Cigna 공식 연보에 별도 공시 없음 |

**주의:** The Cigna Group의 1억 8,840만이라는 수치는 미국 내 약국 혜택 관리(Express Scripts) 고객이 대부분을 차지한다. 해외 Expat 특화 보험인 Cigna Global의 순수 개인 국제보험 가입자 수는 약 **70만 명** 수준으로 업계에서 통용되나, Cigna가 공식 연보에 별도 집계하여 공시하지 않는다.

> 출처 1: [The Cigna Group 2025 Full Year Results — PR Newswire (2026.02.05)](https://www.prnewswire.com/news-releases/the-cigna-group-reports-strong-fourth-quarter-and-full-year-2025-results-establishes-2026-outlook-and-increases-dividend-302679556.html)
> 출처 2: [Cigna International — International Citizens Insurance](https://www.internationalinsurance.com/cigna/)

---

## 3. 한국 거주 외국인 관련 현황

### 한국 내 Cigna 가입자 수

**Cigna는 한국 시장 가입자 수를 공개하지 않는다.** 국제 민간 의료보험 가입자 통계는 한국 금융감독원·건강보험공단 모두 별도 집계하지 않아 현재 공신력 있는 수치가 존재하지 않는다. 다만 아래 간접 지표로 시장 규모를 가늠할 수 있다.

### 간접 지표

| 지표 | 수치 | 출처 |
|------|------|------|
| 한국 체류 외국인 총수 (2025) | **278만 명** (인구 대비 5.44%) | [법무부 2024 체류외국인 통계연보](https://www.ekw.co.kr/news/articleView.html?idxno=12302) |
| 미국 국적 체류자 (TRICARE 잠재 대상) | **18만 명 이상** | 법무부 출입국 통계 |
| 외국인 건강보험 가입자 (국민건강보험) | **약 128만 명** (2023년 말) | [공공데이터포털 — 건강보험공단 외국인 통계](https://www.data.go.kr/data/15138933/fileData.do) |
| 외국인 Expat의 국제 민간보험 의존 비율 | 공식 통계 없음 | — |

### 맥락

국민건강보험 의무 가입 대상 외국인(6개월 이상 장기체류자)도 본인 고용주가 제공하는 국제 민간보험과 중복 가입하는 경우가 많다. 특히 다국적 기업 주재원, 외국계 대학 교수·연구원, 외국군(주한미군 TRICARE) 등은 국민건강보험과 별도로 Cigna·Bupa 등 국제 민간보험에 이중으로 가입되어 있는 것이 일반적이다. Cigna Global은 Pacific Prime, AXA 등과 함께 한국 Expat 시장의 주요 국제 민간보험사로 분류된다.

> 출처: [South Korea Health Insurance for Expats — Pacific Prime](https://www.pacificprime.com/country/asia/south-korea-health-insurance-pacific-prime-international/)

---

## 4. 한국 적용 법인 구조

한국 거주 외국인이 Cigna Global 개인 플랜에 가입하면, 법적으로 아래 entity의 관할을 받는다.

| Entity 코드 | 법인명 | 등록지 | 적용 대상 |
|------------|-------|-------|---------|
| **CGIC** | Cigna Global Insurance Company | 건지 섬(Guernsey) | 아시아·글로벌 거주 외국인 (싱가포르 제외). 한국 거주자의 주요 적용 entity로 추정되나 Cigna 공식 문서상 국가별 명시 없음 |
| UKCEIC | UK Cigna Entity | 영국 | UK/EEA 거주자 |
| CEIC | Cigna Europe Insurance Company S.A.-N.V. 싱가포르 지점 | 싱가포르 | 싱가포르 및 일부 아시아 |

URL에서 `/dvc-pdfs/CGIC-EP31/` 형태로 법인 코드가 명시된 문서가 한국 적용 버전이다.

---

## 5. RAG 인덱싱 문서 목록

### 핵심 문서 (필수)

| 문서명 | 설명 | URL |
|-------|------|-----|
| **Customer Guide (최신)** | 보장 항목·한도·청구 절차·카운슬링 조건 전체. RAG의 핵심 소스 | [CGHO Customer Guide EN 0225](https://www.cignaglobal.com/dvc-pdfs/UKCEIC-UKCEICP9/en/CGHO%20Customer%20Guide%20EN%200225.pdf) |
| **Policy Rules CGIC 2024** | 보장 제외 항목, 법적 약관 조건. CGIC 코드 = 한국 적용 법인 명시. "이건 안 된다"는 질문에 필수 | [CGHO Policy Rules CGIC EN 02_2024](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP31/en/CGHO%20Policy%20Rules%20CGIC_EN_02_2024.pdf) |

### 보조 문서 (품질 향상용)

| 문서명 | 설명 | URL |
|-------|------|-----|
| **Benefits Summary (USD)** | Silver·Gold·Platinum 3개 플랜의 보장 금액 비교표 압축본. 표 추출(pdfplumber) Demo 2에 적합 | [Cigna Global Benefits Summary USD](https://www.cignaglobal.com/dvc-pdfs/GENERIC-172/en/591116%20Cigna_Global_International_Health_Plans_Benefits_Summary_USD_EN_0523.pdf) |
| **IPID Silver CGIC 2025** | Silver 플랜 핵심 정보 요약 시트 (Gold·Platinum은 IPID 목록 페이지에서 확인) | [IPID Silver CGIC EN 02_2025](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP35/en/IPID%20-%20Silver%20CGIC%20EN_02_2025.pdf) |
| **IPID 전체 목록** | Gold·Platinum 포함 전체 IPID 문서 목록 | [Insurance Product Information Documents](https://www.cignaglobal.com/individuals-families/members/resources/insurance-product-information-documents) |

> **참고:** `cignaglobal.com` 도메인은 한국에서 Cloudflare 보호로 직접 열리지 않을 수 있음. VPN(미국/영국 IP) 사용 또는 브로커 문서 페이지([Plans & Documents for Brokers](https://www.cignaglobal.com/brokers/global-individual-health/plans-useful-documents))에서 직접 탐색 권장.

### 제외 문서

| 문서명 | 제외 이유 |
|-------|---------|
| South Korea Expat Guide | 내용 검토 결과 한국 의료 일반 정보 위주, RAG 검색에 걸릴 보험 약관 내용이 부족 |
| Claim Form (청구서 양식) | 빈 양식으로 텍스트가 거의 없어 RAG 인덱싱 효과 없음. 청구 절차는 Customer Guide로 충분히 커버 |

---

## 6. 문서 버전 관리 전략

| 버전 | 활용 목적 |
|------|---------|
| Customer Guide 2022 (`CLICE-EP24`) | 구버전 인덱싱 → 2025 버전과 비교하여 **"약관 업데이트 자동 반영"** 시연용 |
| Customer Guide 2025 (`UKCEIC-UKCEICP9`) | 실제 서비스 적용 최신 버전 |
| Policy Rules 2024 (`CGIC-EP31`) | 현행 최신 법적 약관 |

> **발표 포인트:** "저희는 2022년과 2025년 버전 Customer Guide를 모두 인덱싱해서, PDF 교체만으로 약관 업데이트가 즉시 반영되는 파이프라인을 시연합니다."
