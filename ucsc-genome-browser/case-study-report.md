
# Reimagining the UCSC Genome Browser Interface

Independent · 2026 · Bioinformatics Tooling

Part of the [Designing for Attention](../README.md) series.

![Status](https://img.shields.io/badge/status-4b5563?style=flat-square): Design Exploration · Tested Concept

Tools: React.js

Links: [Live app](https://genomebrowserdesign.netlify.app/), Feedback Form


## Overview

A self initiated redesign of the UCSC Genome Browser, exploring how a tool used daily by researchers could be made less cognitively demanding while preserving the depth its users rely on.

## Context

The UCSC Genome Browser is an enormously powerful tool, and that power comes with a steep learning curve. It contains extensive functionality, but is difficult to navigate without prior expertise, effectively adding cognitive load on top of the research itself. That raised the question behind this project: is that friction an inherent limitation of the system, or a solvable design problem?

## Problem

The current interface can be overwhelming, causing cognitive overload, inefficient navigation, and missed insights due to poor hierarchy and a lack of context aware guidance.

## Design Question

> How can the interface help users explore genomic data efficiently while keeping flexibility and depth intact?

This project treats that question the same way the [Galaxy case study](../galaxy/README.md) does: as something to diagnose against specific mechanisms of attention and memory, not against taste.

---

## Existing Interface

[UCSC Genome Browser current interface](https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chr7%3A155799529%2D155812871&hgsid=4129256197_sYbaZYTYljuc6ZqS8NyFXAP5PvFB)

Track names are exposed simultaneously, grouped into dense tables with minimal visual differentiation between primary and secondary actions. The current interface can be overwhelming, causing cognitive overload, inefficient navigation, and missed insights due to poor hierarchy and lack of context-aware guidance.

---

## Heuristic Evaluation

Each finding below is mapped to one of Nielsen's usability heuristics (Nielsen, 1994), with a severity rating.

| Heuristic | Ranking | Description |
| :--- | :---: | :--- |
|Visibility of system status | High | Selected tracks don't visibly refresh upon selection, leaving users unsure whether their action registered at all.|
|Recognition rather than recall | High | Hundreds of tool names are displayed simultaneously, with no way to understand which one to use without prior knowledge of the system.|
|Aesthetic and minimalist design | High | Too many competing calls to action are visible at once, with no visual hierarchy between primary and secondary actions.|
|Visibility of system status | Medium | There's no clear indication of which tracks are currently active. Open and closed states aren't visually distinguishable from one another.|
|User control and freedom | Medium | The toggle system is inconsistent and hard to parse. Users can't easily reverse or compare track selections.|
|Help and documentation | Medium| Sections have no labels or explanations. Users with less domain knowledge have no anchor point for navigation.|

---

## Design Decisions

This is a redesign of an existing expert tool, which comes with a real constraint the Galaxy landing page redesign didn't have to the same degree: existing users have built up real muscle memory and mental models (Norman, 2013) around the current layout, and a redesign that ignores that is solving the wrong problem.

**Design strategy**
- Favor familiarity over novelty. Muscle memory matters for a tool experts already use daily.
- Treat density, not missing features, as the core usability problem.
- Let every change earn its place by tracing back to a specific heuristic finding above, rather than a general aesthetic preference.

**Interaction patterns**
- Progressive disclosure, to reduce visible complexity without removing depth (Nielsen, 1994).
- Optional AI acceleration, so power users keep full manual control while newer users get guided help when they want it.

**Components**
- Expand and collapse panels for progressive disclosure.
- An AI assisted search overlay, optional rather than mandatory.
- An auto refresh toggle with a visible active state indicator.

**Foundations kept from the original**
- The original color identity, since expert users navigate the current interface partly by color recognition.
- The track based layout as the primary mental model, since restructuring that entirely would cost more in relearning than it would gain in clarity.

**Outcome aimed for:** a redesign that feels immediately familiar to expert users, while being meaningfully easier to navigate for newcomers.

---

## Prototype

Built directly in React, using the browser itself as the prototyping environment rather than relying on static mockups. Working in code instead of flat images kept the decisions grounded in real interaction behavior, layout density, toggle responsiveness, and the AI search integration could all be tested against how they actually behaved, not just how they looked.

[UCSC Genome Browser redesign prototype](https://genomebrowserdesign.netlify.app/)

The redesigned entry point leads with a search first interaction (including an optional "Ask AI" overlay), followed by grouped, labeled track categories with expand and collapse panels, replacing the original's flat wall of simultaneously visible track tables.

---

## Concept Testing

The live prototype was shared with three users at varying levels of familiarity with the tool, from active daily users to people familiar with genome browsers but not regular users of this one. Each was asked to explore freely, then complete a short survey. The goal was directional signal, not statistical proof, and that limitation is worth stating plainly rather than implying more confidence than three participants can support.

**Results, 5 point scale, n = 3**
- Interface clarity: 4.7
- Task confidence: 4.3
- Layout guidance: 4.7
- Preferred the redesign over the original: 100%

**What users said**

> "Less crowded. I didn't have to refresh the page to show tracks."

> "Updated interface, and responsive."

> "Descriptions for each section help novices and serve as a refresher for familiar users. It updates automatically when you adjust a track."

The auto refresh behavior on track selection and the added section descriptions were each called out specifically as the most impactful changes, which lines up with the two highest severity heuristic findings from the evaluation above (visibility of system status, and recognition rather than recall).

---

## Impact

This exploration suggests the core problem in the UCSC Browser isn't missing features, it's density without hierarchy. Small structural changes, progressive disclosure, a visible active state, and contextual labels, had an outsized effect on how navigable the interface felt to the people who tried it. The three user review is directional, not conclusive, but consistent enough across a small, mixed familiarity group to treat the approach as worth pursuing further, ideally with a larger and more varied participant pool.

---

## Questions for Discussion

- For an expert tool with years of accumulated user muscle memory, how much visual change is too much before familiarity itself becomes a cost?
- Where's the right line between an optional AI assist and a feature that quietly becomes load bearing for newer users?
- What would it take to test this with a larger and more representative sample of the Browser's actual user base?

---

## References

Nielsen, J. (1994). Enhancing the explanatory power of usability heuristics. *Proceedings of the SIGCHI Conference on Human Factors in Computing Systems.*

Norman, D. A. (2013). *The design of everyday things* (Rev. and expanded ed.). Basic Books.
