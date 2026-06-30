Read the `hooks.json` file from the root of this repository. Then read the user's `~/.claude/settings.json` file.

Format of `hooks.json`:

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

Steps:

1. Create the directory `~/.claude/sounds/minecraft/` if it doesn't exist (use `mkdir -p`).
2. Copy every sound file from `sounds/minecraft/` in this repository to `~/.claude/sounds/minecraft/`.
3. Merge the `hooks` field from `hooks.json` into `~/.claude/settings.json`. If a `hooks` field already exists in `settings.json`, replace its value. If it doesn't exist, create it.

IMPORTANT: Do not modify any other fields in `settings.json`. Only change `hooks`.
