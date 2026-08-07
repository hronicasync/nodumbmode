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

нужен `node`. флаги: `-g` глобально, `-y` без вопросов, `--skill '*'` все скиллы,
`-a` куда ставить.

**claude code и codex сразу**

```bash
npx skills@latest add hronicasync/nodumbmode -g -y -a claude-code -a codex --skill '*'
```

**только claude code**

```bash
npx skills@latest add hronicasync/nodumbmode -g -y -a claude-code --skill '*'
```

**только codex**

```bash
npx skills@latest add hronicasync/nodumbmode -g -y -a codex --skill '*'
```

**выбрать вручную** — без `-a` и `-y` cli спросит, куда ставить и какие скиллы:

```bash
npx skills@latest add hronicasync/nodumbmode -g
```

`--all` не использовать: он пытается поставить во всех известных агентов, включая
тех, кто не умеет глобальную установку, и валится с ошибками на каждом.

## обновление

```bash
npx skills@latest update -g -y
```

тянет свежую версию из репы. переустанавливать не нужно — cli помнит источник.

<details>
<summary>если скиллы не появились в codex</summary>

`skills cli` кладёт файлы в `~/.agents/skills/`, но иногда не связывает их с
codex. разово:

```bash
for s in nodumb ask-nodumb changelog-discipline system-feedback; do
  ln -sfn ~/.agents/skills/$s ~/.codex/skills/$s
done
```

симлинки, а не копии — обновление через `skills update` подхватится само.

</details>

в `SKILL.md` лежат основные правила, в `references/` — примеры и подробности.
