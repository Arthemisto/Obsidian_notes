#windows #os #links #hardlink #symlink #shortcut #mklink
## 🪟 Windows links: Hard link / Symlink / Shortcut
**Коротко:** Windows тоже умеет **hard links** и **symlinks**, но есть ещё отдельная сущность — **shortcut (.lnk)**, которая _не является_ ни hard link, ни symlink.

---
### 🧱 Hard link (Windows)
- Работает похоже на Linux: **дополнительная ссылка на те же данные файла** (без копирования содержимого).
- Обычно используется реже, чем symlink.
✅ Команда:
mklink /H hardlink.txt original.txt

---
### 🪢 Symbolic link (Windows)
- Аналог Linux symlink: ссылка на **путь** к файлу/директории.
- Может указывать на **файл или папку**, может быть между **разными томами**.
- Часто требует **админских прав** (аналогия с `sudo`).
Примеры:
mklink link_to_file.txt original.txt  
mklink /D link_to_dir original_dir

---
### 🔖 What is “shortcut” in Windows?
**Shortcut (ярлык)** = файл **`.lnk`** (или “shortcut” на рабочем столе), который хранит:
- путь к цели,
- параметры запуска (arguments),
- рабочую папку (Start in),
- иконку, иногда “Run as admin” и т.п.
Важно:
- Это **не** hard link (не общие данные файла).
- Это **не** symlink (не системная ссылка уровня файловой системы).
- Это объект оболочки Windows (Explorer/Shell), удобный для запуска.
- ![[Pasted image 20260304171211.png|308]]