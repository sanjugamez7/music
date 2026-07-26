# Implementation Plan - Spotify Style Seek Bar

The user wants the player screen's time seek bar to follow the "Spotify style". Spotify's seek bar is characterized by a thin track that thickens when the user interacts with it (dragging or pressing), along with a thumb that only appears during interaction.

## Proposed Changes

### [Constants]

#### [MODIFY] [PreferenceKeys.kt](file:///D:/flux%20copy/Metrolist-main/app/src/main/kotlin/com/metrolist/music/constants/PreferenceKeys.kt)
- Add `SPOTIFY` to the `SliderStyle` enum.

### [UI Components]

#### [MODIFY] [PlayerSlider.kt](file:///D:/flux%20copy/Metrolist-main/app/src/main/kotlin/com/metrolist/music/ui/component/PlayerSlider.kt)
- Implement `SpotifySlider` composable which handles interaction-based animations for track height and thumb size.

### [Resources]

#### [MODIFY] [metrolist_strings.xml](file:///D:/flux%20copy/Metrolist-main/app/src/main/res/values/metrolist_strings.xml)
- Add a string resource for "Spotify" to be used in the settings UI.

### [Player]

#### [MODIFY] [Player.kt](file:///D:/flux%20copy/Metrolist-main/app/src/main/kotlin/com/metrolist/music/ui/player/Player.kt)
- Add a case for `SliderStyle.SPOTIFY` in the seek bar section of `BottomSheetPlayer`.

### [Settings]

#### [MODIFY] [AppearanceSettings.kt](file:///D:/flux%20copy/Metrolist-main/app/src/main/kotlin/com/metrolist/music/ui/screens/settings/AppearanceSettings.kt)
- Add the "Spotify" slider style as a selectable option in the appearance settings dialog.

## Verification Plan

### Automated Tests
- Build the app using `./gradlew :app:assembleFossDebug` to ensure no compilation errors.

### Manual Verification
1. Open the app and go to Settings > Appearance.
2. Select "Slider Style" and choose "Spotify".
3. Open the player and verify that the seek bar:
   - Is thin when idle.
   - Grows in height when touched/dragged.
   - Shows a thumb only when touched/dragged.
