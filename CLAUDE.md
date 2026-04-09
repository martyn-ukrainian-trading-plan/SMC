# SMC Trading Indicators

## Git
- **Origin**: https://github.com/martyn-ukrainian-trading-plan/SMC
- **Backup remote**: peacepeace (https://github.com/peacepeacecreation/SMC)
- Push завжди в `origin`
- **ОБОВ'ЯЗКОВО**: коміти тільки від автора `martyn-ukrainian-trading-plan <martyn.trading.plan@gmail.com>`. Ніколи не комітити як `peacepeacecreation`. Перед комітом перевірити `git config user.name`.

## Що тут
Pine Script індикатори для TradingView — SMC (Smart Money Concepts) торгова система.

## Структура
- `strategies/swing-range.pine` — **Range STR** — головний індикатор з 3 станами: hasBOS, hasCallback, hasCHoCH
- `time-of-weak.pine` — аналіз часу тижня
- `volatility-news-stats.pine` — волатильність + новини
- `strategies/tmp/` — архів старих swing варіантів
- `tmp/` — архів старих індикаторів волатильності

## Мова
Спілкування українською. Код і коментарі — англійською.

## Правила
- Pine Script v6
- `overlay=true` для всіх індикаторів
- Тестування на BTC/USDT (Bybit), різні таймфрейми
- Не використовувати `ta.pivothigh`/`ta.pivotlow` для swing detection — власна логіка через BOS/retrace
- `confHigh`/`confLow` = confirmed діапазон для BOS детекції
- `swingHigh`/`swingLow` = provisional точки що трекаються в реальному часі
