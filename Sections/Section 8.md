# Section 8: Professional Ethics

## Sections Table of Contents

Section 1: [Introduction to Software Engineering](Section%201.md)<br>
Section 2: [Requirement Analysis](Section%202.md)<br>
Section 3: [High-Level System Design](Section%203.md)<br>
Section 4: [Detailed Object Design](Section%204.md)<br>
Section 5: [Implementation](Section%205.md)<br>
Section 6: [Testing](Section%206.md)<br>
Section 7: [Software Management](Section%207.md)<br>
Section 8: [Professional Ethics](Section%208.md)<br>

## Section 8 Table of Contents

Section 8.1: [Professionalism](#section-8.1-professionalism)<br>
Section 8.2: [Code of Ethics](#section-8.2-code-of-ethics)<br>
Section 8.3: [Case Studies](#section-8.3-case-studies)<br>

# Section 8.1: Professionalism
`// fill this out - overview`

## Attributes of a Mature Profession
`// fill this out`

## Attributes of a Mature Profession
`// fill this out`

## Computer-related Careers
`// fill this out`

## Software Reliability
`// fill this out`

## Data Entry / Retrieval Errors
`// fill this out`

## Notable Software System Failures
`// fill this out`

### Patriot Missile System
`// fill this out`

### Ariane 5
`// fill this out`
- uncaught exception caused loss of $500 million worth of satellites

### Therac-25
`// fill this out`
- Software built on older versions
  - older versions used hardware restrictions
  - but software restrictions were not properly implemented
- two investigations: very hard to find root cause
  - there was a race condition

**Machine had two modes:**
- `X`: X-ray
- `E`: Electron beam

**What happened:**
- mistake made where staff entered `X` and dosage
  - then magnets moved
- user fixed mistake to `E`
  - software only checked cursor location
  - and if it found it in the bottom right corner
    - it assumed no fields were changed
- system gave x-ray dose at high dosage

**Analysis:**
- ...

**Lessons:**
- ...

# Section 8.2: Code of Ethics
`// fill this out - overview`

## Ethical Decisions
`// fill this out`

### Brainstorming
`// fill this out`

1. Identify stakeholders
2. Identify [for each stakeholder]
  - risks
  - benefits
  - consequences
  - costs
  - rights
3. Identify possible courses of actions

### Analysis
`// fill this out`

1. Identify impact of each course of action
  - considering code of ethics + morals + experience
  - categorize as ethically: obligatory / prohibited / acceptable
2. Select best option

# Section 8.3: Case Studies
`// fill this out - overview`

## Kickbacks and Disclosure

University wants new security software to recommend to new students.
- they are evaluating software packages
- a company is offering:
  - dinner for you
  - to pay for you to attend conference
  - to give university percentage of sales

**1. Stakeholders:**
- university
- the software company
- other software companies
- students
- yourself

**2. Effects:**
- **university:** money, reputation
- **the software company:** gain money, lose reputation
- **other software companies:** lose contract
- **students:** money, security
- **yourself:** gain bribes, lose job, lose reputation

**3. Courses of Actions:**
- Do not cooperate + report to authorities
- Do not cooperate + do not report
- Cooperate + disclose
- Cooperate + do not disclose

**4. Categorize Courses of Action:**
- **Ethically Acceptable:** Do not cooperate + report to authorities
- **Ethically Acceptable:** Do not cooperate + do not report
- **Ethically Acceptable:** Cooperate + disclose
- **Ethically Prohibited:** Cooperate + do not disclose

**5. Pick Course of Action + Justify:**