# Kubernetes-Cheat-Sheet

### Kubectl Alias
Linux & Mac (~/.zshrc) or (~/.bashrc)

```shell
alias k=kubectl
```
Windows
```shell
Set-Alias -Name k -Value kubectl
```

## Delete All Evicted pods

```shell
k delete pods $( k get pods -A | grep "Evicted" | awk '{print $2}') -n $( k get pods -A | grep "Evicted" | awk '{print $1}')
```
