# Taskfile

https://taskfile.dev

https://taskfile.dev/installation

https://taskfile.dev/installation/#setup-completions

Ubuntu
```sh
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
wget -O /etc/task_completion.bash https://raw.githubusercontent.com/go-task/task/main/completion/bash/task.bash
echo 'source /etc/task_completion.bash' >> ~/.bashrc
```

MacOS
```sh
brew install go-task
wget -O /usr/local/share/zsh/site-functions/_task https://raw.githubusercontent.com/go-task/task/main/completion/zsh/_task
```

Go
```sh
go install github.com/go-task/task/v3/cmd/task@latest
```

Go (all users)
```sh
GOBIN=/usr/local/bin go install github.com/go-task/task/v3/cmd/task@latest
```
