# industry-design

Скилл-директор для Cursor, Claude Code и Codex. Он не рисует «современный интерфейс вообще». Сначала он выясняет отрасль и цель, сверяется с живыми стилями на [Refero Styles](https://styles.refero.design/), и только потом зовёт узкие скиллы на их участок работы.

Канонический файл: `skills/industry-design/SKILL.md`.

## Как это устроено

Чужие `SKILL.md` в этот репозиторий не скопированы. У них разные правила, и если сложить их в один файл, агент получает несколько начальников. Этот скилл задаёт порядок и ставит зависимости в проект, который вы дизайните.

Порядок такой:

1. Один пакет вопросов, затем пауза.
2. Референсы из Refero: стили, а для экранов и сценариев ещё screens и flows. Один основной стиль, без усреднения.
3. Структура лендинга и текст — `landing-page-design`. Кадры продукта — `stageshow`. Проверка на шаблонность — `frontend-design`. Перед сдачей — `web-design-guidelines`.
4. Жёсткая визуальная система `landing-page-design` (Geist, фиксированная тёмная палитра, запрет фоновых градиентов) включается только если нет ни бренда проекта, ни выбранного стиля Refero.

Подробности конфликтов: `skills/industry-design/references/precedence.md`.

## Установка

Из каталога проекта, который нужно дизайнить:

```bash
npx skills add <этот-репозиторий> --skill industry-design -y
```

Пока репозиторий только локальный:

```bash
npx skills add C:/Users/1/Projects/industry-design --skill industry-design -a cursor -y
```

Агент сам доставит недостающие скиллы из `references/companions.md`. Поставить ядро вручную:

```bash
npx skills add benjitaylor/skills --skill stageshow
npx skills add elayadesign/ai-design-skills --skill landing-page-design
npx skills add https://github.com/referodesign/refero_skill --skill refero-design
npx skills add anthropics/skills --skill frontend-design
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
```

Claude Code кладёт скиллы в `.claude/skills`. Для лендинга используйте формулировку из `companions.md`. Codex может поставить тот же набор через `-a codex`. Если Codex нужен именно текстом, содержимое `SKILL.md` скилла `landing-page-design` добавляется в `AGENTS.md` проекта. `stageshow` и `refero-design` так не вставляют: им нужны соседние папки `references/`.

## Refero

Стили — источник того, что сейчас выглядит актуально в категории. Подключение MCP:

```json
{
  "mcpServers": {
    "refero": {
      "url": "https://api.refero.design/mcp"
    }
  }
}
```

Файл: `.cursor/mcp.json` проекта. При первом запросе клиент попросит войти. Без MCP агент читает страницы стилей и их `DESIGN.md` и прямо пишет, что исследование было ручным.

## Что ещё смотрел

В ядро вошло то, что закрывает разные дыры и почти не спорит друг с другом.

| Скилл | Зачем в ядре |
| --- | --- |
| `refero-design` | Метод: сначала референсы, потом лок, без копирования одного сайта |
| `landing-page-design` | Оффер, секции, конверсия, честный текст |
| `stageshow` | Правдоподобный интерфейс в хиро и на карточках, а не серый мокап |
| `frontend-design` | Запрет на вид, который подойдёт любой компании |
| `web-design-guidelines` | Доступность и поведение интерфейса перед сдачей |

Ставятся только под задачу, не вместе со всем ядром:

| Скилл | Когда |
| --- | --- |
| `redesign-existing-projects` | Уже есть сайт, и его надо разобрать, а не переписать с нуля |
| `emil-design-eng` | Движение в настоящем интерфейсе. На фейковый демо-ролик его не ставят, там `stageshow` |
| `ui-ux-pro-max` | Каталог паттернов сложного UI. Палитру и шрифт из него не берут, если лок уже есть |
| `impeccable` и `polish` | Последний проход по уже собранному экрану. Их `frontend-design` не ставить: это устаревший псевдоним и он столкнётся со скиллом Anthropic |
| `better-interface` | Сводка замечаний: доступность, сетка, текст, тип, цвет |
| `figma-designer` | Результат нужен файлом в Figma |
| `apple-design` | Принципы нативного интерфейса, в том числе iOS |
| `mobile-native` | Мобильный веб, который должен ощущаться как приложение |

Смотрел и не ставил в ядро: `design-taste-frontend` и `high-end-visual-design` (их идеи уже внутри `landing-page-design`), `canvas-design` (холст, не продукт), `vercel-composition-patterns` и `vercel-react-best-practices` (структура и скорость React, не вкус), `sleek-design-mobile-apps` (платный API Sleek, а не ремесло). Остальные команды `impeccable` (`bolder`, `quieter`, `delight`, `distill`, `critique`) толкают один экран в разные стороны, поэтому в работу берётся один проход, если лок уже соблюдён, а экран всё ещё сырой.

## Как просить

Обычным языком, в проекте продукта, не в этом репозитории:

```text
Собери лендинг для продукта. Используй скилл industry-design.
```

Агент сначала задаст вопросы одним сообщением. После ответов он назовёт референсы и зафиксирует направление до кода.

## Лицензии

Текст этого скилла можно использовать, менять и распространять. Скиллы из чужих репозиториев остаются под лицензиями авторов. `landing-page-design` опубликован под MIT. У `stageshow` своя лицензия внутри пакета. Этот репозиторий их код не содержит.
