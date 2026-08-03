# Case Study: Reimagining the Galaxy Landing Experience

Part of the [Designing for Attention](../README.md) series. See the [full argument](../THESIS.md) behind this approach.

## Overview

Galaxy is one of the most widely adopted open source platforms for accessible and reproducible bioinformatics. Its web based interface enables researchers to perform complex computational analyses without requiring extensive command line experience, while maintaining transparency and reproducibility.

As the platform has evolved, its interface has expanded to support a growing ecosystem of educational resources, community initiatives, scientific infrastructure, and thousands of bioinformatics tools. Each component serves an important purpose, but supporting that many goals within a single interface presents a real design challenge.

This case study presents a working prototype redesign of three areas of the Galaxy experience: the landing page, the visualizations browser, and the workflows browser. Rather than proposing a definitive solution, it explores how established principles from human computer interaction and user experience design might improve usability while preserving Galaxy's flexibility, transparency, and scientific rigor.

---

## Research Question

> How might established interface design principles improve the usability of Galaxy's landing experience and tool discovery workflow, while preserving the flexibility required by a modern bioinformatics platform?

## Design Hypothesis

Applying principles such as visual hierarchy, information architecture, progressive disclosure, and cognitive load reduction may help users identify relevant information and available actions more efficiently, without reducing access to Galaxy's extensive functionality.

This hypothesis is intended to motivate discussion and future usability evaluation, not to claim a validated improvement.

---

## Existing Interface

![Galaxy current homepage](./assets/galaxy-current.png)

---

## Design Principles

The redesign was guided by seven established principles, drawn from cognitive psychology and human computer interaction research rather than aesthetic preference.

**Visual hierarchy.** Interfaces should communicate importance through layout, spacing, typography, and emphasis, so users can identify primary actions before secondary information. Related to the Von Restorff effect, contrast only signals importance when it's used sparingly (Von Restorff, 1933).

**Progressive disclosure.** Complex systems should reveal information as users need it, instead of presenting every available option simultaneously (Nielsen, 1994).

**Information architecture and Gestalt grouping.** Related information should be organized into meaningful groups that support users' mental models and common workflows, following the Gestalt principles of proximity, similarity, and common region (Wertheimer, 1923).

**Recognition over recall.** Interfaces should make available actions easy to recognize, instead of requiring users to remember where functionality exists (Nielsen, 1994).

**Cognitive load reduction.** Interfaces should minimize unnecessary mental effort, so users can focus on the scientific task rather than on interpreting the interface itself, consistent with cognitive load theory (Sweller, 1988) and the limits of working memory (Miller, 1956).

**Hick's Law.** The time it takes to make a decision increases with the number and complexity of available choices (Hick, 1952). This is the direct justification for collapsing an exhaustive tool list behind a small number of primary actions, rather than exposing everything at once.

**Fitts's Law.** The time to acquire a target is a function of its size and its distance from the current pointer position (Fitts, 1954). This shaped the sizing and placement of primary actions, so the most common next step is also the easiest one to reach.

---

## Interface Observations

These observations are based on the existing interface and interpreted through the principles above. They're intended to motivate discussion, not to represent findings from formal usability testing.

**Observation 1. Flat information hierarchy.**
The landing page introduces navigation, educational resources, announcements, documentation, citations, community information, and infrastructure acknowledgements with relatively similar visual prominence. Because multiple sections compete for attention, the interface gives few visual cues indicating where a new user should begin.

**Observation 2. Multiple competing goals.**
The landing page is trying to introduce Galaxy, teach new users, support experienced users, promote community engagement, highlight scientific publications, and acknowledge funding and infrastructure, all at once. Each objective is valuable individually. Presenting them together creates an interface responsible for too many competing priorities at the same time.

**Observation 3. Tool discovery emphasizes completeness over exploration.**
Galaxy provides access to thousands of analysis tools through a searchable navigation structure. Categories, navigation, and individual tools receive similar visual treatment, requiring users to actively search and browse to discover available functionality. Per Hick's Law, the sheer number of simultaneously visible, undifferentiated options increases the time and effort it takes to decide what to do next (Hick, 1952). This is particularly hard for users who know the biological question they want to answer but aren't yet familiar with Galaxy's available tools.

**Observation 4. A genuinely diverse user population.**
Galaxy supports students, researchers, bioinformaticians, software developers, and system administrators in the same interface. Designing for that range is inherently difficult. Features that benefit experienced users can increase complexity for newcomers, while simplifying too aggressively risks reducing flexibility for the people who rely on it.

---

## Design Goals

1. Establish a stronger visual hierarchy.
2. Reduce unnecessary cognitive effort.
3. Improve first time orientation.
4. Increase discoverability of available tools, visualizations, and workflows.
5. Preserve Galaxy's flexibility and reproducibility.

---

## Proposed Redesign: Landing Experience

![Galaxy landing page prototype](./assets/galaxy-landing-prototype.png)

**Hero section.** The first section answers three questions immediately: what is Galaxy, why would I use it, and what should I do next. Three primary actions, Getting Started, Installing Galaxy, and Browse All Tools, are sized and grouped so the most common next step is also the easiest to reach (Fitts, 1954), and are emphasized ahead of supporting resources.

**Information architecture.** Rather than presenting many unrelated sections simultaneously, the redesign groups content by user intent: introduction, platform capabilities, learning resources, community, scientific citations, then infrastructure partners. This encourages a more gradual introduction to the platform while preserving access to the same information.

**Visual grouping.** Whitespace, consistent spacing, and section boundaries separate unrelated concepts into distinct visual groups. The objective isn't to remove information, it's to reduce competition between unrelated content.

