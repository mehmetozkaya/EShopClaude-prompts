# Course Prompt Library

Every prompt the instructor types on camera lives here, one file per lecture,
so a student can copy it instead of pausing the video and re-typing it.

## Layout

```
06-prompts/
  README.md                      this file
  PROMPTS.md                     the index students land on
  Part-03/S07/L25-eshop-interview.md
  Part-<NN>/S<NN>/L<NN>-<slug>.md
  generate_prompts.py            the generator
  part04spec.py ... part07to11spec.py
  verify_prompts.py              the three checks
```

One file per **lecture**. If a lecture types more than one prompt, the file
holds them all, in the order they are typed, each under its own `## Step N`
heading.

## File shape

Each file is: a short header saying which lecture it belongs to, where the
prompt is typed and what it produces, then the prompt itself in **one fenced
block**, so a student can copy it with a single click. Nothing else goes
inside the fence - no commentary, no ellipses, no placeholders the student
has to fill in unless the prompt really has them.

## How students get it

1. **Udemy lecture Resources.** The `.md` file is attached to its own lecture.
   This is the primary channel: it works offline, and it is version-matched to
   the video the student is watching.
2. **The public companion repository**, linked once on the course landing page
   and again in every lecture's resources. A prompt can be corrected there
   without re-uploading a resource, and students can watch the whole library
   grow as the course goes on.
3. **On camera**, the prompt is written in a VS Code tab with `Ctrl+G`, exactly
   as a developer would write it. The instructor says one line: "the full
   prompt is in this lecture's resources, and in the prompts folder of the
   course repository."

## What never happens

- **A full prompt is never put on a slide.** Slides carry the prompt's
  *structure* (Goal, Decided, Open, Output) and the clauses that do the work.
  A four-hundred-word prompt at the course's minimum type size is unreadable,
  and a student cannot copy text off a video anyway.
- **A prompt is never paraphrased between the file and the video.** The file is
  byte for byte what the instructor types. If the prompt is improved after
  recording, the video is re-recorded or the file carries a dated note saying
  what changed.

## Which lectures get a file

A lecture gets a file when it types a **prompt** - a natural-language
instruction to Claude. A lecture that types only **commands** (`/status`,
`/config`, `git`, `dotnet`, `aspire`, shell lines) gets no file: those live in
the lecture script's On-Screen Action blocks, where they belong.

The rules that decide the edge cases:

- A slash command that carries words you compose is a prompt, and is
  published: `/btw which port does the web frontend use?`, `/compact focus on
  the basket work`.
- **Our own skills**, invoked with arguments, are prompts: `/new-spec
  basket-api 01`, `/start-spec web 02`, `/finish-spec basket-api 05`,
  `/auto-spec web 03`. They are the course's procedures, and a student
  following along types them exactly.
- **Built-in commands with no argument** are not: `/clear`, `/skills`,
  `/hooks`, `/context`, `/permissions`, `/mcp`, `/code-review`, `/chrome`.
- When a block mixes the two - `/clear`, `/rename basket-01`, `/new-spec
  basket-api 01` sent as one piece of session setup - it is published whole,
  because that is what the student types.
- **Text typed into a file rather than sent** is published when the student
  has to reproduce it: a line added to a plan, a backlog table row, an
  `allowed-tools:` line, an `.mcp.json` or `~/.claude.json` snippet. Every one
  of these says so in its **Where** line: *this is not a prompt to send*.
- Scratch notes written outside the repository, and lectures cut from the
  curriculum, are not published.

Parts 1 and 11 have no files: the opening lectures type nothing, and the
closing section is all review.

## Keeping it byte for byte

The library is **generated** from the lecture scripts, never retyped.
`generate_prompts.py` lifts every fenced `text` block verbatim out of
`02-scripts/`, so a prompt can only change in one place - the script -
and the library follows.

`verify_prompts.py` then runs three checks, and all three must pass:

1. Every prompt in the library appears, byte for byte, in a lecture script.
2. Every prose block in a lecture script appears in the library - nothing is
   quietly left out.
3. No published prompt is made only of bare commands or shell lines.

Run `python generate_prompts.py && python verify_prompts.py` after editing any
script that types a prompt.
