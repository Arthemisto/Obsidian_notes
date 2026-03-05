#os #ubuntu #linux #debian #apt #gnome #virtualbox #lts #cloud
![[Pasted image 20260304132533.png|296]]
## 🟠 Name & idea: “Ubuntu”
- Название **Ubuntu** отражает акцент дистрибутива на **сообщество (community)**.
- Термин **“Ubuntu”** пришёл из языков банту Южной Африки (особенно **Zulu** и **Xhosa**).
- Частый перевод: **“humanity”** / **“humanity towards others”** (человечность, человечность по отношению к другим).
---
## 🧩 Introduction: что такое Ubuntu
- **Ubuntu** — open-source операционная система на базе **Debian Linux**.
- Цель: **user-friendly experience** для:
  - desktop
  - server
  - cloud computing
---
## 🖥️ Desktop Environment (DE) и официальные flavors
- По умолчанию Ubuntu обычно использует **GNOME**.
- Есть официальные flavors с другими DE:
  - **Ubuntu Budgie**
  - **Ubuntu MATE**
  - **Xubuntu** (Xfce)
  - **Kubuntu** (KDE Plasma)
  - **Lubuntu** (LXQt)
---
## 📦 Package Management: APT
- Ubuntu использует **APT (Advanced Package Tool)**.
- Позволяет устанавливать/обновлять/удалять пакеты из репозиториев:
  - через команды (`apt-get` / `apt`)
  - через графические менеджеры (например, **Synaptic**, **Ubuntu Software Center**)
---
## 🗓️ Release Cycle: versions & LTS
- Регулярные релизы: **каждые 6 месяцев**.
- **LTS (Long-Term Support)**: раз в **2 года**.
  - поддержка **5 лет** на desktop
  - поддержка **10 лет** на servers
---
## 👥 Community & support
- Большое активное сообщество пользователей и разработчиков:
  - форумы
  - документация
  - IRC
  - тестирование, баг-репорты
---
## ✅ Use cases: где Ubuntu используют
- **Desktop computing:** GUI похож на Windows/macOS → удобно для перехода
- **Server deployment:** стабильность, security features, большой набор пакетов
- **Development:** популярна у разработчиков (языки, tools, libraries)
- **Cloud computing:** частый выбор для облака (AWS, Azure, Google Cloud)
---
## 🧪 Ubuntu as VM on Windows (VirtualBox) — checklist
### 1) Install (скачать и поставить)
- Скачать VirtualBox: https://www.virtualbox.org/
- Скачать Ubuntu ISO: https://ubuntu.com/download/desktop
- Установить VirtualBox (обычный Windows installer)
### 2) Create VM (создать виртуалку)
- VirtualBox → **New**
- Name: например `Ubuntu`
- Type: **Linux**
- Version: **Ubuntu (64-bit)**
- RAM: минимум **1 GB** (лучше больше, если есть)
- Disk: создать виртуальный диск
  - **dynamically allocated** (растёт по мере надобности) или **fixed size**
  - размер: минимум **10 GB** (лучше больше)
### 3) Attach ISO & install Ubuntu
- Settings → **Storage**
- выбрать пустой optical drive
- выбрать ISO (Choose a disk file…)
- Start VM → установщик загрузится с ISO
- пройти установку → reboot VM после завершения
### 4) Guest Additions (optional but recommended)
- В окне VM: **Devices** → *Insert Guest Additions CD image…*
- установить Guest Additions (лучше интеграция host↔guest: драйверы/удобства)

Tutorial: https://ubuntu.com/tutorials/install-ubuntu-desktop-1804#1-overview