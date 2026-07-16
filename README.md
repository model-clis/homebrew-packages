# model-clis packages

Homebrew and Scoop metadata for CLI binaries. Manifests are generated from
upstream GitHub Releases and reconciled daily.

## Install DeepSeek CLI

Homebrew (Apple Silicon macOS):

```sh
brew tap model-clis/packages
brew install deepseek
```

Scoop (Windows x64):

```powershell
scoop bucket add model-clis https://github.com/model-clis/homebrew-packages
scoop install model-clis/deepseek
```

## Install Kimi Code CLI

Scoop (Windows x64 / arm64), tracks the native Windows builds published on
[MoonshotAI/kimi-code](https://github.com/MoonshotAI/kimi-code) releases and
shims the bundled `kimi.exe` as `kimi-code`:

```powershell
scoop bucket add model-clis https://github.com/model-clis/homebrew-packages
scoop install model-clis/kimi-code
```

macOS users should use the official Homebrew formula instead (`brew install kimi-code`).

## Maintenance

`packages.json` is the source of package configuration. Run the updater to fetch each
package's latest stable release and regenerate both package-manager formats:

```sh
python3 scripts/update.py
```

The daily workflow commits only when generated metadata changes. Add packages to
`packages.json`; do not hand-edit generated Formula or bucket files.

Package fields:

- `repository`, `description`, `homepage`, `license`: metadata copied into the manifests.
- `assets.homebrew`: arm64 macOS asset name; omit to skip Formula generation.
- `assets.scoop`: Windows asset name, or a per-architecture map
  (`{"64bit": ..., "arm64": ...}`); omit to skip the Scoop manifest.
- `tag_prefix`: set when upstream tags releases with more than a bare `v`
  (e.g. `@moonshot-ai/kimi-code@`); the updater then scans recent releases for the
  newest matching tag instead of taking the repository's latest release.
- `scoop_bin_source`: file to shim when the Scoop asset is an archive wrapping the
  binary (defaults to the x64 asset name itself).
- `checkver`: custom Scoop checkver block (defaults to `{"github": <homepage>}`).

## License

MIT
