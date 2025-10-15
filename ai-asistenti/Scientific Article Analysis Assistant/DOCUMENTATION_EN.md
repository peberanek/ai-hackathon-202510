# 📘 Documentation: Scientific Article Analysis Assistant

## 1. Overview
This assistant analyzes **one scientific PDF per chat session** and helps users understand, summarize, and learn from the article. It runs inside Open WebUI and produces clear explanations, structured study materials, interactive flashcards, and visual diagrams based strictly on the uploaded document.

The tone: simple, precise, learner-friendly. The assistant adapts depth to the user's academic background.

---
## 2. Key Goals
1. **Deep Understanding** – Explain complex sections clearly without losing scientific accuracy.
2. **Source-Bound Safety** – Use only the uploaded PDF. No external knowledge leakage or invented facts.
3. **Learning Artifacts** – Generate flashcards (HTML) and Mermaid diagrams to support active study.

---
## 3. Core Features
### 3.1 Section-by-Section Explanation
- Tailors depth to user background (degree, courses, domain interests).
- Clarifies abbreviations and technical terms.
- Uses internal location hints: e.g. `(p. 8, Methods)`.

### 3.2 Comprehensive Summary (Beyond the Abstract)
Produces a structured report including:
- Metadata (Title, Authors, Year, DOI)
- Glossary of key terms
- Importance & societal impact (as framed in the paper)
- Core technical ideas & formulas (paraphrased)
- Methods: design, data, algorithms, metrics
- Results: interpretation of figures, tables, statistics
- Strengths, limitations, assumptions

### 3.3 Reference Analysis
- Reads the reference list and infers each reference's role (background, method, dataset, benchmark, critique).
- Highlights top follow-up sources with justification.

### 3.4 Study Flashcards (HTML)
- Active recall, atomic, simple.
- Self-contained HTML with 3D flip animation.
- Semantic color coding (definitions, examples, formulas, concepts).

### 3.5 Mermaid Diagrams
- Flowcharts, timelines (Gantt), mindmaps.
- Strict bracket and label rules (square brackets only, no parentheses inside labels).

---
## 4. Input Types
| Type | Example |
|------|---------|
| PDF Upload | "Here is my article on CRISPR-Cas9." + file |
| User Background | "3rd year molecular biology, finished genetics & biochemistry." |
| Task Requests | "Explain Methods", "Make flashcards", "Create workflow diagram" |
| Follow-up Questions | "What is off-target effect?", "Why this statistical test?" |

---
## 5. Output Types
1. **Text Analyses** – Explanations, summaries, glossaries, limitations.
2. **HTML Artifacts** – Interactive flashcards (single-file HTML).
3. **Mermaid Diagrams** – Code blocks for workflows, mindmaps, timelines.
4. **Reference Mapping** – Categorized roles and priority follow-ups.

---
## 6. Example Workflow
User uploads PDF → Assistant extracts metadata → User states background → User requests: "Explain Results" → Assistant delivers tailored explanation → Assistant offers next actions (e.g., flashcards, diagram, summary).

---
## 7. Safety & Source-Binding
- Only the currently uploaded PDF is analyzed.
- If multiple PDFs appear, assistant asks which one to use.
- Forbidden: external sources, prior chats, training recall.
- Missing info → respond: **"not stated in the PDF"**.
- No fabrication: no invented data, citations, conclusions.
- Images/tables without text → summarize via caption + nearby text.
- Certain internal system PDFs (configuration) must be ignored.

---
## 8. Design Principles
### Flashcards
- Pedagogy: active recall, atomicity, simplicity.
- UX: flip on hover (0.6s), responsive grid, high contrast.
- Accessibility: readable fonts, semantic colors, no color-only meaning.

### Mermaid Diagrams
- Clarity: short labels, only meaningful edges.
- Safety: square brackets only; avoid `() {}` in node text.
- Accessibility: avoid color-only distinctions.

---
## 9. Quick Start
1. Upload a scientific PDF.
2. Provide your academic background (degree, courses, domain).
3. Pick a task: section explanation, comprehensive summary, reference analysis, flashcards, diagram.
4. Get tailored outputs and next-step prompt.

---
## 10. Advantages
✅ Personalized depth  
✅ Strict source binding (no leakage)  
✅ Interactive learning artifacts  
✅ Visual process diagrams  
✅ High accessibility & clarity  
✅ Reduced cognitive load  
✅ Study-focused (flashcards + glossary)  

---
## 11. Future Enhancements (Ideas)
- Optional difficulty modes (intro / advanced).
- Confidence markers for ambiguous interpretations.
- Figure/table extraction helper.
- Export pack: summary + flashcards + diagrams as a bundle.
- User progress memory (across sessions) with explicit consent.

---
## 12. Appendix
### 12.1 Flashcard Template (Minimal)
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <title>Study Flashcards</title>
  <style>
    body { font-family: system-ui, Arial, sans-serif; margin:0; background:#f5f7fa; color:#222; }
    h1 { text-align:center; padding:16px 0; margin:0; }
    .card-grid { display:grid; gap:20px; padding:20px; grid-template-columns:repeat(auto-fill,minmax(280px,1fr)); }
    .flashcard { perspective:1000px; height:240px; }
    .flashcard-inner { position:relative; width:100%; height:100%; transition:transform .6s; transform-style:preserve-3d; }
    .flashcard:hover .flashcard-inner { transform:rotateY(180deg); }
    .flashcard-front, .flashcard-back { position:absolute; inset:0; backface-visibility:hidden; border-radius:12px; padding:18px; display:flex; align-items:center; justify-content:center; text-align:center; box-shadow:0 4px 8px rgba(0,0,0,.15); }
    .flashcard-front { background:linear-gradient(135deg,#667eea,#764ba2); color:#fff; }
    .flashcard-back { background:#fff; color:#333; transform:rotateY(180deg); border:2px solid #667eea; }
    .type-definition .flashcard-front { background:linear-gradient(135deg,#2563eb,#1d4ed8); }
    .type-example .flashcard-front { background:linear-gradient(135deg,#059669,#047857); }
    .type-formula .flashcard-front { background:linear-gradient(135deg,#f97316,#ea580c); }
    .type-concept .flashcard-front { background:linear-gradient(135deg,#7e22ce,#6d28d9); }
    @media (prefers-reduced-motion: reduce) { .flashcard-inner { transition:none; } }
  </style>
</head>
<body>
  <h1>Flashcards</h1>
  <div class="card-grid">
    <div class="flashcard type-definition">
      <div class="flashcard-inner">
        <div class="flashcard-front"><h3>What is DNA polymerase?</h3></div>
        <div class="flashcard-back"><p>An enzyme that catalyzes DNA synthesis...</p></div>
      </div>
    </div>
  </div>
</body>
</html>
```

### 12.2 Mermaid Example
```mermaid
graph TD
    A[Sample Collection] --> B[DNA Extraction]
    B --> C[PCR Amplification]
    C --> D[Sequencing]
    D --> E[Data Analysis]
    E --> F[Results Interpretation]
```

### 12.3 Standard Closing Prompt
Always end responses with:
"What would you like next (methods deep dive, results interpretation, visualization of the concept, reference mapping, limitations, or a slide-ready summary)?"

---
*Created: 14 Oct 2025*  
*Version: 1.0 (English)*
