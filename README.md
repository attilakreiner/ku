Usage
=====

The `ku` utility selects a kubeconfig to use from the available kubeconfig files. The kubeconfig files should be located
in the `$HOME/.kube/configs` directory. The selected file is copied to `$HOME/.kube/config` replacing the existing file there.


```
$ ku ls
available kubeconfig files:
/home/user/.kube/configs
total 32
-rw-------@ 1 attila  staff  5696 Jan 26 14:10 config-1
-rw-------@ 1 attila  staff  5696 Jan 26 14:10 config-2

current kubeconfig file:
/home/user/.kube
-rw-------@ 1 attila  staff  5696 Jan 26 14:16 config

$ ku s config-1
# kubeconfig config-1 selected

$ ku s config-2
# kubeconfig config-2 selected
```
