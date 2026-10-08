# JSi Text Editing

Welcome to the **JSi Text Editing** (`jsi-textediting`) organization!

We focus on building and curating lightweight, hackable, and high-performance text editing tools, core runtimes, and developer-centric extensions. Our goal is to combine the speed and simplicity of minimalist editors with modern capabilities like native remote editing over SSH, declarative package management, and ergonomic navigation.

---

## 📂 Core Repositories

This organization maintains two tightly integrated repositories:

```
jsi-textediting/
├── lite-xl/          # High-performance, lightweight text editor core with thither remote editing
└── lite-xl-plugins/  # Curated plugin suite powered by declarative use-package management
```

---

### 1. [lite-xl](https://github.com/jsi-textediting/lite-xl)

> **A lightweight, fast, and hackable text editor written in Lua with a native C backend.**

[Lite XL](https://github.com/jsi-textediting/lite-xl) is a lightweight editor that provides a clean user interface, minimal resource consumption, and instant startup times while retaining deep customizability through Lua.

#### ✨ Key Features & Enhancements

* **`thither` Remote Editing Support:**
  * Embedded and standalone `thither-server` communicating over standard SSH via a framed msgpack protocol.
  * No background daemon or open listening ports required—authentication and encryption are handled natively by SSH.
  * Conflict-checked atomic file saves, remote directory watching (`inotify` / `kqueue` / `fsevents`), server-side searching, and streamed process execution.
  * Efficiently edit multi-GB remote files without requiring full downloads.
* **Rendering & Performance Optimizations:**
  * Linewrapping-aware drawing for overlays and guides.
  * Optimized line-cache hooks and memory management.
* **Modern Lua Integration:**
  * Powered by Lua 5.4/5.5 with modular architecture and clean C/SDL backend.
  * Bundled integration with declarative package configuration.

---

### 2. [lite-xl-plugins](https://github.com/jsi-textediting/lite-xl-plugins)

> **A curated collection of modular plugins and enhancements for Lite XL, featuring declarative management via `use-package`.**

[Lite-XL Plugins](https://github.com/jsi-textediting/lite-xl-plugins) provides developer ergonomics and functionality inspired by modern editor workflows and Emacs-style power tools.

#### 🧩 Included Plugins Overview

| Plugin | Version | Category | Description | Dependencies |
|---|---|---|---|---|
| [`use_package`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/use_package) | `0.2.0` | Package Manager | Declarative package and plugin manager for Lite XL with repo overrides and state toggling. | — |
| [`thither`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/thither) | `0.1.0` | Remote Editing | Client plugin for remote editing over SSH via `thither-server`. | — |
| [`avy`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/avy) | `0.1.0` | Navigation | Avy-style jump-to-character/word/line navigation using visual label overlays. | — |
| [`isearch`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/isearch) | `0.1.0` | Search | Incremental search with live multi-match highlighting and wrap-around support. | — |
| [`fd-files`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/fd-files) | `0.1.0` | File Finding | High-speed fuzzy file finder overlay powered by `fd`. | `shared` |
| [`rgsearch`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/rgsearch) | `0.1.0` | Code Search | Fast project-wide search overlay with live streaming results powered by `ripgrep`. | `shared` |
| [`bufferex`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/bufferex) | `0.1.0` | Buffers | Helm-mini style buffer and recent-file switcher with fuzzy search. | `shared` |
| [`killring`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/killring) | `0.1.0` | Clipboard | Emacs-style kill ring clipboard history with searchable listview overlay. | `shared` |
| [`whichkey`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/whichkey) | `0.1.0` | UI / Keymaps | Popup panel displaying available key continuation bindings after prefix keys. | — |
| [`indentguideex`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/indentguideex) | `0.1.0` | UI / Editor | Enhanced indentation guides with active scope highlighting and style options. | — |
| [`emacs`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/emacs) | `0.1.0` | Utilities | Emacs navigation utilities including `push_mark` and `universal_argument`. | — |
| [`shared`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/shared) | `0.1.0` | Core / Library | Reusable `listview` overlay base class and shared search runners. | — |

---

## 🚀 Quick Start & Integration

The repositories are designed to work together out of the box:

### 1. Build & Run Lite XL

```bash
git clone https://github.com/jsi-textediting/lite-xl.git
cd lite-xl
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

*(To build the standalone `thither-server` for remote hosts, see [`thither/README.md`](https://github.com/jsi-textediting/lite-xl/tree/main/thither).)*

### 2. Configure Plugins Declaratively

In your Lite XL configuration (`~/.config/lite-xl/init.lua`):

```lua
local up = require 'plugins.use_package'

-- Register plugin repositories
up.repos {
  'https://github.com/jsi-textediting/lite-xl-plugins.git:main',
}

-- Declare desired plugins
up.use 'avy'
up.use 'bufferex'
up.use 'fd-files'
up.use 'indentguideex'
up.use 'isearch'
up.use 'killring'
up.use 'rgsearch'
up.use 'thither'
up.use 'whichkey'
```

### 3. Install & Manage

* Open Lite XL's command palette (`Ctrl+Shift+P` / `Cmd+Shift+P`).
* Execute `use-package:install` to download and link declared plugins.
* Use commands like `use-package:toggle-plugin` or `use-package:disable-plugin` to adjust active plugins on the fly.

---

## 🎯 Design Philosophy

* **Speed & Responsiveness:** Keep the editor startup instant and UI frame rates smooth without background bloat.
* **Daemonless Remote Workflows:** First-class remote editing over SSH (`thither`) without heavy daemon processes or server-side IDE footprints.
* **Declarative Configuration:** Easy-to-reproduce editor environments via `use_package`.
* **Ergonomic Keyboard Navigation:** Modern navigation mechanisms (Avy, Which-Key, Isearch, Helm-style switchers) designed for rapid code manipulation.

---

## 📄 License

Both projects in this organization are open-source and released under the [MIT License](https://opensource.org/licenses/MIT).
