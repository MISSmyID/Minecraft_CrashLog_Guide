🗂️ Полный гайд по сбору логов Minecraft для техподдержки

https://img.shields.io/badge/actual-1.21.10-green.svg
https://img.shields.io/badge/license-MIT-blue.svg

📋 Содержание

· Введение
· Какие логи нужны
· Windows
· macOS
· Linux
· Серверные логи
· Отправка логов
· Частые проблемы
· FAQ
· Дополнительные ресурсы

Введение

Добро пожаловать в гайд по сбору логов Minecraft! Этот документ поможет вам правильно собрать диагностическую информацию для обращения в техническую поддержку.

Важно: 95% проблем можно решить, имея на руках правильные логи!

Какие логи нужны

Обязательные:

Файл Путь Назначение
crash-*.txt crash-reports/ Автоматически создается при вылете
latest.log logs/ История работы игры
debug.log logs/ Расширенная отладка (если включено)

Дополнительные:

· hs_err_pid*.log — ошибки Java
· launcher_log.txt — логи лаунчера
· Скриншоты ошибки (если есть)

🖥️ Windows

Быстрый доступ (рекомендуется):

1. Используйте комбинацию клавиш:
   ```
   Win + R → %appdata%\.minecraft → Enter
   ```
2. Или через проводник:
   · Откройте C:\Users\[Имя_пользователя]\AppData\Roaming\.minecraft
   · Включите "Скрытые элементы" в меню "Вид", если папка не видна

Пути к файлам:

```
📂 .minecraft/
├── 📁 crash-reports/      ← КРАШЛОГИ здесь
│   └── crash-2025-01-03_21.39.30-client.txt
├── 📁 logs/               ← ОБЫЧНЫЕ ЛОГИ здесь
│   ├── latest.log
│   └── debug.log
├── 📁 screenshots/        ← Скриншоты
└── 📁 mods/               ← Папка с модами
```

🍎 macOS

Через Finder:

1. Нажмите Cmd + Shift + G
2. Введите путь: ~/Library/Application Support/minecraft
3. Нажмите "Перейти"

Через терминал:

```bash
# Открыть папку в Finder
open ~/Library/Application\ Support/minecraft

# Или перейти в терминале
cd ~/Library/Application\ Support/minecraft
ls -la crash-reports/
```

Структура папок:

```
📂 minecraft/
├── 📁 crash-reports/
├── 📁 logs/
├── 📁 resourcepacks/
└── 📁 saves/
```

🐧 Linux

Стандартный путь:

```bash
# Основной путь
~/.minecraft/

# Просмотр логов
ls -la ~/.minecraft/crash-reports/
cat ~/.minecraft/logs/latest.log | tail -50
```

Альтернативные пути:

· Flatpak: ~/.var/app/com.mojang.Minecraft/.minecraft/
· Snap: ~/snap/minecraft/common/.minecraft/

🖥️ Серверные логи

Если вы администратор сервера:

```bash
# Стандартный сервер
сервер/
├── 📁 logs/
│   ├── latest.log
│   └── 2025-01-03-1.log.gz
├── 📁 world/
└── server.properties
```

Для популярных хостингов:

Хостинг Где искать логи
Aternos Файлы → Папка logs
FreeMC Файловый менеджер → logs
MineHost Управление → Логи сервера
Локальный сервер Папка сервера → logs

📤 Отправка логов

Метод 1: Прямая загрузка в Discord

· Перетащите файлы в окно чата
· Максимальный размер: 8 МБ (Discord) или 50 МБ (если есть Nitro)

Метод 2: Файлообменники

Для текста (логи, краш-репорты):

1. mclo.gs — специально для Minecraft
2. pastebin.com
3. gist.github.com

Для архивов:

1. dropmefiles.com
2. mediafire.com
3. drive.google.com

Метод 3: Артикуляции

```bash
# Windows (PowerShell)
Compress-Archive -Path "crash-reports/*", "logs/latest.log" -DestinationPath "logs.zip"

# Linux/macOS
zip -r logs.zip crash-reports/ logs/latest.log
```

🚨 Частые проблемы

Проблема 1: "Нет папки crash-reports"

```
Решение:
1. Запустите игру и спровоцируйте вылет
2. Проверьте настройки: Esc → Настройки → Дополнительно
3. Убедитесь, что "Включить вывод лога" активировано
```

Проблема 2: "Логи пустые или старые"

```bash
# Удалите старые логи и создайте новые
rm -rf ~/.minecraft/logs/latest.log
# Перезапустите игру
```

Проблема 3: "Файл слишком большой"

```bash
# Показать только последние ошибки (Linux/macOS)
tail -n 1000 latest.log > latest_short.log

# Или найти только ошибки
grep -i "error\|exception\|crash" latest.log > errors_only.log
```

❓ FAQ

Q: Какие логи нужны при проблеме с модами?

A: Все те же, но дополнительно:

· Скриншот папки mods/
· Версия Forge/Fabric (файл version.txt в папке игры)
· Список модов из лаунчера

Q: Как включить расширенное логирование?

A: Добавьте в аргументы JVM в лаунчере:

```
-Dforge.logging.console.level=debug -Dfabric.log.level=DEBUG
```

Q: Куда отправлять логи?

A:

1. Наш Discord: #техподдержка
2. Или администратору сервера
3. Не в ЛС без предварительного согласования

Q: Как быстро проверить, есть ли ошибки в логе?

A: Откройте файл и поищите:

· ERROR
· Exception
· Crash
· Красный текст

🔧 Дополнительные ресурсы

Полезные программы:

· LogViewer — просмотр логов Minecraft
· Notepad++ — просмотр больших текстовых файлов
· 7-Zip — работа с архивами

Онлайн-инструменты:

· Minecraft Log Analyzer — автоматический анализ логов
· Pastebin — обмен текстом
· Diffchecker — сравнение логов

Документация:

· Официальная Wiki Mojang
· Fabric Documentation
· Forge Documentation

📝 Шаблон обращения

```markdown
**Никнейм:** ВашНик
**Версия:** 1.21.10 Fabric
**Проблема:** Вылет при заходе в Незер
**Моды:** Sodium, Iris, Xaero's Minimap
**Логи:** [прикреплены файлы]
**Что делал:** Зашел в портал, игра зависла и закрылась
**Сервер:** (если проблема на сервере)
```

🤝 Как помочь проекту

Нашли ошибку в гайде или хотите добавить информацию?

1. Создайте Issue на GitHub
2. Или сделайте Pull Request с изменениями
3. Либо напишите в Discord

---

Автор: [MIMISSID]
Последнее обновление: 3 января 2025
Версия гайда: 2.1

Вернуться к началу

---

```Примечание: Этот гайд распространяется под лицензией MIT. Вы можете свободно использовать, модифицировать и распространять его с указанием авторства.```

