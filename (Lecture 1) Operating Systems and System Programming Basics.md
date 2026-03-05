#os #system_programming #intro #kernel #architecture #multiprocessing #clustering #multitasking #process-management #memory-management #storage #io_subsystem #drivers #security #virtualization #cloud #distributed-systems #boot #interrupts #rtos #arinc653

Коротко: **OS (operating system)** — посредник между **hardware (железом)** и **software (ПО)**: управляет ресурсами, изолирует программы, обеспечивает безопасность и контролирует выполнение.
- Подробнее (карта лекции):
  **[[Operating Systems and System Programming Base]]** · **[[Computer-System Architecture — SMP & Clusters]]** · **[[Multiprogramming, Timesharing & Scheduling]]** · **[[Interrupts, Dual-Mode & Timer]]** · **[[Process Concept & Process Management]]** · **[[Memory & Storage — Hierarchy]]** · **[[IO Subsystem & Device Drivers]]** · **[[Protection & Security]]** · **[[Computing Environments — Distributed, Virtualization, Cloud, RTOS]]**

---
## 🗺️ Lecture Flow
**Components → Architecture → Multitasking → Control (Interrupts/Timer) → Processes → Memory/Storage → I/O → Security → Environments → Boot/RTOS**

---
## 🧩 1) OS Basics — что такое ОС и зачем она нужна
- Понять “роль ОС”: **resource allocator** + **control program**.
- Разделение: **kernel** (always running) vs **system programs** vs **applications**.
- Контекст ожиданий: users vs shared systems vs embedded/mobile.
- Перейти: “раз ОС распределяет ресурсы — смотрим, *какие ресурсы и как устроено железо*”.

→ Далее: **[[Operating Systems and System Programming Base]]**

---
## 🧠 2) Computer-System Architecture — на каком “железе” работает ОС
- **general-purpose** + **special-purpose processors**.
- **multiprocessor systems**: преимущества (**throughput / economy of scale / reliability**).
- **AMP vs SMP**, что меняется для ОС.
- **Clustered systems**: SAN, **high-availability**, **HPC**, **DLM**.
- Перейти: “когда ресурсов много, ОС должна *делить CPU/I/O между задачами эффективно*”.

→ Далее: **[[Computer-System Architecture — SMP & Clusters]]**

---
## 🗂️ 3) Multiprogramming & Timesharing — как ОС делает систему “эффективной” и “интерактивной”
- **multiprogramming (batch)**: CPU не простаивает — есть jobs, **job scheduling**.
- **timesharing (multitasking)**: интерактивность, **response time < 1s**.
- **CPU scheduling**, **swapping**, **virtual memory** (как мост к памяти).
- **preemptive vs non-preemptive** (почему одно работает лучше в реальности).
- Перейти: “чтобы вытеснение было реальным — ОС должна *регулярно возвращать себе управление*”.

→ Далее: **[[Multiprogramming, Timesharing & Scheduling]]**

---
## ⚡ 4) Interrupts + Dual-mode + Timer — механизмы контроля
- **interrupt driven**: hardware interrupts vs software interrupts (**trap/exception**).
- **interrupt vector → ISR**, сохранение адреса interrupted instruction.
- **dual-mode**: **user mode / kernel mode**, **privileged** инструкции, **system call**.
- **timer**: counter → interrupt, защита от **infinite loop / process hogging**.
- Перейти: “теперь можно строго описать *единицу планирования*”.

→ Далее: **[[Interrupts, Dual-Mode & Timer]]**

---
## 🧵 5) Process — программа в выполнении (unit of work)
- **process = program in execution** (active) vs program (passive).
- Ресурсы: **CPU/memory/I/O/files**, reclaim on termination.
- **single-threaded / multi-threaded**, concurrency через **multiplexing CPU**.
- OS responsibilities: create/delete, suspend/resume, sync, IPC, deadlocks.
- Перейти: “процесс живёт только если инструкции/данные где-то размещены”.

→ Далее: **[[Process Concept & Process Management]]**

---
## 🧠💾 6) Memory & Storage — где лежат инструкции и данные
- Memory management: tracking / move in-out / allocate-deallocate.
- Единицы: **bit/byte/word**, “почему 64-bit word”.
- **main memory** (CPU direct, volatile) vs **secondary storage** (nonvolatile).
- HDD/SSD и **storage hierarchy** (почему важны алгоритмы диска).
- Mass-storage management: free-space, allocation, disk scheduling.
- Перейти: “доступ к устройствам идёт через драйверы и I/O”.

→ Далее: **[[Memory & Storage — Hierarchy]]**

---
## 🔌 7) I/O Subsystem & Drivers — как ОС разговаривает с устройствами
- ОС скрывает peculiarities hardware.
- **buffering / caching / spooling**.
- **device-driver interface** + drivers для конкретных устройств.
- Перейти: “есть процессы/файлы/устройства → нужен контроль доступа”.

→ Далее: **[[IO Subsystem & Device Drivers]]**

---
## 🛡️ 8) Protection & Security — кто что может делать
- **protection** = control access to resources.
- **security** = defense against attacks (internal/external).
- **user IDs / group IDs → access control**, privilege escalation.
- Перейти: “всё это работает по-разному в разных средах”.

→ Далее: **[[Protection & Security]]**

---
## 🌐 9) Computing Environments — где ОС живёт сегодня
- Traditional / Mobile / Distributed.
- Client-server, P2P.
- **virtualization → VMM** → **cloud computing** (SaaS/PaaS/IaaS; public/private/hybrid).
- RTOS + safety-critical контекст → **ARINC 653** (space/time partitioning).
- Перейти: “остаётся понять старт: bootstrapping + firmware”.

→ Далее: **[[Computing Environments — Distributed, Virtualization, Cloud, RTOS]]**

---
## 🚀 10) Bootstrapping — как всё запускается (микро-мост)
- **bootstrap program + firmware** стартуют систему, после чего ОС становится **interrupt driven** и берёт контроль.
- **Handle boot process**: загрузка (**loading**) и выполнение (**executing**) кода с загрузочного устройства (**boot device**) и перевод системы в рабочее состояние.
- **Initialize hardware**: инициализация **CPU**, **memory**, **disk controllers** и **peripheral devices**.

---
## 🧭 Summary / Сводка
- Эта лекция — про **логическую цепочку**: *роль ОС* → *архитектура железа* → *мультизадачность* → *механизмы контроля (interrupts/dual-mode/timer)* → *процессы* → *память и хранилище* → *I/O и драйверы* → *безопасность* → *современные среды (distributed/virtualization/cloud/RTOS)* → *bootstrapping*.