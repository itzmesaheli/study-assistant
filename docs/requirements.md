# Requirements Document - AI Study Assistant

**Author:** Saheli Sarkar | UNAI TECH Virtual Internship 2026 | Phase 1, Day 4

## Problem
Students spend a lot of time summarizing notes and making practice questions. This tool does it automatically using AI.

## Functional Requirements
1. Read study notes from TXT and PDF files.
2. Clean the text and split long notes into chunks.
3. Generate a short summary of the notes using an AI API.
4. Generate 5 quiz questions with answers from the notes.
5. Save the summary and quiz as a Markdown file.
6. Automatically process every new file placed in the data/ folder.
7. Show clear error messages for unsupported or empty files.

## Non-Functional Requirements
- Usability: simple to run with one command.
- Performance: a 5-page note is processed in under 1 minute.
- Reliability: errors are logged and the program does not crash.
- Security: the API key is stored in .env and never uploaded to GitHub.
- Maintainability: each module has one job and clear file names.
- Portability: runs on Windows with Python 3.

## User Requirements
- Students want a quick summary of long notes.
- Students want practice questions to test themselves.
- Users want results saved in an easy-to-read file.
- Users do not want to repeat the same steps for each file.

## Feature Breakdown
| Feature | Purpose | Input | Processing | Output |
|---|---|---|---|---|
| Note Reader | Load study notes | TXT/PDF file | Extract text | Plain text |
| Text Cleaner | Prepare text for AI | Raw text | Remove extra spaces, split into chunks | Clean chunks |
| Summarizer | Shorten notes | Clean chunks | Send to AI API with summary prompt | Short summary |
| Quiz Generator | Create practice questions | Clean chunks | Send to AI API with quiz prompt | 5 questions + answers |
| Output Writer | Save results | Summary, quiz | Format as Markdown | File in outputs/ |
| Auto Pipeline | Remove manual steps | New file in data/ | Run all steps in order | Results for each file |
| Config and Logging | Safe settings and errors | API key, settings | Load .env, write logs | Log file |

## Modules
| Module | Responsibility | Depends on |
|---|---|---|
| Input | Reads TXT/PDF notes | None |
| Preprocessing | Cleans and chunks text | Input |
| AI | Summary and quiz generation | Preprocessing, Config |
| Output | Saves results to Markdown | AI |
| Automation | Runs the full pipeline | All modules |
| Config/Logging | API key, settings, logs | None |

## Priorities
- **Must Have:** Note Reader (TXT), Text Cleaner, Summarizer, Output Writer, Config (.env)
- **Should Have:** Quiz Generator, PDF support, Error handling and logging
- **Could Have:** Auto Pipeline (watch folder), Difficulty levels, Simple web or GUI interface

## Development Tasks

**Input Module**
1. Create reader.py
2. Read TXT files
3. Add PDF reading
4. Handle empty or missing files
5. Test with sample_notes.txt

**Preprocessing Module**
1. Create cleaner.py
2. Remove extra spaces and symbols
3. Split long text into chunks
4. Test with long notes

**AI Module**
1. Get an AI API key and store it in .env
2. Write summary prompt in summarizer.py
3. Write quiz prompt in quiz_generator.py
4. Parse AI responses
5. Test with sample chunks

**Output Module**
1. Create writer.py
2. Format summary and quiz as Markdown
3. Save to outputs/ folder
4. Test saved file

**Automation Module**
1. Create pipeline.py
2. Connect all modules in order
3. Process every file in data/
4. Test the full flow

**Config/Logging**
1. Create config.py
2. Load .env settings
3. Add error logging
4. Add .env to .gitignore

## Development Order
Input -> Preprocessing -> AI -> Output -> Automation -> Logging/Testing
