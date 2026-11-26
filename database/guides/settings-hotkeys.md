# Settings, Hotkeys & Performance

> Sources: [Fextralife Controls](https://pathofexile2.wiki.fextralife.com/Controls), [official forum performance thread](https://www.pathofexile.com/forum/view-thread/3800105). Movement rules: [mechanics/movement-controls.md](../mechanics/movement-controls.md)

## Controls

- **WASD is the default** movement mode (Settings → Input) — aim stays on cursor; click-to-move remains selectable. Pick one and stick with it.
- **Attack in Place**: default bind **Shift**; also per-skill via Skills menu → skill → **Skill Options → Attack in Place**.
- **"Always Attack without Moving"**: recommended — skill button attacks under cursor instead of walking there.
- **Dodge roll**: default **Space** (rebindable); direction follows WASD. Known quirk: roll can track the cursor if WASD released mid-roll.
- Smart cast / QWER-style systems: not present as dedicated modes `(unconfirmed)` — use per-skill Skill Options.

## QoL settings

| Setting | Recommendation |
|---|---|
| Item labels | **Alt** reveals; **Z** toggles always-show; set "Toggle Label Visibility" → **Permanent**; enable "Use Highlight Key to pick up loot" |
| Health bars | "Always Highlight" → **Enemies Only**; "Show Mini Life Bar Above You" |
| Minimap | Enable edge minimap in UI options |
| Loot pickup | **No loot vacuum exists**; gold auto-picks on walk-over (radius not configurable) |

## Performance (endgame: Breach/Delirium)

Heaviest settings, in order of FPS cost:

1. **Global Illumination** — largest single cost
2. **Shadows**
3. **Effects** — particle spam in Breach/Delirium is the main killer

Common fixes (community-verified):

!!! tip "Stutter fix after patches"
    Clear **ShaderCache** in `%APPDATA%\Path of Exile 2` (game closed) when stutters start after patches. Setting **NVIDIA Shader Cache Size to 100 GB / Unlimited** and adding the shader/cache folder to **Windows Defender exclusions** further reduces recompiles.

- Switch renderer to **Vulkan**; enable **DLSS/FSR** upscaling; update GPU drivers.
- Set **NVIDIA Shader Cache Size to 100 GB / Unlimited**.
- Add the shader/cache folder to **Windows Defender exclusions**.
- Switch renderer to **Vulkan**; enable **DLSS/FSR** upscaling; update GPU drivers.
