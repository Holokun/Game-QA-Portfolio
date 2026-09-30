# Display

## Display Controls

### Window Mode
- Type: Spin box (left/right selector)
- Options: Not fully enumerated
- Current value: Borderless
- Interaction: Left/right arrows cycle through available values

### Resolution
- Type: Spin box (left/right selector)
- Options: Not fully enumerated
- Current value: 1920 × 1200
- Interaction: Left/right arrows cycle through available values

### FPS Limit
- Type: Spin box (left/right selector)
- Range: 30–360, Unlimited
- Current value: 60
- Interaction: Left/right arrows cycle through available values

### V-Sync
- Type: Checkbox
- Values: Unchecked / Checked
- Current value: Unchecked

### Camera Shake Intensity
- Type: Slider
- Range: 0–100
- Current value: 100
- States: Default, Focused

### Field of View
- Type: Slider
- Range: 0–100
- Current value: 80
- States: Default, Focused

## Apply Changes

### Default
- Button is clickable when there are unapplied setting changes.

### Hover
- Mouse pointer is over the button while it is in the Default state.

### Disabled
- No unapplied changes are present, including after changes have been applied.

## Observed Behavior

- Sliders display their current values numerically.
- A slider becomes visually brighter when it is clicked/selected. This is documented as the **Focused** state.
- Spin boxes use left/right arrows to cycle through available values.

## Navigation

- `Back` → Settings

## Evidence

- [Display settings screenshot](../../Evidence/screenshots/display.png)
