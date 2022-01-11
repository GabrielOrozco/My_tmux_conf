#(Un)necessary intro
Okay, this is my tmux configuration file. For ussing it you can just copy the contend of the tmux.conf into your .tmux.conf file in your user home directory. Don't get scared if you find nothing with that name, you can just create it.

# Remaping Ctr-b to Ctr-a
Normally, tmux uses ctrl+b as bind key for sending any of the orders. However, "b" is a little bit far from control don't you think? I'll rather use "a" instead of "b".


# switch panes using Alt-arrow without prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D
