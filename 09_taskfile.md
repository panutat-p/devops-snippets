# Taskfile

https://taskfile.dev

https://taskfile.dev/installation

https://taskfile.dev/installation/#setup-completions

Linux
```sh
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b ~/.local/bin
wget -O /etc/task_completion.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
echo 'source /etc/task_completion.bash' >> ~/.bashrc
```

MacOS
```sh
brew install go-task
wget -O /usr/local/share/zsh/site-functions/_task https://raw.githubusercontent.com/go-task/task/main/completion/zsh/_task
```
