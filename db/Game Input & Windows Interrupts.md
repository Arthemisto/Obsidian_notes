# Game Input & Windows Interrupts

#input #gaming #interrupts #windows #kernel #drivers #user-mode #kernel-mode

---

## Game Input: Key → Action 🔁🎮

В контексте игр (**gaming**), где обработка ввода игрока критична (**player input processing is crucial**), нажатия клавиш (**keystrokes on the keyboard**) вероятно обрабатываются быстрее, чем движения мыши (**mouse movements**). Причина — клавиатура обычно имеет прямое электрическое соединение (**direct electrical connection**) и не требует дополнительного времени на обработку сигнала (**signal processing**), тогда как мыши может требоваться время на обработку движения (**processing movement**) и передачу данных (**transmitting data to the computer**). Также игры часто проектируются с ожиданием активного использования клавиатуры (**players will actively use the keyboard to control their characters and perform actions**), поэтому обработка клавиш может быть оптимизирована (**optimized for quick and responsive feedback**). Скорость ввода зависит от факторов (**various factors**): железо (**hardware**), оптимизация игры (**game optimization**), текущая нагрузка системы (**current system load**).

Вопрос: кто отвечает за то, чтобы нажатие **“A” (“A”)** приводило к движению персонажа влево (**character moving left**), и что реально происходит (**what is actually happened**)?  
Ответ: за обработку прерываний отвечает ядро ОС (**Operating System Kernel / OS kernel**).

Когда нажата кнопка в игре (**When a button is pressed in a game**):

- Игровой движок отслеживает ввод (**game engine tracks input**) — клавиатура (**keystrokes**) и мышь (**button presses on the mouse**).
    
- Железо генерирует электрический сигнал (**hardware generates an electrical signal**), интерпретируемый как событие нажатия (**button press event**).
    
- Сигнал проходит через контроллер прерываний (**interrupt controller**), который определяет тип прерывания (**type of interrupt**) и пересылает его ОС (**forwards it to the operating system**).
    
- Ядро ОС обрабатывает прерывание (**kernel processes the interrupt**) и вызывает обработчик (**invoking the appropriate interrupt handler**); в играх это может относиться к части движка, отвечающей за ввод (**part of the game engine responsible for handling input**).
    
- Движок реагирует на событие (**responds to the button press event**) и активирует действие (**activating the corresponding game element or action**): движение (**moving a character**), выстрел (**shooting**) и др. (**other game functions**).
    
- Итог: движок — посредник (**intermediary**) между железом (**hardware**) и ОС (**operating system**), обрабатывает события (**processing button press events**) и управляет игровым процессом (**managing the game process accordingly**).
    

---

## Windows Interrupts: Technical Chain 🧷⚙️

**Interrupt Controller (interrupt controller)**: аппаратный контроллер прерываний обнаруживает сигнал нажатия (**detects the signal**) и пересылает его CPU (**forwards it to the CPU for processing**).

**CPU (Central Processing Unit)**: получив сигнал прерывания (**interrupt signal**), CPU приостанавливает текущую работу (**suspends its current execution**) и переходит в режим обработки прерываний (**interrupt handling mode**).

**Interrupt Handler (interrupt handler)**: процедура в ядре (**routine within the OS kernel**), которая:

