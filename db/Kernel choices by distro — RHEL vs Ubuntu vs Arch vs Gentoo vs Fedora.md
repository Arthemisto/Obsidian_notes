# Kernel choices by distro — RHEL vs Ubuntu vs Arch vs Gentoo vs Fedora
#os #linux #kernel #distro #rhel #ubuntu #arch #gentoo #fedora #rt #lts #livepatch

**Коротко:** у большинства дистрибутивов базой является **mainline Linux kernel**, но отличия появляются в том, *какие варианты ядра* они предлагают (LTS/RT/low-latency), как долго поддерживают, и насколько дают пользователю свободу выбора.

---

## 🟥 RHEL (Red Hat Enterprise Linux)
Red Hat предлагает несколько вариантов ядра под разные enterprise-задачи:

- **Mainline kernel** — универсальный вариант “на каждый день”.
- **EUS (Extended Update Support) kernel** — расширенная поддержка:
  - упор на **stability**
  - долгий жизненный цикл для enterprise окружений
- **Real-time kernels (RT)** — для задач, где важны **deterministic response times**:
  - промышленность/телеком
  - аудио/low-latency системы
  - любые сценарии, где важна предсказуемая задержка

---

## 🟠 Ubuntu
Ubuntu обычно ставит **mainline kernel** по умолчанию, но даёт альтернативы под конкретные кейсы:

- **Mainline kernel** — дефолтная база.
- **Low-latency kernel** — оптимизация под desktop/multimedia:
  - меньшие задержки
  - полезно для аудио/видео работы и некоторых интерактивных сценариев
- **Ubuntu Kernel Livepatch Service** — “live patching” ядра:
  - закрытие критических security-уязвимостей **без reboot**
  - удобно для серверов/рабочих машин, где простой нежелателен

---

## 🟦 Arch Linux
Arch — это **rolling release** и максимальная свобода выбора:

- Можно ставить разные версии ядра из:
  - official repositories
  - **AUR**
- Пользователь выбирает:
  - **latest stable**
  - **LTS kernels**
  - альтернативные kernels (например, **Zen**, **Liquorix**) под desktop/gaming performance

> Идея Arch: “ты сам управляешь тем, какое ядро и окружение тебе нужно”.

---

## 🟣 Gentoo
Gentoo — **source-based** distro, где кастомизация максимально глубокая:

- Пользователь выбирает:
  - версию ядра
  - конкретные **опции конфигурации**, заточенные под железо и сценарий
- Это даёт контроль и оптимизацию, но требует больше времени/понимания.

---

## 🟦 Fedora
Fedora — community-driven distro, спонсируемый Red Hat, и по логике похож на RHEL, но более “быстрый” и экспериментальный:

- **Mainline kernel** — базовый вариант.
- **Real-Time (RT) kernel** — для сценариев с deterministic response.
- **Modularity project** — возможность выбирать альтернативные версии ядра и софта (как “наборы вариантов” под разные нужды).

---

## ✅ Мини-вывод (как запомнить)
- **RHEL**: стабильность + долгий support (EUS) + RT для enterprise.
- **Ubuntu**: mainline + low-latency + livepatch без reboot.
- **Arch**: rolling + выбор ядра под себя (stable/LTS/custom).
- **Gentoo**: максимум контроля (source-based, config “под железо”).
- **Fedora**: mainline + RT + modularity, ближе к Red Hat экосистеме.