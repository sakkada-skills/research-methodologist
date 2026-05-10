# Research Methodology Agent

A structured prompt-based AI skill for analyzing academic research texts. The agent acts as a scientific methodologist: it evaluates research design, checks the correctness of formulations, assesses method selection, and provides concrete, actionable feedback with corrected examples.

Designed for use with Claude (via Claude.ai Skills, Claude Code, or the API), but fully portable to any LLM that supports system prompts.

---

## What It Does

The agent performs a two-block structured analysis of any academic text:

**Block A — Methodology**
- Problem statement and relevance (research gap identification)
- State of the art / literature review
- Research aim, objectives, object, and subject
- Hypothesis (falsifiability, testability, specificity)
- Methods (alignment with aim, justification, reproducibility, sampling)
- Scientific novelty
- Theoretical and practical significance
- Conclusions and results

**Block B — Logic and Structure**
- Chapter architecture
- Internal coherence (theory ↔ empirics connection)
- Argumentation quality and logical errors
- Introduction and conclusion completeness

**Output format**: structured report with status indicators (✅ / ⚠️ / ❌), quoted problem passages, explanations, corrected formulations, and a prioritized action table.

---

## Repository Structure

```
research-methodologist/
├── SKILL.md                          # Main agent prompt and instructions
└── references/
    ├── formulations-guide.md         # Bank of precise vs. imprecise formulation examples
    ├── formulations-commentary.md    # Rules and criteria for evaluating each element
    └── methods-guide.md              # Comprehensive research methods reference
```

### File Roles

| File | Purpose | Size |
|------|---------|------|
| `SKILL.md` | Core agent logic: role, analysis steps, output format, operating principles | ~12 KB |
| `references/formulations-guide.md` | 80+ paired ❌/✅ examples across 15 research elements | ~32 KB |
| `references/formulations-commentary.md` | Evaluation formulas, criteria, and error typologies for each element | ~11 KB |
| `references/methods-guide.md` | 14-section methods reference: paradigms, design types, method guides, sampling, statistics, validity, ethics, checklists | ~58 KB |

---

## Installation and Setup

### Option 1: Claude.ai (web and desktop app)

Skills in Claude.ai are installed as a ZIP file via **Customize → Skills**. 

**Step 1: Download the ZIP and take out README.md and LICENSE.md**

**Step 2: Install in Claude.ai**

