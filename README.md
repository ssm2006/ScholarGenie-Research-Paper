
# ScholarGenie

An AI-driven scholarship recommendation framework that combines rule-based eligibility checks with multilingual semantic matching, and explains *why* each scholarship is recommended.

> **Status:** Conceptual framework with a prototype in progress. Items marked `[TODO]` are not yet implemented or measured. No results are reported until they have been run.


## Problem

Scholarships are scattered across government, private and international websites. Most portals:

- rely on keyword search or fixed filters (a search for "undergraduate in science stream" can miss a listing titled "bachelor's level STEM programs"),
- are English-only, which excludes many students in multilingual regions such as India,
- list scholarships without explaining why a student qualifies or not,
- often contain outdated, duplicate or fake listings.

## Approach

ScholarGenie uses a two-stage hybrid pipeline:

1. **Rule-based eligibility filter.** Removes scholarships whose hard criteria the student does not meet (age, academic score, degree level, category, income).
2. **Semantic matching.** Embeds the student profile and scholarship descriptions and ranks the remaining scholarships by cosine similarity, so that matches are found by meaning, not exact keywords.
3. **Explanation.** Each recommendation lists the rules passed and the profile-to-description matches that drove its rank.
4. **Multilingual access.** Queries and content are handled in the student's preferred language.

```
Student profile ─► Rule filter ─► Semantic ranking ─► Explanation ─► Ranked results
                      ▲                  ▲
          Verified scholarship data (.gov / .edu / .org sources)
```

## Planned system layers (from the paper)

| Layer | Purpose | Technology |
|---|---|---|
| Data acquisition | Collect listings from trusted sources | Python, BeautifulSoup, Selenium |
| Data storage | Store, update, deduplicate | MongoDB |
| AI processing | Eligibility rules + semantic matching | spaCy, BERT-family embeddings |
| Application tracking | Bookmarks, deadline reminders | Node.js |
| User interaction | Web UI, multilingual chatbot | React.js, Tailwind CSS, Google Translate API |

## Evaluation plan

| Metric | Measures | Result |
|---|---|---|
| Eligibility correctness | Rule filter vs. ground-truth labels | [TODO] |
| Precision@k, Recall@k, MRR | Ranking quality vs. keyword-only baseline | [TODO] |
| User study (N = 20-50) | Usability, explainability, multilingual effectiveness | [TODO] |

Data: a curated set of verified scholarship listings plus synthetic student profiles. Synthetic profiles are a known limitation, since they may not reflect real student behaviour.

## Repository structure

```
ScholarGenie/
├── README.md
├── requirements.txt
├── LICENSE
├── src/          # rules, embeddings, ranking, explanations   [TODO]
├── data/         # scholarship listings, synthetic profiles   [TODO]
├── eval/         # metric scripts and baseline                [TODO]
└── paper/        # paper PDF
```

## Getting started

[TODO: fill in once the prototype exists]

```bash
git clone https://github.com/ssm2006/ScholarGenie.git
cd ScholarGenie
pip install -r requirements.txt
```

## Roadmap

- [x] Conceptual framework and literature review
- [ ] Scholarship dataset and synthetic student profiles
- [ ] Rule-based eligibility filter
- [ ] Multilingual semantic ranking
- [ ] Explanation generation
- [ ] Evaluation against keyword baseline
- [ ] Web interface and chatbot
- [ ] Automated listing verification

## Paper and citation

If you use this work, please cite:

```
S. Mandlik, B. Bhoir. "ScholarGenie: An AI-Driven Intelligent
Scholarship Recommendation System with Eligibility Analysis and Multilingual
Support." Marathwada Mitra Mandal's College of Engineering, Pune. [TODO: add year/venue/link]
```

## Authors

- Soumya Mandlik
- Bhavika Bhoir

Department of Information Technology, MMCOE, Pune, India.

## License

MIT License