---

## Proposed Redesign: Tool Discovery

Two areas of Galaxy's tool ecosystem, visualizations and workflows, were redesigned around the same underlying pattern: search first, then browse a small number of clearly labeled groups, then scan a grid of cards rather than a dense list.

### Visualizations

![Galaxy visualizations prototype](./assets/galaxy-visualizations.png)

A search field sits above the content by default, so a user who already knows what they want never has to browse at all. Below it, a two way tab, All Visualizations and Saved Visualizations, replaces what would otherwise be a single undifferentiated list, applying Hick's Law by cutting the immediate decision down to one of two paths rather than one of many (Hick, 1952). Each visualization type is presented as a card with an icon, a name, and a one line description, so the grid can be scanned by shape and label before a user has to read anything closely, consistent with recognition over recall (Nielsen, 1994) and Gestalt similarity grouping (Wertheimer, 1923).

### Workflows

![Galaxy workflows prototype](./assets/galaxy-workflows-public.png)

The workflows browser applies the same pattern with one addition: a three way tab for My Workflows, Workflows Shared with Me, and Public Workflows, grouping by ownership and origin rather than leaving all workflows in a single pool a user has to filter mentally. Each workflow card shows its title, author, a short description, and a small number of tags, with less common tags collapsed behind a "plus N more" affordance, an application of progressive disclosure (Nielsen, 1994) that keeps the card scannable without hiding information a user might still need. Consistent icon actions, view, download, and run, sit in the same position on every card, so their location becomes something a returning user recognizes rather than has to relocate each time.

![Galaxy workflows shared with me, logged out state](./assets/galaxy-workflows-shared.png)

The logged out state for Workflows Shared with Me is worth calling out on its own. Rather than an empty or broken looking screen, it states plainly why there's nothing to show and offers the two relevant next actions, Login and Register, directly in place. This keeps the system's status visible to the user at all times, one of Nielsen's original usability heuristics (Nielsen, 1994), instead of leaving them to guess whether the page failed to load or they simply have nothing shared with them yet.

---

## Engineering Considerations

This redesign intentionally focuses on interaction design rather than implementation. Several questions remain open:

- How would experienced Galaxy users respond to a simplified landing experience?
- Should interfaces adapt based on user expertise?
- How much customization should institutions have over their own Galaxy deployments?
- Can improved discoverability coexist with Galaxy's extensive feature set?
- Which changes could be implemented incrementally, without disrupting existing workflows?

Answering these well would take collaboration between interface designers, software engineers, and the Galaxy community, not a solo redesign.

---

## AI Considerations

As AI becomes more integrated into scientific software, the relationship between graphical interfaces and command line workflows keeps evolving. AI doesn't have to replace either interaction model, it can bridge them.

Potential applications include natural language workflow generation, AI assisted tool discovery, workflow explanation, parameter recommendations, interactive onboarding, context aware documentation, and workflow summarization.

A future interface could let a researcher describe their biological objective in plain language, while AI translates that intent into a transparent, reproducible Galaxy workflow that stays fully editable, not a black box.

---

## Discussion

This redesign isn't meant to replace Galaxy's existing interface, or to suggest there's a single optimal solution. It applies established human computer interaction principles to explore how scientific software might reduce unnecessary cognitive effort while preserving what has made Galaxy successful.

The intent is to open a conversation about the role of usability in bioinformatics software, and how interface design can evolve alongside advances in AI, computational biology, and increasingly complex analytical workflows.

**Questions for discussion**
- Which usability challenges are unique to bioinformatics software specifically?
- How should scientific software balance flexibility with simplicity?
- When does exposing every available option become counterproductive?
- What role should AI play in scientific interfaces?
- How can usability improvements preserve transparency and reproducibility?
- How should interfaces evolve as bioinformatics workflows become increasingly AI assisted?

---

## References

Card, S. K., Moran, T. P., & Newell, A. (1983). *The psychology of human computer interaction.* Lawrence Erlbaum Associates.

Fitts, P. M. (1954). The information capacity of the human motor system in controlling the amplitude of movement. *Journal of Experimental Psychology, 47*(6), 381 to 391.

Hick, W. E. (1952). On the rate of gain of information. *Quarterly Journal of Experimental Psychology, 4*(1), 11 to 26.

International Organization for Standardization. (2018). *Ergonomics of human system interaction, part 11: Usability, definitions and concepts* (ISO 9241 to 11:2018).

Miller, G. A. (1956). The magical number seven, plus or minus two: Some limits on our capacity for processing information. *Psychological Review, 63*(2), 81 to 97.

Nielsen, J. (1994). Enhancing the explanatory power of usability heuristics. *Proceedings of the SIGCHI Conference on Human Factors in Computing Systems.*

Norman, D. A. (2013). *The design of everyday things* (Rev. and expanded ed.). Basic Books.

Shneiderman, B. (1987). *Designing the user interface: Strategies for effective human computer interaction.* Addison Wesley.

Sweller, J. (1988). Cognitive load during problem solving: Effects on learning. *Cognitive Science, 12*(2), 257 to 285.

Von Restorff, H. (1933). Über die Wirkung von Bereichsbildungen im Spurenfeld. *Psychologische Forschung, 18*, 299 to 342.

Wertheimer, M. (1923). Laws of organization in perceptual forms. *Psychologische Forschung, 4*, 301 to 350.

*Citation details above follow standard HCI referencing conventions and are believed accurate, but have not been independently checked again against a citation database. Worth a quick check before this is presented for formal academic or professional review.*
