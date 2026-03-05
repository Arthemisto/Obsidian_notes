#os #security #protection #access_control #user_id #group_id #privilege_escalation #attacks

---
## 🛡️ [[Protection & Security]]

- Подробнее: **[[Operating Systems and System Programming Base]]** · **[[Computing Environments — Distributed, Virtualization, Cloud, RTOS]]**

> **Зачем это тут:** когда есть процессы, файлы, устройства и сеть, ОС должна контролировать **кто** и **что** может делать с ресурсами. Это разделяется на **protection** (контроль доступа) и **security** (защита от атак).

---
## 🛡️ Protection vs Security / Защита vs безопасность
- **Protection** — механизмы контроля доступа пользователей (**users**) и процессов (**processes**) к ресурсам (**resources**), определённым ОС.
- **Security** — защита системы (**system**) от внутренних и внешних атак (**internal/external attacks**).

---
## 🚨 Threat examples / Примеры угроз
Диапазон угроз большой (**huge range**), включая:
- **denial-of-service (DoS)**
- **worms**
- **viruses**
- **identity theft**
- **theft of service**

---
## 🧾 Identity & Access Control / Идентичность и контроль доступа
Обычно система сначала различает пользователей (**distinguish among users**), чтобы определить, кто что может делать (**who can do what**).

### 🧑 User IDs / Security IDs
- **user identities** (**user IDs / security IDs**) включают имя (**name**) и связанный номер (**associated number**), по одному на пользователя.
- Затем **user ID** связывается со всеми **files** и **processes** пользователя → формируется **access control**.

### 👥 Group ID
- **group identifier (group ID)** задаёт набор пользователей (**set of users**) и упрощает управление правами.
- **group ID** также связывается с каждым **process** и **file**.

### ⬆️ Privilege escalation
- **privilege escalation** позволяет сменить **effective ID** на более привилегированный (**more rights**).

---
## 🔐 Security measures / Меры безопасности (микро-блок)
На практике безопасность опирается на:
- **access control**
- **authentication**
- **data encryption**
- аудит/мониторинг и защитные механизмы (в зависимости от среды)

---
## 🧭 Summary / Сводка
- **Protection**: контроль доступа users/processes к resources.  
- **Security**: защита от атак (DoS, worms, viruses, identity theft, theft of service).  
- Основа access control: **user IDs** и **group ID**, привязанные к **files/processes**.  
- **Privilege escalation** меняет **effective ID** на более привилегированный.

---
### ➡️ Переход дальше
Эти принципы по-разному проявляются в современных средах: **distributed**, **virtualization**, **cloud**, **RTOS** (и safety-critical стандарты вроде **ARINC 653**).  
→ Далее: **[[Computing Environments — Distributed, Virtualization, Cloud, RTOS]]**