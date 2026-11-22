# Editor tools

4 types in this area.

## BattleSkinBrowserWindow

```csharp
public sealed class BattleSkinBrowserWindow : EditorWindow
```

`TurnHerald.Editor` &middot; <small>Editor/Skins/BattleSkinBrowserWindow.cs</small>

Browse the shipped skins, preview them with the real shader, and turn any
of them into an editable asset in one click.

This window exists because the package previously offered no way to
discover or create a look: a customer had to create a blank asset and fill
in fields with no preview. "Save a copy..." is the intended entry
point for authoring a custom skin.

!!! note "Remarks"
    Rebuilt by the editor pass (step E1.4) on the shared browser pattern of the common editor guide:
    nothing scrolls at the minimum size of 720 by 460. A paged list of the skins on the left (the shipped ones, then the
    project's assets, with an "In this project" card while there are none); on the right the selected skin with its HUD preview across
    the whole width of the detail (never below 128 points, so the four status pips are always drawn), the tabs Bars and About, and the
    actions fixed at the foot: Save a copy..., Assign to open scenes and Select. The last operation goes to the status line, never to
    a dialog. The tab, the page of the list and the selected skin survive a domain reload.

**Methods**

`public static void Open()`

:   Opens the skin browser, or brings it forward when it is already open. Also reachable from Tools > TurnHerald > Skin Browser.

`public void Refresh()`

:   Rebuilds the list from shipped skins plus project assets.

---

## CombatStudioSampleArt

```csharp
public static class CombatStudioSampleArt
```

`TurnHerald.Editor.CombatStudio` &middot; <small>Editor/CombatStudio/CombatStudioSampleArt.cs</small>

Builds the editable assets behind the shipped sample themes: display fonts, icon sets, stage backdrops with their ambient
particles, and the complete `BattleTheme` values. Every method creates what is missing and returns what exists,
so running Build Samples again never overwrites an asset the project has edited.

**Fields**

`public const float SampleGroundLineY`

:   Height of the feet line on both sample plates, measured on the 2560x1440 images. It maps to about two thirds of the way down the screen (65.5% from the top at 16:9, 63.4% at 16:10) with the rig's cover fit, scale 1.12 and offset, which keeps the feet and the health bar under them at least 12 pixels above the event strip of the dock.

**Methods**

`public static void ApplyStageContract(BattleStageBackdropAsset asset, CombatStudioSampleTheme theme)`

:   Writes the floor contract measured on the sample plates, normalized with the origin at the bottom left of the plate. Ashen Cloister: the open floor starts at v 0.57 (the pavers end at the low wall and the foot of the stairs, which dip to 0.54 at the left); foreground rocks fill the bottom left up to u 0.26 and the bottom right from u 0.74; the stairs and the ruined wall are props. Moonwell: the open floor starts at v 0.47 below the well steps; the well platform, the mossy rocks on both sides and the fern and rock clusters in the foreground are props. Horizon and vanishing point are the eye line of the plate image's camera.

    - `asset` &mdash; Backdrop to write.
    - `theme` &mdash; Sample theme whose plate the backdrop carries.

`public static BattleTheme CreateTheme(CombatStudioSampleTheme theme)`

:   Builds the complete theme of a sample: palette from the design table, fonts, sprites, icon set and stage backdrop.

    - `theme` &mdash; Sample theme to build.
    - **Returns** &mdash; A new theme value; assets it references are created when missing.

`public static BattlePresentationLabel[] DescriptionLabels()`

:   The one-line descriptions of the starter skills, as labels named ".description".

    - **Returns** &mdash; A new array of labels.

`public static string DisplayFontAssetPath(CombatStudioSampleTheme theme)`

:   Path of the display font asset of a theme.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The project path of the SDF asset.

`public static string DisplayFontFile(CombatStudioSampleTheme theme)`

:   Path of the display font file of a theme.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The project path of the TTF.

`public static void GenerateSampleFonts()`

:   Creates the Cinzel and Cormorant Garamond SDF font assets when they are missing. Safe to run repeatedly.

`public static BattleStageBackdropAsset GetOrCreateBackdrop(CombatStudioSampleTheme theme)`

:   Returns the stage backdrop of a theme: one parallax-1 plate layer and ambient particles, created when missing.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The backdrop asset, or null when the plate sprite is not imported.

`public static TMP_FontAsset GetOrCreateDisplayFont(CombatStudioSampleTheme theme)`

:   Returns the display font asset of a theme, generating it from the shipped TTF when it does not exist.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The font asset, or null when the TTF is missing.

`public static BattleIconSet GetOrCreateIconSet(CombatStudioSampleTheme theme)`

:   Returns the icon set of a theme, creating it from the shipped icon sprites when it does not exist.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The icon set asset.

`public static bool HasDescriptionLabels(BattlePresentationLabel[] labels)`

:   Tests whether a label list already carries the one-line skill descriptions.

    - `labels` &mdash; Labels of a profile.
    - **Returns** &mdash; True when any label is a skill description.

`public static Color SampleAllyText(CombatStudioSampleTheme theme)`

:   Allied text color of a sample theme: the rim blue of Ember & Iron lightened to 5.6:1 on the dock, the silver of Moonwell as it is.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; An opaque color.

`public static Color SampleEnemyText(CombatStudioSampleTheme theme)`

:   Hostile text color of a sample theme: the theme's own light red or rose, which reads at 5.2:1 and 5.5:1 on the dock where the crimson and wine rims do not.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; An opaque color.

`public static string ThemeFolder(CombatStudioSampleTheme theme)`

:   Folder that holds the sprites of a theme.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The project folder.

`public static bool UpgradeTextTokens(BattleTheme value, CombatStudioSampleTheme theme)`

:   Gives the theme of a sample profile created before the text tokens existed its allied and hostile text colors. A token the author already set is kept, so a profile whose author chose other text colors keeps them.

    - `value` &mdash; Theme of an existing sample profile.
    - `theme` &mdash; Sample theme the profile belongs to.
    - **Returns** &mdash; True when the theme was changed and its asset must be saved.

`public static bool UpgradeWorldStyle(BattleTheme value, CombatStudioSampleTheme theme)`

:   Brings the theme of a sample profile created before the stage style existed up to date. Only a theme with no stage style at all is touched, so a profile whose author already chose plates, size or marks keeps every choice.

    - `value` &mdash; Theme of an existing sample profile.
    - `theme` &mdash; Sample theme the profile belongs to.
    - **Returns** &mdash; True when the theme was changed and its asset must be saved.

---

## CombatStudioSampleBuilder

```csharp
public static class CombatStudioSampleBuilder
```

`TurnHerald.Editor.CombatStudio` &middot; <small>Editor/CombatStudio/CombatStudioSampleBuilder.cs</small>

Creates editable starter profiles and native view prefabs using
Unity's asset APIs. No serialized YAML is authored by the tool.

**Methods**

`public static void BuildSamples()`

:   Creates the missing editable sample profiles (Ember & Iron and Moonwell, each on uGUI and UI Toolkit) with their themes, display fonts, icon sets, stage backdrops, stage presets and native view prefabs, repairs missing references in existing examples, and saves the assets. Requires an idle EditMode Editor with a starter catalog and no compilation errors; authored profile choices are retained.

`public static PresentationStagePreset GetOrCreateStagePreset(BattleLayoutIdentity identity)`

:   Creates an editable example using the shipped recipes and neutral art. Repeated calls preserve existing assets and all authored values. Camera movement starts disabled until its composition is validated.

    - `identity` &mdash; Fantasy selects the Ember & Iron example; science fiction selects a legacy console example.
    - **Returns** &mdash; The preserved or newly created editable preset for this identity.

`public static PresentationStagePreset GetOrCreateStagePreset(CombatStudioSampleTheme theme)`

:   Creates the editable stage preset of a sample theme, or returns the existing one.

    - `theme` &mdash; Sample theme.
    - **Returns** &mdash; The preserved or newly created editable preset.

---

## CombatStudioSampleTheme

```csharp
public enum CombatStudioSampleTheme
```

`TurnHerald.Editor.CombatStudio` &middot; <small>Editor/CombatStudio/CombatStudioSampleArt.cs</small>

The two shipped sample themes that share the dock layout.

| Value | Meaning |
| --- | --- |
| `EmberIron` | Smoked leather and aged gold over the Ashen Cloister at dusk. |
| `Moonwell` | Navy glass and silver-blue over the Moonwell Glade at night. |

---
