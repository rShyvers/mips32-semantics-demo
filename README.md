# VibeCheck: a demo of mips32-semantics

VibeCheck runs MIPS programs on a formally verified machine. It is built on an early version of
[mips32-semantics](https://github.com/rShyvers/mips32-semantics), a small-step semantics of MIPS written and proved in
Lean 4. That version has 227 kernel-checked theorems, passes Comparator, and is validated differentially against
MARS 4.5.

The demo shows two things:

- **Bug finding:** the semantics catches two planted arithmetic bugs.
- **Tic-Tac-Toe:** every move, win and block is computed by the verified machine, not by JavaScript. A *Perfect*
  opponent runs a real alpha-beta minimax and never loses.

## Quick start

```sh
git clone --recurse-submodules https://github.com/rShyvers/mips32-semantics-demo
cd mips32-semantics-demo && make install && make run
```

You don't need Lean or Java. The repository bundles a Temurin 21 JRE and a prebuilt `MipsRun` interpreter for
linux-x64. On Windows, use `install.bat` and `run.bat`. On other platforms, `make build-semantics` builds the
interpreter from the pinned semantics (this needs `elan`).

## The semantics

The submodule `semantic-mips/` pins mips32-semantics at the version this demo was built and checked against.
That is the pre-Release 6 model, an earlier stage of what is now tagged
[`mips32r2-final`](https://github.com/rShyvers/mips32-semantics/tree/mips32r2-final). The semantics has since moved to
**MIPS32 Release 6**: all 203 base instructions, proved to refine an independent transcription of the architecture
manuals. See the [mips32-semantics README](https://github.com/rShyvers/mips32-semantics#readme).
