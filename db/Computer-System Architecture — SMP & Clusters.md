# Архитектура систем: SMP и кластеры
#os #architecture #multiprocessing #clustering

**Зачем это здесь:** ОС распределяет ресурсы, а их набор зависит от архитектуры (один CPU, много ядер или сеть серверов). От этого зависят планирование (**scheduling**) и масштабирование.

---
## 🧠 Multiprocessor systems (Parallel / Tightly-coupled)
Большинство современных систем используют **multiprocessor systems** (они же **parallel systems** / **tightly-coupled systems**).

### ✅ Преимущества (advantages)
- **throughput ↑**: больше вычислений за единицу времени
- **economy of scale**: дешевле объединять ресурсы, чем строить отдельные ПК
- **reliability ↑**: **graceful degradation** / **fault tolerance**

---
## 🧱 AMP vs SMP
1) **AMP (Asymmetric Multiprocessing)**: каждому процессору назначается **specific task**  
2) **SMP (Symmetric Multiprocessing)**: процессоры равноправны и выполняют **all tasks** (стандарт для **multicore**)

![[Pasted image 20260216150326.png]]
![[Pasted image 20260216150354.png]]

---
## 🧩 SMP layout (multi-chip / multicore)
- Бывают **multi-chip** и **multicore** системы.
- Варианты компоновки:
  - один узел со всеми **chips**
  - **chassis** с несколькими **separate systems**

![[Pasted image 20260216150424.png]]

> Мостик: SMP/AMP — “много CPU внутри одной системы”. Следующий шаг — “много машин вместе” → clustered systems.

---
## 🏢 Clustered systems (loosely-coupled)
Кластер — несколько отдельных систем (**nodes**), работающих совместно. В отличие от SMP — это “слабо связанные” системы.

- **Storage:** часто используют **SAN (storage-area network)**
- **High-availability:**
  - **asymmetric clustering**: один узел **hot-standby**
  - **symmetric clustering**: все узлы работают и **monitoring each other**
- **Consistency:** **DLM (distributed lock manager)** против **conflicting operations**
- **HPC (high-performance computing):** приложения должны поддерживать **parallelization**

![[Pasted image 20260216150434.png]]

---
## 🧠 Маленький совет: SAN в кластерах
SAN — это **block-level access** к общему хранилищу. Это упрощает **failover**: другой узел подхватывает сервис, потому что данные доступны на уровне блоков.

---
**➡️ Далее:** [[Multiprogramming, Timesharing & Scheduling]]