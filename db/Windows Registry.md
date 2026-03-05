## Windows Registry: Purpose & Usage

#windows #registry #config #hkcu #hklm #powershell

---
### 🗃️ What it is

**Registry (Windows Registry)** — иерархическая база данных (**hierarchical database**), используемая Microsoft Windows (**Microsoft Windows operating system**) для хранения настроек и опций (**configuration settings and options**). Она работает как центральное хранилище (**central repository**) конфигураций для:
- ОС (**operating system**),
- аппаратных устройств (**hardware devices**),
- приложений (**applications**),
- предпочтений пользователя (**user preferences**) и др.

Реестр организован в:
- ключи (**keys**),
- подключи (**subkeys**),
- записи (**entries**),  
    и по виду напоминает дерево (**tree-like structure**). Каждый key может содержать subkeys; каждый subkey может содержать values или другие subkeys. Значения (**values**) могут включать: настройки конфигурации (**configuration settings**), user preferences (**user preferences**), application settings (**application settings**), информацию о драйверах (**device driver information**) и т.д.
Изменения делаются через **Registry Editor (Registry Editor)**. Нужна осторожность: неправильные изменения могут вызвать нестабильность системы (**system instability**) или сделать её неработоспособной (**render the system inoperable**). Рекомендуется делать резервную копию (**backup**) реестра перед изменениями.
---
### 🌳 Keys & paths (examples)
В реестре **key (key)** — контейнер для организации и хранения настроек; аналог папок в файловой системе (**folders in a file system**). Keys формируют иерархическую структуру (**hierarchical structure**). Каждый key может содержать subkeys, которые могут содержать другие subkeys или values.

Keys идентифицируются путями (**paths**) как в файловой системе и используют обратный слэш (**backslash ()**) как разделитель (**delimiter**). Пример:  
`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`

Пример и разбор:  
`HKEY_CURRENT_USER\Control Panel\Desktop`
- **HKEY_CURRENT_USER (HKEY_CURRENT_USER)** — root key, настройки текущего пользователя (**currently logged-in user**).
- **Control Panel (Control Panel)** — subkey.
- **Desktop (Desktop)** — subkey.

Этот key **Desktop (Desktop)** хранит настройки окружения рабочего стола (**desktop environment**): обои (**wallpaper configuration**), размещение иконок (**icon placement**), заставку (**screen saver settings**) и т.д.  
Пример возможного value:  
`Wallpaper (Wallpaper): "C:\Users\User1\Pictures\wallpaper.jpg" ("C:\Users\User1\Pictures\wallpaper.jpg")`

---
### 🌲 B-tree implementation (common view)
Реестр часто реализуется вариацией **B-tree (B-tree data structure)**. Это подходит для эффективного хранения и извлечения key-value пар (**storage and retrieval of key-value pairs**) и управления иерархической структурой (**hierarchical structure**).

**B-trees (B-trees)** дают быстрые операции:
- поиск (**search**),
- вставка (**insertion**),
- удаление (**deletion**),

что важно для работы реестра с настройками ОС и приложений (**configuration settings and options**).

Детали реализации считаются проприетарными (**proprietary**) и не раскрываются Microsoft, но широко предполагается использование вариации B-tree из-за эффективности на больших иерархиях (**large, hierarchical datasets**).

![[Pasted image 20260223154542.png]]
![[Pasted image 20260223154525.png]]

---
### 🚫 Why not store huge data
В целом не рекомендуется хранить исполняемые файлы (**executable files**) или большие объёмы текста (**large amounts of text**) в реестре.
Технически это возможно: у реестра нет явных ограничений (**no explicit limitations**) на типы или размеры данных (**types or sizes of data**). Но делать так не рекомендуется по причинам:
1. **Registry Size (Registry Size)**: большие данные увеличивают размер файлов ульев (**registry hive files**), что может влиять на производительность и стабильность системы (**system performance and stability**). Реестр не оптимизирован для больших объёмов данных (**not optimized for handling large volumes of data**); слишком большие registry files могут приводить к операционным проблемам (**operational issues**).
2. **Maintenance Complexity (Maintenance Complexity)**: хранение данных, не предназначенных для конфигураций (**not explicitly intended for configuration settings**), усложняет обслуживание и поиск проблем (**system maintenance and troubleshooting**). Отладка таких проблем может быть сложнее, особенно если это отклоняется от типичного использования (**deviates from typical usage patterns**).

