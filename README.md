# Albert Shorov

.NET backend engineer. Most of what I build sits in domains where the rules are the
hard part — Arabic phonology, sign language, Islamic jurisprudence — and the code is
what makes those rules executable.

I write down *why*, not only *what*. Every project carries its own `docs/`, and a
decision that outlives the session that made it goes into an ADR rather than a commit
message.

---

## Projects

### [Transliterator](https://github.com/shoraLBRT/Transliterator) · C#

Turns vocalised Arabic into extended Russian Cyrillic under the rules of tajweed.

Not letter-by-letter substitution: a ten-stage pipeline normalises orthography, parses
the text into a stream of phonological segments, applies the tajweed rules to those
segments, and only at the last stage maps the result to graphemes through a JSON
profile. The reverse order is impossible — by the time you are replacing letters,
sukun, shadda, the type of hamza and the word boundaries are already gone, and those
are exactly what tajweed needs. There is not a single Cyrillic grapheme in the rule
code. 250 tests, run against the real profile from resources rather than a copy.

### [ritocode](https://github.com/shoraLBRT/ritocode) · C#, React

A platform for practicing code review instead of algorithmic puzzles: you are given
real code and asked to find the smells, the performance traps and the weak tests.

Modular monolith on .NET 10 — one PostgreSQL schema per module with the boundaries
enforced by architecture tests, problem packages ingested into object storage,
submissions headed for a sandboxed runner. Built as one vertical slice first, and
largely by AI agents working from the backlog. Work in progress, and the README says
box by box what exists and what does not.

### [RISL](https://github.com/shoraLBRT/RISL) · C#, Blazor

A web dictionary of Islamic terms in Russian Sign Language, built for the «Закят»
charity fund. Every term has a definition and a video of the sign; search ranks exact
match → start of word → substring → definition.

The public side is ordinary server-rendered HTML: interactive Blazor is not wired up
and no guest request opens a WebSocket, so the site is indexable and works with
JavaScript off — you only lose search-as-you-type, favourites and the playback-speed
buttons.

### [mktba](https://github.com/shoraLBRT/mktba) · C#, TypeScript

An Islamic wiki where a paragraph can carry several opinions at once, each tagged with
the madhhab it belongs to, and the reader picks a default school that applies across
articles. ASP.NET Core + React 19 + PostgreSQL. A hard fork of my earlier
[WikiWeaver](https://github.com/shoraLBRT/WikiWeaver), with the domain model reworked.

---

## How I work

- A decision that outlives the session goes into an ADR, not a commit message.
- Tests come with the code, not after it.
- Warnings are errors, vulnerability warnings included.
- Partial work ships labelled partial, with what is missing written down — a box is
  ticked only when that piece of work is finished.
- Every repository has a document that says what exists today, so the next person
  (or the next agent) does not have to rediscover it.

---

## Stack

<p>
  <img src="https://skillicons.dev/icons?i=dotnet,cs,ts,react,postgres,docker,tailwind,git&perline=8" alt="Tech stack" />
</p>

ASP.NET Core · EF Core · Blazor · xUnit · PostgreSQL · SQLite · React · TypeScript ·
Docker · S3/MinIO

> Some project documentation is in Russian — the dictionary and wiki projects are
> written for Russian-speaking readers.
