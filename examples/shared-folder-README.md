# Shared private job data

Private. Never publish, never commit. The scout bot and the applier bot both use this folder.

Suggested path: `~/job-private/` (or any path both bots can read). Record the path in each bot's private memory, not in a public repository.

Copy this file to `README.md` in that folder, and start from `examples/answers.example.md` and `examples/tracker.csv`.

## Layout

- `cv/` — official resume
  - official resume PDF — the only resume to upload on applications. Never upload the resume stored inside Simplify.
  - official resume HTML — the editable source.
  - optional faithful French translation PDF — created only when a job needs it, shown to the owner once, then reused.
- `answers.md` — owner-confirmed facts and answers only. Pending items stay blank.
- `tracker.csv` — every job briefed, approved, or submitted.

## Tracker columns

```
date_et,company,role,posting_url,job_id,status,by_bot,resume_file,confirmation
```

Typical status values: `briefed`, `approved`, `submitted`, `declined`, `paused`.

## Handoff

When the owner OKs a job, the scout bot appends a row with status `approved` and sends the posting URL to the applier bot (agent-to-agent). The scout never hands over unapproved jobs. The applier checks this tracker before every submission (no duplicates) and appends a `submitted` row after a confirmed submission.
