## sync user home
```shell
rm -r /root
git clone https://gitee.com/k88936/dev_env.git /root
cd /root
chmod 600 /root/.ssh -R
git remote set-url origin git@gitee.com:k88936/dev_env.git
sh /root/.configure/etc/copy.sh
```

## clasheed
```shell
git clone git@gitee.com:k88936/clasheed /clasheed
cd clasheed
cat README.md
```

## software repo
```shell
sed -i '1i Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch' /etc/pacman.d/mirrorlist
useradd -m -G wheel -s /bin/bash yay \
    && echo '%wheel ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/99-wheel \
    && chmod 0440 /etc/sudoers.d/99-wheel
sudo -u yay  git clone https://aur.archlinux.org/yay-bin.git /home/yay/yay-bin \
    && cd /home/yay/yay-bin \
    && makepkg -si --noconfirm --needed \
    && cd /home/yay \
    && rm -rf /home/yay/yay-bin
```
## keyd
```shell
pacman -S keyd
systemctl enable --now keyd
```

## network
```shell
systemctl enable --now NetworkManager
```

## Desktop
```shell
pacman -S xorg xorg-xinit i3 dmenu  brightnessctl picom
pacman -S alsa-utils alsa-firmware  pulseaudio pulseaudio-alsa

pacman -S xdg-user-dirs
xdg-user-dirs-update
yay -S microsoft-edge-stable-bin firefox
systemctl --user enable --now pulseaudio
```

## 原神
```shell
yay -S mihomo-bin mihomosh-bin
mihomosh profile update
systemctl enable --now mihomo
```
