# zzh
##### SSH with zsh provisioning

Shell functions which SSH to a remote machine and install zsh, without needing root permissions, if not already present.
The functions can also be used to install zsh locally. 

Requirements for the machine where the functions get executed:

* gcc
* libncurses
* wget
* git
* ssh


Use this to make sure you have all of them installed:
```shell script
sudo apt update
sudo apt install build-essential libncurses5-dev wget git openssh-client
```

##### Usage
Might want to source [zzh](./zzh) in your `.zshrc`/`.bashrc` file.
```shell script
source path/to/this/repo/zzh
```

Or just copy the contents directly into them.

The command works as ssh but doesn't support executing a command.
```shell script
zzh my_user@my_remote_instance -i my_pem_file
```

##### How it works
The shell functions are sent to the remote machine and then executed.
`install_zsh` will download zsh, unpack and install it. After that it will install [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)
and download a [powerlevel10k](https://github.com/romkatv/powerlevel10k) configuration file.
Everything will be installed in `~/.zsh`. The [powerlevel10k](https://github.com/romkatv/powerlevel10k) configuration file
will be downloaded in the current user's home folder (`~/.p10k.zsh`).
If you want to remove anything installed by the functions, just delete this folder and file.
