---
name: step-16-kdp-publishing-package-builder
description: "Universal agent skill to assemble the verified publishable files, complete KDP metadata (Title, Subtitle, 300–400 word Description, 7 Backend Keyword Boxes, Categories, Pricing, AI-Disclosure answer, A+ Content draft), and a click-by-click KDP upload checklist in 10_Compliance_and_Publishing/ without ever submitting."
---


# KDP Publishing Package Builder (`Step_13_kdp-publishing-package-builder`)

**Role:** Publishing Preparation Agent  
**Purpose:** Assemble all verified publishing assets, compliant metadata, and a click-by-click upload checklist for Samir. **This skill prepares the package only—it never uploads or submits anything.**

---

## 1. Hard Pre-Flight Gates & Environment Adaptation
- **Three Mandatory Pre-Conditions (If any is missing → STOP & output `BLOCKED`):**
  1. **Quality Audit PASS:** `08_Book_Development/QUALITY_CHECKS/qc_<shortname>_<yyyymmdd>.md` exists with `OVERALL VERDICT: PASS`.
  2. **Samir's Recorded Approval:** Explicit approval for this title is logged in `00_Project_Control/DECISION_LOG.md` (with line/date).
  3. **Fresh Policy Capture (`≤ 30 days`):** `02_Knowledge_Base/KDP_POLICIES/POLICY_INDEX_<yyyymmdd>.md` is fresh (`< 30d`), including metadata, categories, pricing, and AI-disclosure rules.
- **Output Delivery:**
  - **Workspace Agents (Manus, Hermes):** Save to `10_Compliance_and_Publishing/publish_checklist_<shortname>_<yyyymmdd>.md` (never overwrite an existing file).
  - **Web / Chat Agents (Claude Projects, Genspark):** Output the complete Markdown publishing checklist directly in the chat using the exact template in Section 4.

---

## 2. Step-by-Step Package Assembly Procedure

### Step 1: Gather & Verify All Package Files
Locate and inspect each deliverable (`08_Book_Development/MANUSCRIPTS/<shortname>_vNN.md`, `09_Cover_and_Interior/cover_<shortname>/`, `09_Cover_and_Interior/interior_<shortname>/`, and `spec_<shortname>_<yyyymmdd>.md`):
- Check that each PDF/image opens cleanly and matches the verified spec (trim size, embedded fonts, cover pixel dimensions, manuscript word count).
- Record exact observed values. If any check cannot be verified in the current environment, mark that row **`FAIL-INCOMPLETE`** and flag it for Samir to verify on his PC (never mark unverified items `PASS`).

