#os #computing_environments #distributed-systems #client_server #p2p #virtualization #cloud #rtos #arinc653 #security

---
## 🌐 [[Computing Environments — Distributed, Virtualization, Cloud, RTOS]]

- Подробнее: **[[Operating Systems and System Programming Base]]** · **[[Boot & Interrupts]]**

> **Зачем это тут:** одни и те же принципы ОС (processes/memory/I-O/security) живут в разных “мирах” — от standalone ПК до cloud и safety-critical RTOS. Среда определяет ограничения, риски и архитектуру решений.

---
## 🖥️ Traditional / Традиционная среда (connectivity + security)
- **Stand-alone general purpose machines** — автономные машины общего назначения.
- Границы размываются (**blurred**), потому что системы почти всегда **interconnect** (Internet).
- **Portals** дают web-доступ к внутренним системам.
- **Thin clients (network computers)** похожи на web-терминалы.
- Даже дома используются **firewalls** для защиты от Internet attacks.

---
## 💾 Traditional: Storage + File-System (логический взгляд на хранение)
ОС предоставляет единый логический взгляд на хранение (**uniform, logical view of information storage**), абстрагируя физику в **file**.

Носители различаются: **access speed**, **capacity**, **data-transfer rate**, **access method** (sequential / random).

### 📁 File-System Management (OS activities)
- creating/deleting **files and directories**
- primitives to manipulate files/directories
- mapping files onto **secondary storage**
- backup onto stable (**non-volatile**) storage media

> Мостик: как только появляется сеть и много узлов — появляются распределённые модели и новые способы общения систем.

---
## 📱 Mobile / Мобильная среда
- Handheld/mobile устройства часто **resource poor** → оптимизация под **usability** и **battery life**.
- Подключение обычно через **wireless networks**.
- Отличие от “обычного ПК”: сенсоры и новые сценарии → новые типы приложений.

> Мостик: mobile — частный случай сетевой/распределённой реальности: много узлов, много соединений, много копий данных.

---
## 🧩 Distributed Computing / Распределённые вычисления
- **Distributed system** = набор отдельных (иногда heterogeneous) систем, соединённых сетью.
- Сеть — **communications path**, чаще всего **TCP/IP**.
- Типы сетей: **LAN / WAN / MAN / PAN**.
- **Network operating system** даёт функции “между системами”.
- Коммуникационная схема (**communication scheme**) позволяет **exchange messages**.
- Цель по ощущениям: “illusion of a single system”.

---
## 🖥️ Client–Server / Клиент–сервер
- Серверы отвечают на запросы клиентов.
- **Compute-server system**: доступ к сервисам (например, database).
- **File-server system**: хранение и выдача файлов (store/retrieve files).

> Мостик: не всегда нужно делить роли. Есть модели, где все равны → P2P.

---
## 🔁 Peer-to-Peer (P2P) / Одноранговые сети
- P2P не различает клиентов и серверы: все узлы — **peers**.
- Узел может быть client/server/both.
- Чтобы участвовать: либо регистрация в **central lookup service**, либо **broadcast + discovery protocol**.
- Примеры (historical): Napster, Gnutella; VoIP (например Skype).

---
## 🧱 Virtualization / Виртуализация
- Идея: запускать среды/ОС “внутри” другой ОС, изолируя окружения.
- **Emulation**: source CPU ≠ target CPU (обычно самый медленный путь).
- **Interpretation**: язык/код исполняется без native compilation (медленнее, чем native).
- **Virtualization**: гостевые ОС (**guest OSes**) запускаются при помощи **VMM (virtual machine manager)**; изоляция и управляемость остаются под контролем.

> Мостик: virtualization — фундамент для cloud: масштабирование, много арендаторов, автоматизация.

---
## ☁️ Cloud Computing / Облачные вычисления
- Cloud доставляет **computing/storage/apps as a service** через сеть.
- Это логическое продолжение virtualization: cloud строится на **VMMs** + инструментах управления.
- Типы: **public / private / hybrid cloud**
- Модели: **SaaS / PaaS / IaaS**
- Практика: internet connectivity → нужны меры **security** (например **firewalls**), часто применяются **load balancers**.

---
## 🗄️ Storage Management / Mass-Storage (почему важны алгоритмы)
Диски используются для данных, которые не помещаются в main memory или нужны “надолго”.  
Производительность системы зависит от disk subsystem и алгоритмов.

### 🧩 OS activities
- **free-space management**
- **storage allocation**
- **disk scheduling**

### 🧱 Tertiary storage
- **optical storage** и **magnetic tape** (WORM / RW)
- может управляться ОС или приложениями

### 🧠 Consistency (почему сложно)
- **cache coherency** в multiprocessor environment (hardware-level)
- в distributed environment могут существовать **several copies of a datum**

---
## ⏱️ Real-time Embedded Systems / RTOS
- Embedded systems — наиболее распространённая форма computers.
- **RTOS** имеет фиксированные временные ограничения (**fixed time constraints**).
- Корректность = выполнение в пределах constraint (иначе система считается работающей неверно).

---
## 🛫 ARINC 653 / Space & Time Partitioning (safety-critical RTOS)
- **ARINC 653** задаёт интерфейс/принципы для **space and time partitioning** в safety-critical avionics RTOS.
- Цель: размещать **multiple applications** разных уровней на **same hardware** (IMA-подход).

---
## 🧩 Open-Source Operating Systems (контекст)
- Open-source ОС доступны в **source-code format** (в противовес closed-source / DRM).
- Истоки: FSF и лицензия GNU GPL (“copyleft”).
- Примеры: GNU/Linux, BSD UNIX (и производные).
- Частый сценарий обучения: запуск гостевых ОС через **VMM** (VMware/VirtualBox и т.п.).

---
## 🖥️ UI & Networking (optional)
### 🖥️ Provide User Interface
- **user interface**: graphical или text-based — если требуется взаимодействие с пользователем.

### 🌐 Implement Networking
- обработка **network protocols** и обмен данных (**communication**) — если ОС/среда требует сетевой доступ.

---
## 🧭 Summary / Сводка
- Traditional → сеть “везде” → безопасность становится обязательной (**firewalls**).
- Distributed → модели общения: **client–server** и **P2P**.
- Virtualization даёт изоляцию и управляемость → база для cloud.
- Cloud = **SaaS/PaaS/IaaS** + масштабирование + требования безопасности.
- Storage management (disk scheduling и т.п.) сильно влияет на производительность; в multiprocessor/distributed средах усложняется консистентность.
- RTOS = корректность по времени; **ARINC 653** формализует partitioning для safety-critical систем.
- Open-source ОС полезны для изучения (source code + VMM для экспериментов).

---
### ➡️ Переход дальше
Осталось добить “самый низ”: **bootstrapping + firmware** и как ОС становится **interrupt driven** (ISR/interrupt vector).  
→ Далее: **[[Boot & Interrupts]]**