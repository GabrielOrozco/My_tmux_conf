# (Un)necessary intro
Okay, this is my tmux configuration file. For ussing it you can just copy `.tmux.conf` file in your user home directory. Don't get scared if you find nothing with that name, you can just create it.

# Remaping Ctr-b to Ctr-a
Normally, tmux uses ctrl+b as bind key for sending any of the orders. However, 'b' is a little bit far from Ctrl don't you think? I'll rather use 'a' instead of 'b'.
```
# Using Ctrl+a instead Ctrl+b
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
```

# Moving between splits 
Remember that for create splits you can use `bind-key + "` for horizontal split and `bind-key + %` for vertical split.

Another awful thing is to have to use `bind-key + o` for moving between panes, I'll rather prefer something more simple, like using `Alt + arrow key` being the arrow the possition of the pane to which you want to move. 
```
#swtich panes using Alt and arrow keys
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D
```
#Avoiding replacement of windows names

For creating a new windows you can use `bind-key + c`. And to put a meaningful name instead of bash+whatever to the windows, use `bind-key + ,`. However, you will realize tmux sense of humor is not respectful and it tends to rename the windows. For avoiding this use:
```
# don't rename windows automatically
set-option -g allow-rename off
```

# Set vim as default editor 

Vim rocks? vim rocks. But it rocks more when it's the default text editor in tmux:

```
# Set vi as the default editor
set -g status-keys vi
```

# Aesthetic is important

How many hours do you spend on your terminal? Make it at least look prettier. This [Reddit Post](https://www.reddit.com/r/unixporn/comments/3cn5gi/tmux_is_my_wm_on_os_x/) helps a bit.

```
######################
### DESIGN CHANGES ###
######################

# loud or quiet?
set -g visual-activity off
set -g visual-bell off
set -g visual-silence off
setw -g monitor-activity off
set -g bell-action none

#  modes
setw -g clock-mode-colour colour5

setw -g mode-style 'fg=colour1 bg=colour18 bold'

# panes
set -g pane-border-style 'fg=colour19 bg=colour0'
set -g pane-active-border-style 'bg=colour0 fg=colour9'

# statusbar
set -g status-position bottom
set -g status-justify left
set -g status-style 'bg=colour18 fg=colour137 dim'
set -g status-left ''
set -g status-right '#[fg=colour233,bg=colour19] %d/%m #[fg=colour233,bg=colour8] %H:%M:%S '
set -g status-right-length 50
set -g status-left-length 20

setw -g window-status-current-style 'fg=colour1 bg=colour19 bold'
setw -g window-status-current-format ' #I#[fg=colour249]:#[fg=colour255]#W#[fg=colour249]#F '

setw -g window-status-style 'fg=colour9 bg=colour18'
setw -g window-status-format ' #I#[fg=colour237]:#[fg=colour250]#W#[fg=colour244]#F '

setw -g window-status-bell-style 'fg=colour255 bg=colour1 bold'

# messages
set -g message-style 'fg=colour232 bg=colour16 bold'
```
# Making the terminal a little bit pretty and customizable

You can follow this tutorial:

[Tutorial for Better terminal](https://medium.com/@ivanaugustobd/your-terminal-can-be-much-much-more-productive-5256424658e8)

However, instead of the Hack Nerd Font I used the Hasklug Nerd Font that I found [here](https://github.com/ryanoasis/nerd-fonts/releases/)

The `.hyper.js` is for the configuration of hyper terminal with the appropiate font and color
The `.zshrc` is for the configuration of the zsh terminal

# Strange colors with tmux?
If you find that after starting tmux with the new theme the colors are not the same, append into the `.zshrc` file 
```
#Some issues with the theme?
export TERM=xterm-256color
```
