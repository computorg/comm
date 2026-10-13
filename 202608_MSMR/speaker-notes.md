# Speaker notes --- Computo at MSMR 2026

10 minutes talk + 3 minutes questions. 9 content slides + title.
Rough budget below assumes ~65s/slide average; it adds up to ~10 min flat, so there
is no slack --- if a slide runs long, cut on delivery rather than rush the next one.

---

## Title (0:00 -- 0:30)

Good morning / good afternoon.

I'm Julien Chiquet, Researcher in Statistical Learning at the University Paris-Saclay
I'm the editor-in-chief of *Computo*, a journal in statistics and machine learning that I co-founded at the very end of 2021 with Pierre Neuvial.

- Computo : hopefully an example of practical deployment of tools for reproducibilité
- Telling you what the journal actually requires of a submission, four years of what happened when we required it, and what of
that seems worth taking beyond our own field.

- "Redefining" maybe a bit too pedantic

---

## Slide 1 --- The gap between claim and computation (0:30 -- 1:40)

Computo's Rationale

A methodological paper's claim rests on a computation: a simulation study, a benchmark.
That's the evidence. The reader gets is a PDF, with the plots and tables, not the path
that produced them. (even if we saw yesterday nicer ways of plotting results).

3 consequences, none of them new to all of you:
- code and data, when shared at all, are rarely runnable as published
- Peer review examines the argument, barely the computation itself
- a year later the environment (software require) has moved on and nothing builds anyway, so even a diligent reader who wanted to check can't.
-> A real pain to reproduce the work (used to be done by PhD student, no helped by AI tools...)

Computo's genral idea/ premise is the flip side of that: if the computation is the evidence, it should part of the reviewing process, and it should still run in ten years.

That's the whole idea in one sentence,  everything else is what it takes to make that literally true

---

## Slide 2 --- Computo in one slide (1:40 -- 2:40)

Quick facts, so the rest of the talk has a frame.
- Founded during autumn 2021 under the French Statistical Society (Learned society, our publisher)
- Diamond open access : free to read, free to publish, no author-facing charge at any point.
- CC-BY, authors keep copyright
- Real "Academic" journal:  Scope is computational and algorithmic contributions to stats and ML
- Review happens in the open on OpenReview, and we're partnered with PCI Statistics and
Machine Learning, more on that in a minute.
- 23 papers since April 2022.

The point of this slide is just to establish that this is a real, running journal, not a proposal anymore.

---

## Slide 3 --- What we publish (2:40 -- 3:35)

Original dev in stat/ML : Three kinds of papers, relatively standard in our field

- Methods papers --- new developments, or a numerical study that
illustrates a theoretical result
- Case studies and surveys, which is where neutral comparison studies live: papers whose entire contribution is telling you honestly when,
how and why competing methods perform well or don't. That category barely exists as a
publishable genre elsewhere, and it's exactly the kind of paper meta-science needs more
of.
- software/tutorial papers --- an implementation plus a real use case, benchmarked
against related work, not just documentation.

Important thing : true academic journal + reproducibility

Whatever the type, reproducibility is a necessary condition for publication and even submission.
If it doesn't build, it isn't a Computo manuscript.

---

## Slide 4 --- The stack (3:35 -- 4:50)

*[point at the diagram]*

So what does "necessary condition" mean mechanically.

Every submission is a git repository that builds itself with 4 pieces

- literate programming --- we use Quarto, so text, equations, code and figures live in one source file, not a paper
with code as an afterthought.
- pinned environment --- `renv.lock` for R, `requirements.txt` or similar for Python, `Project.toml` for Julia --- so the computation
is reproducible, not just re-runnable today.
- Continuous integration that rebuilds the whole thing from scratch on our own infrastructure at every push, not just once at
submission.
- And data, shipped with the repo or deposited, typically on Zenodo.

Templates exist for R, Python and Julia. None of this is language-specific in principle

---

## Slide 5 --- Two review tracks (4:50 -- 6:05)

We run two checks in parallel, and we keep them relatively separate on purpose.

- Scientific review: open, on OpenReview, reports published after acceptance, reviewers can
stay anonymous if they want. Or the paper comes to us already recommended by PCI
Stat/ML, in which case we don't re-review the science at all.

- Reproducibility check: automated, continuous, from the very first submission. Run by the
editorial and technical team, *not* by the referees, to relieve them.

-> A paper that doesn't build simply isn't reviewable yet --- that gate closed before a human referee's time is spent on it.

Splitting it this way means referee load doesn't go up because of the reproducibility requirement.
The machine settles whether it runs; the human argues about whether it's good science.

*[callout]* a 2026 comparative review in *Royal Society Open Science* (Anne Laure supervised, invited to co-author) looked at reproducibility policies across the field and put Computo in the five journals out of nine that actually perform an independent, execution-based
check of results --- in the company of JSS, JASA, Meta-Psychology and the Biometrical
Journal. So this is an externally verified claim, not a marketing one.

---

## Slide 6 --- After acceptance (6:05 -- 6:55) *(cut candidate #1)*

Publication isn't the end of the reproducibility story, it's the start of maintaining it.
Once accepted: the repo moves to our GitHub organisation, tagged with its environment. DOI
via DataCite. Review reports go public alongside the paper. The repo is archived on
Software Heritage for long-term preservation independent of GitHub or us.

