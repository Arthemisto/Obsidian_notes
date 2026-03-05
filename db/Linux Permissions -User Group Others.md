#os #linux #ubuntu #permissions #chmod #chown #chgrp #ls #file_permissions  
**Коротко:** Права в Linux задают, кто может **читать/писать/выполнять** файл: **owner (user)**, **group**, **others**. Смотрим через `ls -l`, меняем через `chmod`, владельца/группу — через `chown`/`chgrp`.
![[Pasted image 20260304165052.png|572]]

---
## 1) 🔐 Permissions: User / Group / Others
Linux использует набор атрибутов (attributes), которые определяют права:
- **read (r)** — чтение содержимого
- **write (w)** — изменение/запись
- **execute (x)** — выполнение (run)
### 👤 User (Owner permissions)
- Владелец файла (**owner**) имеет свой набор `r/w/x`.
- Владелец может быть изменён командой: `chown`.
### 👥 Group (Group permissions)
- Каждый файл принадлежит некоторой группе (**group**).
- Пользователи, которые состоят в этой группе, получают **отдельный** набор прав `r/w/x` (не равный owner).
- Группу файла можно изменить командой: `chgrp`.
### 🌍 Others (Other permissions)
- Все, кто **не owner** и **не в group** файла — это **others**.
- У others есть отдельный набор прав `r/w/x`, независимый от owner и group.
 ![[Pasted image 20260304165214.png|620]]
---
## 2) 🧾 Как отображаются права: `ls -l`
Права показываются как серия символов в выводе `ls -l`.
Пример формата:
-rwxr-x--- 1 alice dev 1234 Mar 4 12:00 file.txt
Ключевая часть: `rwxr-x---`
- порядок всегда один: **owner | group | others**
- каждый блок = **3 символа**: `r` `w` `x`
- если права нет → `-`
### ✨ Special permissions (встречаются в строке прав)
- `s` — **setuid/setgid**
- `t` — **sticky bit**
- `x` — **executable bit** (обычный “execute” в блоках прав)
---
## 3) 🛠️ Как менять права: `chmod`
Права меняются через `chmod` (add/remove permissions).
### 🧩 Symbolic notation (символьный формат)
- `u+r` — добавить read для owner (user)
- `g-x` — убрать execute у group
- `o+w` — добавить write для others
### 🧮 Numeric notation (числовой формат)
Пример: `755`
- **owner**: `rwx`
- **group**: `r-x`
- **others**: `r-x`
## 4) ✅ Пример
![[Pasted image 20260304165707.png|410]]
Расшифровка `750`:
- owner `7` = `rwx`
- group `5` = `r-x`
- others `0` = `---`
