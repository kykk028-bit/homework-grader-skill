# homework-grader-skill 🦅

An [OpenClaw](https://github.com/openclaw/openclaw) skill that automatically grades student homework from images.

## Features

- **Multiple question types**: Math, multiple choice, fill-in-blank, true/false, short answer, matching
- **Automatic scoring**: Per-question correct/incorrect marking + total score
- **Answer key support**: Provide an answer key image for reference, or let AI solve it automatically
- **Partial credit**: Awards partial credit for correct process with minor mistakes
- **Language-aware**: Responds in the same language as the user

## Installation

### Option 1: Install via .skill file

1. Copy `homework-grader.skill` to your OpenClaw skills directory
2. Add to `openclaw.json`:
```json
{
  "skills": {
    "load": {
      "extraDirs": ["path/to/skills"]
    },
    "entries": {
      "homework-grader": { "enabled": true }
    }
  }
}
```

### Option 2: Clone the repo

```bash
git clone https://github.com/kykk028-bit/homework-grader-skill.git
```

Then add the path to your `openclaw.json` skills config.

## Usage

1. Send a photo of a student's homework to your OpenClaw agent
2. Optionally include an answer key photo
3. The AI will analyze and return:
   - Per-question grading (✅ correct / ❌ incorrect / ⚠️ partial)
   - Correct answers for wrong items
   - Total score (X/Y, percentage)
   - Brief encouraging feedback

## Requirements

- OpenClaw with a vision-capable AI model (e.g., Kimi K2, GPT-4o, Claude 3.5 Sonnet)

## License

MIT
