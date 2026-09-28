# How to assemble the artifact

Read this sheet before phase 3. It holds the shape of a unit inside a sheet, the templates, and the size rules.

<unit_format>

## How to write a unit into a reference sheet

A format of five fields, proven in practice. Every unit looks like this:

```markdown
#### 1.4. Write about the reader, not about yourself
- **Rule:** the subject and the topic of the key sentences is the reader and the reader's situation, not the author, the company, or the product.
- Why it works: the reader is interested in themselves and their problem, and scrolls past a text about the author.
- Bad → Good: "We provide a personal specialist and develop a strategy" → "Your specialist walks you through every mistake until you get a result".
- When not to apply: <the author's caveat> or the line "No special caveats in the source".
- Anchor: «Подлежащим ключевой фразы должен быть читатель, а не компания.» (гл. 3, раздел «Подлежащее»)
```

The anchor stays in the language of the source, whatever language the skill is written in. The one above comes from a Russian source; in English it reads "The subject of the key sentence has to be the reader, not the company."

Why these five fields:

- **Rule** is checkable, a yes or no verdict can be delivered on a concrete piece of work by it.
- **Why it works** lets the agent apply the rule in a situation the source never covered, instead of following it blindly.
- **Bad → Good** gives a foothold, without which the rule collapses into a slogan. Where the source carries no example for a rule, put in the explicit line "No example in the source" instead of composing one: an invented example is writing on the author's behalf, and the same explicit line that covers a missing caveat covers a missing example.
- **When not to apply** is the most expensive field. The explicit line "no caveats in the source" is mandatory where there are none. An empty field is indistinguishable from a forgotten one, and an explicit line records that the source was checked.
- **Anchor** makes the unit self-sufficient: a verbatim quote with an address, the ground already inside, and the consumer of the skill needs neither a search over the source nor the source itself at hand. The anchor stays in the language of the source. If the skill is going to be published beyond the user's team, trim the quotes down to addresses: verbatim chunks of a book are not handed outside. Trimming is the last step and it runs on a finished artifact. Assembly and the self-check run on full quotes: the audit checks anchors by mechanical search over the source, and once the quotes are gone there is nothing left to search for.

Numbering runs through each sheet, `NN.M`. It is there so that SKILL.md, the sheets and the basis block that closes an answer can point at a specific rule rather than at "a principle from the book".

</unit_format>

<skill_template>

## The SKILL.md template

```markdown
---
name: <short name in lowercase latin>
description: <what it does and when to apply it, with explicit user trigger phrases>
---

# <The name of the method>

<One paragraph: what the skill does and to what material it applies. If there is a
neighbouring skill, the fork to it goes here.>

## The core of the method (hold in mind at all times)

<5-8 numbered principles, each a bold thesis plus one or two sentences of
unpacking. This is the front-load, the most valuable thing in the skill.>

## The order of work

### 1. Diagnosis
### 2. <Frame or preparation>
### 3. <The main work>
### N. <The mandatory final check>

<Each phase with links to the reference sheets it needs.>

## Routing by task

| Task | Sheets |
|---|---|
| <a typical user request> | 02, 03 + the core |

<Below it, the line: read ONLY the sheets the task needs.>

## Output rules

<How the agent hands over the result, per mode. Every step rests on a rule of an
open sheet, not on taste, and the answer is written for its reader: the substance
of the rule in the body, the rule numbers only in a basis block that closes the
answer, as the Output rules section of this sheet describes; before → after on
fragments; the marker [to clarify: ...] instead of invention; tone.>

## Sources

<Each source by a descriptive name: its kind, title, author, and the edition or
year when the method depends on it. Several sources: their tiers, and the line
that the upper tier wins where formulations diverge. Nothing about the build,
no file names, paths, export dates, or unit counts: that is `PROVENANCE.md`.>
```

Do not rearrange the blocks. The core comes first: the start of the file gets the most attention, and on a partial read that is exactly what the agent sees.

</skill_template>

<output_rules>

## How to write the Output rules: the answer for its reader, the grounding behind it

A rule number after every claim does not keep invented rules out of an answer; it only makes them checkable, and it buries the answer. What keeps them out is that every step is written from a rule the agent has open, and that a check runs before the answer leaves. The Output rules of the generated skill carry each part below, in the skill's language, and the parts hold in every mode, advice, review and rewrite, and in every document an answer produces, not only in the first answer of a conversation.

**The rule comes before the step.** The agent picks the rule of an open sheet first and writes the step or the finding from it. A step written first and matched to a rule afterwards is how an invented rule gets in: some rule always sounds close enough.

