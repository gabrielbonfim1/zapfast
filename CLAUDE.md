# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

`AGENTS.md` is the canonical guide (product boundaries, privacy, architecture,
branches, releasing, definition of done). It is imported here so Claude Code
loads it at session start; put durable project rules there, not in this file.

@AGENTS.md

## Quick reference

Builds go through mise and mbx (`mise trust` once per checkout or worktree);
plain `cargo` works too.

```sh
cargo run                                       # the app, against real accounts
cargo run --features demo -- --demo             # synthetic sample data only
cargo run --features demo -- --demo-shot out.png --demo-size 1180x780
cargo test --locked --lib <name_substring>      # one unit test (or a module path)
cargo test --locked --all-features --lib <name> # tests behind the `demo` feature
cargo test --locked --test update_flags         # one integration test file
cargo run --example aec_replay -- <dump>        # replay a call-audio dump; flags in its doc comment
.github/scripts/update-translations.sh --check  # when translatable strings change
```

The full set of checks to run before finishing is in `AGENTS.md` under
"Definition of done". Translatable literals each stay in their own `gettext`
call so extraction finds them (see `CONTRIBUTING.md`).
