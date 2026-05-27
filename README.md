# Spiders

This directory separates spider work into three layers:

```text
spiders/
  demo/        # Reverse-engineering examples and learning notes
  framework/   # Reusable spider infrastructure
  projects/    # Production or long-running spider projects
```

## Directory Roles

### demo

`demo/` stores site-specific reverse-engineering cases. These scripts are mainly for learning, reference, and one-off experiments.

Typical contents:

- JavaScript signature or cookie generation examples
- Encrypted API response decoding examples
- CAPTCHA, slider, and anti-bot research notes
- Small request scripts for individual websites

The original project README and dependencies are kept under `demo/`.

### framework

`framework/` is reserved for reusable spider building blocks.

Possible modules:

- HTTP session and browser session management
- Cookie and login-state handling
- Retry, throttling, and backoff
- Proxy integration
- URL queue and deduplication
- Logging and run metadata
- Common parsers and storage helpers

Projects may use this framework, but they are not required to.

### projects

`projects/` stores real data-collection projects. Each project should be self-contained enough to run and understand independently.

Suggested project structure:

```text
projects/
  tgb/
    README.md
    requirements.txt
    src/
    data/
    logs/
```

Projects can start as simple scripts. If several projects begin to share the same session, retry, parsing, or storage logic, move that shared logic into `framework/`.

## Working Principle

Use `demo/` as the toolbox, `framework/` as the reusable infrastructure, and `projects/` as the place where actual spider tasks live.

For a new website:

1. Explore the website and identify whether it is HTML-rendered, API-driven, or protected by anti-bot logic.
2. If special reverse engineering is needed, prototype it in `demo/` or reference an existing case there.
3. Build the actual crawler under `projects/`.
4. Extract reusable code into `framework/` only after it is useful to more than one project.

## Notes

- Keep demo scripts close to their original case context.
- Keep project outputs out of source control unless they are small sample fixtures.
- Prefer simple scripts first; add framework abstractions when repetition becomes real.
