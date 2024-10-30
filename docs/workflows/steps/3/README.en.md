# Translation Integration Phase

This document describes the process of managing translations from the TMS system to their integration into the main repository branch.

## Overview

The workflow involves multiple actors and systems:
- Translator
- TMS (Translation Management System)
- GitHub
- Developers
- Local Environment

## Process Phases

### 1. Translation Phase

1. Translator completes the translation flow in TMS.

### 2. Final Development Phase - Pull Request Review

1. TMS automatically creates a Pull Request (PR) on GitHub with translations [EN-PT].
2. GitHub notifies assigned developer about new PR.
3. Developer downloads PR to local environment.

### 3. Local Review Process

Developer must run a supervised script (`script.rb`) that performs:

#### Automated Actions:
- Rebase and squash PR commits
- Run linter on .yml files

#### Manual Actions:
- Resolve rebase conflicts
- Rewrite `pt-br.yml` files to `pt.yml`
- Final visual verification

#### Common Conflicts:
1. Duplicate keys
2. YML indentation issues

#### Linter Validations:
1. Valid YML syntax
2. No extra spaces
3. Correct UTF-8 encoding

### 4. Acceptance Criteria

To approve PR:
1. Linter passes without errors
2. No conflicts exist
3. Translations are complete

### 5. Resolution Flows

#### Approved PR:
1. Developer approves and confirms PR on GitHub
2. Translations integrate into master branch
3. `EN.yml` and `PT.yml` files integrate into main branch

#### PR Requires Changes:
1. Developer rejects PR on GitHub
2. Translator is notified of required changes
3. Process returns to Translation Phase

#### Common Rejection Reasons:
1. Incomplete translations
2. Format errors
3. PR without changes

## Sequence Diagram
The sequence diagram shows the flow in its last phase where the review of a new Pull Request for Translations is performed.

```mermaid
---
config:
theme: mc
---
sequenceDiagram
    participant TD as Translator
    participant TMS as TMS System
    participant GH as GitHub
    participant M as Master Branch
    participant DA as Developer A
    participant L as Localhost
    Note over TD,TMS: ... Translation Phase
    TD->>+TMS: Completes translation flow
    Note over TMS,L: Final Phase - Translation Integration into Buk
    TMS->>-GH: Creates PR with translations [EN-PT]
    GH->>DA: Notifies new PR with translations
    Note over DA: Receives notification<br/>of new PR<br/>
    DA->>L: Downloads new PR
    rect rgb(255, 245, 245)
        Note over L: Supervised execution of script.rb
        L->>L: Rebase and squash PR commits [Auto]
        Note over L: Common conflicts:<br/>1. Duplicate keys<br/>2. YML indentation
        L->>L: Resolve rebase conflicts [Manual]
        L->>L: Linter for .yml files [Auto]
        Note over L: Validations:<br/>1. Valid YML syntax<br/>2. No extra spaces<br/>3. UTF-8 encoding
        L->>L: Rewrite pt-br.yml > pt.yml files [Manual]
        L->>L: Visual verification [Manual]
    end
    alt PR Approved
        Note over L: Acceptance criteria:<br/>1. Linter passes without errors<br/>2. No conflicts<br/>3. Translations complete
        L->>GH: Approves and confirms PR
        GH->>M: Integrates translations
        Note over M: EN.yml and PT.yml files<br/>integrated in master
    else PR Requires Changes
        Note over L: Common rejection reasons:<br/>1. Incomplete translations<br/>2. Format errors<br/>3. PR without changes
        L->>GH: Rejects PR
        GH->>TD: Notifies required changes
        Note over TMS: Returns to<br/>Translation Phase<br/>
    end
```

## Important Notes

- YML file format consistency is crucial (source and target files)
- Manual verification ensures translation quality
- Process designed to maintain translation integrity throughout