1. Go to [claude.ai](https://claude.ai)
2. Open **Customize → Skills**
3. Click **+** → **Create skill**
4. Upload the ZIP file
5. The skill appears in your Skills list — toggle it on
6. Make sure **Code Execution** is enabled in **Settings → Capabilities**

The skill is now active across all your Claude.ai conversations. Claude will load it automatically when you submit an academic text for review.

> **Note**: Skills require code execution to function. If the skill doesn't trigger, verify code execution is enabled and that the skill is toggled on in Customize → Skills.

---

### Option 2: Claude Code

Claude Code loads skills automatically from the `.claude/skills/` directory. Two installation scopes are available:

**Personal install** — skill is available in all your projects:

```bash
# Clone directly into your personal skills directory
git clone https://github.com/YOUR_USERNAME/research-methodologist.git \
  ~/.claude/skills/research-methodologist
```

**Project install** — skill is scoped to one repository and shared with anyone who clones it:

```bash
cd your-project
mkdir -p .claude/skills
git clone https://github.com/YOUR_USERNAME/research-methodologist.git \
  .claude/skills/research-methodologist
```

**Install via npx** (if published to a registry):

```bash
npx skills add YOUR_USERNAME/research-methodologist
```

Once installed, Claude Code picks up the skill automatically — no restart needed. Invoke it explicitly or let Claude load it when relevant:

```bash
# Explicit invocation
claude "/research-methodologist analyze this paper introduction:" < intro.txt

# Or interactively — Claude will load the skill automatically
claude
> Review the methodology of this paper: [paste text]
```

---

### Option 3: Anthropic API

Use the agent programmatically in your own application or pipeline.

```python
import anthropic
from pathlib import Path

client = anthropic.Anthropic()

def load_skill():
    skill = Path("SKILL.md").read_text()
    formulations_guide = Path("references/formulations-guide.md").read_text()
    formulations_commentary = Path("references/formulations-commentary.md").read_text()
    methods_guide = Path("references/methods-guide.md").read_text()
    
    system_prompt = f"""{skill}

---

## Reference Files

### formulations-guide.md
{formulations_guide}

### formulations-commentary.md
{formulations_commentary}

### methods-guide.md
{methods_guide}
"""
    return system_prompt

def analyze_paper(text: str) -> str:
    response = client.messages.create(
        model="claude-opus-4-5",
        max_tokens=4096,
        system=load_skill(),
        messages=[
            {"role": "user", "content": f"Please analyze the following academic text:\n\n{text}"}
        ]
    )
    return response.content[0].text

# Example
with open("my_paper.txt") as f:
    paper = f.read()

report = analyze_paper(paper)
print(report)
```

**Batch processing** — analyze multiple files:

```python
import json
from pathlib import Path

system = load_skill()
results = {}

for paper_path in Path("papers/").glob("*.txt"):
    response = client.messages.create(
        model="claude-opus-4-5",
        max_tokens=4096,
        system=system,
        messages=[{"role": "user", "content": paper_path.read_text()}]
    )
    results[paper_path.name] = response.content[0].text

with open("analysis_results.json", "w") as f:
    json.dump(results, f, ensure_ascii=False, indent=2)
```

---

### Option 4: Other LLMs

The skill is model-agnostic. The prompt uses plain instructions without Claude-specific syntax. Tested patterns for other providers:

**OpenAI (GPT-4o, o1)**

```python
from openai import OpenAI
from pathlib import Path

client = OpenAI()

system_prompt = (
    Path("SKILL.md").read_text() + "\n\n" +
    Path("references/formulations-guide.md").read_text() + "\n\n" +
    Path("references/formulations-commentary.md").read_text() + "\n\n" +
    Path("references/methods-guide.md").read_text()
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "Analyze this paper introduction:\n\n" + paper_text}
    ],
    max_tokens=4096
)

print(response.choices[0].message.content)
```

**Google Gemini**

```python
import google.generativeai as genai
from pathlib import Path

genai.configure(api_key="YOUR_API_KEY")

system_prompt = "\n\n".join([
    Path("SKILL.md").read_text(),
    Path("references/formulations-guide.md").read_text(),
    Path("references/formulations-commentary.md").read_text(),
    Path("references/methods-guide.md").read_text()
])

model = genai.GenerativeModel(
    model_name="gemini-1.5-pro",
    system_instruction=system_prompt
)

response = model.generate_content("Analyze this paper:\n\n" + paper_text)
print(response.text)
```

**Local models via Ollama**

```bash
# Combine all files into one system prompt
cat SKILL.md references/*.md > full_prompt.txt

# Run with ollama
ollama run llama3.1 "$(cat full_prompt.txt)\n\nNow analyze this text: $(cat my_paper.txt)"
```

> **Note on context window**: the full knowledge base is ~113 KB (~28,000 tokens). Make sure your model's context window can accommodate the system prompt plus the paper being analyzed. Models with 32K+ context work reliably; for smaller windows, load only `SKILL.md` + `formulations-commentary.md` (the minimum viable setup).

---

## Practical Use Cases

### For Students and PhD Candidates

- **Introduction review**: paste your introduction draft — the agent checks all mandatory elements (problem, gap, aim, objectives, hypothesis, object/subject, methods, novelty, significance)
- **Hypothesis quality check**: verify that your hypothesis is falsifiable, specific, and non-trivial before submitting
- **Method justification**: get feedback on whether your chosen methods are appropriate for your research aim
- **Pre-defense preparation**: run a full methodological audit before submitting to your supervisor

### For Academic Supervisors

- **Structured feedback generation**: analyze a student's draft and receive a formatted report you can share directly
- **Batch review**: use the API setup to process multiple student papers and generate consistent feedback reports
- **Grading rubric alignment**: the agent's evaluation criteria can be mapped to standard dissertation assessment rubrics

### For Peer Reviewers

- **First-pass methodology check**: quickly identify methodological weaknesses before writing a full review
- **Logical error detection**: the agent explicitly checks for post hoc reasoning, false dichotomies, circular arguments, and correlation/causation confusion
- **Novelty assessment**: verify whether the claimed novelty is substantive and proportionate to the work's scope

### For Research Teams and Labs

- **Standardized methodology QA**: establish a consistent internal review process across team members
- **Grant proposal review**: check the methodology section of grant applications before submission
- **Systematic review of literature**: use the bibliometric analysis section of `methods-guide.md` as a reference when designing literature review protocols

### For Journal Editors

- **Desk rejection decision support**: run a quick methodological scan before sending to peer review
- **Reviewer briefing**: use the output report as a structured briefing document for reviewers

---

## How the Knowledge Base Works

The agent loads three reference files at the start of each analysis session:

**`formulations-guide.md`** contains 80+ paired examples organized by research element. Each entry shows an incorrect formulation (❌) followed by a corrected version (✅) with the same content. The agent uses these as pattern templates when generating corrected formulations for the user's text.

**`formulations-commentary.md`** contains the evaluation logic: formulas, criteria checklists, and error typologies for each of the 15 research elements. The agent uses these rules to justify every remark it makes.

**`methods-guide.md`** is a standalone methods reference covering:
- 4 research paradigms with diagnostics
- 5 research design types with case examples
- Aim-to-method matrix (9 aim types → recommended methods)
- 11 quantitative and qualitative method guides with error checklists
- 6 mixed methods designs
- Sampling strategies and sample size justification tables
- Statistical test decision tree
- Validity/reliability frameworks for both quantitative and qualitative research
- Research ethics requirements
- 12 common methodological error patterns
- Method description checklist (14 mandatory + 10 optional elements)
- Software recommendations, reporting standards (PRISMA, CONSORT, COREQ, JARS), and glossary

---

## Customization

### Adapting for a Specific Discipline

To specialize the agent for a particular field (e.g., medicine, economics, computer science):

1. In `SKILL.md`, update the **Role** section to specify the discipline
2. In `references/formulations-guide.md`, add domain-specific ❌/✅ examples
3. In `references/methods-guide.md`, expand the relevant method sections (e.g., add clinical trial specifics for medicine, or ML evaluation protocols for computer science)

### Adjusting Output Format

The output report format is defined in **Step 3** of `SKILL.md`. You can modify:
- Section headers and their order
- Status indicator symbols
- Priority table structure
- Level of detail per element

### Adding Reporting Standards

`methods-guide.md` Appendix B lists major reporting standards (PRISMA, CONSORT, etc.). To enforce a specific standard, add a check for it in the relevant method section of `SKILL.md`.

---

## Limitations

- The agent **does not check plagiarism**, spelling, punctuation, or citation formatting
- The agent **does not assign numerical scores** — feedback is qualitative and directional
- The agent **does not write sections** on behalf of the author — it shows direction and provides examples
- Analysis quality depends on the completeness of the submitted text. A full introduction produces a more accurate analysis than isolated fragments
- For papers in languages other than English, performance depends on the base model's multilingual capability. The knowledge base is in English; the agent can analyze texts in other languages but will reference English-language criteria

---

## Contributing

Contributions are welcome, particularly:

- Additional ❌/✅ formulation examples for underrepresented disciplines
- Domain-specific method guides (medicine, law, engineering, education)
- Translations of the knowledge base into other languages
- Corrections to statistical or methodological content

Please open an issue before submitting a large pull request.

---

## References

The methods reference is grounded in the following sources:

- Creswell & Creswell (2022) *Research Design: Qualitative, Quantitative, and Mixed Methods Approaches*
- Bryman (2016) *Social Research Methods*
- Saunders, Lewis & Thornhill (2019) *Research Methods for Business Students*
- Yin (2018) *Case Study Research and Applications*
- Creswell & Plano Clark (2018) *Designing and Conducting Mixed Methods Research*
- Braun & Clarke (2006, 2019) — thematic analysis framework
- Charmaz (2014) *Constructing Grounded Theory*
- Miles, Huberman & Saldaña (2020) *Qualitative Data Analysis*
- Field (2018) *Discovering Statistics Using IBM SPSS*
- Lincoln & Guba (1985) — qualitative validity framework
- Cohen (1988) — effect size conventions
- Patton (2015) — purposive sampling typology

---

## License

MIT License. You are free to use, modify, and distribute this skill for any purpose, including commercial use.
# Research Methodology Agent

A structured prompt-based AI skill for analyzing academic research texts. The agent acts as a scientific methodologist: it evaluates research design, checks the correctness of formulations, assesses method selection, and provides concrete, actionable feedback with corrected examples.

Designed for use with Claude (via Claude.ai Skills, Claude Code, or the API), but fully portable to any LLM that supports system prompts.

---

## What It Does

The agent performs a two-block structured analysis of any academic text:

**Block A — Methodology**
- Problem statement and relevance (research gap identification)
- State of the art / literature review
- Research aim, objectives, object, and subject
- Hypothesis (falsifiability, testability, specificity)
- Methods (alignment with aim, justification, reproducibility, sampling)
- Scientific novelty
- Theoretical and practical significance
- Conclusions and results

**Block B — Logic and Structure**
- Chapter architecture
- Internal coherence (theory ↔ empirics connection)
- Argumentation quality and logical errors
- Introduction and conclusion completeness

**Output format**: structured report with status indicators (✅ / ⚠️ / ❌), quoted problem passages, explanations, corrected formulations, and a prioritized action table.

---

## Repository Structure

```
research-methodologist/
├── SKILL.md                          # Main agent prompt and instructions
└── references/
    ├── formulations-guide.md         # Bank of precise vs. imprecise formulation examples
    ├── formulations-commentary.md    # Rules and criteria for evaluating each element
    └── methods-guide.md              # Comprehensive research methods reference
```

### File Roles

| File | Purpose | Size |
|------|---------|------|
| `SKILL.md` | Core agent logic: role, analysis steps, output format, operating principles | ~12 KB |
| `references/formulations-guide.md` | 80+ paired ❌/✅ examples across 15 research elements | ~32 KB |
| `references/formulations-commentary.md` | Evaluation formulas, criteria, and error typologies for each element | ~11 KB |
| `references/methods-guide.md` | 14-section methods reference: paradigms, design types, method guides, sampling, statistics, validity, ethics, checklists | ~58 KB |

---

## Installation and Setup

### Option 1: Claude.ai Skills (Recommended for non-developers)

Claude Skills allow you to create a persistent, reusable agent in your Claude workspace.

1. Go to [claude.ai](https://claude.ai) and open **Projects**
2. Create a new Project: `Research Methodologist`
3. In Project settings, open **Custom Instructions**
4. Copy the full contents of `SKILL.md` and paste it into the instructions field
5. Upload the three reference files from the `references/` folder as Project knowledge files:
   - `formulations-guide.md`
   - `formulations-commentary.md`
   - `methods-guide.md`
6. Save the Project

The agent will now be available in all conversations within that Project, with persistent access to the reference files.

**Usage**: paste or upload your academic text and ask the agent to review it.

---

### Option 2: Claude Code

Claude Code is Anthropic's CLI tool for agentic tasks. It can read local files directly, making this the most powerful setup — the agent loads the full knowledge base on every run.

**Prerequisites**: [Install Claude Code](https://docs.anthropic.com/en/docs/claude-code)

**Setup**:

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/research-methodologist.git
cd research-methodologist
```

**Basic usage** — analyze a file:

```bash
claude "Read SKILL.md and all files in references/, then analyze the following paper introduction:" < my_paper_intro.txt
```

**Or interactively**:

```bash
claude
> Read SKILL.md and all files in the references/ folder.
> Then analyze this text: [paste your text]
```

**As a reusable command** — add to your shell config (`~/.bashrc` or `~/.zshrc`):

```bash
methodologist() {
  claude "Read $(pwd)/SKILL.md and all files in $(pwd)/references/, then analyze this academic text: $(cat $1)"
}
```

Then run:

```bash
methodologist my_thesis_intro.txt
```

**With a CLAUDE.md project file** — place a `CLAUDE.md` in the repository root so Claude Code automatically loads the context:

```markdown
# Research Methodology Agent

When activated, read SKILL.md and all files in references/ before proceeding.
Apply the full analysis framework from SKILL.md to any academic text provided.
```

Then simply run `claude` from the repository directory — it will auto-load the context.

---

### Option 3: Anthropic API

Use the agent programmatically in your own application or pipeline.

```python
import anthropic
from pathlib import Path

client = anthropic.Anthropic()

def load_skill():
    skill = Path("SKILL.md").read_text()
    formulations_guide = Path("references/formulations-guide.md").read_text()
    formulations_commentary = Path("references/formulations-commentary.md").read_text()
    methods_guide = Path("references/methods-guide.md").read_text()
    
    system_prompt = f"""{skill}

---

## Reference Files

### formulations-guide.md
{formulations_guide}

### formulations-commentary.md
{formulations_commentary}

### methods-guide.md
{methods_guide}
"""
    return system_prompt

def analyze_paper(text: str) -> str:
    response = client.messages.create(
        model="claude-opus-4-5",
        max_tokens=4096,
        system=load_skill(),
        messages=[
            {"role": "user", "content": f"Please analyze the following academic text:\n\n{text}"}
        ]
    )
    return response.content[0].text

# Example
with open("my_paper.txt") as f:
    paper = f.read()

report = analyze_paper(paper)
print(report)
```

**Batch processing** — analyze multiple files:

```python
import json
from pathlib import Path

system = load_skill()
results = {}

for paper_path in Path("papers/").glob("*.txt"):
    response = client.messages.create(
        model="claude-opus-4-5",
        max_tokens=4096,
        system=system,
        messages=[{"role": "user", "content": paper_path.read_text()}]
    )
    results[paper_path.name] = response.content[0].text

with open("analysis_results.json", "w") as f:
    json.dump(results, f, ensure_ascii=False, indent=2)
```

---

### Option 4: Other LLMs

The skill is model-agnostic. The prompt uses plain instructions without Claude-specific syntax. Tested patterns for other providers:

**OpenAI (GPT-4o, o1)**

```python
from openai import OpenAI
from pathlib import Path

client = OpenAI()

system_prompt = (
    Path("SKILL.md").read_text() + "\n\n" +
    Path("references/formulations-guide.md").read_text() + "\n\n" +
    Path("references/formulations-commentary.md").read_text() + "\n\n" +
    Path("references/methods-guide.md").read_text()
)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "Analyze this paper introduction:\n\n" + paper_text}
    ],
    max_tokens=4096
)

