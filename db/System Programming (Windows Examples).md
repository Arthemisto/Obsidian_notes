
#windows #winapi #system-programming #memory #drivers #threads #devices #eventlog

---
### 🧠 Memory management (virtual memory)
**Memory Management (Memory Management)**  
В Windows доступ к управлению памятью ядра (**kernel memory management**) обычно выполняется через специальные функции и структуры **Windows API (Windows API)**, предназначенные для взаимодействия с ядром (**kernel**) и подсистемой управления памятью (**memory management subsystem**).

**Virtual Memory Functions (Virtual Memory Functions)**  
Windows предоставляет набор функций для управления виртуальной памятью (**virtual memory management**) в ядре. Эти функции позволяют управлять:

- выделением (**memory allocation**),
- отображением (**mapping**),
- защитой (**protection**),
- освобождением (**deallocation**).
Ключевые функции:
- **VirtualAlloc (VirtualAlloc)**
- **VirtualProtect (VirtualProtect)**
- **VirtualQuery (VirtualQuery)**
- **VirtualFree (VirtualFree)**

Возможности:
- выделять и управлять регионами виртуальной памяти (**allocate and manage virtual memory regions**);
- задавать атрибуты защиты памяти (**memory protection attributes**) — например read-only/read-write/execute (**read-only**, **read-write**, **execute**);
- запрашивать информацию о регионах памяти (**query information**);
- освобождать выделенную память (**free allocated memory**).

Пример из слайда:  
`LPVOID lpMem =`  `VirtualAlloc(NULL, dwSize, MEM_COMMIT | MEM_RESERVE, PAGE_READWRITE);`

---

### 🧩 Kernel-mode drivers

**Kernel Mode Drivers (Kernel Mode Drivers)** — компоненты, работающие в привилегированном режиме (**privileged mode**) внутри ядра Windows (**Windows kernel**). Они имеют прямой доступ к памяти ядра (**direct access to kernel memory**) и могут выполнять низкоуровневые операции управления памятью (**low-level memory management operations**).

Написание собственного драйвера режима ядра (**custom kernel mode driver**) позволяет получать прямой доступ к управлению памятью ядра (**kernel memory management**) — напрямую (**directly**).
Однако разработка драйверов требует специализированных знаний:
- программирование ядра Windows (**Windows kernel programming**),
- разработка драйверов (**driver development**),
и может быть сложной и потенциально рискованной (**complex**, **potentially risky**), если допустить ошибки (**done incorrectly**).

**Set Up Development Environment (Set Up Development Environment)**:
- установить **WDK (Windows Driver Kit)** — инструменты, библиотеки и заголовки (**tools, libraries, headers**) для разработки драйверов (**driver development**);
- использовать **Visual Studio (Visual Studio)**, где есть инструменты для отладки в режиме ядра (**kernel mode debugging**) и разработки драйверов (**driver development**).

![[Pasted image 20260223152610.png]]

---

### 🧵 Processor / threads

Для прямого управления операциями процессора (**processor operations**) или низкоуровневого взаимодействия с CPU (**interact with the CPU at a low level**) обычно нужно писать код на ассемблере (**assembly language**) или код режима ядра (**kernel-mode code**).

Важно: прямое вмешательство в операции CPU может иметь серьёзные последствия (**serious consequences**) и требует осторожности (**approached with caution**), особенно в режиме ядра (**kernel mode**), где ошибки приводят к нестабильности системы или крахам (**system instability**, **crashes**).

Далее приводится общий обзор того, как можно использовать API ядра Windows (**Windows kernel APIs**) для действий, связанных с управлением процессором (**processor management**).

![[Pasted image 20260223152702.png]]

**Пример логики (WinAPI) (WinAPI)**  
Используются функции:

- **GetSystemInfo (GetSystemInfo)** — запрос информации о процессоре и архитектуре системы (**processor and system architecture**): архитектура процессора (**processor architecture**), число процессоров (**number of processors**), размер страницы (**page size**), тип процессора (**processor type**).
- **SetThreadAffinityMask (SetThreadAffinityMask)** — установка CPU affinity (**CPU affinity**) текущего потока на CPU 0; поток будет выполняться только на CPU 0 (**restricts the thread to run only on CPU 0**).
- **SetThreadPriority (SetThreadPriority)** — установка приоритета текущего потока на максимально высокий (**THREAD_PRIORITY_HIGHEST (THREAD_PRIORITY_HIGHEST)**).
- Затем выполняется вычисление в цикле (**computation in a loop**) для имитации нагрузки (**simulate a workload**).
- В конце выводится сообщение о завершении (**print a message**) выполнения.
Предупреждение: affinity и приоритет могут иметь системные последствия (**system-wide implications**) и должны использоваться аккуратно (**done judiciously**).

Определение:  
**Thread affinity (thread affinity)** — связь потока (**thread**) с конкретным ядром CPU или набором ядер (**specific CPU core or set of CPU cores**). Она определяет, на каких ядрах поток может выполняться (**allowed to run**).
![[Pasted image 20260223152901.png]]![[Pasted image 20260223152824.png]]

---

### 🧰 Devices
`Filesystem`![[Pasted image 20260223152951.png]]![[Pasted image 20260223153123.png]]
`HDEVINFO hDevInfo = SetupDiGetClassDevs(NULL, NULL, NULL, DIGCF_ALLCLASSES | DIGCF_PRESENT);`
![[Pasted image 20260223153145.png]]
![[Pasted image 20260223153201.png]]
![[Pasted image 20260223153210.png]]

---
### 🧾 Event logging
**Event Logging and Monitoring (Event Logging and Monitoring)**: в Windows логирование событий (**event logging**) позволяет записывать системные (**system**), security (**security**) и application (**application**) события. Это полезно для мониторинга (**monitoring**) и диагностики (**troubleshooting**).
В слайде упоминается короткий пример записи события в **Windows event log (Windows event log)** с использованием API ядра Windows (**Windows kernel API**).![[Pasted image 20260223153218.png]]