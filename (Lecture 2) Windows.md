#windows #os #dos #nt #winapi #interrupts #registry #dosbox

---
## 🧱 Windows Origins & Branches & Windows Architecture (Layers)

- Подробнее: **[[Windows Origins & Branches]]** · **[[Windows Architecture (Layers)]]**
### 🧩 MS-DOS as a base

- **[[MS-DOS]] (Microsoft Disk Operating System)** — ОС командной строки (**command-line operating system**), фундамент ранних Windows (**early versions of Windows**).
- Ключевая идея: **commands + syntax** вместо GUI; ориентация на IBM-PC (**IBM-compatible personal computers**).
- Исторический итог: вытеснена ростом **graphical interfaces** и доминированием Windows.

### 🕰️ Windows “DOS core” line
- Ветка: Windows поверх DOS (совместимость + постепенный переход к 32-bit).
- **Windows 1.0 (1985)** — **GUI**, ранняя **multitasking**.
- **Windows 3.0 (1990)** — рост **graphical capabilities**, **TrueType**.
- **Windows 95 (1995)** — **Plug and Play**, **Start menu**, заметный шаг к **32-bit architecture**.
- **Windows ME** — в контексте упоминают **Task Manager**.
- **Windows XP (2001)** — **stability and performance**, **Luna**, **Remote Desktop**.
- **Windows Vista (2006)** — акцент на **security features**, **Windows Aero**, **Windows Sidebar**.
- **Windows 7 (2009)** — удобство **window management**, новая **Taskbar**, **multitouch**.
- **Windows 8 (2012)** — фокус на **touch devices**, **Metro UI**, **Windows Store**.

### 🏢 Windows NT line
- Ветка: “настоящая” NT-архитектура (enterprise-ориентация, безопасность, стабильность).
- **Windows NT 3.1 (1993)** — **32-bit**, **preemptive multitasking**, **NTFS**; бизнес/enterprise.
- **Windows NT 4.0 (1996)** — усиление **networking capabilities**, **TCP/IP**, **Active Directory**, **Windows Desktop Update**.
- **Windows 2000 (2000)** — зрелая **Windows NT architecture**: баланс **compatibility/usability** + стабильность/безопасность; **Plug and Play**, улучшения **Active Directory**.

### 🧱 Windows Architecture (Layers)

- Подробнее: **[[Windows Architecture (Layers)]]**
- Упрощённо по слоям: **CORE → KERNEL → UTILITIES → NEW API**  
    (где что находится и как взаимодействует — в подстатье).
---

## 🎮 DOS Compatibility / Emulation
- Подробнее: **[[DOS Compatibility / Emulation (DOSBox)]]**
### 🕹️ DOSBox purpose
- **[[DOSBox]] (DOSBox)** — open-source эмулятор (**open-source emulator**) для запуска DOS-игр/приложений (**DOS-based computer games and applications**) на современных ОС (**modern operating systems**).
- Что именно даёт: эмуляция **IBM PC-compatible computer** + среда **MS-DOS**, то есть “виртуальная машина” для старого софта.
- Практический смысл: сохранение совместимости, запуск legacy-приложений без реальной DOS.

---
## 🎮 [[Game Input & Windows Interrupts]]

- Подробнее: **[[Game Input & Windows Interrupts]]**
- Тезис: клавиатура (**keystrokes**) иногда ощущается “быстрее” мыши (**mouse movements**) из-за пути события и обработки на уровнях ОС/драйвера/подсистемы ввода.
- Полная цепочка “**A → action**”: **hardware → interrupt controller → CPU → OS kernel → interrupt handler/ISR → device driver → input subsystem → game engine**.
- Низкоуровневый маршрут: **IRQ → IDT → ISR** в **kernel mode (kernel mode)** (+ внутри статьи есть **GPIO interrupts (GPIO interrupts)**).
- Практическое правило: в **user mode (user mode)** **не писать** interrupt handlers (**DO NOT DO SO**). Для приложений использовать штатные механизмы Windows.

---

## 🪟 📨 [[Windows Messages & Input APIs]]

- Подробнее: **[[Windows Messages & Input APIs]]**
- **Windows Messages (Windows Messages)**: **WM_KEYDOWN/WM_KEYUP → message queue → event loop / message handling procedure**.
- **Input APIs (input APIs)**: **DirectInput (DirectInput)** / **XInput (XInput)** — **standardized interface** для **input devices**, абстракция low-level деталей (**abstract away low-level details**).
- **Engines/frameworks**: **Unity (Unity)** / **Unreal Engine (Unreal Engine)** — обычно имеют **built-in support** ввода.
- Мини-контекст: WinAPI-программе нужно **create windows (create windows)**; реакция может быть через **MessageBox (MessageBox)**.

