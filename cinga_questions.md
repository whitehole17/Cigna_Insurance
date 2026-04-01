# Gemini 질문들

은우 님, RAG 성능 테스트를 위해 아주 좋은 접근입니다. 단순 지식 추출(Fact Retrieval)부터 여러 조항을 엮어야 하는 복합 추론(Reasoning)까지 난이도별로 12가지 질문을 뽑아보았습니다.

각 질문은 은우 님이 가지고 계신 **Customer Guide(CG)**와 **Policy Rules(PR)**의 실제 내용을 기반으로 합니다.

---

### 1. 단순 정보 추출 (Level: Low)
문서에 명시된 수치나 명칭을 그대로 가져오는 테스트입니다.

* **Q1.** Cigna Healthcare의 본인부담금(Deductible) 옵션 중 가장 높은 금액은 얼마인가요?
    * *출처: Customer Guide p.15 (How Deductible and Cost Share work)*
* **Q2.** International Vision & Dental 옵션에서 'Routine dental care'의 연간 한도는 Silver 플랜 기준 얼마인가요?
    * *출처: Customer Guide p.45 (Table of Benefits)*
* **Q3.** 보험 증권(Certificate of Insurance)에 기재된 'Start date'의 정의는 무엇인가요?
    * *출처: Policy Rules p.25 (Section 3: Definitions)*

### 2. 절차 및 조건 확인 (Level: Medium)
특정 상황에서 지켜야 할 프로토콜을 확인하는 테스트입니다.

* **Q4.** 입원 치료를 받기 전에 반드시 '사전 승인(Prior Approval)'을 받아야 하나요? 만약 받지 않으면 어떤 불이익이 있나요?
    * *출처: Customer Guide p.10 (Practical Information)*
* **Q5.** 보험 가입 후 마음이 바뀌어 취소하고 싶을 때, 전액 환불이 가능한 'Free look period'는 며칠인가요?
    * *출처: Policy Rules p.7 (Section 1: 4. Free look period)*
* **Q6.** 거주 국가(Country of habitual residence)가 변경되었을 때, Cigna에 언제까지 알려야 하나요?
    * *출처: Policy Rules p.13 (Section 1: 11. Changes to personal information)*

### 3. 복합 추론 및 상황 판단 (Level: High) 🚀
여러 페이지의 정보를 조합하거나 예외 조항을 해석해야 하는 고난도 질문입니다.

* **Q7.** "나는 Silver 플랜 가입자이고 자기부담금(Deductible) $500, 본인부담률(Cost Share) 20%를 선택했어. 이번에 병원비로 $1,000이 나왔다면 내가 실제로 돌려받을 금액은 얼마야?"
    * *출처: Customer Guide p.14-15 (계산 로직) + p.17 (플랜 혜택)*
* **Q8.** "태국에서 오토바이를 타다가 사고가 났어. 약관상 '위험한 활동(Hazardous Activities)'으로 분류되어 보장이 거절될 가능성이 있는 조항이 뭐야?"
    * *출처: Policy Rules p.17-18 (General Exclusions - 'Sport' or 'Hazardous' 관련)*
* **Q9.** "현재 임신 중인데, 6개월 뒤에 태어날 아이를 내 보험에 추가하고 싶어. 언제까지 신청해야 심사 없이(Full Medical Underwriting 없이) 추가할 수 있어?"
    * *출처: Policy Rules p.13-14 (Section 1: 10. Adding beneficiaries)*
* **Q10.** "정신과 상담(Parent and Child Mental Health Support)을 받고 싶은데, 이 서비스는 입원 중에만 가능한가요, 아니면 통원 치료로도 가능한가요?"
    * *출처: Customer Guide p.8 (Our Health Services) + p.19 (Inpatient/Outpatient 구분)*
* **Q11.** "한국 거주자로서 보험금 청구 시 서류를 우편으로 보내야 하나요, 아니면 앱으로도 가능한가요? 싱가포르 지점 연락처도 알려줘."
    * *출처: Customer Guide p.13 (How to Submit Claims) + p.41 (Contact info)*
* **Q12.** "작년(2022년) 가이드와 비교했을 때, 2024년 가이드에서 강조하는 'Cigna Healthcare' 브랜드의 새로운 디지털 서비스는 무엇인가요?"
    * *출처: 2022년 vs 2024년 Customer Guide 표지 및 p.5-9 (Welcome/Services 비교)*

---

### 💡 RAG 테스트 팁
* **Q7(계산)**과 **Q9(조건부 추가)**는 단순 검색으로는 절대 답이 나오지 않습니다. LLM이 약관의 로직을 이해해야 하므로, **LlamaParse** 등을 사용해 표 데이터를 구조화한 뒤 테스트해 보시는 것을 추천합니다.
* **Q12**는 은우 님이 준비하신 '유지보수 및 업데이트' 시연을 위한 킬러 질문입니다.



