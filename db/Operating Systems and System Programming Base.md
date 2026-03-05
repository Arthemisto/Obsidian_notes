# ОС и Системное программирование: Введение
#os #system_programming #intro #kernel #multitasking #resource_management #security

**Краткая суть:** ОС (operating system) — программный слой, который управляет ресурсами (resources), изолирует программы (isolation) и контролирует их выполнение (execution).

---
## 🧩 Структура и роли
- **Связанные темы:** [[Operating Systems and System Programming Base]]
- **Лекции:** [[(Lecture 1) Operating Systems and System Programming Basics]]
- **Архитектура:** [[Computer-System Architecture — SMP & Clusters]]

---
## 🧩 ОС как посредник (Mediator)
ОС — интерфейс между аппаратным обеспечением (**hardware**) и софтом (**software**).
- Управляет ресурсами: **CPU** и **memory**.
- Даёт слой абстракции: драйверы (**drivers**) и системные сервисы.
- Обеспечивает: стабильность (**stability**) и защиту (**security**).
- OS предоставляет абстракции: *process*, *thread*, *file*, *virtual memory*, *socket*.

![[Pasted image 20260216141413.png]]

---
## 🧩 Компоненты системы (4 уровня)
1) **Hardware**: CPU, memory, I/O devices  
2) **Operating System**: “дирижёр”, координирует использование железа  
3) **Application Programs**: браузеры, СУБД, компиляторы и т.д.  
4) **Users**: люди, другие машины, устройства

![[Pasted image 20260216142951.png]]

---
## ⚖️ Две главные функции ОС
### 1) Распределитель ресурсов (Resource Allocator)
ОС управляет ресурсами и разрешает конфликты между программами за доступ к ним.  
Цель: эффективное (**efficient**) и справедливое (**fair**) использование системы.

### 2) Управляющая программа (Control Program)
Контролирует выполнение программ, чтобы предотвращать ошибки и “неподобающее” использование компьютера.

---
## ⏱️ Многозадачность (Multitasking)
|Тип|Описание|Плюсы/Минусы|
|---|---|---|
|**Вытесняющая (Preemptive)**|ОС решает, когда переключать задачи (обычно по **timer/priority/interrupts**).|+ Высокая отзывчивость, лучшее распределение CPU.|
|**Невытесняющая (Non-preemptive)**|Задача отдаёт CPU добровольно (yield/блокировка).|- Риск “зависаний”, если задача не отдаёт управление.|

> **Ключевой механизм:** вытеснение опирается на **interrupts** и **timer**.

![[Pasted image 20260216143020.png]]

---
## 🧠 Kernel vs System Programs vs Applications
- **Kernel (ядро)** — единственная часть ОС, которая работает **всегда**.
- **System programs** — утилиты и службы, поставляемые с ОС, но не часть ядра.
- **Application programs** — прикладной софт пользователя.

Примеры **system programs**: *shell*, *utilities*, *daemons/services*, *system configuration tools*.

---
## 🧱 Изоляция и защита (Isolation & Protection)
- **Memory isolation**: разграничение памяти процессов (обычно через **virtual memory** + **privilege levels**: user/kernel mode).
- **File protection**: **permissions** + **locks** (чтобы процессы не портили данные друг другу).

---
## 🌳 Kernel Data Structures (микро-блок)
Зачем: ядру нужны быстрые структуры данных для таблиц, очередей, планирования и учёта ресурсов.
- **Binary search tree (BST)**: worst-case поиск **O(n)**.
- **Balanced BST**: поиск **O(lg n)**.
- **Hash function → hash map**: быстрый доступ по ключу (в среднем).
- **Bitmap**: строка из *n* битов для статуса *n* элементов.

Linux (пример): include-файлы — `<linux/list.h>`, `<linux/kfifo.h>`, `<linux/rbtree.h>`.

---
## 🧭 Итоговая сводка (Summary)
- Система: **hardware → OS → applications → users**.
- ОС = **resource allocator** + **control program**.
- Современная многозадачность — в основном **preemptive** (timer/interrupts).
- Ядро работает всегда и обеспечивает порядок: изоляция, защита, управление ресурсами.

---
### ➡️ Переход дальше
Дальше важно понять, на каком “железе” всё это работает: **SMP/AMP**, multicore и кластеры.  
→ Далее: **[[Computer-System Architecture — SMP & Clusters]]**