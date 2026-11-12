# WaterWatch SL Modular Pseudocode

```text
MODULE main()
    REPEAT
        report ← collectReport()
        errors ← validateReport(report)

        IF length(errors) > 0 THEN
            displayErrors(errors)
        ELSE
            breakdown ← calculateScoreBreakdown(report)
            totalScore ← sumScore(breakdown)
            priority ← classifyPriority(totalScore)
            alternative ← chooseSafeAlternative(report.alternatives)
            referral ← createReferral(report, breakdown, totalScore, priority, alternative)
            saveReport(report, referral, "NEW")
            displayReferral(referral)
        END IF

        again ← askYesNo("Enter another report?")
    UNTIL again = "NO"
END MODULE

MODULE collectReport()
    report.community ← askText("Community or chiefdom")
    report.waterPointId ← askText("Water-point ID")
    report.sourceType ← askChoice("Source type", ["Borehole", "Hand-dug well", "Piped standpipe", "Other"])
    report.faultType ← askChoice("Fault", ["No water", "Broken handle", "Leak", "Contamination concern", "Other"])
    report.peopleAffected ← askInteger("People affected")
    report.daysUnavailable ← askInteger("Days unavailable")
    report.safetyRisk ← askChoice("Safety risk", ["None known", "Possible", "Confirmed/high"])
    report.alternatives ← collectAlternatives()
    RETURN report
END MODULE

MODULE validateReport(report)
    errors ← empty list
    IF blank(report.community) THEN add(errors, "Community is required") END IF
    IF blank(report.waterPointId) THEN add(errors, "Water-point ID is required") END IF
    IF report.peopleAffected < 0 THEN add(errors, "People affected cannot be negative") END IF
    IF report.daysUnavailable < 0 THEN add(errors, "Days unavailable cannot be negative") END IF
    IF report.alternatives is empty THEN add(errors, "At least one alternative must be assessed") END IF
    RETURN errors
END MODULE

MODULE calculateScoreBreakdown(report)
    breakdown.people ← peoplePoints(report.peopleAffected)
    breakdown.risk ← riskPoints(report.safetyRisk)
    breakdown.downtime ← downtimePoints(report.daysUnavailable)
    breakdown.alternative ← alternativePoints(report.alternatives)
    RETURN breakdown
END MODULE

MODULE peoplePoints(number)
    IF number >= 500 THEN RETURN 35
    ELSE IF number >= 200 THEN RETURN 25
    ELSE IF number >= 50 THEN RETURN 15
    ELSE RETURN 5
    END IF
END MODULE

MODULE riskPoints(risk)
    IF risk = "Confirmed/high" THEN RETURN 30
    ELSE IF risk = "Possible" THEN RETURN 15
    ELSE RETURN 0
    END IF
END MODULE

MODULE downtimePoints(days)
    IF days > 30 THEN RETURN 20
    ELSE IF days >= 8 THEN RETURN 15
    ELSE IF days >= 2 THEN RETURN 10
    ELSE RETURN 5
    END IF
END MODULE

MODULE alternativePoints(alternatives)
    safe ← filter alternatives where status = "SAFE" and available = TRUE
    IF length(safe) = 0 THEN RETURN 15
    nearest ← minimum distanceMinutes in safe
    IF nearest <= 30 THEN RETURN 0
    ELSE RETURN 8
    END IF
END MODULE

MODULE sumScore(breakdown)
    RETURN breakdown.people + breakdown.risk + breakdown.downtime + breakdown.alternative
END MODULE

MODULE classifyPriority(score)
    IF score >= 75 THEN RETURN "CRITICAL — refer immediately"
    ELSE IF score >= 55 THEN RETURN "HIGH — refer within 48 hours"
    ELSE IF score >= 30 THEN RETURN "MEDIUM — schedule within 7 days"
    ELSE RETURN "LOW — monitor or routine maintenance"
    END IF
END MODULE

MODULE chooseSafeAlternative(alternatives)
    candidates ← filter alternatives where status = "SAFE" and available = TRUE
    IF length(candidates) = 0 THEN RETURN "No confirmed safe alternative"
    RETURN candidate with minimum distanceMinutes from candidates
END MODULE

MODULE createReferral(report, breakdown, score, priority, alternative)
    referral.summary ← report.community + " / " + report.waterPointId
    referral.score ← score
    referral.breakdown ← breakdown
    referral.priority ← priority
    referral.alternative ← alternative
    referral.action ← responseAction(priority)
    RETURN referral
END MODULE
```
