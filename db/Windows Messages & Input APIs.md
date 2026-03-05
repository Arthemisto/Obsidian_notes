### 📨 [[Windows Messages & Input APIs]] 🪟

#windows #winapi #input #messages #directinput #xinput #unity #unreal #thirdparty

---
#### 📨 Windows Messages (WM_KEYDOWN/WM_KEYUP)

**Windows Messages (Windows Messages)**: приложения Windows получают ввод клавиатуры как сообщения (**messages**), например **WM_KEYDOWN (WM_KEYDOWN)** и **WM_KEYUP (WM_KEYUP)**, которые отправляются в очередь сообщений приложения (**message queue**). Разработчики обрабатывают их в цикле событий (**event loop**) или в процедуре обработки сообщений (**message handling procedure**) для реакции на события клавиатуры (**keyboard events**).

Хотя **Windows Messages (Windows Messages)** работают в режиме пользователя (**user mode (user mode)**), при событиях клавиатуры сообщения генерирует ядро Windows (**Windows kernel (Windows kernel)**) и доставляет их в нужную очередь через механизм передачи сообщений ядра (**kernel's message-passing mechanism**). Это позволяет приложениям получать и обрабатывать ввод стандартизированно и эффективно (**standardized and efficient manner**).

---
#### 🎮 Input APIs (DirectInput/XInput)
Windows предоставляет API ввода (**input APIs**), такие как **DirectInput (DirectInput)** и **XInput (XInput)**, с более продвинутыми возможностями обработки ввода с клавиатуры, мыши, контроллеров и других устройств (**keyboards, mice, game controllers, and other devices**). Эти API скрывают низкоуровневые детали (**abstract away low-level details**) и дают стандартизированный интерфейс (**standardized interface**) для работы с устройствами ввода (**input devices**).

---
#### 🧰 Engines / frameworks
Игровые библиотеки и фреймворки (**game development libraries and frameworks**), например **Unity (Unity)** и **Unreal Engine (Unreal Engine)**, часто имеют встроенную поддержку ввода (**built-in support for handling keyboard input**). Это позволяет обрабатывать ввод кроссплатформенно и стандартизированно (**cross-platform and standardized manner**).

---
#### 🧩 Third-Party Libraries
Существуют сторонние библиотеки и фреймворки (**third-party libraries and frameworks**) для обработки ввода в Windows-приложениях. Они часто дают более высокоуровневые абстракции (**higher-level abstractions**), кроссплатформенную поддержку (**cross-platform support**) и дополнительные возможности (**additional features**) для input handling (**input handling**).

---
#### 🧠 user mode vs kernel mode (privilege levels)
**User mode (user mode)** и **kernel mode (kernel mode)** — разные уровни привилегий (**privilege levels**), на которых может выполняться ПО. Они определяют уровень доступа к аппаратным ресурсам (**hardware resources**) и чувствительным системным функциям (**sensitive system functions**).

---
#### 🪟 Windows API focus + mini example
**Windows Messages (Windows Messages)** — важная часть **Windows API (Windows API)** и ключевой механизм связи между приложениями Windows и ОС. Они дают стандартизированную обработку пользовательского ввода (**handling user input events**) и важны для приложений с богатыми интерфейсами (**rich user interfaces**).

Windows API имеет много компонентов (**Windows API have a lot of things**), но здесь фокус на **Windows Messages (Windows Messages)**.
В Windows “нужно создавать окна” (**create windows**). Пример реакции на ввод:  
`MessageBox(hwnd, "Escape key pressed!", "Key Press", MB_OK | MB_ICONINFORMATION);` (**MessageBox (MessageBox)**)

![[Pasted image 20260223150957.png]]

---

#### 🛠️ Dev environment (C)

- Установить C-компилятор (**C compiler**): **MinGW (MinGW)** или **Visual Studio (Visual Studio)**.  
    [https://sourceforge.net/projects/mingw/](https://sourceforge.net/projects/mingw/)
- Убедиться, что есть текстовый редактор (**text editor**).
- Создать исходный файл (**source file**) с расширением **.c (.c)**, например **key_press.c (key_press.c)**.

![[Pasted image 20260223151026.png]]
In windows you should create windows
![[Pasted image 20260223151117.png]]
MessageBox(hwnd, "Escape key pressed!", "Key Press", MB_OK | MB_ICONINFORMATION);

---

#### 📚 Resources
**Official Documentation (Official Documentation)**: Windows Dev Center (**Windows Dev Center**)  
[https://docs.microsoft.com/en-us/windows/](https://docs.microsoft.com/en-us/windows/)

**Books (Books)**:
- “Programming Windows” — **Charles Petzold (Charles Petzold)** (включая keyboard input).
- “Windows System Programming” — **Johnson M. Hart (Johnson M. Hart)** (system-level, handling user input).
---

#### 🧭 Summary / Сводка

- **Windows Messages**: **WM_KEYDOWN/WM_KEYUP** → **message queue** → обработка через **event loop/message handling procedure**; доставка опирается на **Windows kernel** и **kernel message-passing mechanism**.
- **Input APIs**: **DirectInput/XInput** — стандартизированный интерфейс для устройств ввода, скрывает low-level детали.
- **Engines/frameworks**: **Unity/Unreal** — встроенная обработка ввода; есть и **third-party libraries**.
- Различие уровней: **user mode** vs **kernel mode** как **privilege levels**.
- Мини-практика: нужно **create windows**, пример — **MessageBox**.