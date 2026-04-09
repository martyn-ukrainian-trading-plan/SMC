# SMC Trading Indicators

## Repo
- **Primary**: https://github.com/martyn-ukrainian-trading-plan/SMC (origin)
- **Backup**: https://github.com/peacepeacecreation/SMC (peacepeace)
- Push завжди в `origin` (martyn-ukrainian-trading-plan)

## Що тут
Pine Script індикатори для TradingView — SMC (Smart Money Concepts) торгова система.

## Структура
- `strategies/` — основні індикатори свінг-детекції
  - `swing-range.pine` — **Range STR** — головний індикатор з 3 станами: hasBOS, hasCallback, hasCHoCH
  - `swing-range2.pine` — робочий бекап Range STR (простіша версія з 2 станами)
  - `swing-abc.pine` — ABC свінг логіка
  - `swing-bos.pine` — BOS zigzag
  - `swing-detection.pine` — базовий pivot zigzag
- `time-of-weak.pine` — аналіз часу тижня
- `v.v1.pine`, `v-stats.v1.pine` — волатильність
- `volatility-news.pine`, `volatility-news-stats.pine` — волатильність + новини

## Мова
Спілкування українською. Код і коментарі — англійською.

## Правила
- Pine Script v6
- `overlay=true` для всіх індикаторів
- Тестування на BTC/USDT (Bybit), різні таймфрейми
- Не використовувати `ta.pivothigh`/`ta.pivotlow` для swing detection — власна логіка через BOS/retrace
- `confHigh`/`confLow` = confirmed діапазон для BOS детекції
- `swingHigh`/`swingLow` = provisional точки що трекаються в реальному часі
