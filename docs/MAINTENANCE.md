# Maintenance Notes

This repository is the Stylisk-maintained fork of:

- Upstream: https://github.com/kkqq9320/ha-xiaomi-clock-time-fixer
- Fork: https://github.com/stylisk/ha-xiaomi-clock-time-fixer-stylisk
- Local working folder: `/Users/jeong/Dropbox/Repositories/ha-xiaomi-clock-time-fixer-stylisk`

The Home Assistant integration domain remains `xiaomi_clock_lywsd02`.
That keeps existing automations compatible with `xiaomi_clock_lywsd02.set_time`.

## Current Local Improvements

- `timeout` is now enforced as a per-device total update timeout.
- Dynamic timestamps are generated after BLE connection succeeds, immediately before the time GATT write.
- Manifest, HACS metadata, translations, and README identify this as the Stylisk fork to avoid confusing it with upstream.

## Remotes

```sh
git remote -v
```

Expected:

- `origin`: `https://github.com/stylisk/ha-xiaomi-clock-time-fixer-stylisk.git`
- `upstream`: `https://github.com/kkqq9320/ha-xiaomi-clock-time-fixer.git`

## Updating From Upstream

```sh
git fetch upstream
git log --oneline --decorate --graph --all --max-count=30
git merge upstream/main
```

Resolve conflicts carefully. Keep the timeout and late timestamp behavior unless a newer upstream release provides an equivalent fix.

## Home Assistant Install Path

The deployed integration folder is:

```text
/config/custom_components/xiaomi_clock_lywsd02
```

Before replacing the installed copy, back it up under:

```text
/config/custom_components_backups/
```

After deployment, restart Home Assistant Core because custom integration Python code is imported at startup.
