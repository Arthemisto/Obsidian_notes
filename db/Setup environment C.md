#os #linux #ubuntu #c #gcc #build_essential #posix #pthread #termios #filesystem #threads #memory #processor #syscalls #cheatsheet #iptables #netfilter #ufw #kernel
## 🧰 Setup environment для C 
**Коротко:** ставим компилятор и базовые инструменты, собираем и запускаем C-программу, затем подключаем POSIX-заголовки (threads/terminal I/O), и дальше курс уходит в темы “низкого уровня”: filesystem, threads, memory, processor, kernel.

---
## 1) 🛠️ Установка toolchain (Ubuntu)
### Build Essentials
sudo apt update  
sudo apt install build-essential
`build-essential` обычно включает GCC, make и базовые инструменты для сборки C/C++.
![[Pasted image 20260304174647.png|513]]
### Editor / IDE (любой удобный)
- VS Code, Atom, Sublime Text, Emacs, Vim  
---
## 2) 🧪 Compile + Run (минимум)
gcc -o hello hello.c  
./hello
- `gcc -o hello hello.c` — compile
- `./hello` — run
---
## 3) 🧩 POSIX в C: headers и примеры “куда копать”
### Threads (пример)
Чтобы использовать POSIX threads:
- подключаем `<pthread.h>`
- используем `pthread_create()`, `pthread_join()`

### Доп. библиотеки (optional)
Если нужно что-то специфическое — ставим через `apt` (поиск/установка библиотек под задачу).

---
## 4) ⌨️ Terminal I/O: `<termios.h>` (keypress / raw mode)
Для работы с вводом с клавиатуры “по символу” часто используют:
- `<stdio.h>`, `<stdlib.h>`, `<unistd.h>`, `<termios.h>`
Логика работы:
- настроить терминал на **non-canonical (raw) mode**
- выключить **echo**
- выполнить работу (читать нажатия)
- **обязательно вернуть** исходные настройки перед выходом
---
## 5) 🧩 Темы, которые дальше будут “ядром” (system programming)
Список-ориентир:
- **FileSystem**
- **Threads**
- **Memory**
- **Processor**
### 🧠 Processor / hardware access (идея)
На Linux в системном программировании можно ближе подойти к “железу” (инструкции/регистры), но это обычно:
- требует правильного контекста (permissions, привилегии)
- и не является “обычным user-level C” как на Windows (где доступ к регистрами напрямую ограничен)

| ![[Pasted image 20260304174740.png\|334]] | ![[Pasted image 20260304174950.png\|472]] |
| ----------------------------------------- | ----------------------------------------- |
| ![[Pasted image 20260304175012.png]]      | ![[Pasted image 20260304175030.png\|494]] |
| ![[Pasted image 20260304175041.png\|493]] | ![[Pasted image 20260304175049.png\|447]] |
| ![[Pasted image 20260304175100.png\|437]] | ![[Pasted image 20260304175106.png\|373]] |
