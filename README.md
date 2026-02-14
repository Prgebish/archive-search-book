# /search-book

An [AI agent skill](https://agentskills.io) that searches [archive.org](https://archive.org) for books and texts directly from your terminal.

No API keys required — uses the public Archive.org Advanced Search API.

## Install

Copy `SKILL.md` into your agent's skills directory (e.g. for Claude Code):

```bash
mkdir -p ~/.claude/skills/search-book
curl -o ~/.claude/skills/search-book/SKILL.md \
  https://raw.githubusercontent.com/Prgebish/archive-search-book/main/SKILL.md
```

Or clone the repo:

```bash
git clone https://github.com/Prgebish/archive-search-book ~/.claude/skills/search-book
```

After that, the `/search-book` command will be available in your AI coding agent.

## Usage

```
/search-book <query>
```

Write your query in natural language. The AI will figure out what's what — title, author, language, format, etc. Typos are OK too.

### Examples

```
/search-book Asimov, Foundation
/search-book Tolstoy, War and Peace
/search-book quantum physics textbook
/search-book Dickens, Great Expectations, epub
/search-book Mark Twain, Tom Sawyer, djvu, japanese
/search-book science fiction, 1960-1980
```

## Features

- **Search by** title, author, subject, language, publisher, date range
- **Filter by format**: pdf, epub, djvu, kindle, txt
- **Multilingual**: works with any language — Cyrillic, CJK, Arabic, etc.
- **Typo-tolerant**: the AI corrects obvious misspellings before querying
- **Pagination**: ask for "more" to see the next page of results
- **Book details**: pick a result to see full metadata (description, publisher, subjects)
- **Smart broadening**: if a query returns zero results, the AI relaxes filters and retries

## Output

```
1. The Adventures of Tom Sawyer
   Author: Mark Twain | Date: 1881 | Language: eng
   Subject: tom sawyer, adventure, fiction...
   Views: 1,841
   https://archive.org/details/adventurestomsa01twaigoog

Found 185 total results. Showing 1-5.
```

## How it works

The skill instructs the AI agent to:

1. Parse your natural-language query into structured fields (title, author, format, etc.)
2. Build a Lucene query for the Archive.org Advanced Search API
3. Call the API via `curl` and format the results
4. On zero results — automatically broaden the search

The entire skill is a single `SKILL.md` file — no scripts, no dependencies. Compatible with any agent that supports the [Agent Skills](https://agentskills.io) standard.

## Like it?

If you find this skill useful, please star the repository — it helps others discover it.

## License

MIT
