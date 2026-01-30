<p align="center">
  <img src="../banner.png" width="100%" alt="BobiVPN Banner"/>
</p>

<h1 align="center">🦀 VPN Checker — Rust Edition 🦀</h1>

<p align="center">
  <b>Сверхбыстрая проверка VPN ключей</b><br>
  <i>32K ключей за 1-2 часа • Sing-box проверка • 1:1 с Python версией</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Rust-🦀-orange?style=for-the-badge" alt="Rust">
  <img src="https://img.shields.io/badge/Speed-⚡_20x_Faster-green?style=for-the-badge" alt="Speed">
  <img src="https://img.shields.io/badge/Sing--box-Integration-purple?style=for-the-badge" alt="Sing-box">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/VLESS-Reality%20%7C%20TLS%20%7C%20WS-blue?style=flat-square" alt="VLESS">
  <img src="https://img.shields.io/badge/VMess-WebSocket%20%7C%20gRPC-green?style=flat-square" alt="VMess">
  <img src="https://img.shields.io/badge/Trojan-TLS-orange?style=flat-square" alt="Trojan">
  <img src="https://img.shields.io/badge/Shadowsocks-AEAD-red?style=flat-square" alt="SS">
  <img src="https://img.shields.io/badge/Hysteria2-UDP-cyan?style=flat-square" alt="Hysteria2">
</p>

---

## ⚡ Почему Rust?

<table>
<tr>
<td width="50%" valign="top">

### 🐍 Python версия
- 32K ключей: **32-53 часа**
- Параллельность: 50 (GIL ограничение)
- RAM: ~2GB
- CPU: 1 ядро

</td>
<td width="50%" valign="top">

### 🦀 Rust версия
- 32K ключей: **1-2 часа**
- Параллельность: 1000+ (tokio)
- RAM: ~500MB
- CPU: Все ядра

</td>
</tr>
</table>

> [!TIP]
> **Ускорение 20-30x** при той же точности проверки!

---

## 🚀 Быстрый старт

### Скачать готовый бинарник

```bash
# Linux
wget https://github.com/ginolrewadsb11/studious-umbrella/releases/download/latest/vpn_checker-linux-amd64
chmod +x vpn_checker-linux-amd64
./vpn_checker-linux-amd64
```

### Использование

```bash
# Создай файл subscriptions.txt с URL подписок
echo "https://example.com/subscription.txt" > subscriptions.txt

# Запусти проверку
./vpn_checker
```

---

## 📁 Структура

```
vpn_checker_bin/
├── .github/
│   └── workflows/
│       └── vpn-checker.yml  # 🔄 GitHub Actions
├── scripts/
│   └── vpn_checker          # 🦀 Скомпилированный бинарник
├── subscriptions.txt        # 📋 Список URL подписок
└── README.md                # 📖 Документация
```

---

## 🔧 Как это работает

```mermaid
graph LR
    A[📥 Загрузка] --> B[🔌 TCP Ping]
    B --> C[⚙️ Sing-box]
    C --> D[🌍 IP Check]
    D --> E[📊 Speed Test]
    E --> F[✅ Рабочие]
    F --> G[📤 Публикация]
    
    style A fill:#4CAF50,color:#fff
    style F fill:#2196F3,color:#fff
    style G fill:#9C27B0,color:#fff
```

| Этап | Описание |
|------|----------|
| **1. TCP Ping** | Отсеиваем мёртвые серверы за миллисекунды |
| **2. Sing-box** | Полная проверка через локальный прокси |
| **3. IP Check** | Проверяем что exit IP изменился |
| **4. Speed Test** | Измеряем скорость загрузки |

---

## 📊 Выходные файлы

| Файл | Описание |
|------|----------|
| `vpn.txt` | Оригинальные рабочие ключи |
| `vpn_renamed.txt` | С красивыми именами (🇷🇺 Russia \| ISP 1) |
| `bobi_vpn.txt` | Для Happ (с заголовком подписки) |
| `bobi_vpn_lite.txt` | Lite версия (RU/DE/FR/FI/EE/LV/LT) |
| `vpn_report.json` | JSON отчёт с метаданными |
| `countries/*.txt` | Подписки по отдельным странам |

---

## ⚙️ Конфигурация

Настройки в коде (менять при пересборке):

```rust
pub const TIMEOUT_TCP: u64 = 5;          // Таймаут TCP пинга (сек)
pub const TIMEOUT_PROXY: u64 = 25;       // Таймаут проверки прокси
pub const MAX_CONCURRENT: usize = 50;    // Параллельных проверок
pub const MAX_LATENCY_MS: u64 = 3000;    // Максимальный пинг (мс)
pub const MIN_SPEED_KBPS: f64 = 50.0;    // Минимальная скорость
```

---

## 🔨 Сборка из исходников

### Требования
- Rust 1.70+
- sing-box в PATH

### Сборка

```bash
cd ../vpn_checker_rust
cargo build --release
cp target/release/vpn_checker ../vpn_checker_bin/
```

---

## 🌍 Поддерживаемые страны

<p align="center">
🇷🇺 Россия • 🇩🇪 Германия • 🇳🇱 Нидерланды • 🇫🇮 Финляндия • 🇸🇪 Швеция<br>
🇵🇱 Польша • 🇫🇷 Франция • 🇬🇧 Великобритания • 🇺🇸 США • 🇰🇿 Казахстан<br>
🇱🇹 Литва • 🇱🇻 Латвия • 🇪🇪 Эстония • 🇨🇭 Швейцария • 🇦🇹 Австрия<br>
🇹🇷 Турция • 🇮🇱 Израиль • 🇯🇵 Япония • 🇸🇬 Сингапур • 🇭🇰 Гонконг
</p>

---

## ⚠️ Требования

- **sing-box** должен быть установлен и доступен в PATH
- **subscriptions.txt** с URL подписок (по одному на строку)

### Установка sing-box

```bash
# Linux
wget -qO- https://github.com/SagerNet/sing-box/releases/download/v1.8.0/sing-box-1.8.0-linux-amd64.tar.gz | tar xz
sudo mv sing-box-1.8.0-linux-amd64/sing-box /usr/local/bin/
```

---

<p align="center">
  <b>⭐ Поставь звезду если полезно!</b>
</p>

<p align="center">
  <sub>Made with 🦀 by BobiVPN Team</sub>
</p>
