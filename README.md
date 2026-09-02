<p align="center">
  <img src="Quantum-logo.png" alt="Quantum" width="120">
</p>

<h1 align="center">Quantum</h1>

<p align="center">
  A fast local notes editor and knowledge base for Windows.<br>
  Your writing stays as plain markdown files in a folder on your disk.
</p>

<p align="center">
  <a href="https://github.com/Freaction/Quantum-release/releases/latest">Download the latest version</a>
</p>

<p align="center">
  <b>English</b> · <a href="README.ru.md">Русский</a>
</p>

---

## What it is

Quantum is a desktop app for a personal knowledge base: notes, links between them,
search, book reading and structured metadata. There is no cloud and no account —
the app opens a folder you choose and works with the `.md` files inside it directly.
Those files stay readable in any other editor, so if Quantum ever stops suiting you,
your notes are already where you need them and require no export.

The app is built on Tauri: the interface is React, while everything touching the disk,
the index and search runs in Rust. That is where its main property comes from — speed.
Opening a note, searching and switching tabs are meant to feel instant on a vault of
any size.

## Features

**Editor**

- Live markdown preview: syntax is only visible where the caret is, the rest of the text reads as a finished document.
- Tables with merged cells, drag-to-reorder rows and columns, resizable widths.
- Images and video inline, added by dropping files into the vault.
- Code blocks with highlighting, quotes, callouts, and lists you can move with Alt+arrows.
- Frontmatter collapses into a tidy block and is edited as a set of fields.
- Note templates: your own starting points for new pages.

**Links and navigation**

- Wiki links `[[Note]]`, backlinks and a list of outgoing links.
- A link graph that updates as you edit.
- Tabs, back/forward history, and a document outline.
- Multiple vaults: each folder gets its own index, and switching never mixes their data.

**Search**

- Full-text search across the vault powered by Tantivy — results appear as you type.
- In-page search with highlighted matches.
- Metadata fields are stored in the index as typed values, which keeps queries over them fast.

**Querying the vault**

A ```` ```dataview ```` block builds tables and lists of notes from conditions: `TABLE` and
`LIST` with `FROM`, `WHERE`, `SORT` and `LIMIT` clauses, file fields and a set of functions.
The syntax follows Obsidian's DQL from the outside so existing queries carry over without
rewriting, while parsing and execution happen entirely in Rust.

**Books**

- A built-in reader for EPUB, MOBI, AZW3 and FB2 files kept in the same vault.
- A book page with cover, author, status and reading progress.
- Text selected in the reader goes into the note as a quote.

**Appearance and output**

- Light and dark themes, adjustable fonts and interface scale.
- Page covers and book thumbnails.
- Export a note to an A4 PDF that matches what you see on screen.
- Russian and English interface.

**For AI agents**

A built-in MCP server gives agents access to the vault: reading, searching, creating and
editing notes, following links and working with metadata. An agent's edits and your own
typing merge instead of overwriting each other — the document lives in a CRDT model, so
text under your caret survives while an agent writes to the same file.

## Installation

1. Open the [latest release](https://github.com/Freaction/Quantum-release/releases/latest).
2. Download `quantum-app_<version>_x64-setup.exe`.
3. Run the installer.

The app installs into your user profile and does not ask for administrator rights.
The installer is not signed with a Windows certificate, so SmartScreen may warn you —
choose "More info" → "Run anyway".

On first launch, pick a folder for your vault: an empty one for a fresh start, or an
existing folder that already holds your markdown files.

## Updates

Quantum updates itself. On launch it checks this repository, and if a newer version is
out, it downloads and installs it while showing the progress, then restarts. Every update
is signed with the developer key and verified before installation. With no network
connection the app simply starts as usual.

There is no need to install a new version over the old one by hand.

## Requirements

- Windows 10 or 11, 64-bit.
- WebView2 — present on the system by default, and the installer pulls it in if it is missing.

macOS and Linux builds are not published yet.

## Your data

Everything lives on your disk:

- notes — `.md` files in the folder you chose, exactly where you see them;
- attachments — inside the vault folder next to the notes;
- the search index, scroll positions and reader bookmarks — service caches you can always
  delete: they are rebuilt from your files.

The app sends nothing to a server. It reaches the network only for updates and — if you
turn source analysis on yourself — for Wikipedia articles.

## Feedback

Bugs and suggestions go to [Issues](https://github.com/Freaction/Quantum-release/issues).
It helps to include the app version — Settings → System → About — and what you were doing
before things went wrong.

## About this repository

Only finished builds and the auto-update manifest are published here. The application
source code lives in a separate private repository.
