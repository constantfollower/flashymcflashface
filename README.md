# Flashy for Islay

A single-page flashcard app for SQA Higher revision, designed to run as a static site (GitHub Pages).

## Run it

### Option A: GitHub Pages (recommended)
1. Create a new GitHub repository.
2. Upload the contents of this folder to the repository root.
3. In GitHub: **Settings → Pages**.
4. Under **Build and deployment**, set:
   - **Source**: Deploy from a branch
   - **Branch**: `main` (or `master`) and **/** (root)
5. Save. Your site URL will appear in the Pages section.

### Option B: Local (for testing)
Some browsers block `fetch()` when you open `index.html` directly from disk.
Run a tiny local web server from the folder, for example:

- Python: `python3 -m http.server 8000`

Then open `http://localhost:8000`.

## Add or edit decks

Decks live in `decks/` as JSON files. The app reads `decks/index.json` to build the deck menu and to load all deck files at startup.

### Deck file format
Each deck file is:

```json
{
  "meta": { "subject": "...", "topic": "...", "deck": "...", "version": "1.0" },
  "cards": [
    {
      "id": "unique_id",
      "subject": "English",
      "topic": "RUAE",
      "deck": "Language and question words",
      "front": "Word choice",
      "back": "The specific words a writer uses...",
      "use": "In RUAE, define word choice and show it with a short quote or reference.",
      "related": ["english", "ruae", "analysis"]
    }
  ]
}
```

### Register a deck
Add a new entry to `decks/index.json`:

```json
{
  "kind": "deck",
  "label": "English / RUAE / New deck name",
  "subject": "English",
  "topic": "RUAE",
  "deck": "New deck name",
  "file": "decks/english/new_deck.json"
}
```

You can also add an “all decks” entry for a subject:

```json
{ "kind": "folder", "label": "English / All decks", "subject": "English" }
```

## Notes
- Everything is static HTML and JSON. No build step.
- The session map is stored only in the browser (no accounts, no syncing).