**The body speaks about the reader's material in the reader's words.** The substance of the rule goes into the text as the advice itself or as the reason for a finding. The body carries no rule numbers, no source titles or years, no "the method says", no retold caveats of the author, and no record of how the method was walked: the reader gets the result of the diagnosis and the user's figures that decide it. That the reader might want to verify, or that a number makes the answer look grounded, is not grounds for a number in the body: verifying is what the basis block is for.

**A basis block closes the answer.** A short block, headed in the language of the answer (in a Russian skill «Основания»), names the skill once and gives one line per step, finding or change: its label and the `NN.M` numbers of the sheet rules it rests on, nothing else, no quotes, no titles, no years. A step that no rule supports gets its line too, saying so in plain words, so the user can trust the answer without reading the block. The user can ask to leave the block out, of a document meant for other readers for instance; the final check runs all the same.

**Whose advice it is.** The body names the author, never "the method": a reader who does not know the skill cannot tell which method is meant. It names the author only where that tells the reader something, at most once per step: to mark the answer's own advice, or where the author's authority is itself the argument. Advice that no open rule supports is marked where it stands, in plain words and with the author's name: "that is my suggestion, not Ilyakhov's". The mark says whose advice it is, not what the books lack: the skill knows its sheets, a selection from the books, and a claim about the whole books could be false. The test: does a rule of an open sheet, applied to the user's facts, lead to this step? If it does, the step gets its basis line and no mark. If it does not, the step is marked. The details that come from the user's own facts, who does it and by when, need no mark. When in doubt, mark: an unmarked suggestion passes for the author's.

**Caveats and years change the advice or stay out.** The author's caveat from the When not to apply field is applied, not retold: it narrows the advice, turns it into a condition, or withdraws the finding. When in doubt whether a caveat matters here, turn it into a condition rather than drop it. Where the reader must know that a figure is soft, one word carries it: "a benchmark of", not "the author himself calls this a pattern, not a rule". A source year appears only where the age of a figure changes the decision, a market figure that may have moved since, for instance. When in doubt, give the age in plain words, "a figure from 2021", never as a citation in brackets. A note that a step rests on a weaker source, a lower tier of the source map such as talks rather than books, is not a retold caveat: it tells the reader how much the step weighs, so it stays, as one plain sentence where the answer relies on that source.

**The author's terms come with their meaning.** A construct keeps the author's exact name, and at its first mention in an answer the name stands next to its meaning in plain words: a bare name is a word the reader without the book cannot use.

**The basis on request is a check, not a new search.** When the user asks where a step comes from, whether it is really the author's, or whether the answer is invented, the agent reopens the sheets, quotes verbatim the Rule field of every rule the basis block names, with its number, adds the anchor where the user asks whether the book itself says so, and says plainly where a step does not match its rule or rests on no rule. It never adds a rule to the basis after the fact and never stretches a rule to cover a step: a rule that seems to fit only once the question is asked is the mark of a search, and a mismatch found here is corrected in the answer.

**The final check asks about the block and the body separately.** Its questions name places: which step, finding or change has no line in the basis block, or a line whose rule does not say what the step says; which advice in the body goes beyond the rule of its step and stands unmarked, a forecast or an extra suggestion inside a step included; which figure, fact or name is neither in the request nor in a sheet; which finding lands on a When not to apply field; which sentence of the body carries a rule number, a source title, a year the decision does not need, "the method" without the author's name, or a caveat that changes nothing for the reader. What the questions find is fixed before the answer leaves.

<examples>
<example>
A finding in a review of a post, from a skill built on "Yasno, ponyatno".
Bad: «Мы рады сообщить, что запустили новый сервис»: by the method, the subject of the key sentence has to be the reader, not the company (1.4, «Ясно, понятно»); the author himself allows exceptions.
Good: «Мы рады сообщить, что запустили новый сервис»: the sentence is about the company, and the reader is not told what changes for them. Start from the reader: «Теперь вы можете…».
The good finding says what rule 1.4 says, about this very sentence, and the number waits in the basis block. The book's title adds nothing, and the caveat, which does not change this finding, stays out.
</example>
<example>
The basis block that closes that review:

Basis (rules of the yasno-ponyatno skill)
1. The opening sentence: 1.4
2. Stop words: 3.2, 3.5
3. Posting time: my suggestion, no rule

