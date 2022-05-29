# ---- [ TMUX ] ----


## 
	tmux list-commands			List All Commands 
	tmux neww -c "#{pane_current_path}	Create new Window with current path
	tmux kill-pane				Close Current Pane
	tmux last-window / previous-window	Go to Last / Previous window		
	tmux resize-pane -Z			Fullscreen Pane 

## KEYBINDING
	tmux splitw -h		Split Pane Horizontal
	tmux splitw -v		Split Pane Vertically

	tmux select-pane -LRDU	Split Pane Left/Right/D/U
	
# POPUP
* OPEN SIMPLE POPUP WITH TERM
	<prefix>:display-popup 

* OPEN POPUP WITH FILEMANAGER
	<prefix>:display-popup -E 'nnn'