이 질문 리스트로 먼저 돌려보시고, 답변이 잘 안 나오는 부분이 있으면 그 부분이 바로 **"PDF 파싱이나 프롬프트 엔지니어링이 더 필요한 부분"**이니 팀원들과 공유해 보세요!  


# Perplexity 질문들


Cigna RAG 성능 테스트용 **질문 12개**를 Customer Guide, Policy Rules CGIC, Benefits Summary에서 뽑았어요. 간단한 사실 확인부터 복잡한 판단까지 포함했습니다. [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591048-cgho-customer-guide-en_05_2023.pdf)

## 🔍 **RAG 테스트 질문셋 (12개)**

### **1. 플랜 기본사항 (Benefits Summary)**
1. **"Cigna Global Silver 플랜에서 연간 deductible은 얼마인가?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591116-cigna-global-benefits-summary-usd_en_02_2025.pdf)
2. **"Gold 플랜에서 outpatient mental health visit당 copay는?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591116-cigna-global-benefits-summary-usd_en_02_2025.pdf)
3. **"Platinum 플랜의 최대 의료비 한도는?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591116-cigna-global-benefits-summary-usd_en_02_2025.pdf)

### **2. 고객 실무사항 (Customer Guide)**  
4. **"심리상담 예약 시 pre-authorization이 필요한가?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/UKCEIC-UKCEICP9/en/CGHO%20Customer%20Guide%20EN%200225.pdf)
5. **"한국에서 Cigna 네트워크 병원으로 심리상담 가능한가?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591048-cgho-customer-guide-en_05_2023.pdf)
6. **"telehealth 상담도 Cigna에서 보장되나?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/UKCEIC-UKCEICP9/en/CGHO%20Customer%20Guide%20EN%200225.pdf)

### **3. 청구/절차 (Customer Guide + Policy Rules)**  
7. **"심리상담 50분 세션 청구 시 어떤 서류가 필요한가?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591048-cgho-customer-guide-en_05_2023.pdf)
8. **"claim 제출 기한은 며칠인가?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP31/en/CGHO%20Policy%20Rules%20CGIC_EN_02_2024.pdf)

### **4. 복잡 판단 (Policy Rules CGIC)**  
9. **"연 10회 이상 psychotherapy 받으면 추가 승인이 필요한가?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP31/en/CGHO%20Policy%20Rules%20CGIC_EN_02_2024.pdf)
10. **"Silver 플랜에서 한국 비네트워크 상담소 이용 시 보장 비율은?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP31/en/CGHO%20Policy%20Rules%20CGIC_EN_02_2024.pdf)

### **5. 예외/제한사항**  
11. **"정신과 약 처방도 outpatient mental health에 포함되나?"** [cignaglobal](https://www.cignaglobal.com/dvc-pdfs/CGIC-EP31/en/CGHO%20Policy%20Rules%20CGIC_EN_02_2024.pdf)
12. **"가족 중 1명만 이용해도 다른 가족 deductible 공유되나?"** [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591116-cigna-global-benefits-summary-usd_en_02_2025.pdf)

## 🎯 **테스트 평가 기준**

```
✅ 정확도: 문서에 명시된 숫자/조건 정확히 인용
✅ Hallucination: 문서에 없는 정보 생성 여부  
✅ Context: 올바른 문서/플랜에서 가져왔는지
✅ Completeness: 필요한 disclaimer("보험사 확인 필요") 포함 여부
```

## 💾 **실제 테스트 방법**

```
질문 → RAG → 답변 → 정답과 비교
예시:
Q: "Silver 플랜 연간 deductible 얼마?"
A: "Silver 플랜 기준 $500 [Benefits Summary 2025 p.12]"
→ 정확도 100%
```

## 📋 **난이도별 분포**
```
쉬움 (플랜 숫자): 1,2,3
중간 (실무 절차): 4,5,6,7,8  
어려움 (판단): 9,10,11,12
```

**이 12개 질문으로 하면 RAG 성능을 정확히 파악할 수 있고, SKN24 채점관이 보기에 "실제 사용자 질문"처럼 보여서 좋습니다.** 각 질문마다 **출처 문서가 분명해서 정답 확인도 쉬워요**. [cignaglobal](https://www.cignaglobal.com/static/cigna-rebranding/pdf/cignaglobal-uvsl/591048-cgho-customer-guide-en_05_2023.pdf)

**지금 Streamlit에 이 질문들 넣고 돌려보세요.** 결과 나오면 어떤 게 잘 되고 어떤 게 실패하는지 바로 알 수 있어요!