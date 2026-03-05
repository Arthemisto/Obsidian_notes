#os #boot #firmware #bootstrapping #interrupts #isr #interrupt_vector #trap #exception #interrupt_driven #rtos #arinc653

---
## 🚀⚡ [[Boot & Interrupts]]

- Подробнее: **[[Operating Systems and System Programming Base]]** · **[[Interrupts, Dual-Mode & Timer]]**

> **Зачем это тут:** это “самый низ” лекции. **Bootstrapping** поднимает ОС на голом железе, а дальше ОС работает как **interrupt driven** система — реагирует на устройства и системные события через прерывания.

---
## 🚀 Bootstrapping / Загрузка (Boot Process)
- **bootstrap program** — загрузочная программа.
- **firmware** — прошивка.
- Смысл: стартовать загрузку, выполнить начальный код и перевести систему в рабочее состояние (**usable state**).

> Мостик: после запуска ОС должна регулярно “забирать управление” и реагировать на события устройств → это и делает interrupts.

---
## ⚡ Interrupts / Прерывания (Interrupt Handling)
- Прерывание (**interrupt**) передаёт управление обработчику **ISR (interrupt service routine)**.
- Обычно через **interrupt vector** — таблицу адресов обработчиков (**service routines**).
- Архитектура прерываний должна сохранять адрес **interrupted instruction** (прерванной инструкции), чтобы продолжить выполнение после ISR.

---
## 🧨 Trap / Exception / Ловушка и исключение
- **trap / exception** — **software-generated interrupt**:
  - либо из-за **error**,
  - либо как **user request** (например запрос сервиса ОС).

---
## 🧠 OS is interrupt driven / ОС управляется прерываниями
- Ключевая идея: ОС “живёт” в модели **interrupt driven** — события от устройств и системные ситуации переводят управление в ОС через обработчики.

---
## 🛫 ARINC 653 (контекст RTOS) / Space & Time Partitioning
- **ARINC 653** описывает **space and time partitioning** в safety-critical avionics **RTOS**.
- Позволяет размещать **multiple applications** разных уровней на **same hardware** (IMA подход).

---
## 🧭 Summary / Сводка
- Bootstrapping запускает ОС через **bootstrap program** и **firmware**.
- Interrupts работают через **interrupt vector → ISR** и требуют сохранения адреса прерванной инструкции.
- trap/exception — программные прерывания из-за **error** или **user request**.
- ОС по сути **interrupt driven**.
- ARINC 653 — пример строгого partitioning для safety-critical RTOS.

---
### ➡️ Переход дальше
Чтобы эта модель была безопасной и управляемой, ОС использует разграничение прав (**user/kernel**), **system calls** и **timer** для принудительного возврата контроля.  
→ Далее: **[[Interrupts, Dual-Mode & Timer]]**