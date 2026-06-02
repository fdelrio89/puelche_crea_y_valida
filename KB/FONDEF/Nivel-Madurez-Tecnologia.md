  
**Technological Research Contest 2026**

**Technology Readiness Level (TRL)**

**1.1 Validation of Minimum Technology Readiness Level( TRL4)**

The application starts from a real technological result that already exists as an integrated prototype. The technological object under claim is a supervised, agent-based, AI-assisted review harness for documentary first review in public procurement. The harness combines deterministic case preparation, a large language model, a library of criterion-specific review procedures, and a supervisory control layer that routes one criterion at a time, writes one cited packet per admitted task, and leaves weak or ambiguous items open for human review. Human evaluators retain committee deliberation, institutional judgment, and the final award decision.

The current evidence supports a bounded TRL 4 claim: technology validated in a laboratory environment. The validation environment is a controlled benchmark built from real public SERVIU Metropolitano procurement bundles. The current benchmark contains 27 admitted criterion tasks from 13 public cases. These tasks are divided into 9 calibration tasks, 7 primary out-of-sample tasks, and 11 supplementary out-of-sample tasks. On the admitted out-of-sample set, the benchmarked harness matches the official human result exactly on all 18/18 tasks. In plain terms, on every out-of-sample task that could be constructed fairly from the public record, the current system got the official answer right.

The experimental design used to validate this integrated system combines four complementary study families. First, a fixed-condition replication reran the three calibration cases (9 tasks) five times under identical conditions to measure repeatability and citation validity; mean criterion stability was 1.0, and mean citation validity was 1.0. Second, two public transfer tests evaluated whether the harness could close comparable tasks on new public case bundles; the admitted criteria in cases 48-39 and 48-27 matched the official result exactly. Third, a frozen staged holdout on case 48-56 tested whether held-out performance improved as additional learned procedures were enabled; exact match rose from 0.9167 to 1.0, and criterion stability rose from 0.75 to 1.0. Fourth, a supplementary staged panel on four additional SERVIU cases broadened the evidence base and showed that the same staged learning pattern was not confined to a single holdout case.

This evidence demonstrates that the components already work as an integrated system in laboratory conditions. The system rebuilds a public tender bundle into a normalized workspace, isolates admissible criterion tasks, routes each task to the appropriate reusable procedure, generates reviewer-facing cited packets, and compares those packets against official human results. The validated scope is documentary first review, not full autonomous adjudication and not sustained operational deployment. For that reason, the strongest credible statement at the time of application is entry at TRL 4, not yet TRL 5\.

[Link to the repo](https://drive.google.com/drive/folders/1q_BaS63LV8QQ6ZUUuTGu9uDKkHwSoM53?usp=drive_link) with all the code for replication.

**1.2 Summary Table of Previous Results**

| Name of the Result Achieved | Description of the Result Achieved | Validation Level | Aspects to Improve or Develop within the Framework of this Project |
| :---- | :---- | :---- | :---- |
| **Integrated AI-assisted first-review harness** | **Supervised, agent-based workflow that converts a public tender bundle into a normalized review workspace, isolates admissible criterion tasks, routes each task to the right reusable procedure, and writes one cited reviewer-facing packet per task. Current benchmark evidence covers 27 admitted tasks from 13 public SERVIU cases, with exact match on all 18 admitted out-of-sample tasks.** | **Laboratory** | **Extend transfer beyond one public buyer, validate under shadow or live reviewer workflow, and measure operational usefulness in routine use.** |
| **Reusable criterion-review procedure library** | **Stable library of criterion-specific procedures for proposal-section review, count-and-band scoring, declaration-plus-support verification, timeline interpretation, and staffing-table reconstruction. These procedures were stabilized on calibration cases and then reused on out-of-sample cases.** | **Laboratory** | **Expand coverage to more criterion families, strengthen robustness on harder tables and noisier document surfaces, and reduce review load on borderline cases.** |
| **Benchmark and validation apparatus** | **Controlled task-based benchmark built from real public procurement bundles, with explicit task-admission rules, criterion-level gold targets, repeatability checks, citation checks, staged holdout logic, and transfer studies. This apparatus makes the maturity claim auditable and reproducible.** | **Laboratory** | **Increase institutional breadth, add more admissible cases from other agencies, and improve the automation and packaging of benchmark regeneration.** |
| **Reviewer-facing packet and traceability format** | **Exportable first-review packet format that records one criterion, one provisional verdict or score, supporting citations, and a closure state. This makes the system usable as a human-review aid rather than a black-box scoring tool.** | **Laboratory** | **Integrate the packet format into a reviewer workflow interface, test usability with institutional staff, and measure verification-time savings and review quality effects.** |

**1.3 Results of Scientific Production and/or Intellectual Protection**

| *Type of Result (Publication, thesis, intellectual property, conference presentation, etc.)* | *Status of the Result (paper published or submitted, thesis completed or awaiting examination, intellectual property requested or granted)* | *Description (indicate Title and journal, or information related to the publication or presentation of the work, scope of the intellectual property)* |
| ----- | ----- | ----- |
| *N/A* |  |  |

**There are no academic publications or patents associated with this project at the time of application.**