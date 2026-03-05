#os #linux #ubuntu #permissions #chmod #chown #sudo #users #groups #links #filesystem #fhs #mount #posix #regex #system_programming #iptables  
**Коротко:** “Linux Advanced” = права доступа (**permissions**) и управление доступом (`chmod/chown`), `sudo` и пользователи/группы, ссылки (**hard/symlink**), иерархия ФС (**FHS**), “Linux registry” (конфиги/ENV/службы), **mount**, основы **POSIX** и **regex**, плюс мостик к системному программированию на C.
![[Pasted image 20260304164935.png|193]]

---
## 1) 🔐 Permissions: user / group / others
### 🧩 Три категории
- **User (owner)** — владелец файла (меняется через `chown`)
- **Group** — группа файла (меняется через `chgrp`)
- **Others** — все остальные пользователи
➡️ Подстраницы:
- [[Linux Permissions -User Group Others]]
---
## 2) 🧾 Как читать права: `ls -l`
Права показываются в `ls -l` строкой вида `rwxr-x---`:
- 3 блока по 3 символа: **owner / group / others**
- `r` read, `w` write, `x` execute, отсутствие = `-`
### ✨ Special bits
- `s` — **setuid/setgid**
- `t` — **sticky bit**
- `x` — **executable bit** (как символ в выводе)
---
## 3) 🛠️ Меняем права: `chmod` (symbolic / numeric)
- **Symbolic:** `u+r`, `g-x`, `o=...`
- **Numeric:** `755`, `750`, `600` (r=4, w=2, x=1)
Пример: `chmod 750 file.txt`
![[Pasted image 20260304165607.png|236]]

---
## 4) 🧪 Quick Exercise 
➡️ Подстраница: [[Quick Exercise chmod practice set (750 600 755)]]

---
## 5) 🧨 sudo: root-права на одну команду
- `sudo` запускает команду с правами **root** (superuser)
- правила/ограничения задаются в **`/etc/sudoers`**

### 🚫 Почему не стоит “делать всё под sudo”
- **Security risk:** лишние привилегии = больше шансов “сломать систему”
- **Ownership mess:** файлы/папки становятся `root:root`, потом обычный user не может править/удалять
- **Bad habit:** теряется грань, когда реально нужны админ-права
➡️ Подстраница: [[sudo + sudoers]]
---
## 6) 👤 Users & Groups: создать и назначить
- Создать пользователя: `sudo adduser username`
- Создать группу: `sudo addgroup groupname`
- Добавить в группу: `sudo usermod -aG groupname username`
- Проверить: `groups username`
---
## 7) 🔗 Links: hard link vs symbolic link (+ Windows)
### 🧱 Hard link
- “другое имя” того же файла/данных
- удалил оригинал → данные остаются, пока есть hard links
- нельзя для директории
- нельзя между файловыми системами/разделами
### 🪢 Symbolic link (symlink)
- отдельный файл с **path** к цели
- удалил цель → symlink становится **broken/dangling**
- можно для директорий
- можно между файловыми системами/разделами
### 🪟 Windows (кратко)
- hard link: `mklink /H`
- symlink в Windows часто требует админских прав
- **shortcut** = ярлык `.lnk` (указатель/метаданные запуска, не hard link)
➡️ Подстраницы:
- [[Hard link vs Symlink — inode vs path]]
- [[Windows Shortcut vs Symlink vs Hardlink]]
---
## 8) 🗂️ File System Hierarchy (FHS): что где лежит
![[Pasted image 20260304171351.png|511]]
Linux — дерево директорий; важно понимать назначение ключевых путей:
- `/bin` — essential binaries/команды
- `/boot` — kernel, initrd/initramfs, GRUB
- `/dev` — device files
- `/etc` — system-wide configuration
- `/home` — home directories пользователей
- `/lib`, `/lib64` — shared libraries
- `/media`, `/mnt` — mount points (auto/manual)
- `/opt` — optional/third-party software
- `/proc` — virtual FS (процессы/параметры ядра)
- `/root` — home directory root
- `/usr/bin`, `/usr/sbin`, `/usr/lib*` — user/admin binaries + libs
➡️ Подстраница: [[FHS]]
---
## 9) 🧩 “Linux Registry”: что вместо реестра Windows
- **Config files:** текстовые конфиги в `/etc` и в home (`~`)
    - примеры: `/etc/passwd`, `/etc/fstab`, `/etc/network/interfaces`
