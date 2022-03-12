
## The best dev setup with Arch e WSL2

This readme is resume of [this vídeo](https://www.youtube.com/watch?v=sjrW74Hx5Po) of Akita On Rails

### Requeriments

* WSL 2 enabled on yout desktop;
* Docker desktop installed on your desktop (if your use docker);

## Steps and commands

### Download ans install [Arch WSL](https://github.com/yuk7/ArchWSL)

    ./Arch.exe

### Set root password

    passwd

### Create User

    echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel
    useradd -m -G wheel -s /bin/bash daniel
    passwd daniel
    exit

### Set default user

    .\Arch.exe config --default-user daniel

### Initialize keyring of pacman

    sudo pacman-key --init
    sudo pacman-key --populate
    sudo pacman -Syy archlinux-keyring

### Update Packages

    sudo pacman -Syyu

### Install general dependencies for this setup

    sudo pacman -S yarn npm
    sudo pacman -S git
    sudo pacman -S rust
    sudo pacman -S base-devel
    sudo pacman -S openssh

### Install WGET (necessary for VsCode integration)

    sudo pacman -S wget

### Install Neovim

    sudo pacman -S neovim

### Install [LunarVim](https://github.com/LunarVim/LunarVim)

    bash <(curl -s https://raw.githubusercontent.com/lunarvim/lunarvim/master/utils/installer/install.sh)
    export PATH=~/.cargo/bin:~/.local/bin:$PATH


### Instal [Yay]()

    cd /tmp
    git clone https://aur.archlinux.org/yay.git
    cd yay
    makepkg -si

### Install ZSH

    yay -S zsh

### Install [PowerLevel10k](https://github.com/romkatv/powerlevel10k#installation)

    yay -S --noconfirm zsh-theme-powerlevel10k-git
    echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
    chsh -s /usr/bin/zsh

### Confirgure newvim on zsh shell

    echo 'export PATH=$HOME/.cargo/bin:$HOME/.local/bin:$PATH' >>~/.zshrc

### Configure [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

    mkdir ~/.zsh
    cd ~/.zsh
    git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
    echo 'source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh' >>~/.zshrc

### Configure [zsh-autocomplete](https://github.com/zsh-users/zsh-autocomplete)

    git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git ~/.zsh/zsh-autocomplete
    echo 'source ~/.zsh/zsh-autocomplete/zsh-autocomplete.plugin.zsh' >>~/.zshrc

### Configure cargo rust plugins

    cargo install bat exa fd procs sd dust starship ripgrep tokei hyperfine ytop tealdeer bandwhich grex rmesg zoxide delta tp bonus

### Create alias for linux tools

    echo 'alias ls="exa --icons"' >>~/.zshrc
    echo 'alias cat="bat --style=auto"' >>~/.zshrc

### Install asdf

    yay -S asdf-vm
    asdf plugin-add java https://github.com/halcyon/asdf-java.git 
    asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
    echo 'source /opt/asdf-vm/asdf.sh' >>~/.zshrc

### Install docker 

    yay -S docker

# Links suggested by Akita

* [Windows Insider](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbWxYTlZ5OVpnS2ZJR21Rc09JOEFiUFRYcmZ3d3xBQ3Jtc0tsOV9oZ0NhMl93VHkwdjI1eDRkNngwTFdqbEJPU1NxZ1NFM2FGVnVEVlNmTHBXTGwxSjl2aEs5NWVBT3RxWHVRRUdtUmZuOEhoaW1JSnZDWUJkWkJQelAxMkxneFpJSjhIaXRRVTZqRjhRUEI4TnpFSQ&q=https%3A%2F%2Finsider.windows.com%2Fen-us%2Fabout-windows-insider-program)
* [WSL Config](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbE51S2M4NXhpNmFBSlNwM190MlNsTWJVZXdNUXxBQ3Jtc0ttWWNfOWJBTS1SUGdMVFVNX0hMY1phZTlWS0UzanJXQ1Z4TExkMEROMHMxZHdKVHo5RmNUeUxKeWNtb2NhaTZSVHNqTFpIOTZEQUIzcVNYUDFYazRON0h6U01tRkEtWm5IallSOWFJMUZWWEFvZU9hOA&q=https%3A%2F%2Fgithub.com%2FMicrosoftDocs%2FWSL%2Fblob%2Fmain%2FWSL%2Fwsl-config.md)
* [Win10 Smart Debloat](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqazJGbTRyOFBaMzVIRldoSFRvWkdVeVZfMGNkZ3xBQ3Jtc0tsVFdGZ05xcTRyaV9PMmc4WEM2LWhHajlsSUwxbmtHdWt2ZWZQV0RKY0QtenpqaTN5X3Q1RXZkVWtMUnpSSnRkazhLbjRzeVFnQVRrY0Z6S1Z6ZjRDY0hadm92WlBnTTh6cFZPeGRhMXdCdmpQTTVTdw&q=https%3A%2F%2Fgithub.com%2FLeDragoX%2FWin10SmartDebloat)
* [Get Windows Terminal](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1N6Zkx2TFItU2k2Y0hxSHVfUzAwMlhlQTg5UXxBQ3Jtc0tsVXd6MlkyNl9uNDFWTTVvNFozRVN5QXZRNkRRSmwwNGY4SVFONGV2WGpUM3ZoRjJ0YXRtdlV6Q0ZOZi14bWluRlQtUkZqRTIyTnNZblhHT21pcEp5eno2djNUbWVwWXlhVDBydGFMRzV5QlNUanlUdw&q=https%3A%2F%2Fwww.microsoft.com%2Fen-us%2Fp%2Fwindows-terminal%2F9n0dx20hk701)
* [Windows Terminal Themes](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbGNIYWxsUUlrOW80UmhkYkdRV29TQzNwQXdiZ3xBQ3Jtc0trNDJ5OUFPZU9KZTFjREtnTVNBcWhyRlpIMGlOVUsyQU51MWNSVS02ZThsUmtyZzZzVjJodV9LWkdZWUlIWlJ4MnF5R0lSY2ZwTFJIVHZscEJSOVB6djJiRkNpeGlrREgtWm95MnNKR25rTGhwMEFzNA&q=https%3A%2F%2Fwindowsterminalthemes.dev%2F)
* [Arch Wiki](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjRhOC1kZ3I0ZEJFcDVwMldtVC1zcDQyNnlkQXxBQ3Jtc0tuUEowSk9ObzlTY3lnYUVvdTNuRm9KRWQyQkZ3ZWhFc3NTcUNnSC1ZTENCeXhWRTRWbkJCbE1KdjVIVVM3X1VkUTc3YnphWVVHUEk4TmNhZ0dLTWVPQXg1dzMyeDFiWi1fUkQ1R0p4WWZUU3FPUnU2SQ&q=https%3A%2F%2Fwiki.archlinux.org%2F)
* [ArchWSL](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqblFiLUdMR2I1UUFhaFdsSWdINEx3UnBWNko3d3xBQ3Jtc0ttMERwcUdtM3ZXZm1mVkI3US1UdnQ5cWgzNndLdF9JR3dRV1JWY1BGamlTVDFONUM5SHFaSHdrbUxOVlVmczdjb3RKWHBWdEtyX0I2cURWVGNwendOVVJhX0xUalhhU0RKSlNfYlNxamRRQmllVkx6WQ&q=https%3A%2F%2Fgithub.com%2Fyuk7%2FArchWSL)
* [VSCodium](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbHV3VU5nNEZ0cUxCZ3pJZHdOczJsYzhrZE4tQXxBQ3Jtc0tsYk9OdVlIZWhjd25KbFdId2FYUU1CaXhNOEhPOUJMa2FyZGd5TjdsS3hoblRueWRYdTFlYVpSVTdlNWRZX09tTUdqdlNuWkNhcnpiZWIyd3paUEtrZEoyTnNBY05lMkJNQlk4V3VEVlVKY1R5VUowVQ&q=https%3A%2F%2Fvscodium.com%2F)
* [Chris@Machine](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbnA5Z1hBYzJIdHJRWC1jOE9hOHdLY3JqSS1wZ3xBQ3Jtc0trS3hJUE1FaUZwTk5ZS3pSaXd4TFBlcUpUTXkwOWxWTlNrS3NmcFBONTY0SU9CWjZjbWFZX3pCUDhlc1FmZk1hQ0xfaUlzSlFyQ1BVQ2pDRXpMaDRiYlc1RVVCdkg1VDFCdTBVWVR3MjBfUkJRdnVjOA&q=https%3A%2F%2Fwww.chrisatmachine.com%2F)
* [LunarVim](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXJ0S3VHa21oRTF6bzg1cjg4aU9VOHZ5TjFWZ3xBQ3Jtc0tuZjZqRElxUmhISHdBMjNQZ0lLTWJSeW5PNTlrcFZPdUtiMmFKUVNOT3RYb1dwbThNbXcyU2ZTWHRDVGVfd25IMmthQng0VWJtQy1qOGo3aXV0NG9PQlUyNXpCOEh3YktuUFNwS1B0cWJtNkYwWUdQZw&q=https%3A%2F%2Fwww.lunarvim.org%2F%23opinionated)
* [Powerlevel10k](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbVhhWXFDR2hPeDc3eEVVSldxN1dnYVp4RHRBQXxBQ3Jtc0tuUVpTMDg4cFlxOFh6aUlZaFNGVXhsY0w4OTEwYVBNSDNEcEpnWVdqT0VkN1RiX0txb29hNHFKS1B4UGs4Y1lMc09ZVjVnQTg3azg2M1VnRTZJYU5hdTlVdnE2TDNpTlo0WlNvanYtVmt3NU40cHFLMA&q=https%3A%2F%2Fgithub.com%2Fromkatv%2Fpowerlevel10k)
* [zsh-autosuggestions](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbFExRG1kaWQ5YW5ROHdUZVVyWU5MS3pSSlVzZ3xBQ3Jtc0trOVVBNEgzTkxFcXJiZEdxLTVpeTRHTzUwellsTWhGdHZEQk5uSDVKNTJsV1ludDdPOHlweVZQbnNQblhVeHBWME9YdmNUMEJ4VWU5MldFeW11UndCR2JSaGQxdGlXTFNhLWhGUFBaNl9Qbm5BdjY2Zw&q=https%3A%2F%2Fgithub.com%2Fzsh-users%2Fzsh-autosuggestions)
* [zsh-histdb](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXM4Yzhlc09IWDhsamNVd0pRUVQzMmJURm9SUXxBQ3Jtc0tueFlNZlJvSnVaWmwzNWlXTWNhdi1tSHI0T2FfeHhMWjRlN25haXhuMUxrMWFRVHMwdXlKbkFGdUJKalRac20ydDZiRC1QcTJEcU1nSEhLdUUxcnRBXzhvaW9nWDkzRkJ2bzlQbndXZkxFMkpwUVhoQQ&q=https%3A%2F%2Fgithub.com%2Flarkery%2Fzsh-histdb)
* [oh-my-zsh](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXAxTjIwa29WQXpiZXJZVW9fLWFCSlZnNDhOZ3xBQ3Jtc0tsSkFYOGhuSU52M3RaWU8yd1MyQXIxbm9QUm52YjNiZkM0dnhpd3A2RV9TR3Jmb1g1Q0Z6RVhLcVdWSlE3LUUyWnY2X1ZIa2Z1MUYya1FWcWFWOWtBeHdtZUl2SVRBMkZNeHQ4YVRSbE1qWS1kRnA3cw&q=https%3A%2F%2Fohmyz.sh%2F)
* [How to install Yay](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbi04WGRVT243NHVjZXItVUZxVDFNRUk3THJzUXxBQ3Jtc0tsV3BMY3haLThCdWt3YlF6LWN0OUt1S2dYRWpqTTl5WENPd29yQ2F6SjJKbC1fQm1HVlU5OWVRZUNQTEdRNDNfRGt0d2l6TnBfS2R5Z2FaX1h5Tm16VUtDTVV0YjNsc25CRXBxY3ptUDRaZ3I1TEUzNA&q=https%3A%2F%2Fwww.tecmint.com%2Finstall-yay-aur-helper-in-arch-linux-and-manjaro%2F)
* [ASDF](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbGFvaFNibUdobkRzb0tlX0RqZndRRWh1S0gzUXxBQ3Jtc0trN01QZFB6T2lLd0EtOVduVkwxWWhDMGk2cmEzZk0yNnlRQmJYTFZQelVSRTllbFdjUDV6Mzl3UFk3T3lVS2hGSUZVdTlPUHdGXy14ZmpsSjUxSHZheWxxci1oV3dlVkplU0Rla3VjVm1OT0I0VUJxOA&q=https%3A%2F%2Fasdf-vm.com%2Fguide%2Fgetting-started.html%23_1-install-dependencies)
* [Nerd Fonts](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa0t5S1d3YVkySVhxSlE2d3VVTzFMOFUwZ1Bwd3xBQ3Jtc0tuOHRaSEgtRHhBaHYtSU5nbnQ4UmljTXZoOUt6ZjdFQXh4OVluUlBZSEN2Q21QY3hacUdZRy1Zb3lTdkJFZXV0WDNyUG1mdmJBOWtzRmVXVzhBR1dYeXhoT1pPVEMxZ0x1Y1B1eE1SR0lFVHFrbHIwaw&q=https%3A%2F%2Fgithub.com%2Fryanoasis%2Fnerd-fonts)
* [Rewritten in Rust: Modern Alternatives of Command-Line Tools](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbndoaE1KdUxncFZ4YjZIcVl4dlJJNnByUFMyZ3xBQ3Jtc0trbmIwcGgtMDhJamJ3LXR5QTlyLW5SZ2YzNkpuZlJrT3pyYzY4Zl9VSDRtOWRIeXozczdxbk5NYnhISjcxaWFmREVweTd0RDUweXE5RURZdEs4ekpIUjQwT3hYNU5XQTBKY0l2bkpTWEp1eEpSWmYtSQ&q=https%3A%2F%2Fzaiste.net%2Fposts%2Fshell-commands-rust%2F)
* [Docker Desktop](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbGd5WkFtV1pqMVNZby12TVdFRmhGSjRRVUYzd3xBQ3Jtc0treVJKc2dackdCMkJqTF92U1ZDRWpYTzNjb21RSzNJZFNPNGhYM1JlQmZnQ3Vyc2NRS0VaamM3SHlzZ3BLeWVIa1MzVDk4VlFVRkFpaEt5TmxzWmZfTUR4akZBOS13anhZbFJ3cGVvUnM4THhvY19nQQ&q=https%3A%2F%2Fdocs.docker.com%2Fdesktop%2Fwindows%2Fwsl%2F)
* [Mount a Linux disk in WSL 2](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbWdBdk1QR05TZC14Zi1OUUh1MlNySmdKS1RmQXxBQ3Jtc0trR1VZSDdIejVhWURWa1BYa3BfWHJEb0xRcmFfYTZDX3pzeXRqZDRHOUxuVXE4MlpVRGQtbl90NkxVcmEzOVVqTHotVC16TF9kUmNuMlptOGNvalgwUnRKSWFHVm9iQU9KNVJwNm91NXJmM2FnejZQcw&q=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fwsl%2Fwsl2-mount-disk)
* [How to create advanced tasks with the Task Scheduler](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbVVJTHhkd3JGbUpiNG52aFdKSllxak5QaHZvUXxBQ3Jtc0ttMFg3Y2VpdkFoUURUYTB3c0swaUt1cEZoNUZMQnhWSVVKLURKMFp6cnRDYVgyYlp1eFdFeWIweENFeFkxanBraTJMM2FKRnFQY3I5bW91dG9FRzRjQ09qRWQ0Zzh0OHlZdEdRbnY4WjZsS1htMXp1bw&q=https%3A%2F%2Fwww.digitalcitizen.life%2Fadvanced-users-task-creation-task-scheduler%2F)
* [How to Shrink a WSL2 Virtual Disk](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1p6SmlZMk85UER3dnVCb2NqOElrbFZkOUd0d3xBQ3Jtc0trb3otUE5fZjUwdktUcGIyZnZ3WnQ3NGoyN1U0X21oZ3VxOE5KU183cEtib0pKV0VNdUllWkpndGVMR1VVaHdBTGItY1VvVVZBdXV0bEstcnk0N24wc19lV3RSa0hVdTU0NGswT2Q4eGxJUmxHX3RWYw&q=https%3A%2F%2Fstephenreescarter.net%2Fhow-to-shrink-a-wsl2-virtual-disk%2F)
