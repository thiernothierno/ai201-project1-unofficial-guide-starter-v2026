# The Unofficial Guide

<!-- Replace this line with your name and which corpus you picked. -->

> **This file is your submission.** Fill it in as you go — most sections get
> written during the milestone that produces them, not at the end.
>
> How the starter works, and every command you'll need, is in `RUNNING.md`.
> Leave that file alone.
>
> **Paste everything as text.** No screenshots, no video. A typed table gets
> full credit; a picture of the same table gets none.
>
> Delete these instruction blocks as you replace them. The `<!-- -->` comments
> are notes to you and don't show up when the page renders — you can leave them
> or remove them.

---

# Unit 1

## What This Does

This is a retrieval-augmented question that provide a response from a pre-built system campus_life corpus: 88 shorts, student writing posts to learn more about certain rules within the campus such as parking permit, graduation requirements, housing lottery and how campus jobs are related to financial aid. When a question is asked for example "how work-study and non-work-study affect financial aid?" or "is the housing lottery random?" the system dig into all resources it contains and provide the answer. In the case if no resource contains information about what has been asked the system reply: "I don't have enough information about that".

## Chunking Strategy

All posts from the campus life are shorts, 317 characters average with (shortest 178, longest 549). Each post contains 2 to 5 paragraphs.

**Chunk size:**
**Overlap:**

## Sample Chunks

**Chunk 1** — source: `source: admin_add_drop_deadline.txt#0` — produced by: `produced by: chunker.py::fallback_split`

```
On the add/drop deadline

You can add a course through the end of the second week. Dropping is a longer window — through the end of week six — but a drop after week two shows as a W on your transcript. Nothing anywhere on the registrar's site says this plainly, and students find out from each other.
```

**Chunk 2** — source: ` source: course_biol_160.txt#0` — produced by: `chunker.py::fallback_split`

```
BIOL 160 Cell Biology

I lived here my sophomore year. Format is lecture three times a week with a weekly lab. Assessment: four unit tests and a cumulative final. Not curved.

Expect 9 to 11 hours a week, the heaviest first-year course by reputation.

The one piece of advice: the unit tests come fast, roughly every three weeks; falling behind once is very hard to recover from.
```

**Chunk 3** — source: `course_hist_118_workload.txt#0` — produced by: `chunker.py::fallback_split`

```
Workload for HIST 118 Modern World History

People keep asking so: a lot of reading, about 120 pages a week, but no problem sets. That's real time, not optimistic time.

It's front-loaded — the first month is heavier than the rest, partly because you're learning the format.
```

**Chunk 4** — source: `dining_pellew_dining_hall_followup.txt#0` — produced by: `chunker.py::fallback_split`

```
Re: Pellew Dining Hall

Adding to what people have said about Pellew Dining Hall. The wait figure of 12 to 18 minutes at peak matches what I've seen. If you're trying to eat between classes, go before 11:45 and it's a different building entirely.

Also worth saying: the furthest hall from anywhere, next to the athletics centre. Nobody tells you this at orientation.
```

**Chunk 5** — source: ` housing_innisfree_hall.txt#0` — produced by: `chunker.py::fallback_split`

```
Innisfree Hall — what it's actually like

Transferred in last year, so take this with a grain of salt. Built 1991, renovated 2022. Rooms are doubles arranged as pairs sharing one bathroom between two rooms.

The good: the shared-bathroom-between-two-rooms arrangement is the best compromise on campus.

The bad: no air conditioning, which matters for the first three weeks of September.

Laundry costs $1.75 wash, $1.75 dry, app-based. On noise: moderate; the building is L-shaped and the short wing is much quieter.
```

## Sample Answer

<!-- One complete question and answer, pasted as text, with the source line
     visible. Milestone 4. -->

**Question:**
"how work-study and non-work-study affect financial aid?"
**Answer:**

```
Work-study earnings do not count against your financial aid the way ordinary income does, whereas non-work-study campus jobs do count against it.

Source: admin_campus_jobs_and_financial_aid.txt
Sources retrieved: admin_campus_jobs_and_financial_aid.txt, admin_study_abroad.txt, course_econ_101_workload.txt, course_engl_205_exams.txt, money_jobs.txt
```

**My relevance cutoff: is 0.6**

<!-- The number you set in config.py, and how you got there.

     You ran five questions your corpus covers and the five in OUT_OF_SCOPE
     that it clearly doesn't, and wrote down the best distance for each. What
     did those two groups look like? Where was the gap? Put the actual numbers
     here — the table below wants all ten rows.

     Milestone 4. -->

| Question                                                    | In corpus? | Best distance |
| ----------------------------------------------------------- | ---------- | ------------- |
| Does studying abroad include in financial aid?              | Yes        | 0.369         |
| how work-study and non-work-study affect financial aid?     | Yes        | 0.304         |
| Which days are best to do laundry?                          | Yes        | 0.427         |
| Does the campus offer a quite environment for study?        | Yes        | 0.515         |
| Which month does the campus offer sale for parking?         | Yes        | 0.437         |
| What is the capital of Mongolia??"                          | No         | 0.825         |
| How do I change the oil in a diesel engine?                 | No         | 0.934         |
| Who won the 1994 World Cup?                                 | No         | 0.886         |
| What is the recommended dosage of ibuprofen for a headache? | No         | 0.884         |
| How do I write a for loop in Rust?                          | No         | 0.896         |

