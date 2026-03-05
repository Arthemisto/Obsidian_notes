# DOS Compatibility / Emulation (DOSBox)

#dosbox #dos #emulation #windows #cli #education #fun

---
## 🎮 DOSBox purpose
**DOSBox (DOSBox)** — open-source эмулятор (**open-source emulator**), созданный в первую очередь для запуска старых DOS-игр и приложений (**older DOS-based computer games and applications**) на современных операционных системах (**modern operating systems**).
Он симулирует IBM PC-совместимый компьютер (**IBM PC-compatible computer**) под управлением **MS-DOS (Microsoft Disk Operating System)** и позволяет устанавливать и запускать DOS-программы в виртуальной среде (**virtual environment**).
#Education  
#Fun  
#Prepare for linux command line

---
## 🛠️ Install DOSBox (Windows)
- Скачать **DOSBox (DOSBox)** (**Download DOSBox**): [https://www.dosbox.com/download.php](https://www.dosbox.com/download.php)
- Запустить установщик (**Run the Installer**): файл **.exe (.exe)**.
- Выбрать параметры (**Choose Installation Options**): мастер установки (**installation wizard**), директория (**installation directory**), ярлыки (**shortcuts**).
- Завершить (**Complete the Installation**): **Install (Install)** / **Finish (Finish)**.
- Открыть (**Open DOSBox**): через **Start menu (Start menu)** или ярлык.
- Использовать (**Use DOSBox**): интерфейс командной строки (**command-line interface**) — запуск программ, **mount (mount)** директорий, настройка (**configure settings**).
---
## 🗂️ Mount (DOSBox)
Операция **mount (mount)** делает директорию на ПК виртуальным диском (**virtual drive**) внутри DOSBox. Это нужно, потому что DOSBox эмулирует окружение **MS-DOS (MS-DOS)**, где хранилища представлены дисками **C:, D: (C:, D:)**.

**Синтаксис (syntax)** из слайда:  
`mount [drive letter] [directory path] (mount [drive letter] [directory path])`

### ✅ Примеры (examples)

- `mount c c:\games (mount c c:\games)`
- `c: (c:)`
- `dir (dir)`
- `cd doom (cd doom)`
- `doom.exe (doom.exe)`

---

## 🎮 Run a game (game.exe)
- Открыть **DOSBox (DOSBox)**.
- Смонтировать папку, где лежит **game.exe (game.exe)**, командой **mount (mount)** (пример выше).
- Переключиться на диск: `C: (C:)`.
- Перейти в папку игры: `cd <folder> (cd <folder>)`.
- Запустить исполняемый файл (**executable file**): `game.exe (game.exe)`.
---
## ⌨️ Popular DOSBox commands (basic)
- `mount (mount)` — смонтировать директорию как диск (**drive**).
- `c: / d: (c: / d:)` — перейти на диск (**switch drive**).
- `dir (dir)` — показать файлы/папки (**list directory**).
- `cd (cd)` — перейти в директорию (**change directory**).
- `cd.. (cd..)` — на уровень выше (**up one level**).
- `cls (cls)` — очистить экран (**clear screen**).
- `exit (exit)` — выйти из DOSBox (**exit DOSBox**).
- `help (help)` — справка по командам (**help**).
---
## 🧩 Homework (optional)
**HOMEWORK (OPTIONAL) (HOMEWORK ( OPTIONAL ))**
- Сайт проекта: [https://www.dosbox.com/](https://www.dosbox.com/)
- Пример игры (DOS): [https://archive.org/details/doom_dos](https://archive.org/details/doom_dos)
Задания:
- Запустить любую старую игру в **DOS-BOX (DOSBox)** и поиграть 10 минут.
- Смонтировать любую папку (**mount any folder**) и посмотреть файлы командой **dir (dir)**.
---
## 🧭 Summary / Сводка
- **DOSBox** эмулирует **MS-DOS** среду и диски **C:/D:**, поэтому ключевая операция — **mount** по шаблону `mount [drive letter] [directory path]`.
- Для запуска игры обычно хватает: `mount → C: → dir/cd → game.exe`.
- База команд: **mount, dir, cd, cls, exit, help**.