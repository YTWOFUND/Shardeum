# Shardeum
#### We did not see the point of publishing a complete guide on installing a Shardeum node, as the project team made the instructions very clear, and described possible problems, and their solution when installing a node.
We suggest you use the [official documentation](https://docs.shardeum.org/node/run/validator). </br>
Below are the minimum system requirements for the project.</br>
CPU: 4 Core </br>
RAM: 16Gb </br>
SSD: 250Gb </br>
OS: Ubuntu 20.04 </br>
#### Script to automatically restart the node, in case it is disabled. </br>

1. Installing tmux 
  ```
   apt-get install tmux.
  ```
2. Starting a tmux session
  ```
  tmux new -s <session name>
  ```
3. Run ./shel.sh
  ```
  cd .shardeum && ./shell.sh
  ```
4. We create a script to restart.
  ```
  sudo tee restart.sh > /dev/null <<EOF
#!/bin/sh

check_status() {
while :
do 
     if operator-cli status | grep "stopped"; then
         echo "---Trying to restart---"
         operator-cli start
     elif operator-cli status | grep "standby"; then
         echo "Waiting for active status"
     fi
sleep 30
done
}

main() {
  echo "start main"
  check_status
}
main
EOF
  ```
 5. Give permission to run
  ```
  sudo chmod +x restart.sh
  ```
6. Run script
  ```
  ./restart.sh &
  ```
7. Exit tmux.
  ```
  Ctrl+B, D
  ```
### Useful tmux commands.
```
tmux attach -Attach to last session
```
```
tmux attach -t <session name> - Attach to a specific session
```
```
tmux ls - List created sessions
```
```
tmux kill-session -t <session name> - Kill a specific session
```
```
tmux kill-server - Terminate all tmux sessions
```
