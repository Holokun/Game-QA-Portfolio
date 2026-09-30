# Graphics

## Graphics Controls

### Quality
- Type: Spin box (left/right selector)
- Options: Not fully enumerated
- Current value: High
- Interaction: Left/right arrows cycle through available values

### Brightness
- Type: Slider
- Range: 0–100
- Current value: 50
- States: Default, Focused

### Bloom
- Type: Checkbox
- Values: Unchecked / Checked
- Current value: Checked

### Shadows
- Type: Checkbox
- Values: Unchecked / Checked
- Current value: Unchecked

### DLSS/FSR
- Type: Checkbox
- Values: Unchecked / Checked
- Current value: Unchecked

### Native Render Scale
- Type: Checkbox
- Values: Unchecked / Checked
- Current value: Unchecked

## Apply Changes

### Default
- Button is clickable when there are unapplied setting changes.

### Hover
- Mouse pointer is over the button while it is in the Default state.

### Disabled
- No unapplied changes are present, including after changes have been applied.

## Observed Behavior

- The Brightness slider displays its current value numerically.
- The slider becomes visually brighter when it is clicked/selected. This is documented as the **Focused** state.
- The Quality spin box uses left/right arrows to cycle through available values.

## Navigation

- `Back` → Settings

## Evidence

- [Graphics settings screenshot](../../Evidence/screenshots/graphics.png)
