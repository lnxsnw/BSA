# Bachelor of Science in Accountancy

This repository is designed to store learning materials and their corresponding practice questions for quick lookups, review, and even llm ingestion. The repository is optimized for **Obsidian**, utilizing YAML frontmatter (Properties) and specific Markdown features to create an interactive and easily queryable knowledge base.

This is based in The Philippines, so expect it to use PH Laws and Standards such as PFRS (Philippine Financial Reporting Standards), PSA (Philippine Standards on Auditing) and even the National Internal Revenue Code.

# LLMs

## Instructions for LLMs: Generating Questions

When acting as an AI assistant in this repository, you will often be asked to generate practice questions based on the provided learning materials. You **MUST** strictly adhere to the following rules and use the provided Obsidian template.

### Generation Guidelines
1. **Contextual Accuracy**: Base the questions strictly on the provided learning materials. Do not introduce outside facts unless explicitly asked.
2. **Meaningful Distractors**: Ensure the incorrect options (distractors) are plausible but demonstrably incorrect based on the text.
3. **Template Strictness**: Every single question must follow the YAML + Markdown template exactly. Do not deviate from the structure.
4. **Metadata Extraction**: Accurately populate the YAML frontmatter. 
   - `tags`: Extract relevant keywords from the text (e.g., `- biology`, `- genetics`).
   - `difficulty`: Assign a difficulty of `easy`, `medium`, or `hard`.
   - `correct_option`: Must strictly be a single uppercase letter (`A`, `B`, `C`, or `D`).
5. **Interactive Solutions**: Always use the Obsidian collapsible callout syntax `> [!success]- Solution` for the explanation so the user can test themselves before revealing the answer.

### The Required Question Template

```markdown
---
type: "question"
tags:
  - insert_topic
  - insert_subtopic
difficulty: "medium"
correct_option: "A"
---

# [Insert the specific question text here]

## Options
- [ ] A. [Option 1 text]
- [ ] B. [Option 2 text]
- [ ] C. [Option 3 text]
- [ ] D. [Option 4 text]

> [!success]- Solution
> **[Correct Option Letter]** is the correct answer. 
> [Insert a detailed explanation here, referencing specific parts of the learning material to reinforce the concept.]
```

### Example Output

```markdown
---
type: "question"
tags:
  - accounting
  - fundamentals
difficulty: "easy"
correct_option: "B"
---

# Why is accounting often called the "language of business"?

## Options
- [ ] A. Because accountants create secret codes to communicate with other accountants
- [ ] B. Because it provides a standardized way of recording, summarizing, and reporting business transactions
- [ ] C. Because it teaches people how to speak financial jargon fluently
- [ ] D. Because it focuses only on money and ignores other aspects of business operations

> [!success]- Solution
> **B** is the correct answer. 
> Accounting communicates financial information in a structured and standardized way, helping stakeholders understand business performance.
> 
> A is incorrect because it is not a literal secret code.
> C is incorrect because while it uses financial terminlology, its main role is structured reporting.
> D is incorrect because accounting covers all aspects of business performance, not just cash.
```

### Multi-Question Template

Some problems present a single scenario followed by multiple questions. For these, use the following adjusted template. The key differences are:

- `type` is set to `"multi_question"`.
- `correct_options` (plural) is a **list** of answers, one per sub-question, in order.
- The problem stem is placed under a `# Problem` heading.
- Each sub-question gets its own `## Question N` heading with its own `### Options` and collapsible `Solution` block.