---
### 🛠️ How to work with registry

Разработчики могут работать с реестром разными способами:

- **Registry Editor (Registry Editor)**: ручной просмотр, редактирование и управление keys/values (**view, edit, manage**).
- **Registry APIs (Registry APIs)**: программное взаимодействие из приложений (**programmatically interact**): чтение (**reading**), запись (**writing**), запрос (**querying**), удаление (**deleting**) keys/values.
- **Registry Scripts (Registry Scripts)**: автоматизация через скрипты (**scripting languages**) — **PowerShell (PowerShell)** или batch scripts (**batch scripts**) для массовых изменений (**bulk changes**) и конфигураций (**configurations**) на системах.
- **Third-party Libraries (Third-party Libraries)**: библиотеки/фреймворки с более высокоуровневыми абстракциями (**higher-level abstractions**) и утилитами (**utilities**) — упрощают работу с реестром (**simplify registry interactions**) и добавляют возможности (**additional features**).
- **Group Policy (Group Policy)**: настройки групповой политики на базе реестра (**registry-based Group Policy settings**) для применения конфигураций/политик в сети (**across an organization's network**).
Пример API:  
`LONG result = RegOpenKeyEx(HKEY_CURRENT_USER, "Software\\MyApp", 0, KEY_SET_VALUE, &hKey);`
Пример PowerShell:  
`New-ItemProperty -Path "HKCU:\Software\MyApp" -Name "MyValue" -Value 123 -PropertyType DWORD Write-Host "Value successfully written to registry."`

---

### 🧩 Why we need registry?

- хранение и получение настроек приложений (**storing and retrieving application settings**);
- конфигурация функций Windows (**configuring Windows features**);
- управление custom-настройками приложений (**managing custom application settings**);
- связь между приложениями (**facilitating cross-application communication**);
- доступ к системным конфигурациям (**accessing system-level configurations**);
- поддержка legacy-приложений (**supporting legacy applications**).

---

### ❓ Is Registry part of kernel?

Реестр Windows не является частью ядра (**not part of the kernel itself**). Это компонент ОС Windows (**component of the Windows operating system**), который находится в режиме пользователя (**resides in user mode (user mode)**).

---
### 🛠️ How we will work with registry? _(Slide 79)_

Разработчики могут работать с **Windows Registry (Windows Registry)** разными способами (**through various means**):
- **Registry Editor (Registry Editor)**: встроенный редактор для просмотра, редактирования и управления ключами и значениями (**view, edit, and manage registry keys and values manually**).
- **Registry APIs (Registry APIs)**: набор API (**Application Programming Interfaces**) для программного взаимодействия с реестром из приложений (**programmatically interact**): чтение (**reading**), запись (**writing**), запрос (**querying**), удаление (**deleting**) keys/values.
- **Registry Scripts (Registry Scripts)**: автоматизация через скриптовые языки (**scripting languages**) — **PowerShell (PowerShell)** или batch scripts (**batch scripts**) для массовых изменений или конфигураций (**bulk changes**, **configurations**) на нескольких системах (**across multiple systems**).
- **Third-party Libraries (Third-party Libraries)**: сторонние библиотеки/фреймворки (**libraries and frameworks**) с более высокоуровневыми абстракциями и утилитами (**higher-level abstractions**, **utilities**), упрощающие работу с реестром (**simplify registry interactions**) и добавляющие функции (**additional features**).
- **Group Policy (Group Policy)**: определение настроек групповой политики на базе реестра (**registry-based Group Policy settings**) для применения конфигураций или политик в сети организации (**enforce specific configurations or policies across an organization's network**).

---

### 🧱 Hive files structure

На низком уровне (**at a low level**) реестр устроен как набор файлов ульев (**collection of hive files**), которые содержат keys/subkeys/values. Эти файлы — бинарные (**binary files**) и хранят данные в структурированном формате (**structured format**).
Вопрос слайда: почему запись реестра может “так выглядеть” (**WHY registry record might look?**).
Структура записи (как разбивка):

- **Header Information (header information)**: метаданные файла (**metadata**), например версия (**version number**), timestamp (**timestamp**) и др. свойства (**properties**).
- **Root Key Entries (root key entries)**: записи корневых ключей (например **HKEY_LOCAL_MACHINE (HKEY_LOCAL_MACHINE)**, **HKEY_CURRENT_USER (HKEY_CURRENT_USER)**) с указателями на root key nodes (**pointers to the root key nodes**).
- **Nodes (nodes)**: узлы данных для keys/subkeys с метаданными: имя (**name**), **security descriptor (security descriptor)**, флаги (**flags**).
- **Values (values)**: значения и их данные: строки (**strings**), числа (**integers**), бинарные данные (**binary data**).
- **Child Node Pointers (child node pointers)**: указатели на дочерние узлы (**child nodes**) для subkeys.
- **Data Blocks (data blocks)**: большие values могут храниться отдельно (**separate data blocks**) и ссылаться из nodes через pointers (**referenced by pointers**).

---

### 📋 nk offsets (table)

![[Pasted image 20260223154719.png]]
![[Pasted image 20260223154725.png]]

---

### 🧭 Tracking subkeys to value (example)
![[Pasted image 20260223154839.png]]

---

### 🗑️ Deleted data & slack

**Deleted registry data (deleted registry data)**: key/subkey/value не удаляются навсегда (**will not be removed forever**).

Каждый subkey/value имеет header — **Dword (Dword)**, который сообщает системе, сколько данных используется (**how much data is being used**). При удалении header меняет знак на положительный (**changes the sign to positive**).

- Для subkey: header value — **0xa0ffffff (0xa0ffffff)** или **0xa8ffffff (0xa8ffffff)**.
- Пример: было **-96** (использовано 96 байт), при удалении → конвертация в **0x60000000 (0x60000000)** (little endian, 96 dec).
- Меняется allocation pointer (**allocation pointer**) с “-” на “+” (**from - to + number**).
- Положительные числа (**positive numbers**) означают нераспределённые записи (**unallocated entries**).
- Это “единственное”, что происходит при удалении (**ONLY thing that happens**).
![[Pasted image 20260223154952.png]]
Упоминается восстановление (**recovering deleted data**) и рекомендация чтения:  
[http://www.dfrws.org/2008/program.shtml](http://www.dfrws.org/2008/program.shtml)
**Hypothetical Hive Bin Diagram (hypothetical hive bin diagram)**: возможный registry slack (**registry slack**) с positive headers (**positive headers**).
![[Pasted image 20260223155048.png]]

---

### 📌 Extra note

Подробности о том, как реестр работает на низком уровне и как читать “bytes” туда/обратно (**how to read bytes and vice versa**) — в другой презентации (**another presentation**).

---
## 🧭 Summary / Сводка

- Блок Registry: что это такое (**hierarchical database**), структура **keys/subkeys/values**, примеры путей (**HKLM/HKCU**), почему не хранить большие данные, способы работы (Editor/APIs/PowerShell/Group Policy/third-party).
- Low-level: **hive files** как **binary files**, разбор структуры (header/nodes/values/pointers/data blocks), таблица **nk offsets**, пример трекинга смещений, и идея “удаления” через positive headers и **registry slack** (forensics).