Bad: the same block with the title of each rule, its anchor and the year of the book in every line. The reader meets the wall the body was spared, while the numbers alone lead to all of it in the sheets.
</example>
<example>
Own advice. Bad: "Post it in the morning (my opinion, not the method's)." A reader who does not know the skill cannot tell which method is meant.
Good: "Post it in the morning, when the channel's readers are online: that is my suggestion, not Ilyakhov's."
Boundary: "Rewrite the opening before Thursday's post" needs no mark: the step comes from rule 1.4, and Thursday is the user's own fact.
</example>
<example>
A caveat applied, not retold. The sheet's rule on cutting carries the author's caveat that cutting stops where the text stops reading naturally.
Bad: "Cut the paragraph down (3.4); note that the author warns against drying a text out completely."
Good: "Cut the two opening sentences and keep the example: without it the paragraph stops reading naturally."
</example>
<example>
The basis on request. The user asks: "Where does the morning advice come from, and is the rest really from the book?"
Good: "The morning advice rests on no rule: it was my suggestion, and the basis block says so. The other steps rest on these rules, quoted from the sheets: 1.4 «the subject and the topic of the key sentences is the reader and the reader's situation, not the author, the company, or the product»; …"
Bad: "The morning advice follows from 2.7, the rule about the reader's attention." A rule found after the fact for a step that had no basis line: the check has turned into a search, and the new answer is more confident, not more grounded.
</example>
</examples>

</output_rules>

<build_record>

## What goes into PROVENANCE.md

`PROVENANCE.md` sits next to SKILL.md and is never loaded on activation. It holds everything about the build that the applying agent has no use for: the build date; the source map from phase 0, the tiers and the rules specific to this build; the export used for each source, its file name and export date, so that a disputed unit can be re-checked against it while the export exists; the statistics, extracted, rejected by filter, merged, included, per source when there are several; and what the checks did not cover, validation run without subagents for one.

</build_record>

<splitting>

## How to split material across sheets

Split by **user tasks**, not by source chapters. A book's table of contents is optimized for linear reading, a skill for targeted access.

The sign of a correct split: by the routing table a typical request opens one or two sheets, not five.

The last-numbered sheet is always `NN-checklist-and-antipatterns.md`: the checklist for checking finished work plus the whole catch of extractor D. It is used in two modes, as the final check and as a diagnosis of someone else's material, and is therefore needed more often than the rest.

</splitting>

<sizing>

## What size the files should be

| File | Target size | Ceiling |
|---|---|---|
| SKILL.md | 100-200 lines | 500 lines |
| Reference sheet | 150-250 lines | 300 lines, split by topic beyond that |
| The core of the method | 5-8 principles | 10, beyond that it is not a core |

A sheet longer than 300 lines needs a table of contents at the top. Better to split it than to give it one.

</sizing>

<naming>

## How to name the skill and the sheets

The folder and the `name` field: latin, lowercase, hyphens. Name it after the method or the book, not after the action: `yasno-ponyatno`, not `text-improver`. A method is recognizable, an action is not.

Sheets carry a numeric prefix for ordering: `01-context.md`, `02-text.md`.

</naming>

<description>

## How to write the frontmatter description

The description is the only triggering mechanism. The agent sees the name and the description alone, and reads the body only after it has decided.

Requirements:
- what it does and when to apply it, both in the description and not in the body;
- explicit user trigger phrases, the ones where the method is not named included;
- the description has to be insistent. The default behaviour is undertriggering, an agent tends not to open a skill where it would help.

Weak: "A method of working with text from the book N".
Strong: "Method N for Russian texts: rewrite something clearly, audit its clarity, design its structure. Triggers: 'by N', 'make this clearer', 'rewrite without the fluff', 'why is this text not working', 'structure this text'."

Technical bounds: a description up to 1024 characters, third person, the skill name in lowercase latin with hyphens. Do not retell the skill's process in the description: an agent that sees the process in the description executes the description instead of reading the body. What the skill does, as one noun phrase; after that, triggers only.

A description is not chosen by eye. The tuning procedure for triggering is in the sheet `04-evals.md`.

</description>

<anti_patterns>

## What must not appear in the output

- Raw chunks of the source longer than three sentences.
- Blocks of the form "in chapter 5 the author explains", that is a reference guide, not a skill.
- Rules carrying neither an example nor the explicit line about its absence in the source.
- An empty "when not to apply" field instead of an explicit line about the absence of caveats.
- File names, paths, export dates, or unit counts in SKILL.md: that is the build record, and it lives in `PROVENANCE.md`.
- Output rules that put rule numbers, source titles, retold caveats, a year on every figure, or "the method says" into the body of an answer, or a final check that counts citations there: the grounding lives in the basis block.
- Horizontal rules between blocks.

</anti_patterns>
