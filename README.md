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

Importing kubeconfig files
--------------------------

`ku import <file> [name]` moves a downloaded kubeconfig file to `$HOME/.kube/configs/<name>` and makes it readable
only by you (`chmod 600`). It refuses to overwrite an existing kubeconfig unless `-f` is given. If the file is not
found as given, it is looked up in the `directory` entries of `$HOME/.kube/ku.conf`, so a bare file name is enough.

If no name is given, it is derived from the file name using the rules in `$HOME/.kube/ku.conf`. The rules are applied
in order; `prefix`/`suffix` replace a literal leading/trailing part of the name, or strip it when no replacement is given:

```
# $HOME/.kube/ku.conf
directory ~/Downloads
prefix engcsadev-66- awc-
suffix -kube-config.yaml
```

```
$ ku i ~/Downloads/ati-b75-kube-config.yaml
imported /home/user/Downloads/ati-b75-kube-config.yaml -> /home/user/.kube/configs/ati-b75

$ ku i engcsadev-66-b489mps-kube-config.yaml
imported /home/user/Downloads/engcsadev-66-b489mps-kube-config.yaml -> /home/user/.kube/configs/awc-b489mps
```
