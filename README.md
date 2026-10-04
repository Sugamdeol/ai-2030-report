# AI in 2030 Report - PDF Generator

This repository contains a comprehensive forecast report on AI in 2030 and a GitHub Actions workflow to automatically generate a beautifully formatted PDF.

## Files

- `ai-2030-report.md` — The full report in Markdown
- `eisvogel.tex` — Custom LaTeX template (based on Eisvogel) for professional PDF output
- `.github/workflows/pdf.yml` — GitHub Actions workflow to build the PDF

## Quick Start

### Option 1: Use GitHub Actions (Recommended)

1. **Create a new GitHub repository** and push these files:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: AI 2030 report"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/ai-2030-report.git
   git push -u origin main
   ```

2. **Trigger the workflow**:
   - Go to **Actions** tab → **Generate PDF Report** → **Run workflow**
   - Or push a tag: `git tag v1.0 && git push origin v1.0`

3. **Download the PDF**:
   - From **Actions** → latest run → **Artifacts** → `ai-2030-report-pdf`
   - Or from **Releases** if you pushed a tag

### Option 2: Build Locally

Requires: `pandoc`, `texlive-xetex`, `texlive-fonts-recommended`, `texlive-fonts-extra`, `texlive-latex-extra`, `fonts-dejavu-core`

```bash
# Ubuntu/Debian
sudo apt-get install pandoc texlive-xetex texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra fonts-dejavu-core

# macOS
brew install pandoc basictex
sudo tlmgr install fontspec unicode-math geometry fancyhdr booktabs longtable array multirow wrapfig float colortbl pdflscape tabu threeparttable threeparttablex ulem makecell xcolor hyperref graphicx setspace titlesec titletoc tocloft sectsty enumitem parskip
sudo tlmgr install dejavu

# Build
pandoc ai-2030-report.md \
  --pdf-engine=xelatex \
  --template=eisvogel.tex \
  --toc --toc-depth=3 --number-sections \
  -V geometry:margin=2.5cm \
  -V fontsize=11pt -V linestretch=1.2 \
  -o ai-2030-report.pdf
```

## Report Contents

The report covers 12 sections:

1. **AGI Timeline** — Expert probabilities, calibration from 60 years of failed predictions
2. **Autonomous Agents** — L1-L4 maturity, market projections, multi-agent systems
3. **Consciousness & Existential Risk** — Intelligence vs consciousness, self-awareness risks, AI rights
4. **Economic Transformation** — Two-track labor market (Goldman Sachs, PwC, McKinsey data)
5. **Energy & Climate** — IEA projections, regional concentration, climate paradox
6. **Historical Patterns** — Four AI eras, recurring failure modes
7. **Failed Predictions Archive** — 50+ falsified forecasts, structural failure modes
8. **Alignment & Interpretability** — Mechanistic interpretability, RepE, scaling laws for proxy gaming
9. **Controversial Topics** — Post-training compute, synthetic data, open-weight proliferation, bio-risk, geopolitics, alignment tax, human-AI coevolution, AI welfare
10. **Scenario Matrix** — Four 2030 worlds with probabilities
11. **Actionable Implications** — For policymakers, technical leaders, individuals
12. **Key Sources** — 30+ institutional/academic references

## Customization

- Edit `ai-2030-report.md` to update content
- Modify `eisvogel.tex` for styling changes (colors, fonts, layout)
- Adjust workflow in `.github/workflows/pdf.yml` for different triggers/outputs

## License

MIT — Free to use, modify, distribute.