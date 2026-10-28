# Public Sentiment & Discourse Analysis on E-Commerce Shipping Discount Regulations
### Social Media Analytics on TikTok Comments Using NLP, WordLink Semantic Graphs, and BERTopic Modeling (Permen Komdigi No. 8/2025: Pembatasan Diskon Ongkir)

[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter&logoColor=white)](code_capstone1_ams.ipynb)
[![Dataset](https://img.shields.io/badge/Dataset-5.967%20TikTok%20Comments-black?logo=tiktok&logoColor=white)](tiktok-ams-capstone1.csv)
[![Topic Modeling](https://img.shields.io/badge/Model-BERTopic%20(PyTorch)-red)]()
[![Network Analysis](https://img.shields.io/badge/Network-WordLink%20Graph-green)]()

---

## Project Overview & Policy Context

The Indonesian **Ministry of Communication and Digital Affairs (*Kementerian Komunikasi dan Digital / Komdigi*)** enacted **Permen Komdigi No. 8/2025** regarding commercial postal and courier logistics services (*Layanan Pos Komersial*). A central provision in this policy restricts **free shipping promotions (*diskon gratis ongkos kirim / ongkir*)** to a maximum of **3 days per calendar month**. This regulation was introduced to curb predatory logistics pricing wars, safeguard **delivery couriers (*mitra kurir logistik*)**, and encourage fair market competition for local **micro, small, and medium enterprises (*UMKM*)** as well as **traditional physical markets (*pasar tradisional*)**.

However, the announcement sparked intense public debate across social media platforms, particularly among digital consumers, online sellers (*merchant e-commerce*), and logistics delivery partners.

This repository conducts an empirical data science investigation into **5,967 public comments on TikTok** (May–June 2025) to evaluate public sentiment distribution, discover latent discussion topics, and evaluate public communication efficacy using:
1. **Natural Language Processing (NLP):** TikTok colloquial Indonesian slang normalization (*bahasa gaul / singkatan prokem*) via a curated dictionary (`slang_GratisOngkir.txt`), text preprocessing, and 3-class sentiment categorization (Negative, Neutral, Positive).
2. **WordLink Bigram Semantic Graphs:** Mapping lexical co-occurrence networks and centrality metrics using `NetworkX`.
3. **Advanced Transformer Topic Modeling (BERTopic):** Leveraging Indonesian/multilingual BERT embeddings, UMAP dimensionality reduction, HDBSCAN clustering, and c-TF-IDF keyword extraction on PyTorch GPU.
4. **Temporal Dynamics & Influencer Engagement:** Tracking virality spikes and mapping prominent Key Opinion Leaders (KOLs / *influencers*) driving public criticism.

---

## Analytical Objectives

1. **Quantify Public Sentiment Polarity:** Measure the proportion of public resistance versus acceptance regarding the 3-day free shipping cap (*pembatasan gratis ongkir 3 hari per bulan*).
2. **Extract Semantic Narrative Clusters:** Automatically identify core themes within public discourse using **BERTopic**.
3. **Analyze Viral Dynamics & Influencer Reach:** Map discourse escalation timelines and identify key accounts driving viral reach on TikTok.
4. **Deliver Policy & Public Communication Recommendations:** Provide evidence-based advisory for government regulators (*Komdigi*) and e-commerce stakeholders.

---

## Methodology & Technical Workflow

* **Data Corpus:** 5,967 comments extracted from TikTok discussions surrounding the announcement of Permen Komdigi No. 8/2025.
* **Text Preprocessing & Normalization:**
  * Stripped URLs, account mentions (`@username`), special characters, and emojis.
  * Normalized informal Indonesian internet slang (*bahasa gaul / prokem TikTok*) using a domain-specific lexicon (`slang_GratisOngkir.txt`).
  * Tokenization and stopword removal using `Sastrawi`.
* **Topic Modeling Pipeline (BERTopic):**
  * Generated contextual document embeddings via transformer architectures.
  * Applied `UMAP` for manifold dimensionality reduction and `HDBSCAN` for density-based cluster extraction.
* **WordLink Semantic Graph:**
  * Constructed bigram co-occurrence networks to inspect lexical relationship structures within each sentiment partition.

---

## Key Findings

### 1. Overall Sentiment Distribution
Across the **5,967 analyzed comments**:

| Sentiment Category | Proportion | Core Discussion Narratives |
| :--- | :---: | :--- |
| **Negative** 🔴 | **55%** | Widespread resistance against shipping discount restrictions (*pembatasan gratis ongkir*); concerns over increased cost of living, declining online merchant sales, courier income disruption (*kekhawatiran pemotongan upah mitra kurir*), and disproportionate burdens on communities **outside Java (*wilayah luar Pulau Jawa*)**. |
| **Neutral** ⚪ | **38%** | Inquiries regarding standard shipping tariffs (*ongkir reguler*), confusion regarding policy scope (platform-funded vs. merchant-funded), debates on paid e-commerce VIP delivery subscription models (*paket langganan VIP e-commerce*), and casual community interactions. |
| **Positive** 🟢 | **6%** | Support from offline merchants and local food stores (*pedagang pasar tradisional & warung fisik*) expecting foot-traffic recovery, advocates of curbing impulsive consumerism (*perilaku konsumtif belanja online*), and approval from the standpoint of **courier welfare protection (*perlindungan kesejahteraan kurir*)**. |

---

### 2. BERTopic Narrative Clusters

| Sentiment Partition | Discovered Thematic Clusters | Summary of Dominant Narratives |
| :--- | :--- | :--- |
| **Negative Themes** | • Household Purchasing Power<br>• Courier Income & Gig Welfare<br>• Critique of Regulatory Priority<br>• Inter-Island Logistics Disparity | Fear of economic slowdown in digital commerce, concerns that couriers bear the burden of declining order volume (*penurunan orderan kurir paket*), and frustration over high shipping tariffs for consumers **outside Java (*ongkir mahal ke luar Pulau Jawa*)**. |
| **Positive Themes** | • Offline Market Resurgence<br>• Personal Budgetary Discipline<br>• Fair Courier Tariff Protection | Expectations that neighborhood MSMEs (*UMKM lokal*) will regain competitiveness, encouragement to curb impulsive online spending, and advocacy for fair logistics wages (*standar upah kurir yang layak*). |
| **Neutral Themes** | • Cost Calculation & Clarification<br>• Paid VIP Subscription Alternatives<br>• General Community Discussions | Debates on alternative subscription programs (e.g., e-commerce VIP delivery passes) and seeking clarity on whether restrictions apply to store promotions or logistics providers. |

---

### 3. Temporal Conversation Spikes
* **Discourse Climax (*Puncak Percakapan*):** A sharp spike occurred on **May 20–21, 2025**, peaking at **nearly 3,000 interactions within 24 hours**.
* **Sentiment Breakdown at Peak:** On May 21, negative comments dominated with **1,750 entries**, followed by **1,000 neutral comments**, while positive remarks comprised fewer than 250 entries.
* **Post-Peak Decay:** Activity subsided sharply back below 100 daily interactions by early June 2025, demonstrating an intense, reactive public response to initial press headlines.

---

### 4. Key Influencers Driving Critical Discourse
The top critical TikTok accounts generating the highest engagement and amplifying public opposition:
1. `@nabillaaptriii` (47,998 engagement)
2. `@ooribeefsnn` (27,199 engagement)
3. `@dioooimida` (16,923 engagement)
4. `@dindakest` (14,149 engagement)
5. `@user71542340382576` (14,103 engagement)
6. `@rifky_m1bb` (12,125 engagement)
7. `@itadwi123` (12,052 engagement)

---

## Policy & Public Communication Recommendations

### 1. Transparent Public Communication & Clarification
Government agencies (*Komdigi*) must explicitly clarify that the regulation restricts predatory discounting by courier logistics companies rather than prohibiting seller-funded promotional programs by e-commerce merchants (*diskon promosi penjual*), directly addressing the widespread misperceptions driving 55% of negative sentiment.

### 2. Courier Welfare Safety Nets
Public backlash is heavily rooted in empathy for delivery drivers. Regulators must establish enforceable baseline logistics tariffs and commission transparency to ensure couriers (*mitra kurir*) are protected from declining parcel volumes.

### 3. Regional Logistics Subsidies for Outer Islands
Given the significant freight price disparity across Indonesian provinces, policy exemptions or targeted shipping subsidies should be implemented for **disadvantaged, outermost, and frontier regions (*wilayah 3T: Tertinggal, Terdepan, Terluar*)** and communities outside Java (*luar Pulau Jawa*) to prevent widening domestic economic divides.
