# File Translation Process

This document describes the workflow for translating language files in our system.

## Overview

The translation process follows a sequential flow involving different actors and systems:
- Developers (A and B)
- GitHub as version control system
- Translation Management System (TMS)
- Translator

## Process Phases

### 1. Initial Development Phase
- Developer A creates a Pull Request (PR) with source files in Spanish (es.yml)
- GitHub notifies Developer B about the new PR
- Developer B reviews and approves the PR
- GitHub merges PR into master branch

### 2. Translation Phase
- TMS retrieves new source files from GitHub
- GitHub syncs source files with TMS
- TMS notifies Translator about pending translations
- Translator performs translations to English and Portuguese [EN-PT]
- Translator completes translation flow in TMS
- TMS creates PR with new translations [EN-PT]

### 3. Final Development Phase
- GitHub notifies Developer A about PR with new translations
- Developer A reviews and approves PR
- GitHub merges translations PR into master branch

## Sequence Diagram

[The sequence diagram](/docs/assets/seq-diagram.en.png) shows the complete translation process flow, including all interactions between the different actors and systems involved.

```mermaid
---
config:
  theme: mc
---
sequenceDiagram
  participant DA as Developer A
  participant DB as Developer B
  participant GH as GitHub
  participant H as TMS
  participant T as Translator
  rect rgb(230, 240, 255)
    Note right of DA: Development Phase
    DA ->> GH: Create PR es.yml (source files)
    GH ->> DB: Notify new PR
    DB ->> GH: Review and Approve PR
    GH ->> GH: Merge PR to master
  end
  rect rgb(255, 245, 245)
    Note right of H: Translation Phase
    H ->> GH: Get new source files
    GH ->> H: Sync source files
    H ->> T: Notify pending translations
    T ->> T: Perform translations to [EN-PT]
    T ->> H: Complete translation flow
    H ->> GH: Create PR new translations [EN-PT]
  end
  rect rgb(230, 240, 255)
    Note right of DA: Development Phase
    GH ->> DA: Notify PR new translations [EN-PT]
    DA ->> GH: Review and Approve PR
    GH ->> GH: Merge PR to master
  end
  Note over DA, T: Translation Process
```

## Important Notes
- Source files are always in Spanish (es.yml)
- Translations are done to English and Portuguese [EN-PT]
- Each phase is clearly delimited and requires approval before moving to the next one
- The process is automated through GitHub and the Translation Management System