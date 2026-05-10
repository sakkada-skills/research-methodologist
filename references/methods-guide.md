# Research Methods Selection and Correction Guide

Use this reference when analyzing the "Methods" section of a research paper.
Verify that the method aligns with the aim, that the choice is justified, and that the application is correct.
If a method is not appropriate — propose a replacement with justification.

**Sources**: Creswell & Creswell (2022) *Research Design*; Bryman (2016) *Social Research Methods*; Kumar (2019) *Research Methodology*; Saunders, Lewis & Thornhill (2019) *Research Methods for Business Students*; Denzin & Lincoln (2018) *The SAGE Handbook of Qualitative Research*; Charmaz (2014) *Constructing Grounded Theory*; Miles, Huberman & Saldaña (2020) *Qualitative Data Analysis*; Creswell & Plano Clark (2018) *Designing and Conducting Mixed Methods Research*; Field (2018) *Discovering Statistics Using IBM SPSS*; Yin (2018) *Case Study Research and Applications*.

---

## Contents

1. Philosophical Foundations of Research (Paradigms)
2. Types of Research Designs
3. Aim → Method Matrix
4. Quantitative Methods: Detailed Reference
5. Qualitative Methods: Detailed Reference
6. Mixed Methods
7. Sampling Strategies
8. Data Collection: Instruments and Procedures
9. Data Analysis: Statistical and Qualitative Methods
10. Statistical Test Selection: Decision Tree
11. Validity and Reliability
12. Research Ethics
13. Typical Errors in Method Selection and Description
14. Method Description Checklist

---

## 1. Philosophical Foundations of Research (Paradigms)

Method selection always derives from the researcher's paradigm. If the author is not aware of their paradigm — they cannot justify the method. Verify whether the author holds at least an implicit methodological position.

### 1.1. Post-Positivism

- **Ontology**: objective reality exists but is imperfectly known
- **Epistemology**: knowledge is built through hypothesis testing and falsification
- **Methods**: quantitative — experiment, survey, statistical analysis
- **Quality criterion**: internal/external validity, reliability, objectivity
- **When appropriate**: testing cause-and-effect relationships, measuring effects, generalization
- **Typical studies**: influence of X on Y, group comparison, prediction

**Case**: "The impact of agile implementation on development team productivity" → post-positivist design: quasi-experiment, before/after metrics, control group.

### 1.2. Constructivism (Interpretivism)

- **Ontology**: reality is constructed by participants, is multiple
- **Epistemology**: knowledge is the result of interpreting meanings and experience
- **Methods**: qualitative — interviews, observation, narrative analysis
- **Quality criterion**: credibility, transferability, confirmability (Lincoln & Guba, 1985)
- **When appropriate**: studying experience, motivation, cultural practices
- **Typical studies**: perception of change, implementation experience, meanings and interpretations

**Case**: "How employees perceive the transition to remote work" → constructivist design: phenomenological study, in-depth interviews.

### 1.3. Transformativism

- **Ontology**: reality is shaped by power relations and inequality
- **Epistemology**: knowledge is linked to action; research serves emancipation
- **Methods**: participatory action research, critical ethnography
- **When appropriate**: research of marginalized groups, developing interventions for vulnerable communities

### 1.4. Pragmatism

- **Ontology**: reality is what works to solve the problem
- **Epistemology**: knowledge is evaluated by practical usefulness
- **Methods**: mixed methods — combination of quantitative and qualitative
- **When appropriate**: complex applied tasks where one approach is insufficient
- **Typical studies**: program evaluation, instrument development and validation

**Case**: "Evaluation of a digital transformation program in public administration" → pragmatist design: survey of officials (quantitative) + interviews with beneficiaries (qualitative) + KPI analysis (secondary data).

### Diagnostics: When the Paradigm Is a Problem

❌ The author claims a quantitative study but the philosophical position is undefined, and in the "limitations" section states the impossibility of accounting for "subjective factors" — a paradigm contradiction.

❌ The author writes "objective analysis" while using unstructured interviews — a mismatch between paradigm and method.

✅ The author explicitly states: "The study is based on a post-positivist paradigm, which determines the choice of a quasi-experimental design and quantitative data collection methods."

---

## 2. Types of Research Designs

### 2.1. Classification by Research Aim

| Type | Aim | Question | Methods | Example |
|------|-----|----------|---------|---------|
| **Exploratory** | Identify the problem, formulate a hypothesis | "What is happening here?" | Interviews, focus groups, pilot surveys, document analysis | "What barriers exist for blockchain implementation in public procurement?" |
| **Descriptive** | Describe the characteristics of a phenomenon | "What is the situation?" | Surveys, observation, secondary data analysis | "What share of companies use AI by industry?" |
| **Explanatory** | Establish cause-and-effect relationships | "Why is this so?" | Experiment, quasi-experiment, regression | "How does employee training affect productivity?" |
| **Evaluative** | Assess the effectiveness of an intervention | "Does this work?" | Experiment, comparative analysis, before/after analysis | "Did the new CRM improve sales conversion?" |
| **Predictive** | Predict future states | "What will happen?" | Regression, machine learning, time series | "What is the forecast for customer churn?" |

### 2.2. Classification by Research Design

#### Experimental Designs

**True Experiment (RCT — Randomized Controlled Trial)**
- Random assignment of participants to groups
- Manipulation of the independent variable
- Control group
- Gold standard for establishing causality
- Example designs: pretest-posttest control group, posttest-only control group, Solomon four-group

**Case**: A company tests two interfaces (A/B test): users are randomly assigned interface A or B, and conversion is measured. This is a true experiment.

**Quasi-Experiment**
- Manipulation of a variable is present, BUT there is no random assignment
- Used when randomization is impossible or unethical
- Typical designs: nonequivalent control group, interrupted time series
- Threats: selection, history, maturation — require control

**Case**: Implementation of a new motivation system in one department, another department serving as the control group. Groups are not randomized → quasi-experiment. It is necessary to demonstrate equivalence of groups on key parameters before the intervention.

**Pre-Experiment**
- One group, no control, no randomization
- One-shot case study, one-group pretest-posttest
- Minimal internal validity
- Acceptable only as a pilot study

#### Non-Experimental Designs

**Cross-Sectional**
- Data collected at one point in time
- Suitable for description and correlations
- NOT suitable for causal inferences or studying dynamics
- Most widespread design in social sciences

**Longitudinal**
- Data collected at multiple time points
- Types: panel (same respondents), trend (different samples), cohort (one cohort)
- Suitable for studying dynamics and predictive models
- Problem: respondent attrition

**Cohort Study**
- A group with a common characteristic is followed over time
- Prospective: from cause to effect
- Retrospective: from effect to cause
- Applications: epidemiology, sociology, marketing

