# 6. Files, Paths, and Documents

Enable the module first:

```janna
use files
```

## 6.1 Text files

- `files.read path` — UTF-8 text.
- `files.write path content` — replace/write UTF-8 text.
- `files.append path content` — append UTF-8 text.
- `files.delete path` — delete a file.
- `files.exists path` — path existence test.

## 6.2 Directories and paths

- `files.make_folder path` — creates parents as needed.
- `files.list path` — sorted entry names.
- `files.delete_folder path` — removes an empty directory; non-empty removal fails.
- `files.join base child`
- `files.name path`
- `files.extension path`
- `files.parent path`
- `files.absolute path`
- `files.is_file path`
- `files.is_folder path`

## 6.3 Markdown output

`files.write_markdown path content` writes UTF-8 Markdown text.

```janna
files.write_markdown "report.md" "# Report"
```

## 6.4 DOCX output

`files.write_docx path content` creates a DOCX document using `python-docx`. Each input line becomes a paragraph. If DOCX support is unavailable in the installation, Janna reports a runtime error rather than silently changing the output format.

```janna
files.write_docx "report.docx" "First line\nSecond line"
```

## 6.5 Build behavior

Document and path functionality is part of the V3 runtime capability set (`document_output`, `files_paths`) and is covered by source, check, run, and build tests.

