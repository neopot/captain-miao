<p align="center">
  <img src="assets/logo.jpg" alt="captain-miao logo" width="220">
</p>

<h1 align="center">captain-miao</h1>

<p align="center"><b>Mission control for AI coding sessions in the terminal.</b></p>

<p align="center">
  <a href="https://www.npmjs.com/package/@hyperlogue/captain-miao"><img src="https://img.shields.io/npm/v/@hyperlogue/captain-miao?color=cb3837&amp;logo=npm&amp;label=%40hyperlogue%2Fcaptain-miao" alt="npm version"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="license: MIT"></a>
  <img src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux-lightgrey" alt="platforms: macOS, Linux">
</p>

- **One dashboard for every session.** Claude Code, Codex, Reasonix, Kimi Code, Grok Build, opencode, Pi, Antigravity, and omp share one status table. `s` selects the next session that needs attention; `Enter` focuses its window.
- **Sessions run in your terminal.** Native windows, tabs, or panes in Kitty, zellij, tmux, Ghostty, or iTerm2, with your fonts, settings, and key bindings.
- **Claude and Codex settings stay yours.** Claude hooks travel in a per-session `--settings` file, leaving `~/.claude/settings.json` unchanged. Codex launches use a captain-miao profile, leaving `~/.codex/config.toml` and `~/.codex/hooks.json` unchanged.
- **Remote sessions keep working with the lid closed.** `miao-server` runs the agent in a [shpool](https://github.com/shell-pool/shpool) pty pool on the SSH host, so a sleep or a dropped link leaves the session running.

<a href="assets/captain-miao.mp4"><img src="assets/dashboard.png" alt="captain-miao dashboard in Kitty with 15 active and waiting agent sessions"></a>

[Watch the 60-second demo](assets/captain-miao.mp4)

## Quick start

```sh
npm install -g @hyperlogue/captain-miao
```

[Prebuilt binaries](https://github.com/hyperlogue/captain-miao/releases) are published for macOS and Linux. `npx @hyperlogue/captain-miao` runs the same binary after the terminal setup below.

Start `miao` inside [Kitty](https://sw.kovidgoyal.net/kitty/), [zellij](https://zellij.dev/) 0.44 or newer, [tmux](https://github.com/tmux/tmux) 3.2 or newer, [Ghostty](https://ghostty.org/) 1.3 or newer, or [iTerm2](https://iterm2.com/) 3.0 or newer. Ghostty and iTerm2 are macOS only and request AppleScript Automation. zellij and tmux are ready once you are inside a session.

Kitty needs a remote-control socket. Add this to `~/.config/kitty/kitty.conf` and restart Kitty:

```conf
allow_remote_control socket-only
listen_on unix:/tmp/captain-miao-kitty
```

Any program that can reach the socket can control Kitty windows. Kitty also supports [password authorization](https://sw.kovidgoyal.net/kitty/remote-control/).

```sh
cd /path/to/your/project
miao
```

`o` starts an agent in the selected session's directory, or opens the directory picker when nothing is selected. `O` always opens that picker. `Enter` focuses the window. `?` lists every key.

## More

- **Remote hosts.** `Space h` adds an SSH host and sets up `miao-server`. `Enter` reconnects a detached session. Closing a window ends the session unless `[remote] on_window_close = "detach"` in `~/.config/captain-miao/config.toml`. Design notes: [remote sessions](docs/remote-sessions.md).
- **A few limits.** Ghostty has no transcript preview; start its agents from the dashboard. iTerm2 previews are plain text. Press `,` for preferences.

## License

MIT. See [LICENSE](LICENSE).