---

## 🐧 Linux Transition (API Comparison)

- Подробнее: **[[Linux Transition (API Comparison)]]**

### ❓ Will it work on Linux?
- Вопрос: будет ли Windows-код работать на Linux (**Will that code work on LINUX?**).
- Суть: всё, что завязано на **Windows API**, “как есть” обычно не переносится — нужен **porting/adaptation** и замена API.
### 🧰 Linux APIs

- **POSIX (Portable Operating System Interface)** — базовый стандарт интерфейсов для Unix-like систем и приложений.
- **glibc (GNU C Library)** — стандартные C-функции в GNU/Linux user-space.
- **Linux kernel API (Linux kernel API)** — интерфейсы **kernel-level programming**, это не то же самое, что user-space (**user space**).
- Вывод: чаще работа идёт через **POSIX/glibc**, а kernel API — отдельный “уровень сложности и ответственности”.
---

## 🧰 [[System Programming (Windows Examples)]]

- Подробнее: **[[System Programming (Windows Examples)]]**
- **Virtual memory (virtual memory)** через **Windows API (Windows API)**: **VirtualAlloc / VirtualProtect / VirtualQuery / VirtualFree** (allocation/mapping/protection/deallocation).
- **Kernel-mode drivers (kernel mode drivers)**: **privileged mode**, доступ к **kernel memory**; стек: **WDK/Visual Studio**, **kernel mode debugging**; ошибки могут быть критичны.
- **Processor/threads (processor/threads)**: низкий уровень часто требует **assembly** или **kernel-mode code**; WinAPI-примеры: **GetSystemInfo**, **SetThreadAffinityMask**, **SetThreadPriority (THREAD_PRIORITY_HIGHEST)**; **thread affinity** = привязка потока к ядрам.
- **Devices (devices)**: перечисление устройств через **SetupDiGetClassDevs (SetupDiGetClassDevs)** / **HDEVINFO (HDEVINFO)**.
---

## 🗃️ Windows Registry: Purpose & Usage

- Подробнее: **[[Windows Registry]]** · **[[Windows Registry — Low-level & Forensics]]**

### 🧾 What it is
- **[[Windows Registry]] (Windows Registry)** — иерархическая база настроек (**hierarchical database**) Windows: центральное хранилище (**central repository**) конфигураций.
- Что хранит: настройки **operating system**, **hardware devices**, **applications**, **user preferences** и др.
- Структура дерева: **keys → subkeys → values** (значения могут включать configuration settings, application settings, device driver information и т.д.).
- Правки: через **Registry Editor (Registry Editor)**; важно делать **backup** — ошибки могут вызвать **system instability** или **render the system inoperable**.

### 🚫 Why not store huge data
- Идея: реестр не предназначен для больших данных (exe/длинные тексты).
- Почему: раздувание **registry hive files** → риски для **system performance and stability** + выше **maintenance complexity** и сложнее **troubleshooting**.

### 🛠️ How to work with it
- Ручное: **Registry Editor**.
- Программно: **Registry APIs** (read/write/query/delete).
- Автоматизация: **PowerShell (PowerShell)** / **batch scripts (batch scripts)** (bulk changes).
- Администрирование: **Group Policy (Group Policy)** (registry-based policy settings).
- Важная ремарка: реестр **не часть kernel (kernel)**; компонент работает в **user mode (user mode)**.

---

## 🕵️ Registry Low-level & Forensics

- Подробнее: **[[Windows Registry — Low-level & Forensics]]**
- **Hive files** как **binary files**: **header / nodes / values / pointers / data blocks**.
- Техдетали: **nk offsets**, **little endian**, трекинг смещений.
- “Удаление” на практике: смена признака **allocation pointer (- → +)** → **unallocated entries** и **registry slack** (следы остаются).
---

## 🧭 Summary / Сводка

- Логика: **[[MS-DOS]]** → ветки Windows (**DOS core** и **NT**) → слои **[[Windows Architecture (Layers)]]** → совместимость через **[[DOSBox]]** → ввод и прерывания **[[Game Input & Windows Interrupts]]** → корректный ввод через **[[Windows Messages & Input APIs]]** → сравнение с Linux (**[[Linux Transition (API Comparison)]]**) → системные WinAPI-примеры **[[System Programming (Windows Examples)]]** → реестр **[[Windows Registry]]** + форензика **[[Windows Registry — Low-level & Forensics]]**.