**Case Study**
- In-depth study of one or several cases in real context (Yin, 2018)
- Case types: single/multiple; explanatory/descriptive/exploratory
- Requirements: justification of case selection, data triangulation, chain of evidence
- Suitable for "how?" and "why?" questions in complex contexts

**Case**: "How company X implemented a blockchain solution in the supply chain" → single explanatory case study. Sources: interviews with managers, project documents, financial reports, observation.

---

## 3. Aim → Method Matrix

If the research aim is → recommended methods:

### "Identify factors / determine influence"

→ Correlation analysis, regression, factor analysis
→ Required: quantitative data, sufficient sample (N≥30 for parametric tests)
→ NOT suitable: descriptive literature review, expert interviews (unless followed by quantification)

**Example**: Aim — "Identify the factors affecting customer loyalty." Method: survey (N=300) measuring 12 potential predictors, multiple regression with stepwise inclusion of variables, multicollinearity check (VIF<5).

### "Develop a model / methodology / algorithm"

→ Modeling, systems analysis, design science research
→ Required: piloting/validation of the developed product
→ Typical error: model is "developed" but not tested on data

**Example**: Aim — "Develop a model for assessing digital transformation maturity." Method: (1) review of existing models, (2) expert interviews to form criteria, (3) model validation through an expert survey with the Delphi method, (4) piloting on 5 organizations.

### "Classify / typologize"

→ Cluster analysis, content analysis, grounded theory
→ Criterion: the classification must be mutually exclusive and exhaustive (MECE)

**Example**: Aim — "Typologize digital transformation strategies of industrial enterprises." Method: cluster analysis (k-means or hierarchical) using 8 parameters on a sample of N=120 enterprises. Optimal number of clusters determined by the elbow method and silhouette coefficient.

### "Assess effectiveness / compare"

→ Experiment, quasi-experiment, comparative analysis
→ Required: control group / benchmark, before/after metrics
→ Typical error: "effectiveness assessment" without a control group and baseline metrics

**Example**: Aim — "Assess the effectiveness of Scrum implementation in project teams." Method: quasi-experiment. Experimental group — 10 teams that transitioned to Scrum. Control — 10 teams with a traditional approach. Metrics: velocity, defect rate, team satisfaction. Measurements: 3 months before and 6 months after. Test: repeated-measures ANOVA.

### "Understand experience / perception / motivation"

→ In-depth interviews, focus groups, phenomenological analysis, narrative analysis
→ NOT suitable: questionnaire with closed questions (does not reveal depth)

**Example**: Aim — "Study the experience of crypto investors in making investment decisions under conditions of high volatility." Method: phenomenological study, 15 semi-structured interviews, interpretive phenomenological analysis (IPA, Smith et al., 2009). Informant criteria: investment experience ≥2 years, experience of at least one "bear market".

### "Test a hypothesis about differences between groups"

→ t-test, ANOVA, chi-square, Mann-Whitney U test
→ Selection depends on: data type (interval/ordinal), normality of distribution, number of groups