```markdown
---
type: "multi_question"
tags:
  - insert_topic
  - insert_subtopic
difficulty: "medium"
correct_options:
  - "A"
  - "B"
---

# Problem

[Insert the shared problem scenario/data here]

## Question 1

[Insert the first question text here]

### Options
- [ ] A. [Option 1 text]
- [ ] B. [Option 2 text]
- [ ] C. [Option 3 text]
- [ ] D. [Option 4 text]

> [!success]- Solution
> **[Correct Option Letter]** is the correct answer. 
> [Insert a detailed explanation here.]

## Question 2

[Insert the second question text here]

### Options
- [ ] A. [Option 1 text]
- [ ] B. [Option 2 text]
- [ ] C. [Option 3 text]
- [ ] D. [Option 4 text]

> [!success]- Solution
> **[Correct Option Letter]** is the correct answer. 
> [Insert a detailed explanation here.]
```

### Example Output (Multi-Question)

```markdown
---
type: "multi_question"
tags:
  - current_assets
  - current_liabilities
  - financial_statements
difficulty: "hard"
correct_options:
  - "D"
  - "D"
---

# Problem

Kabugao Company provided the following information on December 31, 2014:

| Item | Amount |
|---|---|
| Cash in bank, net of bank overdraft of P500,000 | 5,000,000 |
| Petty cash (unreplenished petty cash expenses, P10,000) | 50,000 |
| Notes receivable | 4,000,000 |
| Accounts receivable, net of accounts with credit balances of P1,500,000 | 6,000,000 |
| Inventory | 3,000,000 |
| Bond sinking fund | 3,000,000 |
| **Total current assets (as reported)** | **21,050,000** |

| Item | Amount |
|---|---|
| Accounts payable, net of suppliers' accounts with debit balances of P1,000,000 | 7,000,000 |
| Notes payable | 4,000,000 |
| Bond payable due June 30, 2015 | 3,000,000 |
| Accrued expenses | 2,000,000 |
| **Total current liabilities (as reported)** | **16,000,000** |

## Question 1

What amount should be reported as total current assets on December 31, 2014?

### Options
- [ ] A. 19,040,000
- [ ] B. 20,040,000
- [ ] C. 20,050,000
- [ ] D. 24,040,000

> [!success]- Solution
> **D** is the correct answer.
> 
> The reported total of P21,050,000 requires several adjustments:
> 
> The reported total of P21,050,000 requires adjustments for items that were improperly netted or excluded. 
> 
> Here is the breakdown of the correct current assets:
> 
> | Item | Computation / Explanation | Amount |
> |---|---|---|
> | Cash in bank | Add back overdraft (5,000,000 + 500,000) | 5,500,000 |
> | Petty cash | Reduce by unreplenished expenses (50,000 - 10,000) | 40,000 |
> | Notes receivable | No adjustment | 4,000,000 |
> | Accounts receivable | Add back credit balances (6,000,000 + 1,500,000) | 7,500,000 |
> | Inventory | No adjustment | 3,000,000 |
> | Bond sinking fund | Retained as current because the related bond payable is due June 30, 2015 (within one year) | 3,000,000 |
> | Suppliers' debit balances | Reclassify from accounts payable to current assets | 1,000,000 |
> | **Total current assets** | | **24,040,000** |
> 
> A is incorrect — it improperly excludes the bond sinking fund and the suppliers' debit balances.
> B is incorrect — it partially adjusts but misses certain reclassifications.
> C is incorrect — it does not make all the necessary reclassification adjustments.

## Question 2

What amount should be reported as total current liabilities on December 31, 2014?

### Options
- [ ] A. 15,000,000
- [ ] B. 15,500,000
- [ ] C. 16,000,000
- [ ] D. 19,000,000

> [!success]- Solution
> **D** is the correct answer.
> 
> The reported total of P16,000,000 requires adjustments for items that were improperly netted or excluded:
> 
> | Adjustment | Explanation | Amount |
> |---|---|---|
> | Accounts payable | Add back suppliers' debit balances (reclassify to current assets) | 7,000,000 + 1,000,000 = 8,000,000 |
> | Bank overdraft | Reclassify from offset against cash to current liabilities | +500,000 |
> | Accounts receivable credit balances | Reclassify to current liabilities (these represent customer prepayments/overpayments) | +1,500,000 |
> | Notes payable | No adjustment | 4,000,000 |
> | Bond payable (due June 30, 2015) | Already correctly classified as current | 3,000,000 |
> | Accrued expenses | No adjustment | 2,000,000 |
> 
> **Corrected current liabilities:**
> 8,000,000 + 4,000,000 + 3,000,000 + 2,000,000 + 500,000 + 1,500,000 = **P19,000,000**
> 
> A is incorrect — it removes items that should remain as current liabilities.
> B is incorrect — it only partially adjusts for the reclassifications.
> C is incorrect — it uses the unadjusted reported total without correcting for improperly netted items.
```

