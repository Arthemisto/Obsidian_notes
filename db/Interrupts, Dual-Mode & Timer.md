#os #boot #firmware #interrupts #rtos #arinc653 #kernel #user_mode #kernel_mode #privileged #system_call #timer #vmm

Коротко: **bootstrapping** запускает ОС, а **interrupts** дают ОС механизм реакции на события и возврата контроля.

---
## 🚀 Bootstrapping / Boot Process
- **bootstrap program** + **firmware** стартуют систему и передают управление ОС.
- После старта ОС становится **interrupt driven** (работает “по событиям”).

---
## ⚡ Interrupts / Interrupt Handling
- **Interrupt** передаёт управление обработчику (**interrupt service routine, ISR**) через **interrupt vector** (таблица адресов обработчиков).
- CPU сохраняет адрес прерванной инструкции (**interrupted instruction**) и контекст, чтобы продолжить выполнение после ISR.
- **Trap / exception** — программно сгенерированное прерывание (**software-generated interrupt**): из-за ошибки (**error**) или как механизм запроса сервиса ОС (**system call**).

> Деталь: **interrupt vector** можно понимать как массив в памяти: номер прерывания используется как индекс для быстрого перехода к нужному ISR.

![[Pasted image 20260216143656.png]]

---
## 🛡️ Dual-mode / User vs Kernel
- Есть **user mode** и **kernel mode**.
- Некоторые инструкции — **privileged** и выполняются только в **kernel mode**.
- **System call** — “легальный переход” из user → kernel: программа вызывает **trap**, управление переходит в заранее определённую точку кода ОС, затем возврат возвращает в **user mode**.
- Современные CPU могут иметь дополнительные режимы (**multi-mode operations**), включая поддержку **VMM (virtual machine manager)** для **guest VMs**.

---
## ⏱️ Timer / Принудительный контроль
Зачем нужен **timer**:
- защита от **infinite loop**
- защита от **process hogging resources**
- основа вытесняющей многозадачности (**preemptive multitasking**) и стабильного **scheduling**

Механика:
- есть счётчик (**counter**), который уменьшается физическими часами (**physical clock**)
- ОС устанавливает счётчик (это **privileged instruction**)
- когда счётчик = 0 → генерируется **interrupt**, ОС возвращает себе контроль (**regain control**)

---
## 🛫 ARINC 653 (RTOS) / Space & Time Partitioning
- **ARINC 653** — спецификация интерфейсов для **safety-critical avionics RTOS**.
- Ключевая идея: **space and time partitioning**.
- Позволяет запускать **multiple applications** разных уровней на **same hardware** в архитектуре **IMA (Integrated Modular Avionics)**.

---
## 🧭 Summary / Сводка
- **Bootstrapping**: **bootstrap program + firmware** стартуют систему.
- **Interrupts**: ISR вызывается через **interrupt vector**, CPU сохраняет **interrupted instruction**.
- **Trap/exception**: software interrupt (ошибка или запрос сервиса ОС через **system call**).
- **Dual-mode**: разграничение **user/kernel**, **privileged** инструкции, безопасный вход через **system call**.
- **Timer**: через **interrupt** возвращает контроль ОС → база **preemptive multitasking** и **scheduling**.
- **ARINC 653**: **space/time partitioning** для критичных RTOS (IMA).

---
### ➡️ Переход дальше
Теперь есть “механизмы контроля”, значит можно описать **единицу работы**, которую ОС планирует и переключает.  
→ Далее: **[[Process Concept & Process Management]]**