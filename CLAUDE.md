# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **job search portfolio repository** for a dual-degree engineering graduate (Mines Paris - PSL & Shanghai Jiao Tong University) pursuing data science, machine learning, and software engineering roles. The repository contains professional resumes, project documentation, and technical interview preparation materials.

## Repository Structure

### 1. Resume Management (`cv/`)

**Primary Files**:
- `resume.tex` - English resume (ATS-optimized LaTeX format)
- `resume_fr.tex` - French resume (same structure, translated content)
- `xxd.jpeg` - Profile photo

**Template Source**:
- `templates/template.tex` - Base LaTeX template derived from resume structure

**Git Tracking**:
The repository uses `.gitignore` to track ONLY:
- `resume.tex`, `resume_fr.tex`, `template.tex`
- `CLAUDE.md`
- `CV_Xindong.pdf` (compiled output)
- `.gitignore`

All other files (admin documents, archives, project materials) are excluded from version control.

### 2. Project Documentation (`project_sum/`)

**Detailed Project Summaries** for resume talking points:

1. **project_baijiahao.md** - DeepDyna AI Content Automation Platform
   - End-to-end LLM-powered content generation system
   - 20K+ articles across 50+ accounts, 20% ROI
   - Tech stack: OpenRouter, RAG, PostgreSQL, pgvector, Flask, asyncio
   - Key features: Multi-provider LLM client, two-stage generation workflow, multi-dimensional analytics

2. **project_bank.md** - Banking Q&A Multi-Agent RAG System
   - MCP (Model Context Protocol) agent with 4-iteration reasoning
   - PostgreSQL + pgvector with sub-100ms semantic search
   - Multi-LLM support: Claude, GPT-4, Gemini, DeepSeek
   - Tech stack: SQLAlchemy, IVFFlat indexing, batch embedding

3. **project_crypto.md** - Crypto Trading Intelligence System
   - Real-time smart-money tracker (Ethereum, Solana, BSC)
   - Twitter news intelligence with LLM event assessment
   - Discord/Telegram alert automation
   - Tech stack: web3.py, Discord.py, Telegram API, BeautifulSoup

### 3. Technical Interview Prep (`quant/`)

**LeetCode Solutions** (`quant/leetcode/`):
- Dynamic programming problems: 62, 63, 64, 300, 712, 740, 746, 1027
- String/array problems: 1, 3, 5
- Custom problems: coinflip.py (probability simulation)

**Quantitative Finance Resources**:
- "[Mark Joshi] Quant Job Interview Questions And Answers.pdf"
- "Practical Guide To Quantitative Finance Interview.pdf"

### 4. Administrative Documents (`admin_docs/`)

**Personal Documentation** (not tracked in git):
- Academic: Transcripts, diplomas (SJTU, Mines Paris), admission letters
- Legal: Passport, visa, residence permit (France)
- Professional: Internship agreements (Veolia, b:bot), recommendation letters

### 5. Archives (`archives/`)

**Historical Versions** (not tracked):
- Previous CV versions (Word/PDF formats from 2023-2025)
- Python scripts for CV generation: `translate_cv.py`, `read_docx.py`, `create_word_cv.py`
- Cover letters (QRT quant position)

## Working with LaTeX Resumes

### Compilation Commands

```bash
# Compile English resume
cd cv/
pdflatex resume.tex
# Output: resume.pdf

# Compile French resume
pdflatex resume_fr.tex
# Output: resume_fr.pdf
```

**Note**: The resumes use identical LaTeX structure with content differences only. Both require:
- `fontawesome5` package for icons
- `hyperref` for clickable links
- ATS-compatible formatting (no fancy graphics, machine-readable text)

### Resume Structure

**Common LaTeX Commands** (defined in both files):
- `\resumeSubheading{Company}{Dates}{Title}{Location}` - Job/education entry
- `\resumeItem{text}` - Bullet point under entry
- `\resumeProjectHeading{Title | Tech}{Dates}` - Project header
- `\resumeSubHeadingListStart` / `\resumeSubHeadingListEnd` - Section containers

