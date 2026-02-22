# Tmux Developer Setup (macOS)

This is a **developer-friendly tmux configuration** for macOS Terminal.app:

- **Ctrl + a** prefix (instead of default Ctrl + b)  
- **Vim-style navigation** and resizing  
- **Minimal / clean UI** (status bar hidden)  
- **Copy/paste-friendly**  
- **Automatic session save & restore**  
- Easy splits and window management  

---

## 📂 `.tmux.conf` Highlights

### Prefix
```bash
unbind C-b
set-option -g prefix C-a
bind C-a send-prefix
````

* Use **Ctrl + a** as the tmux prefix.

### Basics

```bash
set -g mouse off
set -s set-clipboard on
set -g mode-keys vi
set -g history-limit 10000
```

* Vim-style keybindings in copy/scroll mode
* Large scrollback buffer
* Clipboard integration for macOS
* Mouse scrolling **off** for easier Cmd+C / Cmd+V

### Status Bar

```bash
set -g status off
```

* Hides the status bar for a clean terminal look

### Splits & Navigation

```bash
bind | split-window -h
bind _ split-window -v

# Navigate panes with h/j/k/l
bind -r h select-pane -L
bind -r j select-pane -D
bind -r k select-pane -U
bind -r l select-pane -R

# Resize panes with H/J/K/L
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# Open new window in current directory
bind c new-window -c "#{pane_current_path}"

# Automatic pane balancing
bind b select-layout tiled
```

### Session Auto-Restore

```bash
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'

set -g @resurrect-dir '~/.tmux/resurrect'
set -g @continuum-restore 'on'
set -g @continuum-save-interval '15'

# Initialize TPM
run '~/.tmux/plugins/tpm/tpm'
```

* `tmux-resurrect`: save/restore tmux sessions manually

  * Save: `Ctrl + a` → `Ctrl + s`
  * Restore: `Ctrl + a` → `Ctrl + r`
* `tmux-continuum`: auto-save and auto-restore on tmux server start

---

##  Quick Reference (Keyboard Shortcuts)

| Action                    | Shortcut                                      |   |
| ------------------------- | --------------------------------------------- | - |
| Prefix                    | `Ctrl + a`                                    |   |
| Split horizontal          | `Ctrl + a` → `\|`                             |   |
| Split vertical            | `Ctrl + a` → `_`                              |   |
| Navigate panes            | `Ctrl + a` → h/j/k/l                          |   |
| Resize panes              | `Ctrl + a` → H/J/K/L                          |   |
| New window in current dir | `Ctrl + a` → c                                |   |
| Auto-balance panes        | `Ctrl + a` → b                                |   |
| Save session              | `Ctrl + a` → Ctrl + s                         |   |
| Restore session           | `Ctrl + a` → Ctrl + r                         |   |
| Enter scroll/copy mode    | `Ctrl + a` → `[`                              |   |
| Scroll                    | `k/j` or arrow keys, `Ctrl+u/d` for half-page |   |
| Exit scroll mode          | `q` or `Esc`                                  |   |
| Reload config             | `Ctrl + a` → r                                |   |

---

## 🔗 Useful GitHub Links

* [tmux Plugin Manager (TPM)](https://github.com/tmux-plugins/tpm)
* [tmux Resurrect](https://github.com/tmux-plugins/tmux-resurrect)
* [tmux Continuum](https://github.com/tmux-plugins/tmux-continuum)

> TPM must be initialized in `.tmux.conf` (`run '~/.tmux/plugins/tpm/tpm'`) for plugin shortcuts to work.

---

##  Installation Quick Steps

```bash
# 1. Install TPM if not already
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# 2. Create resurrect folder
mkdir -p ~/.tmux/resurrect

# 3. Start tmux fresh
tmux kill-server
tmux

# 4. Install plugins inside tmux
# Press Ctrl + a then I (capital I)
```

Now your tmux session is fully set up with auto-restore, vim navigation, tiling, and a clean terminal look.

---

## 💡 Tips

* Auto-restore works only when starting a **new tmux server**, not when reloading config.
* Keep `mouse off` for easy macOS copy/paste.
* Manual save/restore works anytime with `Ctrl + a` → `Ctrl + s/r`.


