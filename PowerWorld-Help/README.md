# PowerWorld Simulator Help — Offline Markdown Repository

An offline, searchable Markdown copy of the PowerWorld Simulator WebHelp
(<https://www.powerworld.com/WebHelp/>), captured 2026-09-18.

Built as a knowledge base for AI assistants (Claude, ChatGPT, Claude Code) and for
plain `grep`. Everything resolves locally: no page in this repository links back out
to the live help site for its content.

## What is here

| | |
|---|---|
| Topics | 1,670 (1,603 from the help system's table of contents + 67 reachable only by links) |
| Chapter files | 80 Markdown files, 6.6 MB total |
| Images | 1,097 figures and screenshots in `images/` (273 MB) |
| PDFs | 3 reference documents in `pdf/` |
| Internal links | 12,308, all verified to resolve |

## Where to start

- **[`00-INDEX.md`](00-INDEX.md)** — every topic, three ways: by chapter, by the original
  table of contents, and alphabetically. Start here to find a specific topic.
- **[`00-MAP.md`](00-MAP.md)** — how the 27 source books map onto the 80 chapter files,
  plus a diagram of how the parts cross-reference each other.
- **`manifest.json`** — machine-readable chapter list, sizes and the cross-reference graph.
- **`toc.json`** — the original help system's table of contents tree.

## File conventions

Each chapter file is one part of the manual, holding 5–65 topics as `##` sections:

```
NN-chapter-name.md          a chapter
NN-chapter-name-partK.md    a chapter split because it exceeded ~150 KB
```

Every file opens with YAML front matter (`title`, `part`, `topics`, `source`,
`generated`) followed by an `H1`, a one-line description, and a list of its topics.

Every topic section looks like this:

```markdown
<a id="stable-anchor"></a>

## Topic Title

*Source: [`Content/MainDocumentation_HTML/Topic.htm`](https://www.powerworld.com/...)*

...body...
```

The `<a id="...">` anchors are stable link targets. Cross-references between topics are
rewritten as `[Text](32-available-transfer-capability.md#atc-dialog)`, so a link from any
topic lands on the exact section, in whichever file it ended up in. Images resolve as
`images/Name.gif`; filenames are ASCII with no spaces.

## Searching it

Plain text search works well because every topic keeps its original title as a heading:

```bash
grep -rn --include='*.md' -i "contingency element"     # find topics
grep -rln --include='*.md' -i "GENROU"                 # find files
```

For an assistant, the useful pattern is to load `00-INDEX.md` first to locate the topic,
then open only the one chapter file it points at — the files are deliberately sized so a
single chapter fits comfortably in context.

## Provenance and regeneration

Content is the property of PowerWorld Corporation, reproduced here as a personal offline
reference copy; it is not for redistribution. The capture reflects the help system as of
the date above — for anything version-sensitive, check the live site.

Conversion pipeline: MadCap Flare TOC (`Data/Tocs/Primary*.js`) → topic HTML → content
extraction (`div#mc-main-content`, MadCap dropdowns flattened, inline styling converted to
real emphasis) → `pandoc -f html -t gfm` → chapter assembly with link and image rewriting.
