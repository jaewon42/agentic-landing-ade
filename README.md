# LandingAI ADE Plugin for Claude Code

Interactive document extraction skill for [Claude Code](https://claude.com/claude-code) powered by [LandingAI's Agentic Document Extraction API](https://docs.landing.ai/ade/ade-overview).

## What it does

When you mention document parsing, PDF extraction, or structured data extraction, the skill activates and walks you through an interactive wizard:

1. **Collects your config** — API key, region (US/EU), operation type, output directory
2. **Executes the right API calls** — via `curl` commands, not Python scripts
3. **Builds schemas interactively** — define extraction fields one-by-one, generate from document content, or load from file
4. **Saves everything** — outputs, schemas, and split configs are saved for reuse
5. **Stays token-efficient** — never dumps large API responses into context; uses targeted `jq` queries

## Operations

| Operation     | What it does                                                         |
| ------------- | -------------------------------------------------------------------- |
| **Parse**     | Convert PDF/image/spreadsheet to markdown + chunks                   |
| **Extract**   | Pull structured key-value fields from a document using a JSON schema |
| **Split**     | Classify/segment a multi-document PDF into categories                |
| **Parse Job** | Async parsing for large documents (50+ pages)                        |

## Installation

```bash
claude plugin add landing-ai/agentic-landing-ade
```

Or add the repository manually:

```bash
claude plugin add-repo landing-ai/agentic-landing-ade
claude plugin install landing-ade
```

## Requirements

- A LandingAI API key (`VISION_AGENT_API_KEY`) — get one at [va.landing.ai](https://va.landing.ai)
- `curl` and `jq` installed (standard on macOS/Linux)

## Supported File Types

| Type         | Formats                                    |
| ------------ | ------------------------------------------ |
| Documents    | PDF, PNG, JPG, JPEG, TIFF, BMP, WEBP, HEIC |
| Spreadsheets | XLSX, CSV                                  |

## Usage Examples

Just tell Claude what you want:

- "Parse this PDF for me" — triggers the parse wizard
- "Extract the invoice number and total from this document" — triggers parse + extract
- "Split this PDF bundle into bank statements and pay stubs" — triggers parse + split
- "I have a large 100-page PDF to process" — triggers async parse job

The skill handles the rest interactively.

## License

MIT
