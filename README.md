# WaterWatch SL

**PROG101 Final Project — Principles of Programming Logic and Design**

WaterWatch SL is a proposed open-source digital public good for helping communities and local WASH actors report non-functional water points, identify safe alternatives, and prioritise repair referrals using a transparent scoring algorithm.

This submission is intentionally a **software design and algorithm project**, not a deployed application. It demonstrates computational thinking, requirements analysis, IPO design, modular design, decision structures, loops, functions, pseudocode, and flowchart design.

## Problem

Many communities in Sierra Leone depend on wells, boreholes, rivers, and other water sources. When a borehole or hand pump fails, the information needed to organise a repair may be incomplete, delayed, or difficult to compare. People may then spend more time collecting water or use unsafe sources.

WaterWatch SL provides a simple, low-bandwidth process to:

1. record a water-point problem;
2. check and classify the report;
3. calculate a priority score;
4. suggest the safest available alternative;
5. produce a referral summary for a WASH focal person or maintenance team.

## Project documents

- [Final report](docs/final-report.md)
- [Downloadable final report PDF](docs/final-report.pdf)
- [Pseudocode](docs/pseudocode.md)
- [Functional modules](docs/functional-modules.md)
- [IPO design](docs/ipo-design.md)
- [Requirements analysis](docs/requirements-analysis.md)
- [Flowgorithm flowchart source](diagrams/waterwatch-flowchart.fprg)

Open `diagrams/waterwatch-flowchart.fprg` with [Flowgorithm](http://www.flowgorithm.org/) to view and edit the native flowchart.
- [Presentation outline](docs/presentation-outline.md)
- [Meeting minutes](minutes/meeting-1.md)
- [Research sources](docs/sources.md)

## Core algorithm

The system assigns a repair-priority score from 0 to 100 using four transparent factors:

- affected people: 0–35 points;
- safety risk: 0–30 points;
- time without service: 0–20 points;
- availability of a safe alternative: 0–15 points.

The score is classified as:

- **Critical:** 75–100 — refer immediately;
- **High:** 55–74 — refer within 48 hours;
- **Medium:** 30–54 — schedule within 7 days;
- **Low:** 0–29 — monitor or include in routine maintenance.

The weights are a design assumption for classroom demonstration. They should be validated with Sierra Leonean WASH authorities and community representatives before real deployment.

## Open-source and sustainability

The project uses the MIT License. It can be adapted by community groups, students, NGOs, local councils, and WASH service providers. It is designed for low-bandwidth use and does not require a paid proprietary platform. Contributions should improve accessibility, language support, data protection, and local maintenance workflows.

## Academic note

This repository is a model submission for the attached project brief. Replace the student, class, group, lecturer, and meeting details with the group's official information before submission.
