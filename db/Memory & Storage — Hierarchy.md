#os #memory_management #storage #hdd #ssd #storage_hierarchy #virtual_memory #swapping #mass_storage_management #caching

---
## 🧠💾 [[Memory & Storage — Hierarchy]]
- Подробнее: **[[Operating Systems and System Programming Base]]** · **[[IO Subsystem & Device Drivers]]**

> Зачем это тут: процесс выполняется только если **инструкции и данные** размещаются в **memory**. Когда RAM не хватает, ОС опирается на **storage hierarchy** (быстрое → медленное) и алгоритмы работы с дисками.

---
## 🧠 Memory Management / Управление памятью
Чтобы выполнить программу, все (или часть) **instructions** и **data** должны находиться в **memory**.

**Memory management** определяет, что находится в памяти и когда, оптимизируя **CPU utilization** и отклик пользователю (**computer response to users**).

### 🧩 Memory management activities
- **tracking**: какие части памяти заняты и кем
- **move in/out**: какие процессы/части и данные перемещать **into/out of memory**
- **allocate/deallocate** memory space

> Мостик: когда процессов больше, чем RAM, нужны механизмы переноса и “неполного присутствия” → swapping / virtual memory.

---
## 🔁 Swapping & Virtual Memory / Подкачка и виртуальная память
- **swapping**: процессы перемещаются **in and out** of memory, чтобы освобождать место и продолжать выполнение.
- **virtual memory**: позволяет выполнять процессы, которые находятся в памяти **не полностью** (**not completely in memory**).

---
## 🧱 Storage Definitions / Единицы и определения хранения
- **bit** — базовая единица (0/1)
- **byte = 8 bits** — минимальный удобный “кусок” хранения на большинстве систем
- **word** — родная единица данных архитектуры (**native unit**), состоит из одного или нескольких байтов  
  Пример: 64-bit registers + 64-bit addressing → обычно **64-bit (8-byte) words**

---
## 📏 Units in Bytes / Единицы в байтах
![[Pasted image 20260216144500.png]]

- Хранение и throughput обычно измеряют в **bytes** и их наборах.
- **KB = 1024**, **MB = 1024^2**, **GB = 1024^3**, **TB = 1024^4**, **PB = 1024^5**.

### 🏭 Manufacturer rounding & networking
- Производители часто округляют: MB = 1,000,000 bytes; GB = 1,000,000,000 bytes.
- В сетях измерения обычно в **bits**, потому что сеть передаёт данные “по битам”.

---
## 🧠 Main Memory vs 🗄️ Secondary Storage
### 🧠 Main memory / Основная память
- Единственная крупная память, к которой **CPU** обращается напрямую.
- **random access**, обычно **volatile**.

### 🗄️ Secondary storage / Вторичное хранилище
- Расширение main memory с большой **nonvolatile** ёмкостью.

---
## 🧲 Hard Disks / Жёсткие диски (HDD)
- HDD = rigid metal/glass **platters** с **magnetic recording material**.
- Поверхность делится на **tracks → sectors**.
- **disk controller** задаёт логическое взаимодействие устройства и компьютера.

---
## ⚡ Solid-state Disks / Твердотельные накопители (SSD)
- **SSD** быстрее HDD и **nonvolatile**.
- Разные технологии (various technologies), становятся популярнее.

---
## 🧊 Storage Hierarchy / Иерархия хранения
![[Pasted image 20260216144553.png]]

- Сверху: быстрее/дороже/меньше. Снизу: медленнее/дешевле/больше.
- ОС должна управлять перемещением данных между уровнями и понимать, где находится “самое свежее значение”.

---
## 💾 Storage & File-System / Файлы и файловая система
ОС даёт единый логический вид хранения (**uniform, logical view of information storage**) и абстрагирует физические свойства носителей в **file**.

Носители различаются: **access speed**, **capacity**, **data-transfer rate**, **access method** (sequential / random).

### 📁 File-system management (OS activities)
- create/delete **files and directories**
- primitives to manipulate files/directories
- mapping files onto **secondary storage**
- backup onto stable (**non-volatile**) storage media

---
## 🗄️ Mass-Storage Management / Управление массовым хранилищем
Диски хранят данные, которые не помещаются в main memory или нужны “надолго”.  
Производительность системы сильно зависит от disk subsystem и его алгоритмов.

### 🧩 OS activities
- **free-space management**
- **storage allocation**
- **disk scheduling**

### 🧱 Tertiary storage
- **optical storage** и **magnetic tape** (WORM / RW)
- может управляться ОС или приложениями

### 🧠 Consistency (почему сложно)
- В **multiprocessor environment** важна **cache coherency** (hardware-level).
- В **distributed environment** могут существовать несколько копий данных (**several copies of a datum**).

---
## 🧾 Memory Hierarchy Table
|Level|1|2|3|4|5|
|---|---|---|---|---|---|
|Name|registers|cache|main memory|solid state disk|magnetic disk|
|Typical size|< 1 KB|< 16MB|< 64GB|< 1 TB|< 10 TB|
|Implementation technology|custom memory with multiple ports CMOS|on-chip or off-chip CMOS SRAM|CMOS SRAM|flash memory|magnetic disk|
|Access time (ns)|0.25 - 0.5|0.5 - 25|80 - 250|25,000 - 50,000|5,000,000|
|Bandwidth (MB/sec)|20,000 - 100,000|5,000 - 10,000|1,000 - 5,000|500|20 - 150|
|Managed by|compiler|hardware|operating system|operating system|operating system|
|Backed by|cache|main memory|disk|disk|disk or tape|

---
## 🧭 Summary / Сводка
- **Memory management**: tracking / move in-out / allocate-deallocate.
- При нехватке RAM: **swapping** и **virtual memory**.
- Единицы: **bit → byte → word** (word = native unit архитектуры).
- **Main memory**: CPU direct, random access, обычно volatile; **secondary storage**: large nonvolatile.
- HDD: platters/tracks/sectors + disk controller; SSD: быстрее и nonvolatile.
- **Storage hierarchy** + алгоритмы диска критичны для производительности; в multiprocessor/distributed средах усложняется консистентность.

---
### ➡️ Переход дальше
Чтобы процессы читали/писали данные и работали с устройствами, ОС скрывает особенности железа через **I/O subsystem** и **drivers** (buffering/caching/spooling).  
→ Далее: **[[IO Subsystem & Device Drivers]]**