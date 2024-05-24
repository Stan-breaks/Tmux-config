# Tmux Configuration

This repository contains my personal tmux configuration. It's designed to be flexible, easy to maintain, and compatible across different versions of tmux and platforms.

## Installation

1. Clone the [Tmux Plugin Manager (TPM)](https://github.com/tmux-plugins/tpm) repository to your local machine:

   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
   ```

2. Set the default terminal to "screen-256color" in your `~/.tmux.conf`:

   ```tmux
   set -g default-terminal "screen-256color"
   ```

3. Customize your key bindings, mouse settings, and other options as needed. Here are some examples:

   - Map default prefix to `C-a`:

     ```tmux
     set -g prefix C-a
     unbind C-b
     bind-key C-a send-prefix
     ```

   - Split windows horizontally and vertically:

     ```tmux
     unbind %
     bind \ split-window -h
     unbind '"'
     bind = split-window -v
     ```

   - Reload config:

     ```tmux
     unbind r
     bind r source-file ~/.tmux.conf
     ```

   - Resize panes:

     ```tmux
     bind -r j resize-pane -D 5
     bind -r k resize-pane -U 5
     bind -r l resize-pane -R 5
     bind -r h resize-pane -L 5
     bind -r m resize-pane -Z
     ```

   - Enable mouse support:

     ```tmux
     set -g mouse on
     ```

   - Set terminal scrollback limit:

     ```tmux
     set -g history-limit 50000
     ```

   - Enable VIM motions:

     ```tmux
     set-window-option -g mode-keys vi
     bind-key -T copy-mode-vi 'v' send -X begin-selection
     bind-key -T copy-mode-vi 'y' send -X copy-selection
     ```

   - Enable mouse dragging in copy mode:

     ```tmux
     unbind -T copy-mode-vi MouseDragEnd1Pane
     ```

   - Install plugins using TPM:

     ```tmux
     set -g @plugin 'tmux-plugins/tpm'
     set -g @plugin 'christoomey/vim-tmux-navigator'
     set -g @plugin 'jimeh/tmux-themepack'
     set -g @plugin 'tmux-plugins/tmux-resurrect' # Sessions persist after restart
     set -g @plugin 'tmux-plugins/tmux-continuum' # Autosaves sessions every 15 minutes
     ```

   - Set your preferred theme (e.g., powerline gray):
     ```tmux
     set -g @themepack 'powerline/default/gray'
     ```

4. Run TPM to install the plugins:

   ```bash
   run '~/.tmux/plugins/tpm/tpm'
   ```

## Closing

Feel free to customize this README and your `.tmux.conf` to suit your needs!