### Step 2: Compose Compliant KDP Metadata
1. **Title & Subtitle:** Must match the locked Positioning Brief (`Step_07`), include the primary target keyword, and contain zero trademarked terms or prohibited claims (e.g., `"#1 Bestseller"`).
2. **Book Description (`300–400 words`, 100% Original Words) `[COURSE]`:**
   - Follow the exact 5-part conversion structure:
     1. **Bold Hook** (question or striking statement).
     2. **Relate + Credibility** (empathize with the Q4 pain point).
     3. **"In this book you will discover:"** Curiosity-driven bullet points (tease the benefit + page/chapter value; **do NOT reveal the exact "how"**).
     4. **"Even if..." Objection Handler** (address the reader's biggest doubt).
     5. **Clear Call to Action (CTA).**
   - Provide both clean plain text and KDP-safe HTML tags (`<b>`, `<i>`, `<br>`, `<ul>`, `<li>`).
3. **7 KDP Backend Keyword Boxes (Strict Policy & Non-Duplication Rules):**
   - Check the character/byte limit from the fresh `00B` metadata policy capture (never guess from memory).
   - Fill all 7 boxes using validated buyer phrases from `Step_03_kdp-keyword-research`.
   - **Optimization & Compliance Rules:** Do **not** repeat words already present in the Title or Subtitle; do **not** use competitor author names, book titles, ASINs, subjective claims (`"best"`, `"new"`), or time-sensitive words.
4. **Categories:**
   - Check current KDP category selection limits from the fresh `00B` policy capture (e.g., 3 BISAC/Amazon store categories at upload; note any course post-upload category expansion rules alongside current KDP policy `[COURSE]` / `[VERIFIED]`).
5. **AI-Content Disclosure Answer:**
   - State the exact upload answer required by `00B_kdp-policy-verification` and the manuscript header (e.g., `Yes — AI-generated text: Extensive, with or without editing; AI-generated images: None / Minimal`).
6. **Pricing & Launch Plan:**
   - **Ebook Launch:** `$0.99` on the `35%` royalty option → KDP Select 5-day free promo → 7–14 days at `$0.99` → raise to `$2.99–$4.99` (`70%` royalty option) `[COURSE]` / `[RECOMMENDATION]`.
   - **Paperback Launch:** `$9.97–$12.97` at launch → raise to `$12.97–$17.97` post-launch (confirm above KDP minimum printing cost) `[COURSE]` / `[RECOMMENDATION]`.
7. **Bonus — A+ Content Draft (Free Conversion Booster):**
   - Provide copy-ready text for 2 simple text-led A+ Content modules (Module 1: *"Who This Book Is For / What You Will Master"*; Module 2: *"Inside the Book — Key Frameworks & Checklists"*) so Samir can paste them into KDP Marketing after the book goes live.

### Step 3: Build Click-by-Click KDP Upload Instructions & Final Lock
- Write a numbered, step-by-step checklist for Samir covering **Paperback upload first, then Ebook upload**.
- End the document with the mandatory line: **`NOTHING HAS BEEN SUBMITTED.`**

---

## 3. Required Output Format

Save to: `10_Compliance_and_Publishing/publish_checklist_<shortname>_<yyyymmdd>.md`  
*(Keep the header block and final statement in this exact structure):*

```markdown
# Publish Checklist — <Book Title>
<!-- skill: Step_13_kdp-publishing-package-builder -->
Shortname: <shortname>
Compliance PASS: 08_Book_Development/QUALITY_CHECKS/qc_<shortname>_<yyyymmdd>.md (<date>)
Policy Index (<30d): 02_Knowledge_Base/KDP_POLICIES/POLICY_INDEX_<yyyymmdd>.md
Samir approval: 00_Project_Control/DECISION_LOG.md (<line/date>)
Manuscript: 08_Book_Development/MANUSCRIPTS/<shortname>_v<NN>.md
Cover: 09_Cover_and_Interior/cover_<shortname>/<file(s)>
Interior PDF: 09_Cover_and_Interior/interior_<shortname>/<file>
Title: <Exact Title>
Subtitle: <Exact Subtitle>
Description: 300-400 words (<exact word count> words, author-written, template structure)
Keywords: 7 backend boxes (policy-verified)
Categories: <Primary category paths>
AI Disclosure Answer: <Exact KDP form selection required>
Price (proposed): ebook $<0.99 launch / $2.99-4.99 regular> [COURSE], paperback $<9.97-12.97 launch / $12.97-17.97 regular> [COURSE]

---

## 1. Final Metadata Copy (Ready to Paste into KDP)

### A. Title, Subtitle & Pen Name
- **Title:** `<Title>`
- **Subtitle:** `<Subtitle>`
- **Author / Pen Name:** `<Pen Name>`

### B. Book Description (300–400 Words — KDP HTML Ready)
```html
<b><Hook line></b><br><br>
<Relate + credibility paragraph><br><br>
<b>In this book, you will discover:</b>
<ul>
  <li><b><Curiosity Bullet 1>:</b> <Tease benefit without giving away the how></li>
  <li><b><Curiosity Bullet 2>:</b> <Tease benefit></li>
  <li><b><Curiosity Bullet 3>:</b> <Tease benefit></li>
  <li><b><Curiosity Bullet 4>:</b> <Tease benefit></li>
  <li><b><Curiosity Bullet 5>:</b> <Tease benefit></li>
</ul><br>
Even if <biggest reader objection>, this step-by-step system gives you <core promise>.<br><br>
<b><Final CTA line></b>

C. 7 KDP Backend Keyword Boxes (Zero Title/Subtitle Word Duplication)
(Policy limit verified from policy_metadata_<yyyymmdd>.md: <limit> chars per box)

Box 1: <phrase>
Box 2: <phrase>
Box 3: <phrase>
Box 4: <phrase>
Box 5: <phrase>
Box 6: <phrase>
Box 7: <phrase>
D. Target Categories & AI Disclosure
Category 1: <Path>
Category 2: <Path>
Category 3: <Path>
KDP AI Content Disclosure Selection: <Exact required selection based on 00B policy>
E. Optional A+ Content Draft (For KDP Marketing Tab Post-Live)
Module 1 (Standard Four Image/Text or Header): <Copy-ready text>
Module 2 (Comparison Chart / Key Takeaways): <Copy-ready text>
2. File Verification Table
File Path	Opens Cleanly?	Matches Spec (Trim / Fonts / Pixels / Word Count)?	Verdict (PASS / FAIL / FAIL-INCOMPLETE)	Evidence Observed
<interior_pdf_path>	<Yes/No>	<6x9, embedded fonts>	<Verdict>	<Observed properties or "Needs Samir PC check">
<paperback_cover_path>	<Yes/No>	<Full wrap dimensions>	<Verdict>	<Observed properties>
<ebook_cover_path>	<Yes/No>	<1600x2560 px>	<Verdict>	<Observed properties>
<manuscript_path>	<Yes/No>	<~30,000 words>	<Verdict>	<Word counter result>
3. Click-by-Click KDP Upload Steps (For Samir)
Sign In: Log into https://kdp.amazon.com (Samir only).
Create Paperback: Click + Create → Create Paperback.
Paperback Details: Paste Title, Subtitle, Author, HTML Description, 7 Keyword Boxes, select 3 Categories, and select the AI Content Disclosure answer above.
Paperback Content: Assign free KDP ISBN (or your own), select Trim Size (<W x H>), Bleed (<Bleed>), Paper Type, and Cover Finish. Upload Interior PDF and Paperback Wrap PDF.
Paperback Previewer: Launch Print Previewer; verify spine alignment, margins, and zero error flags → Click Approve.
Paperback Pricing: Set US list price to $<launch_price> (verify positive royalty above printing cost) → Click Publish Your Paperback Book.
Create Kindle Ebook: Return to Bookshelf → Click Create Kindle eBook under the linked title.
Ebook Details & Content: Verify carried-over metadata, select AI Content Disclosure, upload Ebook manuscript & Ebook Front Cover, preview in Kindle Previewer.
Ebook Rights & Pricing: Enroll in KDP Select (if chosen in Step_14), select 35% royalty tier, set launch price to $0.99 [COURSE], and publish.
4. Post-Upload Launch Sequence [COURSE]
Upload ~3 days before target launch day so both Paperback and Kindle go live together.
Enroll Ebook in KDP Select and schedule the 5-day Free Promotion.
Hold Ebook at $0.99 (35% royalty) for 7–14 days after the free promo ends.
Raise Ebook price to $2.99–$4.99 (70% royalty) and Paperback price to $12.97–$17.97.
Final statement: NOTHING HAS BEEN SUBMITTED.
## Workflow position

**Step 16** — this card is part of the numbered KDP workflow. Use the previous step outputs before starting it and pass its required outputs to the next step.