## How I Used AI

<!-- Two specific moments. For each: what you asked for, what came back, and
     what you changed about it.

     "I asked Claude to write the chunking function from my notes. It ignored
     the overlap, so I added that myself" is the level of detail we're after.
     "I used AI to help me code" is not.

     Milestone 5. -->

**1.**

**2.**

<!-- ── Stretch features ─────────────────────────────────────────────────────
     Doing one? Say so here BEFORE you start. A feature this README never
     claims earns nothing.
     ───────────────────────────────────────────────────────────────────────── -->

---

# Unit 2

## Run Log — Before

| Criterion                                         | Target | Run 1 | Run 2 | Run 3 | Verdict |
| ------------------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer            | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 2. Every answer names a source                    | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 3. Gate stops out-of-corpus questions             | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 4. No claim absent from the chunk                 | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 5. Named source is the chunk the answer came from | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |

### Criterion 1: "Does studying abroad include in financial aid" — run 1

- Best distance: 0.3667 (passed the gate)
- Sources retrieved: admin_campus_jobs_and_financial_aid.txt, admin_declaring_a_major.txt, admin_graduation_requirements.txt, admin_pass_fail_option.txt, admin_study_abroad.txt

Yes, your financial aid package travels with you when you study abroad.
Source: `admin_study_abroad.txt`

### Criterion 2: "how work-study and non-work-study affect financial aid"— run 1

- Best distance: 0.3008 (passed the gate)
- Sources retrieved: admin_campus_jobs_and_financial_aid.txt, admin_study_abroad.txt, course_econ_101_workload.txt, course_engl_205_exams.txt, money_jobs.txt

Work-study earnings do not count against your financial aid the way ordinary income does, whereas non-work-study campus jobs do count against it.

Source: `admin_campus_jobs_and_financial_aid.txt`

### Criterion 3:

Produced by `run_eval.py::check_out_of_scope`, cutoff 0.6. Refused 5 of 5.

Retrieval is deterministic and the gate is a comparison against a
fixed number, so these do not vary between runs — one pass over the
list is the whole measurement.

| Out-of-scope question                                       | Best distance | Gate    |
| ----------------------------------------------------------- | ------------- | ------- |
| What is the capital of Mongolia?                            | 0.825         | refused |
| How do I change the oil in a diesel engine?                 | 0.934         | refused |
| Who won the 1994 World Cup?                                 | 0.886         | refused |
| What is the recommended dosage of ibuprofen for a headache? | 0.844         | refused |
| How do I write a for loop in Rust?                          | 0.896         | refused |

### Criterion 4: "Does the campus offer a quite environment for study" — run 1

Best distance: 0.5218 (passed the gate)

- Sources retrieved: course_econ_101.txt, housing_aldridge_hall.txt, housing_tamsin_court.txt, money_jobs.txt, transit_walking.txt

Yes, Aldridge Hall has quiet floors on levels 3 and 4 that are genuinely enforced (housing_aldridge_hall.txt). Additionally, Tamsin Court is quiet structurally because it has concrete floors between units.
Source: `housing_tamsin_court.txt`.

### Criterion 5: "Which month does the campus offer sale for parking?" — run 1

- Best distance: 0.4374 (passed the gate)
- Sources retrieved: admin_parking_permits.txt, housing_aldridge_hall.txt, money_textbooks.txt, transit_shuttle.txt, transit_walking.txt

Student permits for the west lots go on sale in August.
Source: `admin_parking_permits.txt`.

## Verdicts

| #   | Criterion                                      | Verdict | How I decided                                      |
| --- | ---------------------------------------------- | ------- | -------------------------------------------------- |
| 1   | Retrieved chunk contain the answer             | MET     | All retrieved chunk contain the right answer.      |
| 2   | Every answer name a source                     | MET     | Every answer from the chunk came with a source.    |
| 3   | Gate stops-out-of-corpus question              | MET     | All gate stops-out-of-corpus fail the gate.        |
| 4   | No claim absent from the chunk                 | MET     | Everything in the answer is included in the chunk. |
| 5   | Named source is the chunk the answer came from | MET     | The source listed by each chunk is correct.        |

## Diagnoses

## The Improvement

**What I changed:**
No improvement made since all criterion passed the gate.

**Why I picked it:**
I decided to stay with the same entry point because the chunk return an answer with a source.

### Run Log — After

| Criterion                                         | Target | Run 1 | Run 2 | Run 3 | Verdict |
| ------------------------------------------------- | ------ | ----- | ----- | ----- | ------- |
| 1. Retrieved chunk contains the answer            | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 2. Every answer names a source                    | 5 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 3. Gate stops out-of-corpus questions             | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 4. No claim absent from the chunk                 | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |
| 5. Named source is the chunk the answer came from | 4 of 5 | 5/5   | 5/5   | 5/5   | MET     |

**Did it help?**
Since there was no change with the initial input ran before and the one ran after, there was no more to learn from the result.

## What's Still Broken

Nothing is broken. I get the same result.

## What I'd Do Differently

I guess what I would do differently is either to increase the size of k or change the wording of each question and see what the chunk would return.
