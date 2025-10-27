# ARMT VPN

<div align="center">
  <img src="attached_assets/81018241-4148-45FC-B3A9-EDFFD93CCAB3_1761563132226.png" width="300" alt="ARMT VPN Logo">
  
  **Графическое приложение для подключения к VLESS серверам**
  
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
  [![Python 3.6+](https://img.shields.io/badge/python-3.6+-blue.svg)](https://www.python.org/downloads/)
  [![GTK 3.0](https://img.shields.io/badge/GTK-3.0-green.svg)](https://www.gtk.org/)
</div>

---

## 📋 Описание

ARMT VPN - это современное desktop-приложение с красивым графическим интерфейсом в синих и черных тонах для управления VLESS подключениями. Приложение позволяет легко импортировать конфигурации из буфера обмена или сканировать QR-коды для быстрого добавления серверов.

## ✨ Возможности

- 🎨 **Красивый интерфейс** - современный дизайн в синих и черных тонах
- 📋 **Импорт из буфера обмена** - вставьте VLESS URL и сразу используйте
- 📷 **Сканирование QR-кодов** - импорт конфигураций через камеру
- 💾 **Управление конфигурациями** - сохранение и организация нескольких серверов
- 🔒 **Безопасность** - поддержка VLESS протокола с различными типами шифрования
- 🚀 **Простота использования** - интуитивный интерфейс на русском языке

## 🖼️ Скриншоты

Приложение вдохновлено дизайном:

<div align="center">
  <img src="attached_assets/AF72195D-CE59-49AC-A320-787DCFEF27A8_1761563132226.png" width="250" alt="Design 1">
  <img src="attached_assets/IMG_3557_1761563132226.png" width="400" alt="Design 2">
</div>

## 📦 Установка

### Системные требования

- Ubuntu 20.04+ / Debian 11+ или другой Linux дистрибутив с GTK 3
- Python 3.6 или выше
- Веб-камера (для сканирования QR-кодов)

### Установка из .deb пакета

1. **Скачайте готовый .deb пакет** или соберите его сами (см. раздел "Сборка")

2. **Установите пакет:**
   ```bash
   sudo dpkg -i armt-vpn_1.0.0_all.deb
   ```

3. **Если возникли проблемы с зависимостями:**
   ```bash
   sudo apt-get install -f
   ```

4. **Запустите приложение:**
   ```bash
   armt-vpn
   ```
   
   Или найдите "ARMT VPN" в меню приложений

### Установка из исходного кода

1. **Клонируйте репозиторий или скачайте файлы**

2. **Установите системные зависимости:**
   ```bash
   sudo apt-get update
   sudo apt-get install -y python3 python3-pip python3-gi gir1.2-gtk-3.0 \
       python3-pil python3-opencv python3-pyzbar python3-qrcode \
       python3-pyperclip zbar-tools
   ```

3. **Установите Python зависимости:**
   ```bash
   pip3 install -r requirements.txt
   ```

4. **Запустите приложение:**
   ```bash
   cd src
   python3 main.py
   ```

## 🔨 Сборка .deb пакета

### Установка инструментов сборки

```bash
sudo apt-get install -y dpkg-dev debhelper dh-python devscripts
```

### Сборка пакета

1. **Дайте права на выполнение скрипту сборки:**
   ```bash
   chmod +x build_deb.sh
   ```

2. **Запустите сборку:**
   ```bash
   ./build_deb.sh
   ```

3. **После успешной сборки вы получите файл:**
   ```
   armt-vpn_1.0.0_all.deb
   ```

## ⚙️ Установка Xray-core

**Важно!** Для работы приложения требуется установленный Xray-core - это движок для подключения к VLESS серверам.

### Быстрая установка Xray-core:

```bash
sudo bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```

### Проверка установки:

```bash
xray version
```

Если команда выводит версию Xray, значит установка прошла успешно.

### Альтернативная установка:

Вы также можете установить Xray-core вручную:

1. Скачайте последнюю версию с [GitHub Releases](https://github.com/XTLS/Xray-core/releases)
2. Распакуйте архив и поместите исполняемый файл `xray` в `/usr/local/bin/` или `~/.local/bin/`
3. Дайте права на выполнение: `chmod +x /usr/local/bin/xray`

## 📖 Использование

### Добавление конфигурации из буфера обмена

1. Скопируйте VLESS URL в буфер обмена (например: `vless://uuid@server:port?params#name`)
2. Нажмите кнопку **"📋 Из буфера"**
3. Конфигурация автоматически добавится в список

### Сканирование QR-кода

1. Нажмите кнопку **"📷 Сканировать QR"**
2. Наведите QR-код с VLESS конфигурацией на камеру
3. После распознавания конфигурация добавится автоматически
4. Нажмите `Q` для выхода из режима сканирования

### Подключение к серверу

1. Убедитесь, что Xray-core установлен (см. раздел "Установка Xray-core")
2. Выберите конфигурацию из списка
3. Нажмите кнопку **"Подключиться"**
4. После успешного подключения появится информация о локальных портах прокси:
   - **SOCKS5**: `socks5://127.0.0.1:10808`
   - **HTTP**: `http://127.0.0.1:10809`
5. Настройте ваш браузер или систему на использование этих прокси

### Настройка прокси в системе

**Ubuntu/GNOME:**
1. Откройте Настройки → Сеть → Прокси
2. Выберите "Ручная настройка"
3. Введите:
   - HTTP-прокси: `127.0.0.1:10809`
   - HTTPS-прокси: `127.0.0.1:10809`
   - Socks-прокси: `127.0.0.1:10808`

**Firefox:**
1. Настройки → Основные → Параметры сети → Настроить
2. Выберите "Ручная настройка прокси"
3. Введите:
   - SOCKS Host: `127.0.0.1`, Порт: `10808`
   - Выберите "SOCKS v5"

### Удаление конфигурации

1. Найдите нужную конфигурацию в списке
2. Нажмите кнопку **🗑** справа от конфигурации
3. Подтвердите удаление

## 🔧 Формат VLESS URL

Приложение поддерживает стандартный формат VLESS URL:

```
vless://UUID@SERVER:PORT?type=tcp&security=tls&sni=example.com#ConfigName
```

### Поддерживаемые параметры:

- `type` - тип транспорта (tcp, ws, grpc, etc.)
- `security` - безопасность (none, tls, reality)
- `encryption` - шифрование
- `sni` - Server Name Indication
- `alpn` - Application-Layer Protocol Negotiation
- `flow` - управление потоком
- `host` - заголовок Host
- `path` - путь для WebSocket
- `serviceName` - имя сервиса для gRPC

## 📁 Структура проекта

```
armt-vpn/
├── src/                          # Исходный код приложения
│   ├── main.py                   # Главное приложение GTK
│   ├── vless_parser.py           # Парсер VLESS конфигураций
│   ├── qr_handler.py             # Обработчик QR-кодов
│   ├── xray_manager.py           # Менеджер Xray-core
│   └── style.css                 # Стили интерфейса
├── debian/                       # Файлы для сборки .deb
│   ├── control                   # Метаданные пакета
│   ├── rules                     # Правила сборки
│   ├── changelog                 # История изменений
│   └── compat                    # Версия совместимости
├── attached_assets/              # Ресурсы (логотипы, иконки)
├── setup.py                      # Установочный скрипт Python
├── armt-vpn.desktop              # Desktop entry файл
├── build_deb.sh                  # Скрипт автоматической сборки
├── requirements.txt              # Python зависимости
└── README.md                     # Эта документация
```

## 🔐 Конфигурация

Приложение сохраняет конфигурации в:
```
~/.config/armt-vpn/configs.json
```

Этот файл содержит все сохраненные VLESS конфигурации в формате JSON.

## 🐛 Решение проблем

### Приложение не запускается

1. Проверьте установку зависимостей:
   ```bash
   python3 -c "import gi; gi.require_version('Gtk', '3.0'); from gi.repository import Gtk"
   ```

2. Проверьте наличие display:
   ```bash
   echo $DISPLAY
   ```

### Не удается подключиться

1. Убедитесь, что Xray-core установлен:
   ```bash
   xray version
   ```

2. Проверьте правильность VLESS конфигурации
3. Проверьте логи приложения в консоли
4. Убедитесь, что порты 10808 и 10809 свободны

### Камера не работает

1. Проверьте права доступа к камере
2. Убедитесь, что камера не используется другим приложением
3. Проверьте установку opencv:
   ```bash
   python3 -c "import cv2; print(cv2.__version__)"
   ```

### QR-коды не распознаются

Установите дополнительные инструменты:
```bash
sudo apt-get install zbar-tools libzbar0
```

## 🛠️ Разработка

### Требования для разработки

```bash
sudo apt-get install python3-dev libgtk-3-dev pkg-config \
    libcairo2-dev libgirepository1.0-dev
```

### Запуск в режиме разработки

```bash
cd src
python3 main.py
```

## 📝 Лицензия

Этот проект распространяется под лицензией MIT. См. файл LICENSE для деталей.

## 🤝 Вклад в проект

Если вы хотите внести вклад в проект:

1. Форкните репозиторий
2. Создайте ветку для новой функции (`git checkout -b feature/AmazingFeature`)
3. Закоммитьте изменения (`git commit -m 'Add some AmazingFeature'`)
4. Запушьте ветку (`git push origin feature/AmazingFeature`)
5. Откройте Pull Request

## 📧 Контакты

ARMT VPN Team - support@armt-vpn.local

---

<div align="center">
  Сделано с ❤️ для сообщества
</div>
