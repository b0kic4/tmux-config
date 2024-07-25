# tmux-config
Find your tmux config file. On mac `~/.tmux.conf` and paste this:

```tmux
set -g mouse on
set -sg escape-time 0 
set -g status-interval 0

# Reload configuration
unbind r
bind r source-file ~/.tmux.conf

# Act like Vim
setw -g mode-keys vi
bind-key h select-pane -L
bind-key j select-pane -D
bind-key k select-pane -U
bind-key l select-pane -R

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'dracula/tmux'

# Dracula theme settings
set -g @dracula-show-powerline true
# Uncomment for weather plugin (you need to set your location)
# set -g @dracula-plugins "weather"
set -g @dracula-show-flags true
set -g @dracula-show-left-icon session
set -g status-position bottom

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

# Custom status bar settings (optional, for further customization)
set -g status-left-length 40
set -g status-right-length 90
set -g status-interval 5

# Customize the left and right status bar
set -g status-left '#[fg=#bd93f9]#S #[fg=#ff79c6]| #[fg=#8be9fd]%Y-%m-%d #[fg=#ff79c6]| #[fg=#8be9fd]%H:%M:%S'
set -g status-right '#[fg=#8be9fd]%a #[fg=#ff79c6]| #[fg=#8be9fd]%I:%M %p #[fg=#ff79c6]| #[fg=#50fa7b]#H'

# Additional customization options (optional)
set -g status-justify centre
set -g status-bg '#282a36'
set -g status-fg '#f8f8f2'
set -g status-style bold

# Pane border and active pane styles
set -g pane-border-style 'fg=#44475a'
set -g pane-active-border-style 'fg=#bd93f9'

# Message styling
set -g message-command-style 'bg=#282a36,fg=#f8f8f2'
set -g message-style 'bg=#282a36,fg=#f8f8f2'

# Window status styling
setw -g window-status-current-format '#[fg=#50fa7b]#I #W'
setw -g window-status-format '#[fg=#f8f8f2]#I #W'
setw -g window-status-current-style 'bg=#44475a,fg=#50fa7b'
setw -g window-status-style 'bg=#282a36,fg=#f8f8f2'

# Clock mode styling
setw -g clock-mode-colour '#50fa7b'
setw -g clock-mode-style 24

# Set mouse on
set -g mouse on

# Enable activity alerts
setw -g monitor-activity on
set -g visual-activity on

# Reload tmux environment variables when reloading the config
bind r source-file ~/.tmux.conf \; display-message "Tmux config reloaded!"

# Set default terminal to 256 colors
set -g default-terminal "screen-256color"