**Example**: Hypothesis — "The level of trust in DeFi protocols differs between users with experience ≤1 year and >3 years." Method: survey (N=200), trust scale (7-point Likert, Cronbach's α=0.85). Test: Mann-Whitney U (ordinal data). Effect size: r = Z / √N.

### "Forecast / predict"

→ Regression (linear, logistic), machine learning, time series
→ Required: split into training and test samples, forecast quality metrics

**Example**: Aim — "Build a model for predicting customer churn in an online service." Method: logistic regression + gradient boosting. Data: 50,000 user records. Split: 70/30 (train/test). Metrics: AUC-ROC, precision, recall, F1. Cross-validation: 5-fold.

### "Study a process / dynamics of change"

→ Case study, longitudinal study, process analysis
→ Typical error: one data cross-section when aiming to study dynamics

**Example**: Aim — "Study the process of blockchain institutionalization in the financial sector." Method: multiple case study (3 banks), longitudinal design (18 months of observation). Data: 24 interviews (3 waves), internal documents, public reporting. Analytical strategy: pattern matching + cross-case synthesis (Yin, 2018).

### "Study the state / prevalence"

→ Descriptive design: survey, secondary data analysis, content analysis
→ Suitable for "what?" and "how many?" questions
→ NOT suitable for establishing causes

**Example**: Aim — "Determine the level of small business awareness of blockchain technology." Method: stratified survey (N=500) by industry and company size. Analysis: descriptive statistics (frequencies, proportions, 95% CI), cross-tabulation by industry (χ²).


---

## 4. Quantitative Methods: Detailed Reference

### 4.1. Experiment

**Essence**: the researcher controls the independent variable and observes its effect on the dependent variable, while controlling all other factors.

**Key elements**:
- Independent variable (what is manipulated)
- Dependent variable (what is measured)
- Controlled variables (potential confounders)
- Randomization (random assignment to groups)
- Control group
- Blind/double-blind assignment (if applicable)

**Designs**:
- **Pre-test/Post-test control group**: measurement before and after + control group
- **Post-test only control group**: only measurement after (if pre-test may affect the result)
- **Solomon four-group**: combination of both — controls for the testing effect
- **Factorial design**: two or more independent factors — allows studying factor interactions

**When to use**: when causality needs to be established and randomization is possible.

**When NOT to use**: randomization is unethical (e.g., denying treatment to a group); controlling the environment is impossible; the question is descriptive, not causal.

**Typical errors**:
- ❌ No control group → impossible to separate the intervention effect from external factors
- ❌ Small sample size → insufficient statistical power
- ❌ No power analysis before the experiment begins
- ❌ Causal conclusions from a quasi-experimental design without caveats

### 4.2. Survey

**Essence**: collection of standardized data from a large number of respondents.

**Instruments**: questionnaire, structured interview.

**Question types**:
- Closed (Likert scale, multiple choice, ranking)
- Open-ended (free text — complicates analysis but provides depth)
- Scale-based (semantic differential, visual analog scale)

**Key requirements for a questionnaire**:
1. Operationalization of constructs (how an abstract concept becomes measurable questions)
2. Piloting (N≥10–30 to verify question comprehension)
3. Scale reliability (Cronbach's α ≥ 0.7; if ≥0.9 — possible redundancy)
4. Validity: content (expert assessment), construct (factor analysis), criterion-related (correlation with an external criterion)
5. Question order: from general to specific, sensitive questions — at the end
6. Absence of double-barreled questions, leading formulations, negations

**Distribution methods**: online (Google Forms, SurveyMonkey, Typeform), paper, telephone, face-to-face.

**Typical errors**:
- ❌ No piloting → questions are unclear, data quality is poor
- ❌ Response rate not stated → representativeness unclear
- ❌ Convenience sample with a claim to generalization
- ❌ 5-point Likert scale treated as interval data without caveats
- ❌ No check for common method bias when DV and IV are collected from the same source

**Case — good description**:
✅ "An online survey was conducted among IT professionals in April–May 2024 via the Qualtrics platform. The questionnaire contained 32 questions grouped into 4 constructs. The scales were adapted from Davis (1989) TAM and Venkatesh et al. (2003) UTAUT. Piloting: N=25; as a result, 3 questions were removed (corrected correlation <0.3). Final Cronbach's α: 0.78–0.89 across scales. 500 invitations were sent, 187 responses received (response rate 37.4%), of which 163 were valid. Sample: 58% male, average tenure 7.2 years (SD=3.8). Harman's test showed that the first factor explains 28.3% of the variance — common method bias is not a critical problem."

### 4.3. Secondary Data Analysis

**Essence**: use of data collected by others (statistics, databases, reports, registries).

**Sources**: national statistical offices, World Bank, OECD, Eurostat, CoinMarketCap, Crunchbase, Bloomberg, Web of Science, Scopus, open APIs.

**Advantages**: large samples, long time series, low cost, high external validity.

**Limitations**: cannot control data quality, variables may not precisely correspond to constructs, possible missing data.

**Description requirements**:
1. Data source and period
2. Selection criteria for observations (inclusion/exclusion)
3. Handling of missing data (deletion, imputation, multiple imputation)
4. List of variables with definitions
5. Data limitations

### 4.4. Bibliometric Analysis

**Essence**: quantitative analysis of academic publications to identify trends, key authors, and topic clusters.

**Tools**: VOSviewer, Bibliometrix (R), CiteSpace, Gephi.

**Procedure**: define databases (WoS, Scopus) → search query → filtering criteria → data export → analysis (co-citation, bibliographic coupling, co-authorship, keyword analysis).

**Reporting standard**: PRISMA for systematic review.

**Typical errors**:
- ❌ Search query not specified — not reproducible
- ❌ Only one database without justification
- ❌ No time boundaries for the search
- ❌ Bibliometric analysis is claimed as a method, but the result is only a literature review without quantitative analysis of metadata

---

## 5. Qualitative Methods: Detailed Reference

### 5.1. Grounded Theory

**Founders**: Glaser & Strauss (1967); three schools: Glaserian, Straussian (Strauss & Corbin), constructivist (Charmaz, 2014).

**Essence**: inductive construction of theory from data. The theory does not precede the research; it emerges from it.

**Procedure**:
1. **Open coding**: data are broken into concepts (line-by-line or incident-by-incident)
2. **Axial coding**: concepts are grouped into categories; relationships are established (conditions → action → consequences)
3. **Selective coding**: the core category is identified; all others are integrated around it
4. **Theoretical sampling**: new data are collected purposefully to verify and saturate categories
5. **Theoretical saturation**: new data yield no new categories or properties

**When to use**: the phenomenon is under-studied, no appropriate theory exists, a process or interaction needs to be explained.

**Typical errors**:
- ❌ Grounded theory is claimed, but convenience rather than theoretical sampling is used
- ❌ No description of the coding process, no examples of codes
- ❌ "Theory" is a list of themes, not a coherent explanatory model with a core category
- ❌ Theoretical saturation is claimed but not justified (how was it determined? after how many interviews?)
- ❌ A preliminary literature review creates a framework, and data are "fitted" to it → contradicts GT logic

**Case — correct description**:
✅ "The study is based on the constructivist approach to grounded theory (Charmaz, 2014). 18 semi-structured interviews were conducted with entrepreneurs in the DeFi space. The initial sample (N=5) was purposive; subsequent informants were selected based on theoretical sampling to verify emerging categories. Coding: initial coding (line-by-line) → focused coding → theoretical coding. Example: the fragment 'I don't trust smart contract auditors after the X incident' → initial code: 'distrust of auditors' → focused code: 'skepticism toward trust infrastructure' → category: 'construction of trust in a decentralized environment'. Saturation was reached at the 15th interview (the last 3 interviews yielded no new categories). Result: a substantive theory X describing process Y."

### 5.2. Thematic Analysis

**Founders**: Braun & Clarke (2006, 2019).

**Essence**: identification, analysis, and description of patterns (themes) in data. A flexible method applicable across paradigms.

**Procedure (6 phases per Braun & Clarke)**:
1. Familiarization with data (reading and re-reading, recording impressions)
2. Generating initial codes (systematic coding across all data)
3. Searching for themes (grouping codes into potential themes)
4. Reviewing themes (matching against coded extracts and the full dataset)
5. Defining and naming themes (refining content, identifying the "story" of each theme)
6. Writing the report (analytical narrative with examples)

**Coding approaches**:
- **Inductive**: codes emerge from the data (bottom-up)
- **Deductive**: codes are pre-defined from theory (top-down)
- **Reflexive thematic analysis** (Braun & Clarke, 2019): emphasizes the researcher's positionality

**When to use**: any qualitative study where patterns need to be identified; suitable for beginners; not tied to a specific paradigm.

**Typical errors**:
- ❌ Themes are merely rephrasing of questions from the interview guide
- ❌ No examples of codes and informant quotes
- ❌ A theme = one code (insufficient depth)
- ❌ No description of whether inductive or deductive coding was used
- ❌ "Thematic analysis" is claimed, but in fact only cases are described without cross-case synthesis

### 5.3. Phenomenology

**Types**:
- **Descriptive (Husserl, Moustakas)**: describes the "essence" of an experience; researcher brackets (suspends) their preconceptions
- **Interpretive (Heidegger, IPA — Smith et al., 2009)**: interprets the meaning of experience from the researcher's perspective

**Essence**: in-depth understanding of the essence of lived experience. Question: "What is it like to experience X?"

**Sample**: 3–10 informants for IPA (Smith et al., 2009); a homogeneous group united by a common experience.

**Typical errors**:
- ❌ Sample >25 — depth is lost; this is not phenomenology
- ❌ Bracketing procedure not described (for descriptive) or reflexivity not described (for IPA)
- ❌ Result describes "what people think", not "how they experience"

### 5.4. Ethnography

**Essence**: immersion of the researcher in a cultural group to study its practices, values, and meanings from within.

**Characteristics**: extended field observation (months–years), participant observation, field notes, artifacts.

**Types**: classical (full immersion), digital ethnography (online communities), autoethnography (reflexive study of one's own experience), netnography (ethnography of online communities, Kozinets, 2020).

**When to use**: studying organizational culture, online communities, subcultures, professional practices.

**Case**: "Netnography of a crypto community on Discord: 6 months of observation across 3 servers, 120 archived discussions, 15 interviews with active participants. Analytical approach: thematic analysis of field notes and transcripts."

### 5.5. Narrative Analysis

**Essence**: analysis of stories told by participants as ways of constructing identity and meaning.

**Types**: structural (Labov), thematic narrative analysis, dialogic/performance analysis.

**When to use**: studying biographies, career trajectories, transformational experience, identity.

### 5.6. Content Analysis

**Essence**: systematic coding of textual/visual content.

**Types**:
- **Quantitative content analysis**: counting the frequency of categories, statistical comparisons
- **Qualitative content analysis** (Mayring, 2014): interpretive coding, reconstruction of meanings

**Mandatory elements**:
1. Population of texts and sampling justification
2. Unit of analysis (article, paragraph, sentence, image)
3. Unit of context (interpretive frame for the unit)
4. Coding categories (definitions, examples, classification rules)
5. Codebook
6. Inter-rater reliability (Cohen's κ ≥ 0.61 — acceptable; ≥ 0.81 — good)
7. Procedure for resolving disagreements between coders

**Typical errors**:
- ❌ "Content analysis" is claimed, but there are no coding categories
- ❌ One coder — no inter-rater reliability
- ❌ No definition of the unit of analysis
- ❌ Source selection not justified (why these media / documents / posts?)
- ❌ Qualitative content analysis is confused with a simple literature review

### 5.7. Case Study

**Primary source**: Yin (2018) *Case Study Research and Applications: Design and Methods*.

**Types by number**:
- Single case: critical, unique, typical, revelatory, longitudinal
- Multiple case: replication logic (literal replication — similar result expected; theoretical replication — different result expected)

**Types by aim**: descriptive, explanatory, exploratory.

**Mandatory components** (Yin, 2018):
1. Justification for case selection and design type
2. Unit of analysis (organization, project, event, person)
3. Theoretical framework or propositions (what directs the analysis)
4. Data triangulation (minimum 2–3 sources: interviews + documents + observation)
5. Chain of evidence: from question → through data → to conclusion
6. Analysis strategy: pattern matching, explanation building, time-series analysis, logic models, cross-case synthesis
7. Description of the case context

**Typical errors**:
- ❌ Case study = "I described one company" without an analytical strategy
- ❌ Single data source (only interviews)
- ❌ No theoretical framework — unclear what to look for and why
- ❌ Multiple case study without cross-case analysis
- ❌ Case selection not justified (why this particular company?)

### 5.8. Interview

**Types**:
- **Structured**: fixed questions in a fixed order (essentially an oral questionnaire)
- **Semi-structured**: a guide with main themes/questions, but digressions and follow-ups are permitted
- **Unstructured (in-depth)**: minimal structure; the informant leads the narrative

**Mandatory description elements**:
1. Type of interview and justification for the choice
2. Interview guide (in an appendix)
3. Number of informants and selection criteria
4. Recording method (audio, video, notes)
5. Transcription method (full, selective)
6. Analysis method (thematic, IPA, narrative, content analysis)
7. Interview duration
8. Quality assurance method (member checking, peer debriefing)

**Recommendations for number of informants**:

| Analysis method | Minimum | Typical range | Source |
|----------------|---------|---------------|--------|
| IPA | 3 | 3–10 | Smith et al. (2009) |
| Thematic analysis (small project) | 6 | 6–15 | Braun & Clarke (2013) |
| Grounded theory | 20–30 | 20–60 | Charmaz (2014) |
| Phenomenology (Moustakas) | 5 | 5–25 | Creswell (2013) |
| Case study | Depends on the case | 5–30 per case | Yin (2018) |

### 5.9. Focus Groups

**Essence**: group interview for studying collective meanings and participant interactions.

**Parameters**:
- Group size: 6–10 people (optimal)
- Number of groups: minimum 3–4 for saturation
- Homogeneity: participants must be similar enough for comfortable discussion
- Roles: moderator + observer/recorder
- Duration: 60–120 minutes

**When to use**: studying group norms, product perception, responses to concepts, social representations.

**When NOT to use**: sensitive topics (participants may not be candid in a group); individual trajectories are needed; the topic requires deep personal engagement.

### 5.10. Observation

**Types**:
- **Participant**: researcher is part of the group
- **Non-participant**: researcher observes from outside
- **Structured**: fixed categories for recording
- **Unstructured**: free field notes

**Mandatory elements**: observation protocol, duration and frequency, description of the researcher's role, data recording strategy.

### 5.11. Delphi Method

**Essence**: iterative expert survey to achieve consensus.

**Procedure**:
1. Formation of expert panel (10–30 experts; selection criteria are mandatory)
2. Round 1: open questions to generate ideas/factors
3. Round 2: structured assessment (ranking, scaling) based on Round 1 results
4. Feedback: each expert sees the aggregated results and their own position
5. Round 3+: re-assessment until consensus is reached (Kendall's W, IQR)
6. Usually 2–4 rounds suffice

**Consensus criterion**: Kendall's concordance coefficient W ≥ 0.7 or IQR ≤ 1 (for scales).

**Typical errors**:
- ❌ One round = this is not Delphi, it is an expert survey
- ❌ No expert selection criteria
- ❌ No consensus criterion — unclear when to stop
- ❌ Expert dropout between rounds is not described


---

## 6. Mixed Methods

**Primary source**: Creswell & Plano Clark (2018) *Designing and Conducting Mixed Methods Research*.

### 6.1. Mixed Methods Designs

| Design | Structure | When to use | Example |
|--------|-----------|-------------|---------|
| **Sequential Explanatory** | QUAN → qual | Quantitative results need qualitative explanation | Survey shows low satisfaction → interviews to understand reasons |
| **Sequential Exploratory** | QUAL → quan | Qualitative data inform an instrument for the quantitative phase | Interviews identify constructs → questionnaire to test on large sample |
| **Convergent Parallel** | QUAN + QUAL | Quantitative and qualitative results need to be compared | Simultaneously: survey (N=300) + interviews (N=15), then comparison and integration |
| **Embedded** | QUAN(qual) or QUAL(quan) | One approach dominates, the second is supplementary | Within an experiment: short interviews to understand participants' experience |
| **Transformative** | Determined by theoretical framework (feminism, critical race theory) | Research aimed at social justice | Evaluation of a migrant support program: statistics + participants' voices |
| **Multiphase** | A series of connected studies | Long-term programs, grants, dissertations | Phase 1: exploratory interviews → Phase 2: questionnaire development → Phase 3: large-scale survey → Phase 4: case study |

### 6.2. Integration Points

Integration is the key distinction between mixed methods and "simply two studies in one paper." Check:

1. **At the design level**: how are the phases connected (sequential, parallel)?
2. **At the methods level**: how do qualitative data inform quantitative data (or vice versa)?
3. **At the interpretation level**: where are the results of the two approaches compared, confirmed, or contradicted?

**Diagnosing the problem**:
❌ "The study uses mixed methods: a survey (N=150) and 5 interviews."
→ But the interviews are mentioned in a separate chapter, and their results are nowhere integrated with the survey data.
→ This is not mixed methods, but a poorly connected quantitative design with illustrative quotes.

✅ "In Phase 1, 12 interviews with managers were conducted (thematic analysis). The identified themes ('implementation barriers', 'motivation factors', 'role of leadership') were operationalized into 24 statements for the survey questionnaire (Phase 2, N=250). In Phase 3, the regression results were compared with the qualitative data in a joint display table: quantitatively significant predictors were confirmed by qualitative examples; discrepancies were identified for the construct 'organizational culture'."

### 6.3. Notation

When recording the design, use the established notation:
- QUAN / QUAL — dominant approach (uppercase)
- quan / qual — supplementary approach (lowercase)
- → sequential design
- + parallel design

Examples: QUAN → qual; QUAL → quan; QUAN + QUAL; QUAN(qual)

---

## 7. Sampling Strategies

### 7.1. Probability Sampling — for Quantitative Research

| Strategy | Essence | When to use | Requirements |
|----------|---------|-------------|--------------|
| **Simple random** | Every element of the population has an equal probability of inclusion | Population is known and accessible | Complete list of elements (sampling frame) |
| **Stratified** | Population is divided into strata (subgroups), with a random sample from each | Representation of subgroups is important | Stratification variables are known |
| **Cluster** | Clusters (e.g., cities, schools) are randomly selected, then all or a random sample within | Population is geographically distributed | List of clusters |
| **Systematic** | Every k-th element from a list | Large list, no stratification | No periodicity in the list |
| **Multi-stage** | Combination of strategies at different levels | Complex populations (e.g., country → region → city → organization → employee) | Sampling frame at each level |

### 7.2. Non-Probability Sampling

| Strategy | Essence | When to use | Limitations |
|----------|---------|-------------|-------------|
| **Convenience** | Whoever is accessible | Pilot studies, limited resources | No basis for generalization |
| **Purposive** | Deliberate selection by criteria | Qualitative studies, expert surveys | Depends on researcher's judgment |
| **Snowball** | Participants recommend others | Hidden/hard-to-reach populations | Clustering around social networks |
| **Quota** | Quotas set by subgroup, with convenience sampling within | Proportionality by group is needed, but no sampling frame | Not random within quotas |
| **Theoretical** | Informant selection guided by emerging theory | Grounded theory | Requires an iterative process |

### 7.3. Purposive Sampling: Subtypes (per Patton, 2015)

- **Maximum variation**: maximum diversity of characteristics → breadth of perspectives
- **Homogeneous**: uniform group → depth on a specific experience
- **Typical case**: a representative case → illustration of the norm
- **Extreme/deviant case**: an outlier case → best/worst practices
- **Critical case**: a case decisive for theory testing → "if it works here — it works everywhere"
- **Criterion sampling**: all who meet a specific criterion
- **Intensity sampling**: cases with vivid manifestations of the studied phenomenon (but not extreme)

### 7.4. Sample Size Justification

**For quantitative research**:

| Analysis method | Minimum N | Recommendation | Source |
|----------------|-----------|----------------|--------|
| t-test | 30 per group | Power analysis (G*Power): α=0.05, power=0.80, effect size=medium → N≈64 per group | Cohen (1992) |
| Correlation | 50 | Stable estimates at N≥50 | Field (2018) |
| Multiple regression | 10–15 per predictor | Minimum 50 + 8×predictors (Tabachnick & Fidell) | Green (1991) |
| Factor analysis | 5 per variable, min 100 | Preferably N≥300 (Comrey & Lee) | Hair et al. (2019) |
| SEM | 200 | 10–20 per parameter; >200 for stable results | Kline (2016) |
| Chi-square | Expected frequency ≥5 in each cell | If <5 — use Fisher's exact test | Field (2018) |
| Cluster analysis | 10× number of variables | For k-means: min 50–100 | Hair et al. (2019) |

**For qualitative research**:
- The concept of "statistical power" is not applicable
- Key criterion: **theoretical/thematic saturation**
- Guest et al. (2006): for thematic analysis, saturation is often reached by 12 interviews
- For justification: describe the point at which new data stopped yielding new codes/themes

**Formula for survey research** (with known population):

n = (Z² × p × q) / e²

Where Z — z-value for confidence level (1.96 for 95%), p — expected proportion (0.5 if unknown), q = 1−p, e — margin of error (0.05 for 5%).

For finite population: n_adj = n / (1 + (n−1)/N)

**Typical errors**:
- ❌ "87 respondents participated in the survey" → Who? How were they selected? Why 87?
- ❌ Convenience sample + generalization to the entire industry
- ❌ N=300 for SEM with 50 parameters — insufficient
- ❌ "Saturation was reached" without describing how this was determined

---

## 8. Data Collection: Instruments and Procedures

### 8.1. Standardized Instruments (Scales, Questionnaires)

If the author uses an existing instrument — check:
- Original reference to the instrument
- Validated in a comparable context (country, industry, culture)?
- If adapted/translated — is the adaptation procedure described (back-translation, piloting)?
- Reliability indicators in this study (Cronbach's α)
- Has the instrument been shortened without justification?

**Examples of standardized instruments**:
- TAM (Davis, 1989): Technology Acceptance Model → perceived usefulness, perceived ease of use
- UTAUT (Venkatesh et al., 2003): Unified Theory of Acceptance and Use of Technology
- SUS (Brooke, 1996): System Usability Scale — 10 items
- NPS (Reichheld, 2003): Net Promoter Score — 1 item
- SERVQUAL (Parasuraman et al., 1988): service quality — 5 dimensions

### 8.2. Custom Instruments

If the author creates their own instrument — check:
1. Operationalization of constructs: how are abstract concepts transformed into questions?
2. Piloting: was it conducted? On what sample?
3. Content validity: assessed by experts?
4. Construct validity: was an exploratory factor analysis (EFA) conducted?
5. Reliability: Cronbach's α ≥ 0.7 for each scale?
6. Item analysis: were items with low corrected correlation (<0.3) removed?

### 8.3. Data Collection Procedure — Mandatory Description Elements

- Data collection period (dates)
- Distribution method (online platform, in person, by mail)
- Response rate (for surveys) and non-response bias analysis
- Duration (for interviews, observations)
- Data recording and storage method
- Informed consent
- Anonymization

---

## 9. Data Analysis: Statistical and Qualitative Methods

### 9.1. Descriptive Statistics

- **Central tendency**: mean (interval/ratio), median (ordinal, skewed), mode (nominal)
- **Dispersion**: standard deviation, IQR (inter-quartile range), range
- **Distribution shape**: skewness, kurtosis
- **Visualization**: histograms, boxplots, scatter plots

### 9.2. Inferential Statistics: Key Tests

#### Group Comparison

| Situation | Parametric test | Non-parametric analog | Conditions |
|-----------|----------------|----------------------|------------|
| 2 independent groups, interval data | t-test (independent samples) | Mann-Whitney U | Normality, homogeneity of variances |
| 2 related groups (before/after) | t-test (paired samples) | Wilcoxon signed-rank | Normality of differences |
| 3+ independent groups | One-way ANOVA | Kruskal-Wallis | Normality, homogeneity of variances (Levene) |
| 3+ related groups | Repeated-measures ANOVA | Friedman | Sphericity (Mauchly) |
| 2 factors, 2+ levels | Two-way ANOVA | ART (Aligned Rank Transform) | Normality, homogeneity |
| Categorical data (frequencies) | — | Chi-square (χ²) / Fisher's exact test | Expected frequency ≥5 |

**Post-hoc tests** (after significant ANOVA):
- Tukey HSD: equal group sizes, homogeneity of variances
- Bonferroni: conservative, any situation
- Games-Howell: unequal group sizes, unequal variances

#### Relationship Between Variables

| Situation | Test | Conditions |
|-----------|------|------------|
| 2 interval variables, normality | Pearson (r) | Linearity, normality, homoscedasticity |
| 2 ordinal/non-normal variables | Spearman (ρ) | Monotonic relationship |
| Categorical variables | Chi-square, Cramér's V, φ | Expected frequency ≥5 |
| Predicting a continuous DV | Linear regression | Normality of residuals, linearity, absence of multicollinearity, homoscedasticity |
| Predicting a binary DV | Logistic regression | Absence of multicollinearity, linearity of logits, sufficient N |
| Latent variables | SEM (structural equation modeling) | N≥200, normality (or robust estimators), theoretical justification of model |

#### Effect Size (always require)

| Test | Effect size | Small | Medium | Large |
|------|------------|-------|--------|-------|
| t-test | Cohen's d | 0.2 | 0.5 | 0.8 |
| ANOVA | η² (eta-squared) | 0.01 | 0.06 | 0.14 |
| Correlation | r | 0.1 | 0.3 | 0.5 |
| Chi-square | Cramér's V | 0.1 | 0.3 | 0.5 |
| Regression | R², f² | 0.02 | 0.15 | 0.35 |

**Typical error**: the author reports the p-value but not the effect size. The p-value depends on N: at N=10,000 even trivial differences will be statistically significant. Effect size shows practical significance.

### 9.3. Multiple Comparisons

When multiple tests are performed — has a correction been applied?
- **Bonferroni**: α_adj = α / m (conservative; suitable for a small number of comparisons)
- **Holm-Bonferroni**: less conservative, orders p-values
- **FDR (Benjamini-Hochberg)**: controls the false discovery rate (preferred for >10 tests)

Without correction: the probability of Type I error is inflated. With 20 tests at α=0.05, the expected number of false positives = 1.

### 9.4. Assumption Testing

**Normality**:
- Visually: Q-Q plot, histogram
- Tests: Shapiro-Wilk (N<50, more powerful), Kolmogorov-Smirnov (N≥50)
- If violated: non-parametric tests, bootstrap, data transformation (log, sqrt)

**Homogeneity of variances**:
- Levene's test — more robust than Bartlett
- If violated: Welch's t-test instead of Student's t-test; Games-Howell post-hoc

**Multicollinearity** (for regression):
- VIF (Variance Inflation Factor): VIF > 5 — problem; VIF > 10 — critical
- Tolerance < 0.2 — problem
- Solutions: remove variables, combine, use PCA/ridge regression

**Linearity** (for regression):
- Scatter plots of DV against each IV
- Residuals vs. fitted values plot: should show random scatter

**Homoscedasticity** (for regression):
- Visually: residuals vs. fitted (cone-shaped pattern = heteroscedasticity)
- Test: Breusch-Pagan
- Solutions: robust standard errors (HC3), WLS, transformation

### 9.5. Qualitative Data Analysis

**General process** (Miles, Huberman & Saldaña, 2020):
1. Data condensation: coding, identifying themes
2. Data display: matrices, networks, diagrams
3. Conclusion drawing/verification

**Coding** (Saldaña, 2021):
- **First cycle codes**: descriptive, in vivo (quotes), process (gerund), emotion, values, etc.
- **Second cycle codes**: pattern, axial, theoretical, focused
- **Software**: NVivo, ATLAS.ti, MAXQDA, Dedoose


---

## 10. Statistical Test Selection: Decision Tree

```
What is the aim of the analysis?
|
+-- COMPARE GROUPS
|   +-- How many groups?
|   |   +-- 2 groups
|   |   |   +-- Related (repeated/paired)?
|   |   |   |   +-- Yes --> Data normal?
|   |   |   |   |   +-- Yes --> Paired t-test
|   |   |   |   |   +-- No  --> Wilcoxon signed-rank
|   |   |   |   +-- No (independent) --> Data normal?
|   |   |   |       +-- Yes --> Variances equal?
|   |   |   |       |   +-- Yes --> Student's t-test
|   |   |   |       |   +-- No  --> Welch's t-test
|   |   |   |       +-- No  --> Mann-Whitney U
|   |   +-- 3+ groups
|   |       +-- Related?
|   |       |   +-- Yes --> Data normal?
|   |       |   |   +-- Yes --> Repeated-measures ANOVA
|   |       |   |   +-- No  --> Friedman
|   |       |   +-- No  --> Data normal?
|   |       |       +-- Yes --> One-way ANOVA --> Post-hoc
|   |       |       +-- No  --> Kruskal-Wallis --> Post-hoc (Dunn)
|   |
|   +-- Data categorical (frequencies)?
|       +-- 2x2 table, expected >=5 --> Chi-square
|       +-- 2x2 table, expected <5  --> Fisher's exact test
|       +-- Larger than 2x2         --> Chi-square
|       +-- Related (before/after, binary) --> McNemar
|
+-- ASSESS RELATIONSHIP
|   +-- Both variables continuous and normal --> Pearson r
|   +-- Ordinal or non-normal              --> Spearman rho
|   +-- Both categorical                   --> phi, Cramer's V, chi-square
|   +-- One continuous, one binary         --> Point-biserial correlation
|
+-- PREDICT AN OUTCOME
|   +-- DV continuous --> Linear regression (simple/multiple)
|   +-- DV binary     --> Logistic regression
|   +-- DV count      --> Poisson regression
|   +-- DV ordinal    --> Ordinal regression
|   +-- Hierarchical/nested data     --> Multilevel modeling (HLM)
|   +-- Latent constructs            --> SEM (AMOS, lavaan, Mplus)
|
+-- REDUCE DIMENSIONALITY / FIND STRUCTURE
    +-- Exploratory factor analysis (EFA)  -- identify latent factors
    +-- Confirmatory factor analysis (CFA) -- verify assumed structure
    +-- Cluster analysis                   -- identify groups of observations
    +-- PCA                                -- reduce dimensionality without a theoretical model
```

---

## 11. Validity and Reliability

### 11.1. For Quantitative Research

**Internal validity**: can one claim that X caused Y?
- Threats: history (external events), maturation, testing, instrumentation, regression to the mean, selection, attrition
- Controls: randomization, control group, blinding, pre-test

**External validity**: can results be generalized?
- Threats: non-representative sample, artificial conditions, reactivity (Hawthorne effect)
- Controls: representative sample, field experiment, replication

**Construct validity**: does the instrument measure what is claimed?
- Content: expert assessment of construct coverage
- Convergent: correlation with other measures of the same construct (AVE ≥ 0.5)
- Discriminant: weak correlation with measures of other constructs (√AVE > inter-construct correlations)
- Criterion-related: does the instrument predict an external criterion?

**Reliability**:
- Cronbach's α: ≥ 0.7 (acceptable), ≥ 0.8 (good), ≥ 0.9 (excellent, but possible redundancy)
- Composite reliability (CR) ≥ 0.7 — for SEM
- Test-retest: stability over time (r ≥ 0.7)
- Inter-rater reliability: Cohen's κ ≥ 0.61 (for categorical assessments)

### 11.2. For Qualitative Research (Lincoln & Guba, 1985)

| Criterion | Quantitative analog | Assurance strategies |
|-----------|--------------------|--------------------|
| **Credibility** | Internal validity | Triangulation, prolonged engagement, member checking, peer debriefing, negative case analysis |
| **Transferability** | External validity | Thick description of context so the reader can assess applicability |
| **Dependability** | Reliability | Audit trail, researcher's journal, transparency of procedures |
| **Confirmability** | Objectivity | Reflexivity, transparency of researcher's positionality, chain of evidence |

### 11.3. Triangulation

**Types** (Denzin, 1978):
1. **Data triangulation**: different sources (interviews + documents + observation)
2. **Investigator triangulation**: multiple researchers code the same data
3. **Methodological triangulation**: combination of quantitative and qualitative
4. **Theoretical triangulation**: interpretation through multiple theoretical frameworks

---

## 12. Research Ethics

### 12.1. Mandatory Elements (When Working With Human Participants)

1. **Informed consent**: participants are aware of aims, procedures, risks, and the right to withdraw
2. **Confidentiality**: data are anonymized or pseudonymized
3. **Voluntariness**: participation without coercion, possibility of refusal without consequences
4. **Ethical committee approval**: IRB / Local Ethics Committee
5. **Data storage**: secure storage, scheduled destruction
6. **Minimization of harm**: research must not harm participants

### 12.2. Special Cases

- **Vulnerable groups** (children, patients, prisoners): additional protection protocols
- **Online research**: question of public/private status of data (posts in open groups vs. closed chats)
- **Covert observation**: permissible only when informed consent is impossible and the risk is minimal
- **Secondary data**: if data are depersonalized — ethics committee may not be required, but this must be documented

### 12.3. Typical Errors

- ❌ No mention of informed consent (when working with human participants)
- ❌ No ethics committee approval, or no explanation of why it is not required
- ❌ Interview quotes with real names / identifiable details
- ❌ For online research (netnography, post analysis): consent and privacy questions not discussed

---

## 13. Typical Errors in Method Selection and Description

### Error 1: Method Listed in Introduction but Not Applied

❌ "Methods: systems analysis, structural-functional method, synthesis"
    [The main text contains only a descriptive literature review]

**Diagnosis**: find in the main text exactly where the author applies each method. If a method is mentioned only in the introduction and applied in no section — it is not part of the study.

**Recommendation**: remove methods that are not used in the text; retain only those actually employed. Add a "Methodology" section describing the procedure for applying each method.

### Error 2: Survey for Everything

❌ Aim: "Identify the deep motivations behind AI implementation decisions by top management"
   Method: questionnaire with 15 closed questions, sample N=30

**Problems**:
- Closed questions do not reveal "deep motivations" — they impose options
- N=30 is insufficient for statistical generalizations
- Top managers rarely complete questionnaires honestly and in detail

✅ Replacement: semi-structured interviews (12–15 informants), thematic analysis (Braun & Clarke, 2006). Justification: interviews reveal non-obvious motivations; follow-up questions provide depth that a closed questionnaire cannot offer.

### Error 3: Correlation Does Not Equal Causation

❌ "Correlation analysis confirmed that agile implementation LEADS TO productivity growth (r=0.67)"
→ Correlation does not confirm a causal relationship.

✅ "A positive correlation was found between agile practices and productivity indicators (r=0.67, p<0.01). To verify the causal relationship, an experiment with a control group or a quasi-experimental design with control for confounders is required."

### Error 4: Expert Survey Without Justification of Expertise

❌ "An expert survey of 10 specialists in field X was conducted."
→ Who are these experts? By what criteria were they selected? Why is their opinion valid?

✅ "The expert panel was formed using the following criteria: (1) industry experience ≥10 years, (2) publications on the topic, (3) experience leading relevant project types. 12 experts were selected; Kendall's concordance coefficient W=0.73 (p<0.05), indicating consistency of assessments."

### Error 5: SWOT / PEST as a "Research Method"

❌ "Research method: SWOT analysis."
→ SWOT is a strategic planning tool, not a scientific method. There is no procedure, no criteria; the result depends on the author's subjective judgment.

✅ If environmental analysis is needed: "Content analysis of strategic documents of 15 companies with subsequent categorization of factors using a matrix 'internal/external — favorable/unfavorable'. Classification criteria are defined in the codebook (Appendix 1); inter-rater reliability κ=0.82."

### Error 6: Content Analysis Without Procedure

❌ "Content analysis of media publications was conducted."
→ Missing: units of analysis, coding categories, source sampling, inter-rater reliability.

✅ "Content analysis of 200 publications in business media for the period 01.2022–12.2024. Unit of analysis: article. Categories: [list]. Coding was performed by two independent coders; Cohen's κ=0.78."

### Error 7: Comparative Analysis Without Comparison Criteria

❌ "A comparative analysis of risk management approaches was conducted."
→ By what parameters? How were they assessed? Where is the result (table, matrix)?

✅ "Comparative analysis of 5 risk management frameworks (COSO ERM, ISO 31000, PMBOK, PRINCE2, SAFe) using 8 criteria: [list]. Scoring on a 5-point scale; results are presented in Table 3. Criteria were selected based on the literature review and validated by an expert panel (N=7)."

### Error 8: "General Scientific Methods" as Window Dressing

❌ "The work uses methods of analysis and synthesis, induction and deduction, abstraction and concretization, and the systems approach."
→ This list communicates nothing about the actual research procedure. Every academic work presupposes thinking that includes analysis and synthesis. Listing general cognitive operations is not a description of a method.

✅ Replace with a concrete description of the procedure: "To systematize factors, content analysis of 45 academic articles (Scopus, 2018–2024) was used, with coding into 6 categories; to build the model — structural equation modeling (SEM) on survey data N=250."

### Error 9: Single Data Cross-Section When Claiming to Study Dynamics

❌ Aim: "Study the dynamics of development of digital competencies among employees"
   Method: a single survey in March 2024
→ A single cross-section does not show dynamics.

✅ Either a longitudinal design (minimum 2 measurements), or reformulate the aim: "Assess the current level of digital competencies among employees" (descriptive task).

### Error 10: No Description of Method Limitations

❌ The author does not mention the limitations of the chosen method.
→ Every method has limitations. Failure to acknowledge them reduces confidence in the work.

✅ "Method limitations: (1) cross-sectional design does not allow for causal inferences; (2) convenience sample limits generalization; (3) self-report is subject to social desirability bias; (4) retrospective data may be distorted by recall bias."

### Error 11: Incorrect Handling of Likert Scale

❌ The author calculates a mean on a 5-point Likert scale and applies parametric tests without caveats.
→ Strictly speaking, Likert is an ordinal scale. The mean assumes equal intervals.

✅ Two permissible approaches:
1. Acknowledge the ordinal nature → use median, IQR, non-parametric tests
2. Justify treating the scale as quasi-interval (citing the debate: Norman, 2010; Sullivan & Artino, 2013) → use parametric tests, but explicitly state the assumption

### Error 12: p-Hacking and HARKing

❌ The author tests many variables, finds one significant relationship, and builds a hypothesis around it in the "introduction" section.
→ This is HARKing (Hypothesizing After Results are Known) — formulating a hypothesis after data analysis and presenting it as a priori.

❌ The author sequentially removes observations or subgroups until p < 0.05.
→ This is p-hacking.

✅ Transparency: pre-registration of hypotheses, indication of the exploratory nature of analysis, reporting all tests conducted (not only significant ones).

---

## 14. Method Description Checklist

A complete method description in a paper must contain:

### Mandatory Elements

- [ ] Research paradigm / philosophical approach (at least implicitly)
- [ ] Type of research design (experimental, descriptive, case study, etc.)
- [ ] Name of method and reference to a methodological source
- [ ] Justification of selection: why this method and not an alternative
- [ ] Description of procedure: sufficient detail for replication
- [ ] Sample: size, formation strategy, inclusion/exclusion criteria
- [ ] Sample size justification (power analysis / saturation)
- [ ] Instruments: questionnaires/scales/guides/software (references to originals)
- [ ] Reliability and validity of instruments (for quantitative)
- [ ] Data analysis method: which tests, which software
- [ ] Verification of statistical test assumptions
- [ ] Effect size (for quantitative)
- [ ] Method limitations: what it cannot show
- [ ] Ethics: informed consent, anonymization, ethics committee approval

### Additional Elements (improve quality)

- [ ] Piloting of the instrument
- [ ] Response rate and non-response bias analysis
- [ ] Handling of missing data
- [ ] Common method bias test (for surveys where DV and IV come from the same source)
- [ ] Pre-registration (for experiments)
- [ ] Researcher reflexivity (for qualitative)
- [ ] Coding protocol and code examples (for qualitative)
- [ ] Audit trail
- [ ] Member checking / respondent validation
- [ ] Graphical representation of the research design (flowchart)

---

## Appendix A: Software for Data Analysis

### Quantitative Analysis

| Software | Specialization | When to recommend |
|----------|---------------|-------------------|
| SPSS | Standard statistical analysis | Most social science research |
| R / RStudio | Flexible, free, reproducible | Advanced statistics, visualization, SEM (lavaan) |
| Python (pandas, scipy, statsmodels, sklearn) | Data analysis + ML | Big data, predictive models |
| Stata | Econometrics, panel data | Economic research |
| AMOS / Mplus / SmartPLS | SEM, PLS-SEM | Structural equation modeling |
| G*Power | Power analysis | Sample size calculation BEFORE the study |
| JASP | Free, GUI, Bayesian statistics | Alternative to SPSS for beginners |

### Qualitative Analysis

| Software | Specialization |
|----------|---------------|
| NVivo | Comprehensive analysis, works with various data types |
| ATLAS.ti | Visual coding, network diagrams |
| MAXQDA | Mixed methods, visualization, collaborative work |
| Dedoose | Cloud-based, affordable, mixed methods |

### Bibliometric Analysis

| Software | Specialization |
|----------|---------------|
| VOSviewer | Visualization of bibliometric networks |
| Bibliometrix (R) | Comprehensive analysis, programmatic approach |
| CiteSpace | Trend analysis, burst detection |

---

## Appendix B: Key Reporting Standards

| Standard | For | URL |
|----------|-----|-----|
| PRISMA | Systematic review and meta-analysis | prisma-statement.org |
| CONSORT | Randomized controlled trials | consort-statement.org |
| STROBE | Observational studies | strobe-statement.org |
| COREQ | Qualitative research (interviews, focus groups) | equator-network.org |
| SRQR | Qualitative research (Standards for Reporting Qualitative Research) | equator-network.org |
| CHEERS | Economic evaluation in healthcare | ispor.org |
| JARS-Quant | Quantitative research (APA) | apastyle.apa.org |
| JARS-Qual | Qualitative research (APA) | apastyle.apa.org |
| JARS-Mixed | Mixed methods research (APA) | apastyle.apa.org |

---

## Appendix C: Key Terms Glossary

| Term | Definition |
|------|-----------|
| **Operationalization** | The translation of an abstract construct into measurable indicators |
| **Confounder** | A third variable that influences both the cause and the effect, creating a spurious relationship |
| **Effect size** | A quantitative measure of the strength of a relationship or difference (unlike p-value, does not depend on N) |
| **Power analysis** | Calculation of the minimum N needed to detect an effect of a given size with a given probability |
| **Theoretical saturation** | The point at which new data yield no new categories or properties |
| **Member checking** | Verifying results with study participants — did the researcher understand them correctly? |
| **Triangulation** | Use of multiple sources/methods/researchers to enhance credibility |
| **MECE** | Mutually Exclusive, Collectively Exhaustive — a classification without overlaps or gaps |
| **Common method bias** | A systematic error arising when DV and IV are measured by the same method/at the same time |
| **Bracketing** | In phenomenology: suspension of the researcher's preconceptions for "clean" perception of data |
| **Audit trail** | Documentation of all researcher decisions to ensure transparency |
| **Thick description** | A detailed, contextualized description enabling transferability of results |
| **Joint display** | A table or visualization integrating quantitative and qualitative data in mixed methods research |