- **Environment variables:** `/etc/profile`, `/etc/environment`, `~/.bashrc`
- **Package DB:** APT/Dpkg → `/var/lib/dpkg`
- **systemd units:** `/etc/systemd/system`
- **D-Bus:** IPC/message bus между процессами
➡️ Подстраница: [[Linux Registry]]
---
## 10) 📦 Где “живут” установки 
### MySQL (пример)
- binaries: `/usr/bin` или `/usr/sbin`
- configs: `/etc/mysql/...`
- data: `/var/lib/mysql` или `/var/mysql`
- logs/temp/plugins: зависит от конфигурации
### Diablo IV (пример)
- через менеджер/Steam: часто `/opt`, `/usr/share/games`, или `~/.local/share/`
- вручную: например `/opt/diablo4`, `/usr/local/games`, или в home
➡️ Подстраница: [[Where software is installed Linux]]
---
## 11) 🪝 Mount: что это
**Mounting** = “прикрепить” файловую систему/раздел к директории (**mount point**) в дереве каталогов.
➡️ Подстраница: [[Mount]]

---
## 13) 🧩 POSIX: зачем это важно
**POSIX** задаёт стандарты API/интерфейсов для Unix-like систем, чтобы софт было проще переносить.
Ключевые области:
- system calls, commands/utilities, shell scripting
- env vars, regex
- file ops, process mgmt, IPC
- threads, signals
➡️ Подстраница: [[POSIX]]
---
## 15) 🧰 Set up environment C (Ubuntu)

### POSIX заголовки/темы
- terminal I/O: `<termios.h>` (non-canonical/raw mode, echo off)
- threads: `<pthread.h>` (`pthread_create`, `pthread_join`)
- важно: **в конце вернуть исходные terminal attributes**
➡️ Подстраницы:
- [[Setup environment C]]
- [[termios — raw mode + restore]]
- [[pthread — basics]]
---
## 16) 🧾 Cheat Sheet (essentials)
- Process: `ps`, `kill`, `top`
- apt: `apt install/update/upgrade/remove`
- files: `ls`, `cd`, `pwd`, `mkdir`, `cp`, `mv`, `rm`
- editors: `vim`, `nano`
- users/perms: `adduser`, `usermod`, `groupadd`, `chown`, `chmod`
- network: `ping`, `ifconfig`, `ip`, `netstat`, `traceroute`
- logs/monitoring: `htop`, `sar`, `vmstat`, `/var/log`, `tail`, `grep`, `less`
- security: `ufw`
➡️ Подстраница: [[Linux Cheat Sheet]]
---
## 17) 🧱 Firewall: Netfilter + iptables (база)
**Netfilter** — firewall framework в ядре Linux.  
**iptables** — user-space утилита для управления правилами.
##### Показать правила
sudo iptables -L
##### Показать конкретную цепочку (например INPUT)
sudo iptables -L INPUT
##### Найти правила по IP (пример 192.168.1.100)
sudo iptables -L -v -n | grep 192.168.1.100

---
## 🧭 Summary / Сводка
- Permissions: **owner/group/others**, читаем через `ls -l`, меняем `chmod`, ownership через `chown/chgrp`.
- `sudo` = временные root-права, правила в `/etc/sudoers`; не стоит делать всё “под sudo”.
- Links: **hard link** (те же данные) vs **symlink** (путь, может “сломаться”).
- FHS объясняет назначение `/bin /etc /home /usr /proc /opt …`
- “Linux registry” = конфиги + env vars + package DB + systemd + D-Bus.
- `mount` встраивает файловую систему в дерево каталогов; закрепление — через `/etc/fstab`.
- POSIX + regex + C toolchain = база для системного программирования; дальше — **kernel**.