**Standard Sections**:
1. Header: Name, phone, email, LinkedIn, GitHub
2. Education: SJTU (Master & Bachelor), Mines Paris (Diplôme d'Ingénieur)
3. Experience: DeepDyna AI, Veolia Asia, b:bot
4. Projects: Banking RAG, Crypto Trading, Underwater Robotics, VR Game, NLP Sentiment Analysis, GANs
5. Technical Skills: Languages, ML/AI Frameworks, Data & Cloud, Human Languages

### Customization Patterns

**For Different Job Applications**:
1. Reorder projects based on job relevance (fintech → Banking RAG first; web3 → Crypto Trading first)
2. Adjust bullet point emphasis using `\textbf{}` for keywords matching job description
3. Modify technical skills order to highlight most relevant stack
4. Keep ATS parsability: no tables for main content, clear section headers, standard fonts

**Version Control Strategy**:
- Only commit changes to `cv/resume.tex` and `cv/resume_fr.tex`
- Generate PDFs locally, optionally commit `CV_Xindong.pdf` for quick sharing
- Archive old versions in `archives/` directory (not tracked)

## Project Documentation Usage

### When Writing Cover Letters

**Extract Quantifiable Achievements** from `project_sum/*.md`:
- DeepDyna AI: "20K+ articles, 50+ accounts, 20% ROI, 70% API latency reduction"
- Banking Agent: "95%+ intent recognition, sub-100ms search, 10x cost reduction via batch processing"
- Crypto Trading: "Real-time monitoring across 3 chains, automated phone alerts for critical events"

### When Preparing for Interviews

**Deep Dive Sections**:
1. **LLM Integration**: Review async batch processing, multi-provider architecture, retry logic (project_baijiahao.md §1, §2)
2. **Vector Databases**: Study pgvector indexing strategies, IVFFlat vs HNSW tradeoffs (project_bank.md §4, §6)
3. **Agent Architecture**: Understand MCP reasoning loop, tool orchestration, working memory (project_bank.md §2, §3)
4. **Data Pipelines**: Review multi-level aggregation, snapshot-based delta calculation (project_baijiahao.md §3)

### Technical Stack Summary

**Most Frequently Used Technologies** (for quick reference):
- **Languages**: Python, C/C++, SQL, JavaScript, Solidity
- **ML/AI**: PyTorch, TensorFlow, OpenAI API, LangChain, RAG, pgvector
- **Data**: pandas, NumPy, PostgreSQL, vector databases
- **Web**: Flask, FastAPI, Discord.py, Telegram API
- **Cloud**: Azure ML Studio, GCP, Docker
- **Blockchain**: web3.py, Ethereum, Solana, BSC

## Development Workflow

### Making Resume Changes

1. **Edit LaTeX source**:
   ```bash
   # Open in any text editor
   open cv/resume.tex  # macOS
   code cv/resume.tex  # VS Code
   ```

2. **Compile to PDF**:
   ```bash
   cd cv/
   pdflatex resume.tex
   ```

3. **Preview changes**:
   - Open `resume.pdf` in PDF viewer
   - Check for formatting issues, typos, alignment

4. **Commit updates** (only if significant changes):
   ```bash
   git add cv/resume.tex
   git commit -m "Update: [describe changes]"
   ```

### Updating Project Summaries

**When Adding New Projects**:
1. Create new markdown file in `project_sum/`: `project_[name].md`
2. Follow structure from existing files:
   - Executive Summary with quantifiable metrics
   - Technical architecture breakdown
   - Code examples (if applicable)
   - Resume-ready bullet points
3. Extract 2-3 key achievements for resume Projects section
4. Update resume with condensed project entry

### Running Python Scripts

**LeetCode Practice**:
```bash
cd quant/leetcode/
python3 [problem_number].py
```

**Archive Utilities** (if needed):
```bash
cd archives/
python3 translate_cv.py  # CV translation helper
python3 read_docx.py     # Word document parser
```

## Key Considerations

### ATS Optimization

**Resume Best Practices** (already implemented):
- Single-column layout (no fancy multi-column designs)
- Standard section headers (Education, Experience, Projects, Skills)
- No images/graphics in main content area
- Clickable links using `\href{}`
- `\pdfgentounicode=1` for text extraction compatibility
- 10pt font for optimal readability

### Bilingual Maintenance

**When updating resume content**:
1. Make changes to English version first (`resume.tex`)
2. Translate new content to French (`resume_fr.tex`)
3. Maintain parallel structure (same LaTeX commands, different text)
4. Verify technical terms: some stay in English (e.g., "Deep Learning"), others translate (e.g., "Diplôme d'Ingénieur")

### Privacy & Sensitivity

**Personal Information**:
- Contact details are real (phone: +33 752063188, email domain: minesparis.psl.eu)
- LinkedIn/GitHub profiles are public
- Admin documents in `admin_docs/` contain sensitive data (passports, visas) - DO NOT commit to git
- Archives may contain previous application materials - keep private

## Common Tasks

### Task: Update Job Experience

1. Locate Experience section in `cv/resume.tex` (lines 171-198)
2. Add new `\resumeSubheading{}{}{}{}` entry
3. Add bullet points with `\resumeItem{}`
4. Recompile and check formatting
5. Repeat for French version

### Task: Reorder Projects for Job Application

1. Identify target job focus (e.g., fintech, web3, ML)
2. Rearrange `\resumeProjectHeading` entries in Projects section (lines 201-252)
3. Place most relevant project first
4. Adjust bullet point emphasis with bold keywords
5. Compile and verify

### Task: Generate Custom Resume Version

1. Save current resume: `cp cv/resume.tex cv/resume_backup.tex`
2. Make customizations for specific application
3. Compile to PDF: `cd cv/ && pdflatex resume.tex`
4. Rename output: `mv resume.pdf CV_Xindong_[Company]_[Date].pdf`
5. Restore original: `mv cv/resume_backup.tex cv/resume.tex` (if needed)

## Git Workflow Notes

**Current Status** (from git status):
- Deleted files staged: `CLAUDE.md`, `CV_Xindong.pdf`, `resume.tex`, `resume_fr.tex`, `template.tex`
- This appears to be a repo reset - these files should be restored

**Typical Commit Pattern**:
- Resume updates: Descriptive messages like "Update Veolia experience bullet points"
- Project additions: "Add Banking RAG system to projects section"
- Translations: "Sync French resume with English version"
- Recent commits show: "veolia update", "1029", "first version", "cv update"

**Branch Strategy**:
- Main branch: `main`
- No feature branches currently (single-user repo)
- Direct commits to main for resume iterations

## Professional Background Summary

**Educational Credentials**:
- **Shanghai Jiao Tong University** (2024-2026): Master in Deep Learning & Mechanical Engineering
- **Mines Paris - PSL** (2021-2026): Diplôme d'Ingénieur (France Excellence Eiffel Scholar)
- **Shanghai Jiao Tong University** (2018-2022): Bachelor in Mechanical Engineering (Shanghai Outstanding Graduate)

**Work Experience**:
- **DeepDyna AI** (Dec 2024-Present): Co-Founder, Full-Stack Developer - AI content automation platform
- **Veolia Asia** (Jan-Jun 2024): Data Science Intern - ML-based HVAC optimization for West Kowloon Cultural District
- **b:bot by GreenBig** (May-Nov 2023): CV & Embedded Systems Intern - YOLOv8 deployment on Jetson Nano

**Core Competencies**:
- LLM application development (RAG, MCP agents, multi-provider integration)
- Data engineering (PostgreSQL, pgvector, ETL pipelines)
- Computer vision (YOLOv8, dual-modality detection, Azure ML)
- Full-stack development (Flask, FastAPI, async Python)
- Blockchain/Web3 (Solidity, on-chain analytics, DeFi)

This repository serves as both a version-controlled resume management system and a comprehensive portfolio reference for job applications in data science, ML engineering, and software development roles.
