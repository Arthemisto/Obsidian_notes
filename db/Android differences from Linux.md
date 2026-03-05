# Android is Linux? — differences
#os #android #linux #kernel #aosp #google_services

**Коротко:** Android построен на **Linux kernel**, но **не считается классическим Linux-дистрибутивом** (как Ubuntu). Ядро даёт базовую функциональность, а всё “пользовательское” окружение у Android своё: UI, фреймворк приложений и плотная интеграция сервисов Google, плюс сильная кастомизация производителями.

---
## ✅ Что Android берёт от Linux kernel
Linux kernel обеспечивает “низкий уровень” (core functionality):
- **hardware abstraction** (абстракция железа)
- **process management** (процессы)
- **memory management** (память)
- **device drivers** (драйверы)
---
## ❗ Почему Android ≠ traditional Linux distro
Android отличается от классических дистрибутивов по ключевым слоям “сверху ядра”.
### 🎨 1) User Interface (UI)
- У Android свой UI framework.
- Основной дизайн-подход: **Material Design**.
- Оптимизация под **touchscreens** и **mobile devices**:
  - home screens
  - app drawer
  - notifications
### 🧩 2) Application Framework (модель приложений)
Android использует свой фреймворк приложений:
- **activities**
- **services**
- **content providers**
- **broadcast receivers**
Разработка приложений обычно на:
- **Java**
- **Kotlin**
### 🔒 3) Google Services (интеграция экосистемы)
Android часто поставляется с Google-приложениями и сервисами:
- **Google Play Store**
- **Google Maps**
- **Gmail**
- и др.
Эти сервисы глубоко встроены в экосистему Android и расширяют функциональность.
---
## 🧱 Customization by vendors (производители/операторы)
- В отличие от “обычных” Linux distro, Android часто **сильно кастомизируется**:
  - модификации интерфейса
  - предустановленные приложения
  - системные конфигурации
- Поэтому “Android” на разных устройствах может заметно отличаться.
---
## 🌿 Open Source, но с ограничениями
- Android (через **AOSP**) открыт, и ОС можно модифицировать.
- Но на практике степень свободы ограничивается:
  - контролем Google над AOSP-экосистемой
  - распространённостью proprietary Google services
---
## ✅ Итог
- **Android uses Linux kernel as its foundation**, поэтому наследует многие плюсы Linux: **stability, security, performance**.
- Но из-за собственного UI, application framework и Google services Android **не является traditional Linux distribution** вроде Ubuntu.