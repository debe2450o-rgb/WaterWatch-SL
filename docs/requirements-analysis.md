# Requirements Analysis

## Stakeholders

- Community members and reporters
- Community water-point committees
- District WASH focal persons
- Local councils and water-service providers
- NGOs and maintenance teams
- Public-health and water-quality stakeholders
- Students and contributors who extend the open-source design

## User stories

- As a community reporter, I want to record a failed water point so that a responsible team receives useful details.
- As a WASH focal person, I want cases ranked by transparent urgency so that I can organise limited repair capacity.
- As a resident, I want the system to identify a safer alternative when my normal source is unavailable.
- As a maintainer, I want the scoring rules documented so that I can review and improve them.
- As a contributor, I want the project to be open and modular so that I can add languages, data fields, or integrations.

## Assumptions

- Users can identify the affected community and water point.
- The design can receive an assessment of alternatives, even if a future implementation gathers it offline.
- Priority is a referral aid, not a replacement for engineering inspection or health advice.
- The scoring weights are provisional and require local validation.

## Constraints

- Low bandwidth and intermittent connectivity
- Limited technical support in some communities
- Need for simple language and possible translation
- Incomplete or outdated water-point information
- Privacy and safety risks if personal information is collected unnecessarily

## Acceptance criteria

A design is acceptable when it can take a complete report, reject missing or invalid data, calculate a score from documented rules, classify the urgency, choose a safe alternative when one exists, produce a referral summary, and repeat the process for another report.