print(response.choices[0].message.content)
```

**Google Gemini**

```python
import google.generativeai as genai
from pathlib import Path

genai.configure(api_key="YOUR_API_KEY")

system_prompt = "\n\n".join([
    Path("SKILL.md").read_text(),
    Path("references/formulations-guide.md").read_text(),
    Path("references/formulations-commentary.md").read_text(),
    Path("references/methods-guide.md").read_text()
])

model = genai.GenerativeModel(
    model_name="gemini-1.5-pro",
    system_instruction=system_prompt
)

response = model.generate_content("Analyze this paper:\n\n" + paper_text)
print(response.text)
```

**Local models via Ollama**

```bash
# Combine all files into one system prompt
cat SKILL.md references/*.md > full_prompt.txt

# Run with ollama
ollama run llama3.1 "$(cat full_prompt.txt)\n\nNow analyze this text: $(cat my_paper.txt)"
```

> **Note on context window**: the full knowledge base is ~113 KB (~28,000 tokens). Make sure your model's context window can accommodate the system prompt plus the paper being analyzed. Models with 32K+ context work reliably; for smaller windows, load only `SKILL.md` + `formulations-commentary.md` (the minimum viable setup).

---

## Practical Use Cases

### For Students and PhD Candidates

- **Introduction review**: paste your introduction draft — the agent checks all mandatory elements (problem, gap, aim, objectives, hypothesis, object/subject, methods, novelty, significance)
- **Hypothesis quality check**: verify that your hypothesis is falsifiable, specific, and non-trivial before submitting
- **Method justification**: get feedback on whether your chosen methods are appropriate for your research aim
- **Pre-defense preparation**: run a full methodological audit before submitting to your supervisor

### For Academic Supervisors

- **Structured feedback generation**: analyze a student's draft and receive a formatted report you can share directly
- **Batch review**: use the API setup to process multiple student papers and generate consistent feedback reports
- **Grading rubric alignment**: the agent's evaluation criteria can be mapped to standard dissertation assessment rubrics

### For Peer Reviewers

- **First-pass methodology check**: quickly identify methodological weaknesses before writing a full review
- **Logical error detection**: the agent explicitly checks for post hoc reasoning, false dichotomies, circular arguments, and correlation/causation confusion
- **Novelty assessment**: verify whether the claimed novelty is substantive and proportionate to the work's scope

### For Research Teams and Labs

- **Standardized methodology QA**: establish a consistent internal review process across team members
- **Grant proposal review**: check the methodology section of grant applications before submission
- **Systematic review of literature**: use the bibliometric analysis section of `methods-guide.md` as a reference when designing literature review protocols

### For Journal Editors

- **Desk rejection decision support**: run a quick methodological scan before sending to peer review
- **Reviewer briefing**: use the output report as a structured briefing document for reviewers

---

## How the Knowledge Base Works

The agent loads three reference files at the start of each analysis session:

**`formulations-guide.md`** contains 80+ paired examples organized by research element. Each entry shows an incorrect formulation (❌) followed by a corrected version (✅) with the same content. The agent uses these as pattern templates when generating corrected formulations for the user's text.

**`formulations-commentary.md`** contains the evaluation logic: formulas, criteria checklists, and error typologies for each of the 15 research elements. The agent uses these rules to justify every remark it makes.

**`methods-guide.md`** is a standalone methods reference covering:
- 4 research paradigms with diagnostics
- 5 research design types with case examples
- Aim-to-method matrix (9 aim types → recommended methods)
- 11 quantitative and qualitative method guides with error checklists
- 6 mixed methods designs
- Sampling strategies and sample size justification tables
- Statistical test decision tree
- Validity/reliability frameworks for both quantitative and qualitative research
- Research ethics requirements
- 12 common methodological error patterns
- Method description checklist (14 mandatory + 10 optional elements)
- Software recommendations, reporting standards (PRISMA, CONSORT, COREQ, JARS), and glossary

---

## Customization

### Adapting for a Specific Discipline

To specialize the agent for a particular field (e.g., medicine, economics, computer science):

1. In `SKILL.md`, update the **Role** section to specify the discipline
2. In `references/formulations-guide.md`, add domain-specific ❌/✅ examples
3. In `references/methods-guide.md`, expand the relevant method sections (e.g., add clinical trial specifics for medicine, or ML evaluation protocols for computer science)

### Adjusting Output Format

The output report format is defined in **Step 3** of `SKILL.md`. You can modify:
- Section headers and their order
- Status indicator symbols
- Priority table structure
- Level of detail per element

### Adding Reporting Standards

`methods-guide.md` Appendix B lists major reporting standards (PRISMA, CONSORT, etc.). To enforce a specific standard, add a check for it in the relevant method section of `SKILL.md`.

---

## Limitations

- The agent **does not check plagiarism**, spelling, punctuation, or citation formatting
- The agent **does not assign numerical scores** — feedback is qualitative and directional
- The agent **does not write sections** on behalf of the author — it shows direction and provides examples
- Analysis quality depends on the completeness of the submitted text. A full introduction produces a more accurate analysis than isolated fragments
- For papers in languages other than English, performance depends on the base model's multilingual capability. The knowledge base is in English; the agent can analyze texts in other languages but will reference English-language criteria

---

## Contributing

Contributions are welcome, particularly:

- Additional ❌/✅ formulation examples for underrepresented disciplines
- Domain-specific method guides (medicine, law, engineering, education)
- Translations of the knowledge base into other languages
- Corrections to statistical or methodological content

Please open an issue before submitting a large pull request.

---

## References

The methods reference is grounded in the following sources:

- Creswell & Creswell (2022) *Research Design: Qualitative, Quantitative, and Mixed Methods Approaches*
- Bryman (2016) *Social Research Methods*
- Saunders, Lewis & Thornhill (2019) *Research Methods for Business Students*
- Yin (2018) *Case Study Research and Applications*
- Creswell & Plano Clark (2018) *Designing and Conducting Mixed Methods Research*
- Braun & Clarke (2006, 2019) — thematic analysis framework
- Charmaz (2014) *Constructing Grounded Theory*
- Miles, Huberman & Saldaña (2020) *Qualitative Data Analysis*
- Field (2018) *Discovering Statistics Using IBM SPSS*
- Lincoln & Guba (1985) — qualitative validity framework
- Cohen (1988) — effect size conventions
- Patton (2015) — purposive sampling typology

---

## License

MIT License. You are free to use, modify, and distribute this skill for any purpose, including commercial use.
# research-methodologist
Custom skill for Claude | Claude Code | Any LLM you like, which helps in completing academical researches by auditing your research text and seeking for weak parts. Can be useful for goal planning, experiment designing etc. Fully based on common rules and principles. 
