# Sanctuary

## Entry Flow

- `New Game` opens the Squad hint before the Sanctuary can be used.
- The Sanctuary is the squad-management screen shown before starting a mission.

## Squad Hint

### Hint Window
- Type: Modal window
- States: Default
- The Sanctuary screen is dimmed while the hint is open.
- The hint explains the following rules:
  - Up to 3 heroes can be selected for a mission.
  - The game has 6 squad heroes.
  - A squad slot can be clicked to assign a hero.
  - Additional heroes are unlocked through progression.
  - Hero death is permanent.

### Continue
- Type: Button
- States: Default, Hover
- Action: Closes the hint and opens the Sanctuary screen.

### Disable Hints
- Type: Checkbox
- States: Default, Hover
- Values: Unchecked / Checked
- Current value in captured state: Unchecked

## Character Portraits

- Character portrait hexagons are displayed along the left and right sides of the Sanctuary.
- Type: Button
- States: Default, Hover
- Action: Opens the selected character's information screen.

## Character Information

### Information Panel
- Displays the selected character's portrait and name.
- Displays character information such as:
  - Born
  - Country
  - Class
- Displays a biography/lore section.
- A vertical scrollbar is present for the text area.

### Back
- Type: Button
- States: Default, Hover
- Action: Returns to the Sanctuary screen.

## Squad

### Squad Slots
- Number of slots: 3
- A slot can be either occupied by a selected hero or empty.
- An occupied slot displays the selected hero's portrait.
- An empty slot displays a silhouette with a `+` icon.
- Interactive states: Default, Hover

### Empty Squad Slot
- Type: Button
- States: Default, Hover
- Action: Opens the hero-selection interface.

## Hero Selection

### Hero Cards
- Total squad heroes shown: 6
- Each hero is represented by a square portrait card.
- States observed:
  - Available
  - Selected
  - Locked
  - Hover

### Current Progression State
- 2 heroes are currently available.
- 4 heroes are currently locked.
- In the captured state, both available heroes are already assigned to the squad when the hero-selection interface is opened.
- Locked heroes display a padlock icon.

### Selected Hero
- Clicking a hero who is already assigned to the squad displays an `X` control on that hero's card.
- The `X` control can be used to remove the hero from the squad.
- After removal, the corresponding squad slot becomes empty and displays the `+` icon again.

### Exploration Gap
- Adding an unlocked hero who is not already assigned was not observed in the captured state because both currently available heroes were already selected.

## Start Mission

### Start Mission
- Type: Button
- States: Default, Hover
- Purpose: Starts a mission using the current squad.

## Observed Behavior

- Interactive elements have a visible Hover state.
- The squad contains a maximum of 3 slots.
- Squad composition is reflected immediately by the portraits shown in the squad slots.
- Removing a selected hero updates the squad display.
- Locked heroes cannot currently be selected from the captured progression state.

## Navigation

- `New Game` → Squad hint
- `Continue` → Sanctuary
- Character portrait hexagon → Character information
- `Back` → Sanctuary
- Empty squad slot (`+`) → Hero selection
- Selected hero → Removal control (`X`)
- `Start Mission` → Mission

## Evidence

- [Squad hint](../Evidence/screenshots/sanctuary/squad-hint.png)
- [Sanctuary with selected squad](../Evidence/screenshots/sanctuary/sanctuary-squad.png)
- [Character information](../Evidence/screenshots/sanctuary/character-info.png)
- [Hero-selection interface](../Evidence/screenshots/sanctuary/hero-selection.png)
- [Selected hero removal control](../Evidence/screenshots/sanctuary/hero-removal.png)
- [Squad after hero removal](../Evidence/screenshots/sanctuary/squad-after-removal.png)
