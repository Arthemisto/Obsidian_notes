#os #linux #ubuntu #fhs #filesystem #install_paths #mysql #apache #openssh #steam
## 📦 Где устанавливаются программы в Linux (по FHS)
**Коротко:** пути зависят от distro/пакетного менеджера/метода установки, но логика обычно одна:  
**bin** → `/usr/bin` или `/usr/sbin`, **configs** → `/etc`, **data** → `/var/lib`, **content** → `/var/www`, сторонний софт → `/opt`, user-данные → `~`.

---
## 1) 🗄️ Пример: MySQL (DBMS)
Типичное размещение по FHS:
### ⚙️ Executables (server/client)
- `/usr/bin` или `/usr/sbin`
### 🧩 Configuration
- `/etc/mysql`
- `/etc/mysql/mysql.conf.d`
### 💾 Data (databases, tables)
- `/var/lib/mysql` (часто)
- или `/var/mysql`
### 🧾 Остальное (varies)
- логи, временные файлы, плагины — в зависимости от конфигурации и пакета
---
## 2) 🎮 Пример: Diablo IV (Game)
Путь зависит от способа установки:
### 📦 Через менеджер / Steam
Возможные места:
- `/opt`
- `/usr/share/games`
- `/home/<username>/.local/share/` (user-local data)
### 🛠️ Вручную (manual install)
Частые варианты:
- `/opt/diablo4`
- `/usr/local/games`
- или внутри `~` (home directory)
---
## 3) ⚠️ Важно про “пути установки”
- Реальные пути могут отличаться из-за:
    - конкретного дистрибутива
    - пакетного менеджера
    - способа установки
    - кастомной конфигурации (install options / config files)
✅ Пользователь может менять пути при установке или через конфиги.
---
## 4) 🧪 Exercise: Where will be installed?
### A) Apache HTTP Server
- **configs:** `/etc/apache2/`
- **web content:** `/var/www/html/`
- **executables:** `/usr/sbin/`
### B) OpenSSH Server
- **configs:** `/etc/ssh/`
- **executables:** `/usr/sbin/`
