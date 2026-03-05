#os #linux #posix #api #system_calls #ipc #threads #signals #regex #regexp #termios #c #android
## 🧩 POSIX + Regex 
**Коротко:** **POSIX** (Portable Operating System Interface) — стандарты API для Unix-like систем, чтобы софт был **совместим** и легко **портировался**. **Regex** — часть этого мира: стандартный инструмент поиска/валидации текстовых шаблонов.
![[Pasted image 20260304173208.png|273]]

---
## 1) 🧩 POSIX: что это
- **POSIX** определяет стандарты **API** для ПО под Unix-like ОС.
- Цель: **compatibility** между системами + облегчение **porting** (переноса).
- Linux как Unix-like система реализует много POSIX-стандартов: system calls, libc функции и интерфейсы.
---
## 2) 🧱 Что покрывает POSIX (ключевые области)
- **System interfaces** (system calls)
- **CLI**: commands & utilities
- **Shell and Utilities** (shell scripting)
- **Environment variables**
- **Regular expressions**
- **File system operations**
- **Process management**
- **IPC** (interprocess communication)
- **Threads**
- **Signals**
Итог: соблюдение POSIX даёт высокий уровень переносимости программ между Unix-like платформами.
---
## 3) 🔎 Regex: что это и зачем
**Regular expressions (regex/regexp)** — последовательности символов, которые задают **search pattern**:
- поиск (match)
- обработка текста (manipulate)
- валидация (validate)
---
## 4) 📧 Regex пример: email pattern + разбор
Шаблон:
[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}
Разбор:
- `[A-Za-z0-9._%+-]+` — local part (например `username`)
- `@` — символ `@`
- `[A-Za-z0-9.-]+` — domain (например `example`)
- `\.` — точка перед TLD
- `[A-Za-z]{2,}` — top-level domain (например `com`)
---
## 5) ☎️ Task: phone `(XXX) XXX-XXXX`
Требование: строго формат `(123) 456-7890`, а `123-456-7890` — не подходит.
✅ Решение:
^\(\d{3}\) \d{3}-\d{4}$

---
## 6) 🧪 Где тестировать regex
- regex101
- regular-expressions.info
- regexr
- rexegg
---
## 7) 🧰 POSIX в C: keypress и терминал
Для работы с POSIX-системами (Linux) в C обычно используют:
- стандартные C-библиотеки + POSIX-заголовки
- ключевой заголовок для terminal I/O: **`<termios.h>`**
    - управление режимом терминала (canonical/non-canonical), echo и т.п.
---
## 8) 🤖 Android и POSIX (важная ремарка)
![[Pasted image 20260304173300.png|126]]
Android построен на **Linux kernel**, который придерживается многих POSIX-идей, поэтому:
- значительная часть POSIX API/подходов доступна
- но “Android” ≠ “классический Linux distro” (свой userspace/framework)