# Functional Module Design

## 1. Report Intake Module

**Purpose:** collect the fields required to describe a water-point problem.

**Inputs:** user responses.  
**Outputs:** report object.

## 2. Validation Module

**Purpose:** check required fields, non-negative numbers, allowed categories, and at least one alternative assessment.

**Inputs:** report object.  
**Outputs:** list of errors.

## 3. Scoring Module

**Purpose:** calculate people, safety, downtime, and alternative points.

**Inputs:** validated report.  
**Outputs:** score breakdown and total.

## 4. Priority Module

**Purpose:** convert the score into a named response level.

**Inputs:** total score.  
**Outputs:** Critical, High, Medium, or Low.

## 5. Alternative Selection Module

**Purpose:** remove unsafe/unavailable sources and select the nearest safe available source.

**Inputs:** alternatives.  
**Outputs:** recommended alternative or no confirmed safe alternative.

## 6. Referral Module

**Purpose:** combine report data, score, priority, and recommendation into an actionable message.

**Inputs:** report and processed results.  
**Outputs:** referral summary.

## 7. Status Module

**Purpose:** track New, Referred, In Progress, Resolved, and Closed states.

**Inputs:** current status and authorised update.  
**Outputs:** updated status.
