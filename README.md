start new:
tmux

start new with session name:
tmux new -s myname

attach:
tmux a  #  (or at, or attach)

attach to named:
tmux a -t myname

list sessions:
tmux ls

kill session:
tmux kill-session -t myname

Kill all the tmux sessions:
tmux ls | grep : | cut -d. -f1 | awk '{print substr($1, 0, length($1)-1)}' | xargs kill

ctrl+b:
c  parallel tmux in current session (ctrl+b 0  and  ctrl+b 1) to switch between 
d  detach
t  big clock
?  list shortcuts
:  prompt
[  navigate using arraw keys, page up/down or mouse wheel (q to exit)

Permanent tmux scrollable fix:
```
Open or create tmux config file:
nano ~/.tmux.conf

Add this line: set -g mouse on
Save and exit: ctrl+x, y, enter

Reload configurations:
inside a tmux session, press ctrl+b, then :

and then type: source-file ~/.tmux.conf
```

To watch gpu usage continously:
watch -n 1 nvidia-smi

to count the lines in file
wc -l data/eval_outputs.jsonl

to print first few lines
head -1 data/eval_outputs.jsonl

To get disk space info:
df

If I am in my mac and want to copy file from remote machine to my mac:
scp rohan@172.27.21.156:/home/rohan/scad_project/CONSTANTS.py ~/Desktop/cad_shape_synthesis

If I am in my mac and want to copy file from my mac to remote machine:
scp ~/Desktop/VIT/main.py rohan@172.27.21.156:/home/rohan/VIT

To copy a folder use -r:
scp -r sour_addr dest_addr
scp -r /data/rohan/VIT/results/predicted_scad rovish@172.23.131.44:/Users/rovish/Desktop/VIT/dataset/results/

If I am in remote machine and want to copy a file from my mac to remote machine:
scp rovish@172.23.131.44:/Users/rovish/Downloads/train.py /home/rohan/VIT/

To copy multiple files and folders:
scp -r ~/Desktop/VIT/dataset_build/{main.py,test.py,gt_stl} rohan@172.27.21.156:/data/rohan/VIT/

ls -d ./dataset/batch_depth_maps/*/ | shuf -n 287 | xargs -I {} mv {} ./dataset/data_for_model/training_data
ls -d ./dataset/batch_depth_maps/*/ : Lists only the directories (-d) within that path.
shuf -n 287 : Shuffles the input lines randomly and picks the first 287.
xargs -I {} : Passes each folder name to the next command, using {} as a placeholder.
mv {} ./dataset/data_for_model/training_data : Moves those 287 folders into your training_data folder.

