# release-info

Version manifests for WWFO tools. Each tool has its own JSON file. Tools fetch
their file at startup and compare against the locally installed version to surface
update notifications in the UI.

## Structure

Each file is named after the tool it describes:

```
beacon.json          # Infoblox Beacon (customer + SE upload tool)
```

New tools add their own file; there is no shared schema enforced across files, but
the convention is a flat object whose keys are the named components of the tool.

## Updating

When you ship a new release, update the relevant file and commit directly to `main`.
The raw GitHub URL is what tools poll, so `main` is the live channel.

Raw URL pattern:
```
https://raw.githubusercontent.com/Infoblox-WWFO/release-info/main/<tool>.json
```

## Planned migration

This repo may move to `infoblox-open` in the future. When that happens, update the
`version_check_url` field in each tool's `versions.toml` (or equivalent config) and
the old URLs will redirect automatically via GitHub's repo-transfer mechanism.
