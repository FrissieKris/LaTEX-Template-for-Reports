# NWU Faculty of Engineering – Final Year Project Report Template

## Folder structure

```
nwu_template/
├── main.tex               ← START HERE – edit project info here
├── NWUStyle.sty           ← House-style package (do not edit unless necessary)
├── NWUBack.png            ← NWU purple banner image (add your own copy)
├── bib/
│   └── MyBib.bib          ← Your BibTeX references
├── img/                   ← All figures (.png / .pdf / .jpg)
└── content/
    ├── 00_abstract.tex
    ├── 01_introduction.tex
    ├── 02_problem_analysis.tex
    ├── 03_literature.tex
    ├── 04_concept.tex
    ├── 05_preliminary.tex
    ├── 06_detailed.tex
    ├── 07_implementation.tex
    ├── 08_testing.tex
    ├── 09_conclusion.tex
    ├── A_ai_usage.tex
    ├── B_risk_register.tex
    └── C_additional.tex
```

---

## Quick-start: 5 steps

1. **Add your banner image** – place the official `NWUBack.png`
   (purple diagonal NWU banner) next to `main.tex`.

2. **Edit the info block in `main.tex`** – fill in your name,
   student number, supervisor, degree, etc.

3. **Write your content** – open the files in `content/` and
   replace the placeholder text chapter by chapter.

4. **Add figures** – save all images to `img/` and reference
   them with `\includegraphics{my_figure}` (no path or extension needed).

5. **Compile** – see compilation instructions below.

---

## Compilation

The template uses **biblatex + biber** for references (IEEE numeric style).
You must run the full sequence:

```bash
pdflatex main
biber main
pdflatex main
pdflatex main
```

Or simply:

```bash
latexmk -pdf main
```

`latexmk` handles all passes automatically and is the recommended approach.

### Recommended editors

| Editor | Notes |
|--------|-------|
| **Overleaf** | Upload the entire folder; set compiler to pdfLaTeX and bibliography tool to Biber. |
| **VS Code** | Install the *LaTeX Workshop* extension; it runs `latexmk` automatically on save. |
| **TeXstudio** | Tools → Configure → Build → Default bibliography to Biber. |

---

## Customisation reference

### Changing project information

All variable setters live at the top of `main.tex`:

| Command | Purpose |
|---------|---------|
| `\Title{...}` | Main cover-page title |
| `\ReportTitle{...}` | Subtitle / report type |
| `\FirstName{...}`, `\Surname{...}`, `\Initials{...}` | Author |
| `\StudentNumber{...}` | Student number |
| `\Supervisor{...}` | Supervisor name |
| `\CoSupervisor{...}` | Optional co-supervisor (leave `{}` if none) |
| `\AssistantSupervisor{...}` | Optional (leave `{}` if none) |
| `\Degree{...}` | e.g. `Bachelor of Engineering` |
| `\Discipline{...}` | e.g. `Mechatronic Engineering` |
| `\Campus{...}` | e.g. `Potchefstroom Campus` |
| `\SubmissionDate{...}` | e.g. `22 November 2024` |
| `\TurnitinScore{...}` | e.g. `5\%` (or leave `{}` to omit) |
| `\ORCID{...}` | ORCID number – also uncomment `\showorcidtrue` |

### Enabling ORCID on the cover

In `main.tex`, uncomment:
```latex
\showorcidtrue
```
and place `ORCID.png` (the green ORCID icon) next to `main.tex`.

### Adding a co-supervisor

```latex
\CoSupervisor{Prof. J. Bloggs}
```

Leave `\CoSupervisor{}` to suppress the line entirely.

### Switching to a coursework report

Fill in `\Module{}` and `\Assignment{}` in `main.tex`:
```latex
\Module{INGM225}
\Assignment{Practical Report}
```
These lines appear on the cover only when non-empty.

### Adding chapters

1. Create a new file in `content/`, e.g. `10_appendixD.tex`.
2. Add `\input{content/10_appendixD}` in `main.tex`.

### Landscape pages

Wrap the content in a `landscape` environment (provided by the
`pdflscape` package, already loaded in `NWUStyle.sty`):

```latex
\begin{landscape}
  \begin{figure}[H]
      \centering
      \includegraphics[width=0.95\linewidth]{big_schematic}
      \caption{Full system schematic.}
  \end{figure}
\end{landscape}
```

### Including datasheet pages

```latex
\includepdf[pages=1-2,
            pagecommand={\thispagestyle{fancy}},
            scale=0.9]{datasheets/component.pdf}
```

---

## Common issues

| Symptom | Fix |
|---------|-----|
| `NWUBack` image not found | Place `NWUBack.png` next to `main.tex` |
| References show `[?]` | Run `biber main` then compile twice more |
| TOC page numbers wrong | Compile twice (LaTeX needs two passes) |
| `biber` not found | Install TeX Live full, or use Overleaf |
| `NWUStyle.sty not found` | Ensure `NWUStyle.sty` is in the same folder as `main.tex` |
