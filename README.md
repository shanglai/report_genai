# report_genai


## Description

General Use GenAI project for creating automated reports.

A multi-agent system with compartmented roles, delimited tasks, evolving knowledge, insights generator and audits.

# Process

[Dataset] --> [AI System] --> [Report]

# Structure

* the agents are defined with <agent> and the inputs and outputs by brackets [element]:
TASKS: given a certain data and certain context and auxiliary datasets and policies, generate a report that tells the story within the data by transforming (summarizing, deriving, pivoting) the data into other datasets and then generate according visualizations, interpretations and conclusions.

![report_genai_structure](https://github.com/user-attachments/assets/b31fe4e1-342f-487f-bddb-f6faffc0664c)

## STRUCTURE: 
* there is a main AI Agent, called <mainAI>. <mainAI> understands the dataset with a given context. it also understands the given policies as restrictions, biases and directions that must be applied to the data. <mainAI> gives instructions in sequence to the following agents:
* there's an agent that records inconsistencies or anomalies found when <mainAI> integrates new knowledge, it's called <auditAI>.
* there's an agent responsible for interpreting policies and generating summarized, clear text that constitute restrictions, bias and focus of the reports, it's called <policyAI>.
* there's an agent responsible for transforming the code, called <dataAI>. <dataAI> receives <mainAI>'s prompt regarding what kind of data it needs (summarized, transposed, transformed, applying corresponding filters) from the source data, and generates additional datasets.
* there's another agent called <interpreterAI> that interprets the data from <dataAI> and gets context from <mainAI> on what kind of interpretations it requires. output is simple text.
* another agent is <vizAI>, which generates visualizations (bar, point, line or box plots) using <mainAI> context and <interpreterAI>'s interpretations.
* another agent is <reportAI>, which specializes on generating coherent reports with cover, index, formatting, sections (introduction, summary, dcontent, conclusion, next steps), while also presenting everything in a professional and dynamic style and highlighting important insights.

## PROCESS:
* <mainAI> gets the [original dataset], [context of the data], [policies and bias], generates an [understanding] of the main dataset. the [understanding] is the complete understanding of the data, interpretations, policies, bias, focus and other elements surrounding the data, enabling <mainAI> to dictate new knowledge and incorporate it to itself, turning <mainAI> into a subject matter expert by a continuous cycle of giving instructions, integration of data and reflection on it to refine understanding.
* when <mainIA> finds inconsistent, conflicting or anomalous data in *ANY* of the steps in the process when it tries to integrate knowledge into [understanding], it tries to either a. solve the conflict or b. discard the data, and sends and [audit incident] to <auditAI>, which records it. the [audit incident] describes in detail the step of the process where it was found, the <AI> that generated it, the <AI> that detected it, the description of the incident, the reason of why it's an incident (conflict, inconsistency, anomaly or other), possible workarounds or information needed to solve it.
* <mainAI> sends [policies, bias and focus] to <policyAI>, which interprets them and generates concise, well-defined outputs: [policies] defines an organization's policies (ie. "price for X item must never be lower than $50#, or "revenue goals are $50 million for this Q"), [bias] define an organization's restrictions (ie. "though it's an energy company, we don't involve in fracking endeavours because of environmental concerns"), [focus] details an organization's direction (ie. "we want to grow new business in South Asia this year").
* <mainAI> gets the [policies], [bias] and [focus] and updates its [understanding], then uses it to generate [dataAI prompt], [interpreterAI prompt] and [vizAI prompt].
* <dataAI> gets [dataAI prompt] and generates the required datasets, concise and compact. outputs are [dataset 1] , ..., [dataset N] and their corresponding descriptions [description 1], ..., [description N] as requested by <mainAI>
* <mainAI> gets [dataset 1] , ..., [dataset N] datasets and [description 1], ..., [description N] from <dataAI> and uses <mainAI>'s [understanding] to create a set of requirements for interpretation for the datasets, this is the [interpreterAI prompt].
* <interpreterAI> gets [interpreterAI prompt] and [dataset 1] , ..., [dataset N], and generates the required interpretations [interpretation 1], ..., [interpretation N], each of which examines the corresponding dataset [dataset i], highlighting features, generating synopsys, defining summary statistics and generating valuable insights from it, following the [interpreterAI prompt]'s requirements.
* <mainAI> gets the interpretations [interpretation 1], ..., [interpretation N] and examines them: cross-examines them with [understanding] to see if they are compatible and sound (ie. "there can't be an underage person requesting a credit card"), uses statistics to double check results (max, min, median, average, stddev, etc). it then summarizes the interpretations [interpretation 1], ..., [interpretation N] and adds them to [understanding].
* <mainAI> then uses interpretations [interpretation 1], ..., [interpretation N] and [understanding] and generates a [vizAI prompt], specifying a list of visualizations requiremients that can be generated from the [dataset 1] , ..., [dataset N] datasets following [interpretation 1], ..., [interpretation N] and deciding which datasets generate the most impact. each item in the visualization requirements list in [vizAI prompt]] defines the type of visualization, variables used, title, axis lables, tick labels and measures, groups, colors, facets and more data required for producing them.
* <vizAI> gets the [dataset 1] , ..., [dataset N] datasets and the [vizAI prompt] and generates a list of visualizations [viz 1], ..., [viz N] that match the requirements.
* <mainAI> uses the [understanding] to generate a [conclusion] on the data, highlighting insights by the following categories: critical, important and relevant. it also generates [next steps] as follow-up activities.
* <mainAI> sends [understanding], [dataset 1] , ..., [dataset N], [interpretation 1], ..., [interpretation N], [viz 1], ..., [viz N], [conclusion] and [next steps] to <reportAI> which generates a coherent [final report], by: analyzing the assets (datasets, insights, visualizations, etc), setting the report layout, ordering the assets within the layout, generating the report with a professional and dynamic style.
* finally, <auditAI> generates a separate [anomaly report] with all the anomalies it has recorded, with the same style as found in the [final report].
## ADDITIONAL DEFINITIONS:
* [understanding] is a JSON-formatted string, with the following layout as a base (layout can change depending on the evolution of [understanding] and of <mainAI> as an SME:
{
  "context": "...",
  "policies": [...],
  "data_insights": [...],
  "contradictions": [...],
  "key_entities": ["revenue", "customer region"],
  ...
}
* [policies], [bias] and [focus] are also JSON-formatted strings, example:
{"biases": ["focus on minority groups"]}

## Flow

flowchart TD
    A[original dataset, context, policies] --> M1[<mainAI> generates understanding]
    M1 --> P[<policyAI> summarizes policies]
    P --> M2[<mainAI> updates understanding]
    M2 --> D[<dataAI> generates transformed datasets]
    D --> M3[<mainAI> updates understanding with descriptions]
    M3 --> I[<interpreterAI> produces interpretations]
    I --> M4[<mainAI> validates and summarizes insights]
    M4 --> V[<vizAI> generates visualizations]
    V --> M5[<mainAI> creates conclusion + next steps]
    M5 --> R[<reportAI> generates report]


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