*[callout]* And --- this is the part people don't expect --- we periodically re-run
published articles' workflows to check they still build. A reproducible artifact isn't a
one-off publication event, it's something that needs to be kept alive, the same way software does.

---

## Slide 7 --- What the record shows (6:55 -- 7:55)

Four years of data. 23 papers, April 2022 through July 2026, growing year over year, (2026 count is partial, paper in review/production)
On language: 14 papers R-only, 6 Python-only, 3 using both, and Julia has a template but no
submission yet --- worth being honest about that gap.

The headline is simple: the policy is feasible. These aren't papers that built once at
submission and then bit-rotted. They build now, four years later, because we keep
checking.

---

## Slide 8 --- What it costs, and what transfers (7:55 -- 9:15) *(cut candidate #2 if #1 wasn't cut)*

Cost of all this falls almost entirely on the first submission ---
templates absorb most of the technical burden after that, and editors get a form of check
they never had before, essentially for free.

* still genuinely hard: finding authors and reviewers is our real
bottleneck, and it has nothing to do with reproducibility as such. Getting indexed by
academic databases takes real effort. Heavy computation and large data remain awkward.
Dependencies go stale outside well-pinned ecosystems.

* transfers to other fields: nothing in the
stack is statistics-specific, it's git, notebook templates, a lockfile, CI --- any
computational field has these tools already. The hard part is the editorial move, not the
technical one --- deciding that the build is a condition, not a virtue --- and that move
is free once you decide to make it. Splitting scientific from reproducibility review keeps
referee workload flat. And diamond open access is viable *because* the infrastructure
stays light and a learned society hosts it --- that's not incidental, it's the condition
that makes the economics work at all.

---

## Slide 9 --- Come and try it (9:15 -- 9:50)

So: we're looking for authors --- methods, benchmarks, software papers particularly
welcome. Reviewers, same as any journal needs. And neutral comparison studies
specifically, since that genre is undersupplied everywhere and fits our scope exactly.
Pre-submission enquiries are welcome if you're unsure whether something fits --- just send
a title and abstract to the address on screen.

Thank you.

*(References slide stays up during questions; not spoken unless asked.)*

---

## Timing checkpoints

- Should be finishing slide 5 (two review tracks) around **6:00** --- if past 6:30, cut
  slide 6 entirely and move straight to the record slide.
- Should be starting slide 9 by **9:15** at the latest, to leave a real "thank you" rather
  than trailing off.

---

## Anticipated questions (Q&A, ~3 min)

**On scale / sustainability**

- *"Who actually runs the reproducibility checks — is that sustainable as volume grows?"*
  The editorial/technical team, currently a handful of people, largely volunteer time from
  the editorial board plus some INRAE-supported engineering. It scales with CI compute,
  not with referee time, which is the point --- but yes, it does not scale to zero
  marginal cost, and growth is bounded by that team's bandwidth today.
- *"What happens when a published article's workflow breaks on re-run?"* We flag it; the
  authors are contacted; if unfixable we annotate the record rather than retract silently.
  This is still a young process, not fully formalised.
- *"Is SFdS funding this indefinitely? What's the business model of diamond OA?"* Learned
  society hosting plus light infrastructure is the whole model --- no APCs, no
  subscriptions, costs are infrastructure + volunteer/institutional labour. That's
  precisely why keeping the stack light is not a technical preference, it's existential.

**On scope / comparisons**

- *"How is this different from JOSS, or from a journal just requiring a Zenodo DOI for
  code?"* JOSS reviews software itself as the contribution; Computo reviews a scientific
  claim *and* requires the computation behind it to rebuild --- broader scope than
  software papers, narrower and stricter than "here's a code archive link."
- *"Registered reports do something similar for pre-registration — is this comparable?"*
  Different axis: registered reports fix the analysis plan before seeing data; Computo
  fixes nothing about the science, only requires that whatever was done is executable and
  disclosed. Complementary, not competing.
- *"Why only R/Python/Julia? What about closed-source or licensed software (MATLAB,
  proprietary solvers)?"* No principled exclusion, but no template yet, and CI needs a
  runnable, freely obtainable environment --- that's a practical constraint on
  contributions using non-free tooling, worth being upfront about if asked directly.

**On incentives / careers**

- *"Does publishing in Computo count for tenure/promotion the way a 'normal' journal
  does?"* Indexing (Google Scholar since 2026, DOAJ application in progress) is where that
  battle is actually fought; being young and small is a real handicap here, which is
  exactly why growing an international, recognised editorial board matters.
- *"Isn't finding reviewers/authors always going to be the bottleneck for a niche,
  reproducibility-strict journal?"* Yes, named directly on slide 8 --- it's not solved, it's
  the open problem, and it's a large part of why I'm here talking to this room specifically.

**On the reproducibility bar itself**

- *"What about legally/ethically restricted data (clinical, confidential) — can those
  papers ever meet the bar?"* Case by case: synthetic/access-controlled data with a
  documented access procedure can satisfy the *methodology* reproducibility bar even
  without public data; this is handled per submission, not templated yet.
- *"Ten years is a strong claim — what's the actual retention/archival guarantee?"*
  Software Heritage archival plus periodic CI re-runs is the honest answer; "still runs in
  ten years" is the aspiration the periodic re-run policy is built to chase, not a
  guarantee already proven over ten years (the journal is only four years old).
