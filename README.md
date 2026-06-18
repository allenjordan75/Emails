# Email Repository

This repository contains a searchable archive of the email and PDF files provided by Jordan Allen.

## What is here

- `originals/` keeps the source files, grouped by file type.
- `text/` contains extracted text used for keyword search.
- `metadata/index.csv` and `metadata/index.json` list every file, category, hash, extracted text path, and duplicate status.
- `metadata/duplicates.csv` and `metadata/duplicates.json` identify exact file duplicates and same-text duplicates.
- `tools/search_archive.py` searches the archive from the command line.
- `tools/build_archive.py` rebuilds the archive from the source file list.

## Quick Search

Search for a single word:

```sh
python3 tools/search_archive.py curriculum
```

Search for multiple words, matching any word:

```sh
python3 tools/search_archive.py funding UCC
```

Require every word:

```sh
python3 tools/search_archive.py --all "James" "Jacob"
```

Limit to a category:

```sh
python3 tools/search_archive.py --category funding UCC
```

Show duplicate files too:

```sh
python3 tools/search_archive.py --include-duplicates funding
```

## Categories

The archive builder assigns broad categories from filenames, email headers, and text snippets:

- `funding`
- `curriculum-review`
- `demand-complaint`
- `policy-legal`
- `other`

## Notes

PDF text extraction is best effort with the tools available on this machine. The original PDFs are preserved even when extracted text is noisy. The PST mailbox file is retained as an original binary; to expand it into individual messages, install `readpst` or another PST converter and rerun the archive build after adding the extracted `.eml` files.
