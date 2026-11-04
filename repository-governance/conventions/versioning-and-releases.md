# Versioning and Releases

## Purpose and Scope

Allow plugins to evolve and release independently. Read this convention when changing versions or preparing releases. No plugin release is part of initialization.

## Rules

- Each plugin must have an independent SemVer version, starting at `0.1.0`.
- The plugin's root `plugin.json` must own its canonical version. Do not add a shared monorepo release version.
- Skills ship with their containing plugin; do not assign separate skill versions initially.
- Maintain a plugin-level `CHANGELOG.md` describing meaningful changes and compatibility implications. Unreleased work may be recorded before a release is prepared.
- Use plugin-specific tags in the form `<plugin-name>/v<version>`, such as `fm-research-and-analysis/v0.1.0`. This is illustrative, not an existing release.
- Follow SemVer: patch for compatible fixes, minor for compatible capabilities, and major for incompatible changes to a stable public contract. During `0.x` development, explicitly document compatibility changes rather than implying stability from the version number alone.
- Document skill renames, removals, and incompatible input or output changes as breaking changes, including migration guidance. Explain any deprecation and its replacement before removal where practical.
- A change to one plugin must not require releasing unrelated plugins. Review shared policy changes for their effects on each affected package.

## Future Release Verification

Check the canonical version, changelog, intended tag, package contents, and documented migration steps. Verify installation and representative workflows in the supported target before claiming the package works there. Check [Agent compatibility](agent-compatibility.md) before introducing a marketplace or additional target.

License selection, publishing, and release automation remain outside initialization. Introducing distribution requires a separate concrete change and review under [Change management](change-management.md).
