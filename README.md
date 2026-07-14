# model-clis packages

Homebrew and Scoop metadata for binaries published by the
[`model-clis`](https://github.com/model-clis) organization. Manifests are generated from
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

## Maintenance

`packages.json` is the source of package configuration. Run the updater to fetch each
package's latest stable release and regenerate both package-manager formats:

```sh
python3 scripts/update.py
```

The daily workflow commits only when generated metadata changes. Add packages to
`packages.json`; do not hand-edit generated Formula or bucket files.

## License

MIT
