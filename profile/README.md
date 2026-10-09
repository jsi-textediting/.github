# JSi Text Editing

Lightweight, hackable, and high-performance text editing tools, runtimes, and extensions.

## Projects

* **[lite-xl](https://github.com/jsi-textediting/lite-xl)** — A lightweight, fast text editor written in Lua with a native C backend, featuring native performance optimizations, SDL GPU rendering, and remote editing integration.
* **[lite-xl-plugins](https://github.com/jsi-textediting/lite-xl-plugins)** — A curated collection of plugins for Lite XL, featuring declarative package management via [`use_package`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/use_package), remote editing integration ([`plugins/thither`](https://github.com/jsi-textediting/lite-xl-plugins/tree/main/plugins/thither)), and ergonomic navigation and search tools (Avy, Which-Key, Isearch, Ripgrep, and more).
* **[libeditingcore](https://github.com/jsi-textediting/libeditingcore)** — A lightweight, SDL-free static C library providing native Lua bindings for process execution, PCRE2 regex, directory monitoring (inotify, kqueue, fsevents, win32), and system core operations, shared between Lite XL and Thither.
* **[thither](https://github.com/jsi-textediting/thither)** — A small, standalone remote-editing server spoken to over plain SSH stdio via framed msgpack, featuring conflict-checked atomic saves, directory watching, server-side search, process execution, and lazy large-file editing without background daemons.
* **[thither.el](https://github.com/jsi-textediting/thither.el)** — An Emacs package for the Thither remote editing protocol (`/thither:host:/path`), enabling transparent remote file access and remote process management.

## License

Projects in this organization are open-source and released under the [MIT License](https://opensource.org/licenses/MIT).
