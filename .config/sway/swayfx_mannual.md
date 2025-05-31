+ Window blur:
    - `blur enable|disable`
    - `blur_xray enable|disable`: this will set floating windows to blur based on the background, not the windows below. You probably want to set this to `disable` :)
    - `blur_passes <integer value 0 - 10>`
    - `blur_radius <integer value 0 - 10>`
    - `blur_noise <float value 0 - 1>`
    - `blur_brightness <float value 0 - 2>`
    - `blur_contrast <float value 0 - 2>`
    - `blur_saturation <float value 0 - 2>`
+ Corner radius: `corner_radius <val>`
+ Window shadows:
    - `shadows enable|disable`
    - `shadows_on_csd enable|disable` (**Note**: The shadow might not fit some windows)
    - `shadow_blur_radius <integer value 0 - 99>`
    - `shadow_color <hex color with alpha> ex, #0000007F`
    - `shadow_offset <x offset> <y offset>`
    - `shadow_inactive_color <hex color with alpha> ex, #0000007F`
+ LayerShell effects (to blur panels / notifications etc):
    - `layer_effects <layer namespace> <effects>`
    - The current layer namespaces can be shown with `swaymsg -r -t get_outputs | jq '.[0].layer_shell_surfaces | .[] | .namespace'`
    - Example: `layer_effects "waybar" blur enable; shadows enable; corner_radius 6`
      - Note: If an application uses gtk, its namespace is likely to be "gtk-layer-shell"
    - SwayIPC Example: `swaymsg layer_effects "waybar" "blur enable"` (you can only set one effect at a time through `swaymsg`)
    - Config Example:
        ```
        layer_effects "waybar" {
            blur enable;
            blur_xray enable;
            blur_ignore_transparent enable;
            shadows enable;
            corner_radius 20;
        }
        ```
    - Available Effects:
        - `blur <enable|disable>`
        - `blur_xray <enable|disable>`
        - `blur_ignore_transparent <enable|disable>`
        - `shadows <enable|disable>`
        - `corner_radius <int>`
        - `reset`: To reset/disable all previously applied effects to the layer application
+ Dim unfocused windows:
    - `default_dim_inactive <float value 0.0 - 1.0>`
    - `for_window [CRITERIA_HERE] dim_inactive <float value 0.0 - 1.0>`
    - `dim_inactive_colors.unfocused <hex color> ex, #000000FF`
    - `dim_inactive_colors.urgent <hex color> ex, #900000FF`
+ Keep/remove separator border between titlebar and content: `titlebar_separator enable|disable`
+ Treat Scratchpad as minimized: `scratchpad_minimize enable|disable`: **we recommend keeping this setting off, as there are many kinks to iron out here**
