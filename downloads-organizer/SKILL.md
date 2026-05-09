---
name: downloads-organizer
description: Organize the user's Downloads folder by scanning files, classifying them by priority (matched to recent Claude chats/tasks), age (older than 30 days), or file type, then proposing and executing a folder structure with user approval. Trigger this skill whenever the user says anything like "organize my downloads", "clean up my downloads folder", "my downloads is a mess", "sort my files", "tidy up downloads", or asks about what's in their Downloads folder. Also trigger when the user asks about recent files or mentions needing to find something they downloaded. Never attempt this without explicit user approval before moving any files.
---

# Downloads Organizer

Helps the user scan, classify, and reorganize their Downloads folder. Always requires explicit user approval before moving any files.

---

## Step 1: Scan the Downloads Folder

Use `bash_tool` to list all files in the Downloads folder. Target the standard macOS/Linux path unless context suggests otherwise.

```bash
# List all files (not directories) with metadata
find ~/Downloads -maxdepth 1 -type f -not -name ".*" | while read f; do
  echo "$(stat -f "%SB|%Sm|%N" -t "%Y-%m-%d" "$f" 2>/dev/null || stat --format="%y|%n" "$f" 2>/dev/null)"
done
```

Also list existing subdirectories so you know what folder structure already exists:

```bash
find ~/Downloads -maxdepth 1 -type d | tail -n +2
```

**System file filtering** — skip any file that:
- Starts with `.` (hidden/dot files)
- Has extensions: `.tmp`, `.part`, `.crdownload`, `.download`, `.lock`, `.sys`, `.dll`, `.dmg` (unless user explicitly wants DMGs organized)
- Name matches patterns like `Thumbs.db`, `desktop.ini`, `.DS_Store`

---

## Step 2: Search Recent Claude Conversations

Use the `conversation_search` tool to look for recent chats that might relate to files found in Downloads. 

**Strategy:**
- For each file with a non-generic name (skip names like `image001.jpg`, `document.pdf`, `screenshot.png`), extract 1–3 meaningful keywords from the filename
- Run `conversation_search` queries for those keywords
- Also run a few broad recent searches using `recent_chats` (last 10–15 chats) to get a sense of active projects
- Match filenames against chat topics — look for keyword overlap, project names, client names, or topic areas

**Matching heuristic:**
- Strong match: filename keywords appear in a recent chat title or content
- Weak match: file type + date aligns with a recent work session on a related topic
- Only classify as "priority" on strong matches — when in doubt, fall through to age/type classification

---

## Step 3: Classify Each File

Apply classification rules **in strict priority order**:

### 1. PRIORITY (checked first)
- File has a strong keyword match to a recent Claude conversation or active project
- Goes to: `_Priority/`

### 2. OLD (checked second)
- File was downloaded or created more than 30 days ago
- Goes to: `_Archive/`

### 3. TYPE CLASS (fallback)
Assign based on file extension:

| Folder | Extensions |
|---|---|
| `Images/` | `.jpg`, `.jpeg`, `.png`, `.gif`, `.webp`, `.svg`, `.heic`, `.bmp`, `.tiff` |
| `PDFs/` | `.pdf` |
| `Presentations/` | `.pptx`, `.ppt`, `.key` |
| `Text/` | `.txt`, `.md`, `.rtf`, `.doc`, `.docx`, `.pages` |
| `Data/` | `.xlsx`, `.xls`, `.csv`, `.numbers`, `.json`, `.xml` |
| `Other/` | anything not matched above |

---

## Step 4: Summarize Results for User

Present the plan using this exact format before doing anything:

```
I scanned {X} files in your Downloads folder. Here's what I found:

**📌 Priority — Matched to Recent Projects ({N} files)**
- `filename.ext` → possible match to: [chat title or topic]
- `filename.ext` → possible match to: [chat title or topic]

*(none)* ← use this if no priority matches found

**🗂 Archive — Older than 30 Days ({N} files)**
- `filename.ext` — downloaded [date]
- `filename.ext` — downloaded [date]

*(none)* ← use this if no old files

**📁 Type-Based ({N} files)**
- Images: {N} files
- PDFs: {N} files
- Presentations: {N} files
- Text: {N} files
- Data: {N} files
- Other: {N} files

**Folders I'll create (if they don't already exist):**
- `_Priority/` ← only if there are priority files
- `_Archive/` ← only if there are old files
- `Images/`, `PDFs/`, etc. ← only what's needed

Shall I go ahead and move everything?
```

If the counts are large (20+ files), you may optionally list only the first 5 examples in each category and say "(and X more)".

---

## Step 5: Wait for Explicit Approval

**Do not move any files until the user says yes.** Accept any clear affirmative: "yes", "go ahead", "do it", "looks good", etc.

If the user wants to modify the plan (e.g., "don't move the PDFs", "skip the archive folder"), update the plan accordingly and confirm the changes before executing.

---

## Step 6: Execute

```bash
# Create folders as needed (only ones required by the plan)
mkdir -p ~/Downloads/_Priority
mkdir -p ~/Downloads/_Archive
mkdir -p ~/Downloads/Images
# etc.

# Move files
mv ~/Downloads/filename.ext ~/Downloads/TargetFolder/
```

Move files one category at a time. After all moves are complete, report:

```
✅ Done. Here's what I did:

- Moved {N} files to `_Priority/`
- Moved {N} files to `_Archive/`
- Moved {N} files to `Images/`
- Moved {N} files to `PDFs/`
- etc.

Your Downloads folder now has {X} items organized across {Y} folders.
```

---

## Edge Cases

- **File already in a subfolder**: Skip it — only organize loose files at the top level of Downloads (`-maxdepth 1`)
- **Duplicate filenames**: Before moving, check if a file with the same name exists in the target folder. If so, append `_1`, `_2`, etc. to avoid overwriting
- **Permission errors**: Report the specific file and skip it; continue with the rest
- **Empty categories**: Don't create folders for empty categories
- **User says no or wants changes**: Re-present the modified plan and ask again before executing anything
