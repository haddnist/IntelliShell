# IntelliShell 🚀

**Intelligent Terminal Agent powered by Natural Language and Tool Calling**

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

IntelliShell acts as an intelligent layer over your standard terminal, allowing you to execute complex command-line operations using natural language instructions. It leverages Large Language Models (LLMs) like those from OpenAI for understanding intent and uses a robust tool-calling mechanism to interact safely and effectively with system utilities and applications.

**Think `ChatGPT` but deeply integrated with your local command-line tools.**

---

## ✨ Key Features

*   **Natural Language Interface:** Interact with your terminal using plain English (or other languages, potentially).
*   **Intelligent Tool Calling:** Automatically identifies the right command-line tool(s) for your request (e.g., `git`, `tar`, `ffmpeg`, `yt-dlp`, `docker`, system commands).
*   **Parameter Extraction:** Parses your request to identify necessary arguments and flags for the chosen tools.
*   **Multi-Step Command Execution:** Handles complex requests that require chaining multiple commands together.
*   **Context Awareness (Planned):** Remembers previous interactions within a session for more natural follow-up commands.
*   **Safety First:** Executes commands within configurable safety boundaries (e.g., sandboxing, user approval levels).
*   **Extensible Tool Library:** Easily define and add support for new command-line tools via simple configuration files.
*   **Interactive & Non-Interactive Modes:** Use it as an interactive shell replacement or for scripting/automation.
*   **Potential Codex CLI Integration:** Can delegate specific code-related tasks (generation, refactoring) to OpenAI's Codex CLI for specialized handling.

---

## 🤔 Motivation

The command line is powerful but often requires remembering arcane syntax, complex flag combinations, and specific tool names. IntelliShell aims to:

1.  **Lower the Barrier:** Make complex terminal operations accessible to users who haven't memorized command syntax.
2.  **Boost Productivity:** Speed up workflows for experienced users by allowing them to express intent directly.
3.  **Reduce Errors:** Minimize typos and incorrect flag usage by translating natural language to validated commands.
4.  **Provide a Safer Interface:** Implement safeguards before executing potentially destructive commands.

---

## 🎬 Demo (Conceptual)

```bash
# Interactive Mode
$ intellishell
> compress the 'project-docs' folder into a high-compression 7z archive named 'docs-backup.7z'

🤖 Okay, I will run the following command:
   7z a -mx=9 docs-backup.7z ./project-docs/
   [P]roceed, [E]dit, [A]bort? P
   Running: 7z a -mx=9 docs-backup.7z ./project-docs/
   ... (command output) ...
   ✅ Success!

> show me the git log for the last 3 commits with stats

🤖 Okay, I will run the following command:
   git log -n 3 --stat
   [P]roceed, [E]dit, [A]bort? P
   Running: git log -n 3 --stat
   ... (git log output) ...
   ✅ Success!

> download the audio only from this youtube video [youtube-url] as mp3

🤖 Okay, I will run the following command:
   yt-dlp -x --audio-format mp3 [youtube-url]
   [P]roceed, [E]dit, [A]bort? P
   Running: yt-dlp -x --audio-format mp3 [youtube-url]
   ... (yt-dlp output) ...
   ✅ Success!

# Direct Command Mode
$ intellishell "find all markdown files modified in the last 2 days and copy them to /tmp/recent-docs"
🤖 Okay, I will run the following command:
   find . -name "*.md" -mtime -2 -exec cp {} /tmp/recent-docs/ \;
   [P]roceed, [E]dit, [A]bort? P
   Running: find . -name "*.md" -mtime -2 -exec cp {} /tmp/recent-docs/ \;
   ✅ Success!
