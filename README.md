# Mihomo Rule Sets

Коллекция правил для ядра [mihomo](https://github.com/MetaCubeX/mihomo) (ранее Clash Meta).

## Описание

Этот репозиторий содержит наборы правил для настройки прокси-сервера mihomo. Правила организованы по категориям и предназначены для различных сценариев использования.

## Доступные наборы правил

### 🎮 games-direct.yaml
Набор правил для игр, которые должны работать напрямую (DIRECT). Включает:
- Популярные игры: Apex Legends, PUBG, Counter-Strike 2, Valorant, Dota 2, GTA V и др.
- Игровые лаунчеры: Steam, Epic Games, Ubisoft Connect, Rockstar Social Club
- Античиты: Easy Anti-Cheat, BattleEye, Vanguard
- Сетевые порты для игр

### 🤖 ai-set.yaml
Набор правил для AI-сервисов и связанных доменов:
- OpenAI (ChatGPT)
- Anthropic (Claude)
- Google AI сервисы
- Amazon AI
- MongoDB Atlas
- Canva
- Cursor IDE
- Grok

### 🇷🇺 ru-inline.yaml
Набор правил для российских доменов и сервисов:
- Яндекс сервисы
- ВКонтакте
- Российские домены (.ru, .su, .by)
- Популярные российские сервисы (Avito, Ozon, Wildberries)
- Стриминговые платформы (Premier, Okko, Wink)

### 🚫 ru-inline-banned.yaml
Набор правил для заблокированных в России ресурсов:
- Habr
- Аниме сайты
- Snapchat
- Другие заблокированные ресурсы

## Использование

### Добавление в конфигурацию mihomo

Добавьте rule-providers в ваш конфиг:

```yaml
rule-providers:
  games-direct:
    type: http
    behavior: classical
    format: yaml
    url: https://github.com/SawGoD/mihomo-rule-sets/blob/main/data/yaml/games-direct.yaml
    path: ./rule-sets/games-direct.yaml
    interval: 86400

  ai-set:
    type: http
    behavior: classical
    format: yaml
    url: https://github.com/SawGoD/mihomo-rule-sets/blob/main/data/yaml/ai-set.yaml
    path: ./rule-sets/ai-set.yaml
    interval: 86400

  ru-inline:
    type: http
    behavior: classical
    format: yaml
    url: https://github.com/SawGoD/mihomo-rule-sets/blob/main/data/yaml/ru-inline.yaml
    path: ./rule-sets/ru-inline.yaml
    interval: 86400

  ru-inline-banned:
    type: http
    behavior: classical
    format: yaml
    url: https://github.com/SawGoD/mihomo-rule-sets/blob/main/data/yaml/ru-inline-banned.yaml
    path: ./rule-sets/ru-inline-banned.yaml
    interval: 86400
```

### Добавление правил

```yaml
rules:
  # Игры - прямое подключение
  - RULE-SET,games-direct,DIRECT
  
  # AI сервисы - через прокси
  - RULE-SET,ai-set,PROXY
  
  # Российские сервисы - прямое подключение
  - RULE-SET,ru-inline,DIRECT
  
  # Заблокированные ресурсы - через прокси
  - RULE-SET,ru-inline-banned,PROXY
  
  # Остальной трафик
  - MATCH,PROXY
```

## Обновление правил

Правила обновляются автоматически каждые 24 часа (86400 секунд). Вы можете изменить интервал обновления в параметре `interval`.

## Вклад в проект

Если вы хотите добавить новые правила или улучшить существующие:

1. Создайте форк репозитория
2. Внесите изменения в соответствующие YAML файлы
3. Создайте Pull Request с описанием изменений

## Лицензия

Этот проект распространяется под лицензией MIT. См. файл LICENSE для подробностей.

## Поддержка

Если у вас есть вопросы или предложения, создайте Issue в репозитории.
