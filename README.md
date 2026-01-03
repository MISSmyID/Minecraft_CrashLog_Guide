# 🗂️ Полный гайд по сбору логов Minecraft для техподдержки

![Актуально](https://img.shields.io/badge/актуально-1.21.10-green.svg)
![Лицензия](https://img.shields.io/badge/лицензия-MIT-blue.svg)

## 📋 Содержание

* [Введение](#введение)
* [Какие логи нужны](#какие-логи-нужны)
* [Windows](#windows)
* [macOS](#macos)
* [Linux](#linux)
* [Серверные логи](#серверные-логи)
* [Отправка логов](#отправка-логов)
* [Частые проблемы](#частые-проблемы)
* [FAQ](#faq)
* [Дополнительные ресурсы](#дополнительные-ресурсы)
* [Шаблон обращения](#шаблон-обращения)
* [Как помочь проекту](#как-помочь-проекту)

---

## Введение

Добро пожаловать в гайд по сбору логов Minecraft! Этот документ поможет вам правильно собрать диагностическую информацию для обращения в техническую поддержку.

> **Важно:** 95% проблем можно решить, имея на руках правильные логи.

---

## Какие логи нужны

### ✅ Обязательные

| Файл          | Путь             | Назначение                          |
| ------------- | ---------------- | ----------------------------------- |
| `crash-*.txt` | `crash-reports/` | Автоматически создается при вылете  |
| `latest.log`  | `logs/`          | История работы игры                 |
| `debug.log`   | `logs/`          | Расширенная отладка (если включено) |

### ➕ Дополнительные

* `hs_err_pid*.log` — ошибки Java
* `launcher_log.txt` — логи лаунчера
* Скриншоты ошибки (если есть)

---

## 🖥️ Windows

### Быстрый доступ (рекомендуется)

1. Используйте комбинацию клавиш:

   ```text
   Win + R → %appdata%\.minecraft → Enter
   ```
2. Или через проводник:

   * `C:\Users\[Имя_пользователя]\AppData\Roaming\.minecraft`
   * Включите **Скрытые элементы** в меню **Вид**, если папка не видна

### Структура папок

```text
📂 .minecraft/
├── 📁 crash-reports/      ← КРАШЛОГИ
│   └── crash-2025-01-03_21.39.30-client.txt
├── 📁 logs/               ← ЛОГИ
│   ├── latest.log
│   └── debug.log
├── 📁 screenshots/
└── 📁 mods/
```

---

## 🍎 macOS

### Через Finder

1. Нажмите `Cmd + Shift + G`
2. Введите путь:

   ```text
   ~/Library/Application Support/minecraft
   ```
3. Нажмите **Перейти**

### Через терминал

```bash
# Открыть папку в Finder
open ~/Library/Application\ Support/minecraft

# Или перейти в терминале
cd ~/Library/Application\ Support/minecraft
ls -la crash-reports/
```

### Структура папок

```text
📂 minecraft/
├── 📁 crash-reports/
├── 📁 logs/
├── 📁 resourcepacks/
└── 📁 saves/
```

---

## 🐧 Linux

### Стандартный путь

```bash
~/.minecraft/
```

```bash
# Просмотр логов
ls -la ~/.minecraft/crash-reports/
cat ~/.minecraft/logs/latest.log | tail -50
```

### Альтернативные пути

* **Flatpak:** `~/.var/app/com.mojang.Minecraft/.minecraft/`
* **Snap:** `~/snap/minecraft/common/.minecraft/`

---

## 🖥️ Серверные логи

Если вы администратор сервера:

```text
сервер/
├── 📁 logs/
│   ├── latest.log
│   └── 2025-01-03-1.log.gz
├── 📁 world/
└── server.properties
```

### Популярные хостинги

| Хостинг          | Где искать логи            |
| ---------------- | -------------------------- |
| Aternos          | Файлы → `logs`             |
| FreeMC           | Файловый менеджер → `logs` |
| MineHost         | Управление → Логи сервера  |
| Локальный сервер | Папка сервера → `logs`     |

---

## 📤 Отправка логов

### Метод 1: Discord

* Перетащите файлы в окно чата
* Лимит: **8 МБ** (или **50 МБ** с Nitro)

### Метод 2: Файлообменники

**Для текста:**

1. mclo.gs
2. pastebin.com
3. gist.github.com

**Для архивов:**

1. dropmefiles.com
2. mediafire.com
3. drive.google.com

### Метод 3: Архивация

```bash
# Windows (PowerShell)
Compress-Archive -Path "crash-reports/*", "logs/latest.log" -DestinationPath "logs.zip"

# Linux/macOS
zip -r logs.zip crash-reports/ logs/latest.log
```

---

## 🚨 Частые проблемы

### Проблема: нет папки `crash-reports`

**Решение:**

1. Запустите игру и спровоцируйте вылет
2. Проверьте: `Esc → Настройки → Дополнительно`
3. Убедитесь, что включён вывод логов

### Проблема: логи пустые или старые

```bash
rm -f ~/.minecraft/logs/latest.log
# Перезапустите игру
```

### Проблема: файл слишком большой

```bash
# Только последние строки
tail -n 1000 latest.log > latest_short.log

# Только ошибки
grep -i "error\\|exception\\|crash" latest.log > errors_only.log
```

---

## ❓ FAQ

**Q: Какие логи нужны при проблемах с модами?**
A: Обычные логи + скриншот папки `mods/`, версия Forge/Fabric, список модов.

**Q: Как включить расширенное логирование?**
A: Добавьте в аргументы JVM:

```text
-Dforge.logging.console.level=debug -Dfabric.log.level=DEBUG
```

**Q: Куда отправлять логи?**
A: В Discord `#техподдержка` или администратору сервера.

**Q: Как быстро найти ошибки?**
A: Ищите в логах слова: `ERROR`, `Exception`, `Crash`.

---

## 🔧 Дополнительные ресурсы

### Программы

* LogViewer
* Notepad++
* 7-Zip

### Онлайн-инструменты

* Minecraft Log Analyzer
* Pastebin
* Diffchecker

### Документация

* Mojang Wiki
* Fabric Documentation
* Forge Documentation

---

## 📝 Шаблон обращения

```markdown
**Никнейм:** ВашНик
**Версия:** 1.21.10 Fabric
**Проблема:** Вылет при заходе в Незер
**Моды:** Sodium, Iris, Xaero's Minimap
**Логи:** ссылка / прикреплены
**Что делал:** Зашел в портал, игра зависла
**Сервер:** (если есть)
```

---

## 🤝 Как помочь проекту

1. Создайте Issue на GitHub
2. Сделайте Pull Request
3. Напишите в Discord

---

**Автор:** MIMISSID
**Последнее обновление:** 3 января 2025
**Версия гайда:** 2.1

---

> Гайд распространяется под лицензией **MIT**. Разрешено свободное использование с указанием авторства.

