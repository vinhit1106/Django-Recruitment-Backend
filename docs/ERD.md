# ERD (draft)

No database schema exists in the surveyed directory. The intended initial entity groups from the project brief are:

```text
User 1--1 CandidateProfile
User 1--* CandidateCV
CandidateProfile 1--* CandidateSkill *--1 Skill
CandidateProfile 1--* Experience
User (employer) 1--* Company
Company 1--* Job *--1 Category
Job 1--* Application *--1 CandidateProfile
CandidateCV 1--* Application
Application 1--* ApplicationStatusHistory
```

Required database protections include unique `(job_id, candidate_id)` applications, unique `(candidate_id, skill_id)` pairs, non-negative salaries, ordered salary bounds, valid experience dates, and indexes for public jobs, job status, and applications. This diagram is a planning artifact pending confirmation against the real repository and frontend needs.
