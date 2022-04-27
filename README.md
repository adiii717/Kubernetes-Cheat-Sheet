# Kubernetes-Cheat-Sheet

### Kubectl Alias
Linux & Mac `(~/.zshrc)` or `(~/.bashrc)`

```shell
alias k=kubectl
```
Windows
```shell
Set-Alias -Name k -Value kubectl
```

## Delete All Evicted pods

```shell
 evicated_pods=$(k get pods -A | grep "Evicted") && 
 echo $evicated_pods && while IFS= read -r pod ; do ns=$(echo $pod | awk '{print $1}'); po=$(echo $pod | awk '{print $2}'); k delete po $po -n $ns ;done <<<  $evicated_pods```


## Get pods from multiple namespace

```shell
for ns in api auth admin webapp; do k get pods -n $ns;done
```

or

```shell
export namespaces="api auth admin webapp"
for ns in $namespaces; do k get pods -n $ns;done
```
