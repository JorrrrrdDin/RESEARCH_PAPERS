# GHOST Domain — arXiv Paper Draft

**Title**: GHOST Domain: Information-Theoretic Semantic Camouflage for External LLM Queries
**Author**: Myeong Jun Jo (ORCID: 0009-0006-9540-4666)
**Status**: Pre-print draft v1, ready for arXiv submission
**Patent**: KIPO Application No. 10-2026-0068007 (filed 2026-04-15)

---

## 파일 구성

| 파일 | 용도 |
|---|---|
| `ghost_domain.tex` | 메인 논문 소스 (single column arXiv style, TikZ architecture diagram 포함) |
| `references.bib` | BibTeX 참고 문헌 (16건, 실존 최신 인용) |
| `README.md` | 본 파일 — 컴파일·투고 안내 |

## 버전 이력

- **v3 (현재)**: TikZ 시스템 아키텍처 다이어그램, 실험 N=512 스케일, 3개 case study 정량 측정, 실존 최신 citation (Carlini 2021, PLeak 2024, MIA 2024)
- v2: 588줄 arXiv 중간 공개 (Gemini report 수준)
- v1: 986줄 풀 공개 (PhD 수준, deprecated)

---

## 컴파일

### 로컬 (pdflatex)
```bash
cd "C:/Users/HR/OneDrive/특허/010/paper"
pdflatex ghost_domain.tex
bibtex   ghost_domain
pdflatex ghost_domain.tex
pdflatex ghost_domain.tex    # 최종 (cross-ref + biblio 해결)
```

### Overleaf
1. Overleaf 프로젝트 생성
2. `ghost_domain.tex` 와 `references.bib` **동시 업로드**
3. Compile 버튼 클릭 (Overleaf는 자동으로 bibtex 실행)
4. 필요 패키지 (전부 표준): `geometry`, `amsmath`, `amssymb`, `amsthm`, `booktabs`, `hyperref`, `natbib`, `tikz`, `graphicx`, `tabularx`, `multirow`, `url`, `xcolor`

모든 패키지는 TeX Live 표준에 포함되어 있어 추가 설치 불필요. TikZ 라이브러리: `arrows.meta`, `positioning`, `fit`, `backgrounds`, `shapes.geometric`, `calc` (전부 표준).

---

## 논문 구조

총 ~15 pages 예상 (single column, 11pt)

1. **Abstract** — 정보이론적 보장 명시
2. **Introduction** — 문제 동기 + 4가지 기존 실패 + 6개 기여
3. **Threat Model** — 6개 공격 클래스 T1~T6 정식화, T7은 future work
4. **System Design** — 5계층 아키텍처 + 등가 클래스 + per-session token + structural padding + 의사코드 2개
5. **Formal Guarantees** — 정리 1~3 + 증명 + 구조 패딩 lemma
6. **Evaluation** — 18개 실험 요약, 3개 핵심 표
7. **Related Work** — DP, FHE, k-anonymity, prompt obfuscation, TEE
8. **Discussion** — 유틸-보안 트레이드, 엔티티 추출 의존성, 메타 추론 future work
9. **Conclusion**
10. **References** — 8개 (core 인용)
11. **Appendix** — 구조 패딩 lemma 증명

---

## 투고 체크리스트

### arXiv 선공개 (즉시)
- [ ] 영문 교정 pass (grammar, typo)
- [ ] 저자 ORCID 확인
- [ ] 특허 출원번호 각주 확인
- [ ] 18개 실험 raw 데이터 → GitHub 공개 (재현성)
- [ ] arXiv 카테고리: `cs.CR` (primary), `cs.CL` (secondary)
- [ ] PDF 생성 → arXiv 업로드

### 정식 학회 투고 (이후)
- [ ] venue 결정: USENIX Security 2027 / CCS 2027 / NDSS 2027
- [ ] 학회 .cls 파일로 재조판
- [ ] anonymization (double-blind 학회인 경우 저자/소속 제거)
- [ ] deadline 확인

---

## 주의 사항

### 공개해도 되는 것
- ✅ 5계층 아키텍처 설명
- ✅ 정리 1~3 + 증명 (출원 후 priority 보호)
- ✅ 18개 실험 수치 (수치 자체는 공지에 기여)
- ✅ 파이썬 reference implementation (GitHub 권장)

### 주의할 것
- ⚠️ 선행 출원 (10-2026-0002392 등 본인 출원) 인용은 자유, 단 출원번호 직접 명시는 최소화
- ⚠️ 경쟁사·업체명 직접 비교는 objective하게 (Samsung, JPMorgan은 공개 사례이므로 OK)

### 하지 말 것
- ❌ 라이선스 조건 정보 포함 금지 (논문은 학술, 비즈니스 모델 분리)
- ❌ 실제 기업 고객 이름 언급 (아직 없음)
- ❌ 과장된 성능 주장 (수치는 측정된 것만)

---

## 작성 후 수정 포인트 (v2에서)

1. **Figures 추가**: 도 1 (시스템 블록도), 도 9 (Shannon 엔트로피 곡선), 도 10 (Bayesian view-independence), 도 13 (power law) 4개는 논문에 필수
2. **References 확장**: 현재 8개 → 20~25개로 (각 related work 섹션에 3~5 cite 추가)
3. **Appendix 보강**: 구조 패딩 lemma 정식 증명, 실험 세부 프로토콜
4. **Acknowledgments**: 협력자·리뷰어 반영

---

*작성: 2026-04-15 (A-010 출원 당일)*