- подтверждает прерывание (**acknowledges the interrupt**),
- сохраняет состояние CPU (**saves the CPU's current state**),
- определяет действие (**determines the appropriate action to take**).

**Device Driver (device driver)**: если ввод идёт от клавиатуры/мыши (**input device**), драйвер переводит электрический сигнал (**electrical signal**) в формат, понятный ОС (**format that the OS can understand**).

**Event Queue (event queue)**: ОС может хранить очередь/буфер событий (**queue or buffer**) для входящих событий (**incoming events**), чтобы обрабатывать их по порядку (**processed in the order**) и не терять данные при загрузке (**prevents data loss if the system is busy**).

**Input Subsystem (input subsystem)**: подсистема ввода ОС обрабатывает события от устройств (**processes input events**) — клавиатура, мышь, контроллеры (**keyboard, mouse, game controllers, etc.**) — и распределяет их приложениям (**dispatches them to the appropriate applications or processes**).
![[Pasted image 20260223135430.png]]
---

## IRQ → IDT → ISR (Windows kernel) 🧠🧷

**Hardware Interrupt Generation (hardware interrupt generation)**:

- Устройство генерирует сигнал запроса прерывания (**interrupt request / IRQ**).
    
- Линия IRQ (**IRQ line**) несёт сигнал к контроллеру прерываний (**interrupt controller**), который приоритизирует и отправляет его CPU (**prioritizes and forwards the interrupt to the CPU**).
    

**Interrupt Processing in Windows Kernel (interrupt processing in Windows kernel)**:

- CPU передаёт управление ядру Windows (**transfers control to the Windows kernel**).
    
- Ядро содержит процедуры обработки, включая **ISR (Interrupt Service Routines)** — небольшие фрагменты кода (**small sections of code**) для конкретных прерываний.
    
- **IDT (Interrupt Descriptor Table)** — структура данных ядра (**data structure maintained by the kernel**), которая сопоставляет векторы прерываний (**interrupt vectors / IRQ numbers**) с соответствующими ISR (**corresponding ISRs**).
    

**Execution of ISR (execution of interrupt service routine)**:

- CPU выполняет **ISR (ISR invocation)**, связанную с устройством (**interrupting device**).
    
- **Kernel-Mode Execution (kernel-mode execution)**: ISR выполняются в режиме ядра (**kernel mode**), что даёт привилегированный доступ (**privileged access**) и обеспечивает целостность/безопасность (**integrity and security**).
    
- ISR взаимодействует с устройством (**interacts with the hardware device**): чтение регистров (**reading data from device registers**), подтверждение прерывания (**acknowledging the interrupt**), запуск доп. действий (**initiating further actions**).
    
- Возможные реакции системы (**system response**): пробуждение потока (**waking up a sleeping thread**), обновление драйверов (**updating device drivers**), уведомление приложений user-mode (**notifying user-mode applications**).
    
- После завершения ISR управление возвращается прерванному коду (**return to interrupted execution context**), CPU возобновляет работу (**resumes normal operation**).
    

**GPIO interrupts doc (GPIO interrupts)**:  
[https://learn.microsoft.com/en-us/windows-hardware/drivers/gpio/gpio-interrupts](https://learn.microsoft.com/en-us/windows-hardware/drivers/gpio/gpio-interrupts)

---
![[Pasted image 20260223135507.png]]
## Correct Input Handling in Windows Apps ✅🪟

Схема уровней из слайда:

- **KERNEL (KERNEL)**
- **API (API)**
- **PROCESSOR (PROCESSOR)**
- **C program (C program)**
- **ASSEMBLER (ASSEMBLER)**
- **JAVA programm (JAVA programm)**
- **FRAMEWORK (FRAMEWORK)**
- **Only Hardcore! (Only Hardcore!)**
- **Driver (Driver)**
- **USER-MODE (USER-MODE)**
- **KERNEL-MODE (KERNEL-MODE)**

В стандартной среде Windows (**standard Windows environment**) напрямую реализовывать обработчики прерываний для клавиатуры (**interrupt handlers for handling keyboard input**) — нетипичный подход (**not a typical approach**) для разработки игр/приложений (**game development or application programming**). Презентация подчёркивает: **DO NOT DO SO (DO NOT DO SO)**.

Windows предоставляет высокоуровневые абстракции (**high-level abstractions**) и API (**APIs**) для обработки ввода (**handling input events**) — через механизмы:
- **Windows messages (Windows messages)**,
- **input APIs (input APIs)**, например **DirectInput (DirectInput)**, **XInput (XInput)**,
- событийно-ориентированные техники (**event-driven programming techniques**).

Технически возможно писать кастомные interrupt handlers (**custom interrupt handlers**), но это требует низкоуровневой работы (**working at a low level**) и взаимодействия с аппаратными прерываниями (**hardware interrupts**), что плохо поддерживается и не рекомендуется в пользовательском режиме (**not well-supported or recommended in user-mode applications**) на Windows.