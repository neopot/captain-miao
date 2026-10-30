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

- **One dashboard for every session, solely keyboard-driven.** A few keystrokes jump you to the session that needs you. Claude Code, Codex, Reasonix, Kimi Code, Grok Build, opencode, Pi, Antigravity, and omp share the table.
- **It fits your existing workflow, totally isolated.** Your tools, config, and frameworks stay as they are, with no required configuration method and no required terminal. Kitty, zellij, tmux, Ghostty, and iTerm2 all work, and Claude and Codex global config stays untouched.
- **Persistent sessions over SSH.** The agent keeps running on the host, so closing the lid or losing the network leaves the session running.

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

`o` starts an agent in the selected session's directory, or opens the directory picker when nothing is selected. `O` always opens that picker. `s` selects the next session that needs attention, and `Enter` focuses its window. `?` lists every key.

## More

- **Remote hosts.** `Space h` adds an SSH host and sets up `miao-server`. `Enter` reconnects a detached session. Window close is set in preferences: the default ends the session, and detach keeps it running (`[remote] on_window_close` in `~/.config/captain-miao/config.toml`). Design notes: [remote sessions](docs/remote-sessions.md).
- **A few limits.** Ghostty has no transcript preview; start its agents from the dashboard. iTerm2 previews are plain text. Press `,` for preferences.

## License

MIT. See [LICENSE](LICENSE).
