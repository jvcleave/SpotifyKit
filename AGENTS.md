# SpotifyKit Agent Guidance

This repository owns the reusable Spotify package. The reference application is
maintained separately in `jvcleave/SpotifyHelperApp`.

- Keep authorization, PKCE, token persistence/refresh, callback listening,
  networking, decoding, pacing, and playback monitoring in this package.
- The macOS browser adapter may use AppKit; do not import SwiftUI or reference
  application types, and do not introduce a lyrics dependency.
- Keep public APIs small and use Sendable values across concurrency boundaries.
  Mutable services own isolation, cancellation, and resource cleanup.
- Preserve meaningful recoverable errors for authorization, callbacks, tokens,
  networking, and empty playback. Never silently change registered callback ports.
- Preserve the Swift 6 and macOS 15.6 baselines unless explicitly changed.
- Prefer explicit control flow, descriptive names, and direct mutations. Avoid
  one-use helpers and extensions of repository-owned types.
- Do not add behavior or compatibility shims during a source-only relocation.
- Update callers and focused tests when changing public contracts.
- Preserve unrelated work; inspect status and diff before editing and handoff.
- Run the existing relevant package tests using a stable `--scratch-path`
  outside this checkout. Use injected HTTP/token stores; tests must not contact
  Spotify, open browsers, or mutate the user's Keychain.
- Version releases deliberately; never move published tags.
