# IPO Design

## Input

- Community/chiefdom
- Water-point identifier
- Source type
- Fault type
- Number of people affected
- Days unavailable
- Safety-risk category
- Alternative source list
- Alternative safety and availability
- Alternative collection time

## Process

1. Read the report fields.
2. Validate required values and ranges.
3. Convert people affected into points.
4. Convert safety risk into points.
5. Convert downtime into points.
6. Convert alternative availability and collection time into points.
7. Add the four components.
8. Map the total to a priority class.
9. Rank safe, available alternatives by distance.
10. Produce a referral summary and status.

## Output

- Validation errors, if any
- Priority score from 0 to 100
- Score breakdown
- Priority class and response window
- Recommended safe alternative or no confirmed alternative
- Referral summary
- Report status
