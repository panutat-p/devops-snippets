# Taskfile

https://taskfile.dev

https://taskfile.dev/installation

https://taskfile.dev/installation/#setup-completions

Ubuntu
```sh
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d -b /usr/local/bin
echo 'eval "$(task --completion bash)"' >> ~/.bashrc
```

MacOS
```sh
brew install go-task
echo 'eval "$(task --completion zsh)"' >> ~/.zshrc
```

Go
```sh
go install github.com/go-task/task/v3/cmd/task@latest
```

Go (all users)
```sh
GOBIN=/usr/local/bin go install github.com/go-task/task/v3/cmd/task@latest
```
