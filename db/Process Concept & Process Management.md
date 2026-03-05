#os #process-management #processes #threads #program_counter #concurrency #multiplexing #deadlocks #synchronization #ipc

---
## 🧵 [[Process Concept & Process Management]]
- Подробнее: **[[Operating Systems and System Programming Base]]** · **[[Memory & Storage — Hierarchy]]**

> Зачем это тут: после **interrupts/dual-mode/timer** у ОС есть контроль над выполнением, значит можно формально описать **единицу работы (unit of work)**, которую ОС планирует и переключает → **process**.

---
![[Pasted image 20260216150529.png]]

## 🧵 Process / Процесс (Process)
- **Process = program in execution**: процесс — активная сущность (**active entity**), программа — пассивная (**passive entity**).
- Процессу нужны ресурсы (**resources**): **CPU, memory, I/O, files** (+ **initialization data**).
- При завершении ОС освобождает и возвращает повторно используемые ресурсы (**reclaim reusable resources**).

---
## 🧵 Single-threaded vs Multi-threaded / Один и несколько потоков
- **Single-threaded process**: один **program counter** → указывает следующую инструкцию (**next instruction**); выполнение последовательное (**sequential**).
- **Multi-threaded process**: по одному **program counter per thread**.

---
## 🔁 Concurrency / Конкурентность
- В системе много процессов: часть **user**, часть **operating system**; они выполняются **concurrently** на одном или нескольких CPU.
- **Concurrency** достигается **multiplexing the CPUs** между processes/threads (**CPU multiplexing**).

> Мостик: раз процессов много и они конкурируют за ресурсы, ОС должна управлять их жизненным циклом и взаимодействием → process management responsibilities.

---
## 🧩 Responsibilities (Process Management) / Обязанности ОС
ОС отвечает за:
- **create/delete** both **user** and **system processes**
- **suspend/resume** processes
- mechanisms for **process synchronization**
- mechanisms for **process communication (IPC)**
- mechanisms for **deadlock handling**

---
## 🧭 Summary / Сводка
- **Process** = **program in execution**; требует **CPU/memory/I/O/files** и освобождает ресурсы при завершении.
- Single-threaded: один **program counter**; multi-threaded: **program counter** на поток.
- Concurrency достигается **CPU multiplexing**.
- OS process management: create/delete, suspend/resume, sync, IPC, deadlocks.

---
### ➡️ Переход дальше
Процесс выполняется только если его инструкции/данные где-то размещены и подкачиваются при необходимости → это **memory + storage hierarchy**.  
→ Далее: **[[Memory & Storage — Hierarchy]]**