### True/False Template

For true or false statements, use the following template. The `correct_option` should be `"True"` or `"False"`.

```markdown
---
type: "true_false"
tags:
  - insert_topic
difficulty: "easy"
correct_option: "True"
---

# [Insert the statement here]

## Options
- [ ] True
- [ ] False

> [!success]- Solution
> **[True/False]** is the correct answer. 
> [Insert a detailed explanation here.]
```

### Example Output (True/False)

```markdown
---
type: "true_false"
tags:
  - inventory_management
difficulty: "easy"
correct_option: "True"
---

# Inventory management is the process of tracking and controlling the flow of goods—raw materials, works-in-progress, and finished products—through every stage, from initial purchase through final sale.

## Options
- [ ] True
- [ ] False

> [!success]- Solution
> **True** is the correct answer. 
> Inventory management encompasses the entire lifecycle of goods from acquisition to sale.
```

### Supply the Answer Template

For computational or direct answer questions where no choices are provided, use the following template. The `type` is `"supply_answer"` and a `correct_answer` field replaces `correct_option`.

```markdown
---
type: "supply_answer"
tags:
  - insert_topic
difficulty: "medium"
correct_answer: "[Insert exact answer]"
---

# [Insert the specific question or problem text here]

> [!success]- Solution
> **[Correct Answer]** is the correct answer. 
> [Insert a detailed explanation or computation here.]
```

### Multi-Question Supply the Answer Template

For problems with a shared scenario and multiple computational questions, use this template.

```markdown
---
type: "multi_supply_answer"
tags:
  - insert_topic
difficulty: "medium"
correct_answers:
  - "[Answer 1]"
  - "[Answer 2]"
---

# Problem

[Insert the shared problem scenario/data here]

## Question 1

[Insert the first question text here]

> [!success]- Solution
> **[Correct Answer 1]** is the correct answer. 
> [Insert a detailed explanation or computation here.]

## Question 2

[Insert the second question text here]

> [!success]- Solution
> **[Correct Answer 2]** is the correct answer. 
> [Insert a detailed explanation or computation here.]
```

### Example Output (Multi-Question Supply the Answer)

```markdown
---
type: "multi_supply_answer"
tags:
  - cost_volume_profit
  - break_even_analysis
difficulty: "medium"
correct_answers:
  - "5.20"
  - "600"
  - "5,970.00"
---

# Problem

Perfect Stampers makes and sells aftermarket hub caps. The variable cost for each hub cap is P4.75 and the hub cap sells for P9.95.
Perfect Stampers has fixed costs per month of P3,120.

## Question 1

Compute the contribution margin per unit.

> [!success]- Solution
> **5.20** is the correct answer. 
> Contribution Margin per Unit = Selling Price - Variable Cost
> CM per unit = P9.95 - P4.75 = P5.20

## Question 2

Compute the break-even sales in units for the month.

> [!success]- Solution
> **600** is the correct answer. 
> Break-even Sales in Units = Fixed Costs / Contribution Margin per Unit
> BEP in units = P3,120 / P5.20 = 600 units

## Question 3

Compute the break-even sales in pesos for the month.

> [!success]- Solution
> **5,970.00** is the correct answer. 
> Break-even Sales in Pesos = Break-even Sales in Units * Selling Price
> BEP in pesos = 600 units * P9.95 = P5,970.00
```
