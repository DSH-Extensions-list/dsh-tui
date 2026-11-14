# Harness RC3 compatibility

Upstream: https://github.com/ccch1mneyyy/dsh-TUI

Base: @deepseek-harness-tui/dsh-tui 0.20.0, npm gitHead 8958f08e3ba09a3db37d35c490d9589c114e7136. The compatibility edition retains the upstream package name and uses version 0.20.0-rc3.20261114.1.

## Changes

- Declare exact Harness 0.2.2-rc.3 compatibility in engines.dsh.
- Add exact 0.2.2-rc.3 to the CLI adapter's validated-host set.
- Update the keyless real-runtime regression to expect RC3 headless credential-service omission while retaining the explicit credential-service override check.
- Point repository and issue metadata to this maintained fork; keep upstream author and license attribution.

## Verification

The focused CLI suite and real keyless RC3 runtime regression cover run, resume, continue, session list/show/export, models, skills, MCP and credential capability handling. The runtime test isolates its home and uses a fixture provider, with no network inference or production-data changes.

```sh
node --test cli/test/cli.test.mjs cli/test/edges.test.mjs cli/test/package.test.mjs cli/test/boundary.test.mjs
DST_TEST_DSH_BIN=/absolute/path/to/deepseek-harness/apps/cli/lib/bin.js node cli/test/runtime.mjs
```

The full interactive TTY experience and the complete upstream build-gate matrix were not independently rerun for this CLI compatibility patch. See upstream docs/contributing.md for build requirements. Generated lib files are built from upstream source and are not hand-edited or tracked.

This push does not publish to npm or replace the already verified desktop installation.
