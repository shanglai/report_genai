# report_genai


## Description

General Use GenAI project for creating automated reports.

A multi-agent system with compartmented tasks

## Structure


## Features

### Agent Modularity and Specialization
Each agent has clear and powerful responsibilities:
- <mainAI>: Orchestrator and evolving SME
- <policyAI>: Policy abstraction and standardization
- <dataAI>: Dataset engineering
- <interpreterAI>: Analytical narration
- <vizAI>: Visual translation
- <reportAI>: Output composition and storytelling

This division makes the system easily extensible and testable.

### SME Cycle in <mainAI>
The design enables <mainAI> to:
- Absorb knowledge incrementally (datasets, interpretations, policies)
- Validate with domain-specific heuristics (e.g., underage credit card holders)
- Reflect and refine understanding
- This transforms <mainAI> from a passive dispatcher into an active learning and integration engine.

### Modular agent orchestration
Each agent has:
- A clear, focused scope
- Defined inputs/outputs
- Independence for scaling or fine-tuning

### SME loop in <mainAI>
The system is:
- Cumulative in knowledge
- Reflexive to anomalies and contradictions
- Verifiable through both internal and external validation

### Audit trail via <auditAI> and [execution trace]
This is a critical enabler for:
- Debugging
- Explainability
- Regulatory reporting (e.g., financial or medical applications)

### Strict I/O design
- All JSON
- Deterministic
- Assumptions explicitly called out (This makes the system testable, inspectable, and maintainable).
- Hallucination control (<interpreterAI> low temperature)

### Confidence control:
A [confidence_score] field in each agent’s output helps <mainAI>:
- Prioritize insights
- Discard low-certainty elements
- Flag results for human review






# License
Creative Commons Attribution-NonCommercial 4.0 International Public License

By exercising the Licensed Rights (defined below), You accept and agree to be bound by the terms and conditions of this Creative Commons Attribution-NonCommercial 4.0 International Public License ("Public License").

You may freely:
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material

Under the following terms:
- Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made.
- NonCommercial — You may not use the material for commercial purposes.

No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

This is a human-readable summary of (and not a substitute for) the [full license](https://creativecommons.org/licenses/by-nc/4.0/legalcode).

---

📌 **Commercial Use Clause**

Commercial use of this software, or derivative works that result in commercial products or services, is **strictly prohibited** without explicit written permission from the copyright holder.

To obtain a **commercial license**, please contact:

📧 dalopeznoria@gmail.com

Include your intended use, organization, and expected scope of deployment or monetization.

---

© 2025 David López

This software is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.


