# nodumbmode

скиллы для агентов, собранные из реальных ошибок в проектах.

новый скилл появляется только после конкретного фейла. теоретические best
practices сюда не добавляются.

## что внутри

### nodumb

[nodumb](./nodumb/SKILL.md) — манифест здравого смысла для агента и набор правил
против типичных тупняков: сначала понять задачу, проверить масштаб и собрать
факты — потом писать код.

использовать перед нетривиальным кодом, массовой правкой и второй попыткой
отладки. на выходе — коротко: что известно, где риск, что делать дальше и как
проверить результат.

### changelog-discipline

[changelog-discipline](./changelog-discipline/SKILL.md) — ведёт changelog как
журнал решений: что поменялось, почему, как было раньше и что отвергли.

### system-feedback

[system-feedback](./system-feedback/SKILL.md) — проверяет, понятно ли
пользователю, что произошло после действия и что делать при ошибке.

### ask-nodumb

[ask-nodumb](./ask-nodumb/SKILL.md) — дизайн-консультант для продуктовых и
ux-задач. помогает увидеть скрытое предположение, разделить образ продукта,
модель и технологию

## установка

### с автообновлением

```bash
mkdir -p ~/.local/share
git clone --single-branch --depth 1 https://github.com/hronicasync/nodumbmode.git ~/.local/share/nodumbmode
~/.local/share/nodumbmode/setup --host all --auto-update
```

нужны `git`, `bash` и `python 3`.

`setup` ставит симлинки в codex и claude code. в начале сессии обновлятор не
чаще раза в час проверяет `main`, делает только fast-forward и молча оставляет
текущую версию при проблемах с сетью или локальных правках. в codex новый hook
нужно один раз подтвердить через `/hooks`.

обновить сразу:

```bash
~/.local/share/nodumbmode/bin/nodumbmode-update --force
```

### через skills cli

```bash
npx skills add hronicasync/nodumbmode -g -y -a codex -a claude-code --skill '*'
```

этот способ управляется самим `skills cli` и не ставит hook. обновление ручное:

```bash
npx skills update -g -y
```

в `skill.md` лежат основные правила, в `references/` — примеры и подробности.
