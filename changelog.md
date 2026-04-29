### 2026-04-29-v001:
- Make flashing depend on firmware existing
    - running `meson compile flash` will now build the firmware if it does not exist
### 2026-04-29-v002:
- Make sure compiler sanity checks are disabled, they do not play well with AVR
