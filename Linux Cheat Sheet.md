os #linux #ubuntu #cheatsheet #cli #process #apt #files #vim #nano #users #permissions #networking #logs #monitoring #ufw

---
### 🧠 Process Management
- `ps` — список процессов (снимок)
    - `ps aux` — все процессы
    - `ps -ef` — “полный” формат (часто на серверах)
- `top` — процессы в реальном времени (CPU/RAM)
    - `top -u username` — процессы конкретного пользователя
- `kill` — отправить сигнал процессу по PID
    - `kill <PID>` — “попросить завершиться” (SIGTERM)
    - `kill -9 <PID>` — жёстко убить (SIGKILL, крайний случай)
---
### 📦 Package Management (APT)
- `apt update` — обновить список пакетов (репозитории)
- `apt upgrade` — обновить установленные пакеты
- `apt install <pkg>` — установить пакет
- `apt remove <pkg>` — удалить пакет (обычно оставляет конфиги)
- полезные рядом:
    - `apt search <keyword>` — поиск пакетов
    - `apt show <pkg>` — информация о пакете
    - `apt autoremove` — убрать ненужные зависимости
---
### 📁 File Management
- `pwd` — показать текущую директорию
- `ls` — список файлов
    - `ls -la` — включая скрытые + подробный формат
- `cd` — перейти в директорию
    - `cd ..` — на уровень выше
    - `cd ~` — в home
- `mkdir` — создать директорию
    - `mkdir -p path/to/dir` — создать цепочку директорий
- `cp` — копировать
    - `cp file.txt backup.txt`
    - `cp -r dir1 dir2` — копировать директорию рекурсивно
- `mv` — переместить/переименовать
    - `mv old.txt new.txt`
- `rm` — удалить
    - `rm file.txt`
    - `rm -r dir` — удалить директорию рекурсивно
    - `rm -rf dir` — без вопросов (опасно)
---
### ✍️ Text Editing
- `nano file.txt` — простой редактор “на месте”
    - подсказки по горячим клавишам обычно внизу экрана
- `vim file.txt` — мощный редактор (требует привычки)
    - `i` — insert mode
    - `Esc` → `:wq` — сохранить и выйти
    - `Esc` → `:q!` — выйти без сохранения
---
### 👤 Users & Permissions
- `adduser username` — создать пользователя (удобный интерактивный способ)
- `groupadd groupname` — создать группу (иногда вместо `addgroup`)
- `usermod -aG groupname username` — добавить пользователя в группу
- `chown user file` / `chown user:group file` — сменить владельца/группу
    - `chown -R user:group dir` — рекурсивно
- `chmod 755 file` / `chmod u+x file` — сменить права (numeric/symbolic)
---
### 🌐 Networking
- `ping host` — проверить доступность + задержку
- `ip a` — показать сетевые интерфейсы и IP (замена `ifconfig`)
- `ifconfig` — legacy команда (встречается в старых материалах)
- `netstat` — legacy (статистика соединений; часто заменяется `ss`)
- `traceroute host` — показать путь пакетов по сети (маршрут)
---
### 📊 Monitoring & Logs
**Мониторинг:**
- `htop` — удобный интерактивный монитор процессов (как “улучшенный top”)
- `vmstat` — память/процессы/IO (срез статистики)
- `sar` — системная статистика (часто из пакета `sysstat`)
**Логи:**
- директория логов: `/var/log`
- `tail -n 50 file.log` — последние строки
    - `tail -f file.log` — “следить” за логом в реальном времени
- `less file.log` — просмотр с прокруткой/поиском
- `grep "pattern" file.log` — поиск по логам
---
### 🛡️ Security (UFW)
- `ufw` — простой интерфейс для firewall rules
    - `sudo ufw status` — статус и правила
    - `sudo ufw enable` — включить
    - `sudo ufw allow 22/tcp` — разрешить порт (пример SSH)
    - `sudo ufw deny 80/tcp` — запретить порт
