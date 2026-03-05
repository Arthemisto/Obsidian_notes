#os #unix #linux #ubuntu #freebsd #dos #android #virtualbox #filesystem #steam #proton
**Коротко:** путь от **UNIX** к **Linux** и экосистеме дистрибутивов, затем практический вход в **Ubuntu**: установка в **VirtualBox**, базовые команды CLI, файловые системы, Steam/Proton.

---
## 1) 🕰️ История и корни: UNIX → Linux
### 🧩 UNIX (1960s–1980s)
- Bell Labs: **Ken Thompson**, **Dennis Ritchie**
- Multi-user / multitasking
- Переписан на **C (1973)** → **portability (переносимость)**
- Ветка **BSD**: virtual memory, **TCP/IP**, **vi**
➡️ Подстраница: [[UNIX — History (1960s–Present)]]
### 💾 Почему DOS победил UNIX на ранних ПК (DOS vs UNIX)
- **Historical context:** UNIX проектировался под minicomputers/mainframes, а не под первые PC
- **Hardware limits:** мало RAM/CPU/storage → DOS легче
- **Market dynamics:** дешевле, доступнее, совместимость/экосистема (IBM PC)
- **Developer ecosystem:** больше софта под DOS
➡️ Подстраница: [[Why DOS over UNIX on early PCs]]
### 🐧 Linux (1991 → …)
- **Linus Torvalds**: ядро под PC, вдохновлён **UNIX/MINIX**
- 1991: старт проекта (comp.os.minix), ранние версии
- 1995: kernel 1.0
- 2000s–2020s: servers/cloud/mobile/containers
➡️ Подстраницы:
- [[Linux — History (1980s–2020s)]]
- [[Linux Distro Time Line]]
---
## 2) 🧩 Архитектура и дистрибутивы: Kernel vs Distro
### ⚙️ Kernel (ядро)
- “Двигатель” ОС: CPU scheduling, memory management, drivers/modules
- У разных distro исходник ядра **в целом один**, различаются **версии/конфиги/патчи/модули**
➡️ Подстраница: [[Linux Kernel — что общее у distro]]
### 📦 Distribution (дистрибутив)
Kernel + userland tools + package manager + configs + DE (desktop environment)
- **RHEL / Fedora**: enterprise / corporate ecosystem
- **Ubuntu (Debian-based)**: user-friendly, community idea “Ubuntu”
- **Arch / Gentoo**: высокая кастомизация (Arch — выбор kernels; Gentoo — source-based)
➡️ Подстраница: [[Kernel choices by distro — RHEL vs Ubuntu vs Arch vs Gentoo vs Fedora]]
### 🤖 Android ![[Pasted image 20260304131656.png|80]]
- Основан на **Linux kernel**, но:
  - другой UI framework
  - другой application framework (Java/Kotlin)
  - Google services, vendor customization
- “Linux-based”, но не “classic Linux distribution”
➡️ Подстраница: [[Android differences from Linux]]
---
## 3) 💽 Файловые системы и данные
### 🧾 Journaling (журналирование)
- Перед коммитом изменений пишем в **journal/log**
- После crash/power loss журнал “replay” → консистентность, меньше corruption
### 🗄️ Типы File Systems
- **Ext4**: стандарт Ubuntu
- **Ext3/Ext2**: старше; Ext2 без journaling (часто для embedded/flash)
- **Btrfs / ZFS**: advanced features (snapshots, integrity, RAID-like)
- **XFS**: high-performance, большие объёмы/файлы
- **NTFS**: Windows FS (Ubuntu read/write, иногда нужны пакеты)
- **FAT32 / exFAT**: флешки/совместимость
➡️ Подстраницы:
- [[Filesystems - ext2 ext3 ext4 btrfs xfs ntfs]]
- [[Removable FS - fat32 exfat zfs]]

---
## 4) ⌨️ Практика: CLI (командная строка) и поиск
### 🧰 Базовые команды
| Команда           | Что делает         | Пример                 |
| ----------------- | ------------------ | ---------------------- |
| `ls`, `pwd`, `cd` | навигация          | `cd /home/user`        |
| `mkdir`, `touch`  | создание           | `mkdir MyProject`      |
| `cp`, `mv`, `rm`  | операции с файлами | `cp file.txt backup/`  |
| `sudo`, `apt`     | админ/пакеты       | `sudo apt install vlc` |
| grep              | Поиск текста       | grep "error" log.txt   |

➡️ Подстраница: [[Linux CLI — базовый набор команд]]
### 🔎 grep (поиск по шаблону)
- `grep "pattern" file.txt`
- `-i` ignore case, `-n` line numbers, `*.txt`, regex, `^`, `$`
➡️ Подстраница: [[grep — pattern search]]

---
## 5) 🧪 Лабораторная среда: VirtualBox + Ubuntu
### 🧱 Зачем VM
- “Компьютер внутри компьютера” → безопасная песочница для практики
### ✅ Минимальные ресурсы (рекомендация)
- RAM: **2 GB+**
- Disk: **10 GB+**
### 🧩 Guest Additions
- драйверы/интеграция: мышь, видео, общий буфер, shared folders
### 🛠️ Troubleshooting
- `vmwgfx` / проблемы графики: проверить настройки видеоадаптера в VM
- возможный конфликт с **Hyper-V** в Windows
➡️ Подстраницы:
- [[Ubuntu - meaning, overview, and VirtualBox install]]
---
## 6) 🎮 Гейминг на Linux: Steam + Proton
**Steam + Proton:** Proton — это слой совместимости (на базе WINE), который переводит команды Windows (DirectX) на язык Linux (Vulkan). Благодаря ему игры вроде CS работают почти как нативные.
### 🧪 Proton
- compatibility layer: Windows APIs → Linux
- не “VM-эмуляция”: позволяет использовать железо напрямую
- проверка совместимости: ProtonDB
➡️ Подстраница: [[Proton]] 
---
### 🔗 Where to search fixes
- AskUbuntu (по вопросам/ошибкам)
- Tanenbaum–Torvalds debate (как мостик к темам ОС, resource management, Docker/K8S)
---
## 🧭 Summary / Сводка
- **UNIX** дал принципы и дизайн, переносимость через **C**
- **DOS** выиграл ранний PC-рынок из-за простоты/ресурсов/экосистемы
- **Linux** стал массовым UNIX-like благодаря Open Source и развитию железа
- **Distro** = kernel + окружение; **kernel** общий, различается “упаковка”
- **Ubuntu** — удобный вход: VM, CLI, FS, Steam/Proton
