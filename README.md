# claude-code-spinner — zoomer / gamedev edition

A fork of [i1kazantsev/claude-code-spinner](https://github.com/i1kazantsev/claude-code-spinner).

**What changed:**

- **Phrases** — replaced the businessman slang with a gaming / gamedev / dev-pain set (`Изи катка`, `ГГ ВП`, `Пинг 300`, `Хуяк хуяк и в продакшн`, `На моей машине работает`, `Никогда не копай вниз!`, `Домик из грязи`, …). 76 in total.
- **Stop-hook sound** — instead of one fixed clip, a **random** Minecraft villager / pillager / trader "Hmm" plays each time the agent finishes (22 `.ogg` files in `sounds/minecraft/`).

## Install via Claude Code

```bash
git clone https://github.com/shimkovich/claude-code-spinner.git
cd claude-code-spinner
```

Then run in Claude Code:

```
/install-spinner
/install-hook
```

## Manual install

**Phrases** — copy `spinnerVerbs` from `spinners.json` into `~/.claude/settings.json`.

**Sound** — copy `sounds/minecraft/` to `~/.claude/sounds/minecraft/` and add the `hooks` block from `hooks.json` to `~/.claude/settings.json`:

```json
{
  "hooks": {
    "Stop": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "f=(~/.claude/sounds/minecraft/*.ogg); afplay -v 1 \"${f[$RANDOM % ${#f[@]}]}\""
          }
        ]
      }
    ]
  }
}
```

The command picks a random `.ogg` on every response — add or remove files freely. Lower `-v 1` to `-v 0.5` if it's too loud.

## License

MIT, same as the original. Phrases & idea: [i1kazantsev/claude-code-spinner](https://github.com/i1kazantsev/claude-code-spinner). Sounds: Mojang / Minecraft.
