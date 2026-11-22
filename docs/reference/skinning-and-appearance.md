# Skinning and appearance

29 types in this area.

!!! abstract "On this page"
    [BattleActionKind](#battleactionkind) &middot; [BattleIconSet](#battleiconset) &middot; [BattleSkinDefaults](#battleskindefaults) &middot; [BattleSkinPreset](#battleskinpreset) &middot; [CompiledBattleSkin](#compiledbattleskin) &middot; [FloatingNumberLegibility](#floatingnumberlegibility) &middot; [IdEntry](#identry) &middot; [KindEntry](#kindentry) &middot; [SkinAnchor](#skinanchor) &middot; [SkinBarTokens](#skinbartokens) &middot; [SkinContrast](#skincontrast) &middot; [SkinEasing](#skineasing) &middot; [SkinFillMode](#skinfillmode) &middot; [SkinFloatingNumberTokens](#skinfloatingnumbertokens) &middot; [SkinLayoutProfile](#skinlayoutprofile) &middot; [SkinMaterialPool](#skinmaterialpool) &middot; [SkinMotionTokens](#skinmotiontokens) &middot; [SkinPaletteTokens](#skinpalettetokens) &middot; [SkinRegionStretch](#skinregionstretch) &middot; [SkinRegionTokens](#skinregiontokens) &middot; [SkinShape](#skinshape) &middot; [SkinStagePresenceTokens](#skinstagepresencetokens) &middot; [SkinStatusPipTokens](#skinstatuspiptokens) &middot; [SkinSurfaceGraphic](#skinsurfacegraphic) &middot; [SkinSurfaceTokens](#skinsurfacetokens) &middot; [SkinTargetingTokens](#skintargetingtokens) &middot; [SkinTypographyTokens](#skintypographytokens) &middot; [WorldFade](#worldfade) &middot; [WorldFadeTiming](#worldfadetiming)

## BattleActionKind

```csharp
public enum BattleActionKind
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleIconSet.cs</small>

Broad category of a command, used to pick a default icon when a skill has no icon of its own.

| Value | Meaning |
| --- | --- |
| `Attack` | A basic attack. |
| `Skill` | A skill or spell. |
| `Guard` | A defensive stance. |
| `Item` | An item use. |
| `Flee` | An attempt to leave the battle. |

---

## BattleIconSet

```csharp
public sealed class BattleIconSet : ScriptableObject
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleIconSet.cs</small>

Maps action kinds, skill identities and status identities to sprites. A skill or status without its own
entry falls back to the icon of its kind, so a set with five kind icons already covers every command.
It lives in the presentation layer; simulation and authoring data never reference it.

**Properties**

`public Sprite Damage`

:   Icon of the damage estimate chip; may be null.

`public Sprite Energy`

:   Icon of the energy resource family; may be null.

`public Sprite FallbackStatus`

:   Icon shown for a status that has no entry of its own; may be null.

`public Sprite Focus`

:   Icon of the focus resource family; may be null.

`public Sprite Healing`

:   Icon of the healing estimate chip; may be null.

`public Sprite Target`

:   Icon of the chip that names who an action reaches; may be null.

**Methods**

`public void SetKindIcon(BattleActionKind kind, Sprite icon)`

:   Sets or clears the default icon of an action kind.

    - `kind` &mdash; Action kind to configure.
    - `icon` &mdash; Icon to store, or null to remove the entry.

`public void SetResourceIcon(StableId resourceId, Sprite icon)`

:   Sets or clears the icon of one resource.

    - `resourceId` &mdash; Stable resource identity.
    - `icon` &mdash; Icon to store, or null to remove the entry.

`public void SetSkillIcon(StableId skillId, Sprite icon)`

:   Sets or clears the icon of one skill.

    - `skillId` &mdash; Stable skill identity.
    - `icon` &mdash; Icon to store, or null to remove the entry.

`public void SetStatusIcon(StableId statusId, Sprite icon)`

:   Sets or clears the icon of one status.

    - `statusId` &mdash; Stable status definition identity.
    - `icon` &mdash; Icon to store, or null to remove the entry.

`public bool TryGetActionIcon(StableId skillId, BattleActionKind kind, out Sprite icon)`

:   Finds the icon of a skill, falling back to the icon of its kind.

    - `skillId` &mdash; Stable skill identity; an invalid id skips the per-skill lookup.
    - `kind` &mdash; Kind used when the skill has no icon of its own.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when a per-skill or per-kind icon exists.

`public bool TryGetKindIcon(BattleActionKind kind, out Sprite icon)`

:   Finds the default icon of an action kind.

    - `kind` &mdash; Action kind to look up.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when the kind has an icon.

`public bool TryGetResourceIcon(StableId resourceId, BattleDockResourceKind kind, out Sprite icon)`

:   Finds the icon of a resource, falling back to the icon of its family.

    - `resourceId` &mdash; Stable resource identity; an invalid id skips the per-resource lookup.
    - `kind` &mdash; Resource family used when the resource has no icon of its own.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when an icon exists.

`public bool TryGetStatusIcon(StableId statusId, out Sprite icon)`

:   Finds the icon of a status, falling back to `FallbackStatus`.

    - `statusId` &mdash; Stable status definition identity; an invalid id uses the fallback.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when a per-status icon or the fallback exists.

---

## BattleSkinDefaults

```csharp
public static class BattleSkinDefaults
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinDefaults.cs</small>

The shipped skins, defined in code rather than as serialized assets.

Two reasons. First, the interface always has a complete, valid look even
when a scene assigns no skin asset, so the package never renders as
unstyled boxes. Second, no texture, font, or material is redistributed,
which keeps the provenance audit clean; every look is drawn procedurally
from these numbers.

The Skin Browser materializes any of these into an editable
`BattleSkinPreset` asset via "Duplicate and Edit".

**Fields**

`public const float CommandDeckHeight`

:   Height of the full-bleed command deck, in reference pixels.

`public const string DefaultSkinId`

:   Identity of the skin loaded when a scene assigns none.

`public const float GaugeBandHeight`

:   Height of the full-bleed turn-order band, in reference pixels.

`public const float LogStripHeight`

:   Height of the log strip that caps the command deck, in reference pixels.

`public const string PreviousDefaultSkinId`

:   Identity of the look that was the default before Ironlight. It is still shipped and still selectable; only the default moved, so a project that recorded this id keeps the look it chose.

`public const float SafeMargin`

:   Safe margin held clear at the screen edge, in reference pixels.

**Methods**

`public static IReadOnlyList<CompiledBattleSkin> All()`

:   Every shipped skin, in browser order.

    - **Returns** &mdash; A fresh five-item list ordered Ironlight, Slate Nocturne, Parchment Atlas, Neon Circuit, then Minimal Mono.

`public static CompiledSkinLayout BandLayout(SkinLayoutProfile profile)`

:   The three-band region placement for one aspect profile.

    - `profile` &mdash; Which composition to build. Wide and Ultrawide share their numbers on purpose - band heights are fixed, so a wider screen spends every extra pixel on the stage instead of inflating the interface.
    - **Returns** &mdash; A complete layout whose regions all dock into a band edge or the safe margin.

`public static CompiledBattleSkin Default()`

:   The skin used when a scene assigns none.

    - **Returns** &mdash; A freshly compiled Ironlight skin used as the package fallback.

`public static SkinFloatingNumberTokens DefaultFloatingNumbers()`

:   Floating-number sizing and timing shared by every shipped skin. A number spawned over the stage competes with a 300-pixel character, so 26 disappeared against it. Criticals land at 80 with the skin's warning colour and a halo, which is the one moment the interface is allowed to shout. A number lives one second (a critical a quarter second more): it fades in over a tenth of a second, holds, and fades out over the last 0.3, and it rises 48 pixels after a short pop, which keeps it over the head it belongs to instead of drifting into the neighbour; the scatter is a small wobble, not a lane. Every number is drawn with a dark outline, and its colour is lifted until it reads against that outline.

    - **Returns** &mdash; Shared floating-number size, critical scale, rise, lifetime, fades, easing, scatter and outline tokens.

`public static CompiledSkinLayout DefaultLayout()`

:   The region placement shared by every shipped skin.

    - **Returns** &mdash; The wide-profile three-band region placement used by every built-in skin.

`public static SkinMotionTokens DefaultMotion()`

:   Transition timings shared by every shipped skin.

    - **Returns** &mdash; Shared bar, panel, pip, timeline, and pulse transition timings at full motion scale.

`public static SkinStagePresenceTokens DefaultStagePresence()`

:   Depth falloff, contact shadow, and key light shared by every shipped skin.

    - **Returns** &mdash; Staging enabled, with a rank falloff and a shadow width in the middle of the windows the visual direction specifies, so a skin that edits neither still satisfies the composition audit.

`public static SkinTypographyTokens DefaultTypography()`

:   Type sizing shared by every shipped skin. The floor is 16, not 13. Thirteen reference pixels on a 27-inch monitor at arm's length is about a quarter of a degree of arc, which is fine for an inspector field and far too small for something a player has to read while deciding a turn. Everything above the floor is a step in the same four-size scale - caption, body, name, heading - so at most four sizes are ever on screen at once.

    - **Returns** &mdash; Shared caption, body, tracked-label, name, heading, title, spacing, and dark-outline typography tokens.

`public static CompiledBattleSkin Ironlight()`

:   Dark iron lit by one warm lamp. The shipped default.

    - **Returns** &mdash; A complete freshly compiled Ironlight skin with the band layout, chamfered surfaces, and team-coloured health.

`public static SkinSurfaceTokens IronlightBackdrop()`

:   Default-look stage backdrop drawn behind the combatants.

    - **Returns** &mdash; Borderless radial Ironlight backdrop tokens for the combat stage.

`public static SkinSurfaceTokens IronlightButton()`

:   Default-look card surface: the resting skill card and rail chip.

    - **Returns** &mdash; Ironlight resting button surface tokens.

`public static SkinSurfaceTokens IronlightButtonDisabled()`

:   Default-look card surface for a skill the actor cannot currently use.

    - **Returns** &mdash; Ironlight disabled-button tokens with muted contrast.

`public static SkinSurfaceTokens IronlightButtonSelected()`

:   Default-look card surface for the selected or hovered entry.

    - **Returns** &mdash; Ironlight selected-button tokens using the brass accent treatment.

`public static SkinBarTokens IronlightCastBar()`

:   Default-look cast bar. It carries no delta ghost, since progress only rises.

    - **Returns** &mdash; Ironlight cast-progress tokens without a delayed ghost.

`public static SkinBarTokens IronlightGauge()`

:   Default-look scheduler gauge for the combatant plate; no delta ghost either.

    - **Returns** &mdash; Ironlight scheduler-gauge tokens without a delayed ghost.

`public static SkinBarTokens IronlightHealthBar()`

:   Default-look health bar. Its fill is the ally team colour, not green.

    - **Returns** &mdash; Ironlight health-bar track, fill, ghost, border, and timing tokens.

`public static SkinPaletteTokens IronlightPalette()`

:   Dark iron lit by one warm lamp. The default look. The single rule that separates it from the others is that health is team-coloured rather than green: allies read bone-steel, enemies read rust, and green is freed up to mean healing and nothing else. On a 6v6 board that is the difference between twelve identical bars and a picture of who is winning.

    - **Returns** &mdash; Dark-iron palette tokens with a brass accent, steel alternate, and team-coloured health roles.

`public static SkinSurfaceTokens IronlightPanel()`

:   Default-look base panel: feedback log, tooltip, and band backings.

    - **Returns** &mdash; Ironlight base-panel surface tokens derived from its palette and look profile.

`public static SkinSurfaceTokens IronlightPanelRaised()`

:   Default-look raised surface: the acting chip and hovered rows.

    - **Returns** &mdash; Ironlight raised-panel tokens with stronger separation than the base panel.

`public static SkinStatusPipTokens IronlightPips()`

:   Default-look status pip strip drawn above each combatant.

    - **Returns** &mdash; Ironlight status-pip shape, color, size, spacing, and pop-motion tokens.

`public static SkinBarTokens IronlightResourceBar()`

:   Default-look resource bar for the actor's spendable pools.

    - **Returns** &mdash; Ironlight resource-bar tokens for spendable pools.

`public static SkinBarTokens IronlightShieldBar()`

:   Default-look shield bar, drawn as a second thinner rail under health.

    - **Returns** &mdash; Thin Ironlight shield-bar tokens.

`public static SkinSurfaceTokens IronlightTooltip()`

:   Default-look tooltip and result banner backing.

    - **Returns** &mdash; Ironlight elevated tooltip and result-banner surface tokens.

`public static CompiledBattleSkin MinimalMono()`

:   Light, flat, glowless; the neutral base to customize from.

    - **Returns** &mdash; A complete freshly compiled light skin with flat surfaces, no glow, and reduced pulse scale.

`public static SkinPaletteTokens MinimalMonoPalette()`

:   Light, flat, glowless. The neutral base to customize from.

    - **Returns** &mdash; Light neutral palette tokens intended as a glowless customization base.

`public static CompiledBattleSkin NeonCircuit()`

:   Deep indigo with saturated neon rims and heavy halos.

    - **Returns** &mdash; A complete freshly compiled neon skin with strong in-shader halos.

`public static SkinPaletteTokens NeonCircuitPalette()`

:   Deep indigo with saturated neon rims. The loudest look.

    - **Returns** &mdash; Deep-indigo palette tokens with saturated cyan, magenta, and violet accents.

`public static CompiledBattleSkin ParchmentAtlas()`

:   Warm paper and ink, no glow.

    - **Returns** &mdash; A complete freshly compiled parchment skin with outline-free sepia typography.

`public static SkinPaletteTokens ParchmentAtlasPalette()`

:   Warm paper and ink. Suits adventure and campaign framing.

    - **Returns** &mdash; Warm parchment palette tokens with sepia ink and muted red and green states.

`public static CompiledBattleSkin Resolve(BattleSkinPreset preset)`

:   Resolves the skin a component should draw with: the assigned asset when present, otherwise the shipped default. Never returns null, so callers need no null branch.

    - `preset` &mdash; Assigned authored preset to compile, or null to select Slate Nocturne.
    - **Returns** &mdash; The preset's compiled tokens when assigned; otherwise a non-null default skin.

`public static CompiledBattleSkin SlateNocturne()`

:   Dark slate with cyan and amber accents.

    - **Returns** &mdash; A complete freshly compiled dark-slate skin with default typography, motion, and layout.

`public static SkinSurfaceTokens SlateNocturneBackdrop()`

:   Default-look stage backdrop drawn behind the combatants.

    - **Returns** &mdash; Borderless radial Slate Nocturne backdrop tokens for the combat stage.

`public static SkinSurfaceTokens SlateNocturneButton()`

:   Default-look button surface: skill tray, timeline, and transport buttons.

    - **Returns** &mdash; Slate Nocturne resting button surface tokens.

`public static SkinSurfaceTokens SlateNocturneButtonDisabled()`

:   Default-look button surface for a skill the actor cannot currently use.

    - **Returns** &mdash; Slate Nocturne disabled-button tokens with muted contrast.

`public static SkinSurfaceTokens SlateNocturneButtonSelected()`

:   Default-look button surface for the selected or hovered entry.

    - **Returns** &mdash; Slate Nocturne selected-button tokens using the active accent treatment.

`public static SkinBarTokens SlateNocturneCastBar()`

:   Default-look cast bar. It carries no delta ghost, since progress only rises.

    - **Returns** &mdash; Slate Nocturne cast-progress tokens without a delayed ghost.

`public static SkinBarTokens SlateNocturneGauge()`

:   Default-look scheduler gauge for the combatant plate; no delta ghost either.

    - **Returns** &mdash; Slate Nocturne scheduler-gauge tokens without a delayed ghost.

`public static SkinBarTokens SlateNocturneHealthBar()`

:   Default-look health bar for nameplates and roster rows.

    - **Returns** &mdash; Slate Nocturne health-bar track, fill, ghost, border, and timing tokens.

`public static SkinPaletteTokens SlateNocturnePalette()`

:   Dark slate with cyan and amber accents. The previous default look.

    - **Returns** &mdash; Dark slate palette tokens with cyan informational and amber selection accents.

`public static SkinSurfaceTokens SlateNocturnePanel()`

:   Previous-default base panel: status roster, feedback log, timeline backing.

    - **Returns** &mdash; Slate Nocturne base-panel surface tokens derived from its palette and look profile.

`public static SkinSurfaceTokens SlateNocturnePanelRaised()`

:   Default-look raised surface: roster rows and the next timeline entry.

    - **Returns** &mdash; Slate Nocturne raised-panel tokens with stronger separation than the base panel.

`public static SkinStatusPipTokens SlateNocturnePips()`

:   Default-look status pip strip drawn above each combatant.

    - **Returns** &mdash; Slate Nocturne status-pip shape, color, size, spacing, and pop-motion tokens.

`public static SkinBarTokens SlateNocturneResourceBar()`

:   Default-look resource bar for the actor's spendable pools.

    - **Returns** &mdash; Slate Nocturne resource-bar tokens for spendable pools.

`public static SkinBarTokens SlateNocturneShieldBar()`

:   Default-look shield bar, drawn thinner than the health bar.

    - **Returns** &mdash; Thin Slate Nocturne shield-bar tokens.

`public static SkinSurfaceTokens SlateNocturneTooltip()`

:   Default-look tooltip and result banner backing.

    - **Returns** &mdash; Slate Nocturne elevated tooltip and result-banner surface tokens.

`public static SkinSurfaceTokens StageGround(SkinPaletteTokens palette)`

:   The lit ground a formation stands on: a soft, wide pool of light warmed towards the skin's accent, fading to nothing at its rim. Nothing like it existed. Without a ground plane every combatant hung in mid-air, which is most of why the shipped screenshots read as an unfinished scene rather than a battle. It is derived from the palette rather than stored on the skin asset, so every existing preset -- including one a buyer authored before this shipped -- gets a floor with no migration and no new serialized field.

    - `palette` &mdash; The palette the ground is tinted from.
    - **Returns** &mdash; Surface tokens for one team's ground pool.

`public static bool TryFind(string stableId, out CompiledBattleSkin skin)`

:   Finds a shipped skin by its stable id.

    - `stableId` &mdash; Id to match exactly; a skin asset's own id is never found here, since only the shipped looks are searched.
    - `skin` &mdash; The matching skin, or null when nothing matches.
    - **Returns** &mdash; True when a shipped skin carries that id.

---

## BattleSkinPreset

**Start here**

```csharp
public sealed class BattleSkinPreset : ScriptableObject
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinPreset.cs</small>

Every value the battle interface draws itself with, in one asset.
Duplicate a shipped skin, edit it in the inspector, and the whole HUD
restyles with no prefab surgery and no code changes.

A skin is presentation-only. It never enters a snapshot, a replay, a
state hash, or a compiled catalog, so swapping skins can never change a
battle outcome.

**Properties**

`public string Description`

:   Description shown in the Skin Browser.

`public string DisplayName`

:   Name shown in the Skin Browser.

`public string StableIdText`

:   Persistent skin identity.

**Methods**

`public CompiledBattleSkin Compile()`

:   Resolves this asset into the immutable value set the HUD consumes. Out-of-range authored values are clamped rather than rejected, so a half-edited skin still renders instead of throwing at runtime.

    - **Returns** &mdash; A complete skin, never null. Every token group is copied by value, so editing this asset afterwards does not alter an already-compiled skin.

`public void CopyFrom(CompiledBattleSkin source, string newStableId, string newDisplayName)`

:   Overwrites every field from `source`. Used by "Duplicate and Edit" in the Skin Browser and by the editor tests; it is the only supported way to author a skin from code.

    - `source` &mdash; Values to write in. Required; a null source throws.
    - `newStableId` &mdash; Replacement identity, or null or empty to keep the source's id.
    - `newDisplayName` &mdash; Replacement Skin Browser name, or null or empty to keep the source's name.

---

## CompiledBattleSkin

```csharp
public sealed class CompiledBattleSkin
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinPreset.cs</small>

The immutable skin the HUD reads. Built either from a
`BattleSkinPreset` asset or from `BattleSkinDefaults`
so the interface always has a complete, valid look even when no asset is
assigned.

**Constructors**

`public CompiledBattleSkin(string stableIdText, string displayName, string description, SkinPaletteTokens palette, SkinTypographyTokens typography, CompiledSkinSurfaces surfaces, CompiledSkinBars bars, SkinStatusPipTokens statusPips, SkinFloatingNumberTokens floatingNumbers, SkinMotionTokens motion, SkinStagePresenceTokens stagePresence, SkinTargetingTokens targeting, CompiledSkinLayout layout)`

:   Assembles a skin from finished token groups. Values are stored exactly as given; clamping is `BattleSkinPreset.Compile`'s job, not this constructor's. A null surface, bar, or layout group throws, because the interface has nothing to fall back to for those.

    - `bars` &mdash; Complete styling for health, shield, resource, cast, and scheduler bars.
    - `description` &mdash; Player-facing prose describing the skin, or `null` for no description.
    - `displayName` &mdash; Player-facing skin name, or `null` for an empty name.
    - `floatingNumbers` &mdash; Size, travel, and easing tokens for combat floating numbers.
    - `layout` &mdash; Canvas scaling and placement for every HUD region; must not be `null`.
    - `motion` &mdash; Durations, easing, and reduced-motion policy shared by HUD animations.
    - `palette` &mdash; Semantic colors consumed by surfaces, bars, text, and feedback.
    - `stableIdText` &mdash; Persistence-safe skin identifier, or `null` for an empty identifier.
    - `statusPips` &mdash; Size, spacing, and count presentation for combatant status pips.
    - `stagePresence` &mdash; Grounding, silhouette and selection-presence tokens for world-space combatant art.
    - `surfaces` &mdash; Complete styling for panels, buttons, tooltips, and the stage backdrop; must not be `null`.
    - `typography` &mdash; Font reference, sizes, and text style shared across the HUD.
    - `targeting` &mdash; Reticle and affected-area preview tokens used to show a pending target request.

**Properties**

`public CompiledSkinBars Bars`

:   Styling for the health, shield, resource, cast and scheduler bars. Never null.

`public string Description`

:   The short prose describing the look, shown under the name in the Skin Browser. Empty, never null, when the source supplied none.

`public string DisplayName`

:   The name to list this skin under in a picker. Empty, never null, when the source supplied none.

`public SkinFloatingNumberTokens FloatingNumbers`

:   Size, rise distance and easing for the damage, healing and shield numbers. Their colours come from `FloatingNumberColor` instead, so that damage and healing stay tied to the palette.

`public CompiledSkinLayout Layout`

:   Reference resolution, canvas match, safe-area handling and the position of every HUD region. Never null.

`public SkinMotionTokens Motion`

:   Transition timings for the whole interface. Widgets scale their durations through `SkinMotionTokens.Scale`, which is how a single reduce-motion flag snaps every animation at once instead of each widget deciding for itself.

`public SkinPaletteTokens Palette`

:   The semantic colour roles every widget draws from. Because widgets ask for a role rather than a literal colour, recolouring the whole interface is a change here and nowhere else.

`public string StableIdText`

:   The skin's persistent identity, carried over from the asset it was compiled from. Renaming the asset does not change it, so this is what to record when saving a player's chosen look. Empty, never null, when the source supplied none.

`public SkinStagePresenceTokens StagePresence`

:   Depth falloff between ranks, the contact shadow under every combatant, and the key light they are tinted by. This is what separates a stage from a set of correctly-placed coordinates; turn `SkinStagePresenceTokens.Enabled` off for a flat stage.

`public SkinStatusPipTokens StatusPips`

:   Size, spacing and stack-count settings for the status pip strip drawn above each combatant.

`public CompiledSkinSurfaces Surfaces`

:   Fills, strokes, glows and shadows for the panels, buttons, tooltip and stage backdrop. Never null.

`public SkinTargetingTokens Targeting`

:   How a target pick is expressed, and whether that choice adapts to the device. Never changes what is legal; see `TargetPreview`.

`public SkinTypographyTokens Typography`

:   Type sizes and treatment. Read the font through `ResolveFont` rather than from here, since an unset font falls back to Unity's built-in one.

**Methods**

`public Color FloatingNumberColor(FloatingNumberStyle style)`

:   The colour a floating number of `style` uses.

    - `style` &mdash; Semantic event category whose palette role should be selected.
    - **Returns** &mdash; The palette color assigned to the requested category, or primary text for an unknown enum value.

`public Color HealthFill(bool isAlly, Color teamColor)`

:   The fill colour of a combatant's health bar on the stage.

    - `isAlly` &mdash; Whether the combatant is on the player's team.
    - `teamColor` &mdash; Team tint used when the skin sets no dedicated health color.
    - **Returns** &mdash; The skin's ally or enemy health color when its alpha is above zero; otherwise `teamColor`.

`public TMP_FontAsset ResolveDisplayFont()`

:   The font combatant names are drawn with on the stage.

    - **Returns** &mdash; The skin's display font when set; otherwise the result of `ResolveFont`.

`public TMP_FontAsset ResolveFont()`

:   The font the skin draws text with. It always returns one, even in a project that has never imported TextMeshPro's resources, so the battle interface can never come up wordless or unbuilt.

    - **Returns** &mdash; The configured font, TextMeshPro's default, the essential-resources font, or one built from Unity's own built-in typeface.

---

## FloatingNumberLegibility

```csharp
public static class FloatingNumberLegibility
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/FloatingNumberLegibility.cs</small>

What makes a floating number legible on whatever stage it is drawn over, stated as numbers a test can read.

A number is drawn over a stage image that can be almost black in one corner and bright in another. No single colour
reaches 4.5 to one against both ends, so the number carries its own background: a dark, solid outline around every glyph.
The fill is then held to `MinimumRatio` against the outline, which is a fixed pair of colours and does not
depend on the stage, and the outline separates the pair from the stage on either side of the range. The contrast that
matters at the edge of a glyph is therefore fill against outline, and it is declared here instead of being left to the
luck of the backdrop.

**Properties**

`public static Color DefaultOutline`

:   The ink of the outline when a skin states none: a near black with a little warmth, so it sits well on every shipped stage.

**Fields**

`public const float MinimumRatio`

:   The least contrast, as a ratio, of a number's fill against its outline. The same floor as any text a player reads to play.

`public const float TargetRatio`

:   The contrast `Fill` aims for, a little over the floor so that rounding a colour to eight bits per channel, or a shader that blends the outline and the fill at the seam, can never take a number under `MinimumRatio`.

**Methods**

`public static Color Fill(CompiledBattleSkin skin, FloatingNumberStyle style)`

:   The colour a number of a style is filled with: the skin's colour for the style, moved as little as it takes toward white (or toward black, when the ink is light) to reach `TargetRatio` against the outline, so the hue the skin chose is kept as far as the contrast allows.

    - `skin` &mdash; The skin the numbers are drawn with; null uses the shipped defaults.
    - `style` &mdash; The kind of number.
    - **Returns** &mdash; The opaque fill colour.

`public static Color Outline(CompiledBattleSkin skin)`

:   The ink the outline of the numbers of a skin is drawn with, always solid.

    - `skin` &mdash; The skin the numbers are drawn with; null uses the shipped defaults.
    - **Returns** &mdash; The skin's outline colour, or `DefaultOutline` when the skin leaves it transparent.

`public static float OutlinePixels(CompiledBattleSkin skin)`

:   Thickness of the outline of a skin's numbers, in reference pixels.

    - `skin` &mdash; The skin the numbers are drawn with; null uses the shipped defaults.
    - **Returns** &mdash; The skin's outline thickness, never under one pixel.

`public static float Ratio(CompiledBattleSkin skin, FloatingNumberStyle style)`

:   The contrast, as a ratio, of the fill of a style against the outline of the skin.

    - `skin` &mdash; The skin the numbers are drawn with; null uses the shipped defaults.
    - `style` &mdash; The kind of number.
    - **Returns** &mdash; A ratio from one to twenty-one; `MinimumRatio` or more for every shipped skin and style.

`public static float RingPixels(float width, float fontSizePixels, float samplingPointSize, float atlasPadding, float weight)`

:   How many pixels of outline the text shader draws outside a glyph, at the size the text is laid out at, for an outline width of `width` with the face dilated by the same amount (so the face keeps the shape of the glyph and the whole width shows outside it). The signed distance field of a glyph reaches `atlasPadding` texels past its edge, and one texel is `fontSizePixels` over `samplingPointSize` pixels. The shader spends the range on outline, dilation and weight together and shrinks all three by one common ratio when they add up to more than the field holds (TextMesh Pro keeps that ratio in its material as the "scale ratio A"), so the thickness grows with the width but not without limit: that is the ceiling this returns near one.

    - `width` &mdash; Outline width in the shader's units, from zero to one.
    - `fontSizePixels` &mdash; Font size the text is laid out at, in pixels of the canvas it is drawn on.
    - `samplingPointSize` &mdash; Point size the glyphs of the font atlas were sampled at.
    - `atlasPadding` &mdash; Padding of the font atlas, in texels.
    - `weight` &mdash; The weight term of the shader: the larger of the normal and the bold weight, over four.
    - **Returns** &mdash; The thickness outside the glyph, in pixels.

`public static float WidthFor(float pixels, float fontSizePixels, float samplingPointSize, float atlasPadding, float weight)`

:   The outline width, in the shader's units, that draws an outline of `pixels` outside the glyphs; the inverse of `RingPixels`. A thickness the field cannot hold gives the widest outline there is.

    - `pixels` &mdash; Wanted thickness outside the glyph, in pixels of the canvas the text is drawn on.
    - `fontSizePixels` &mdash; Font size the text is laid out at, in pixels of that canvas.
    - `samplingPointSize` &mdash; Point size the glyphs of the font atlas were sampled at.
    - `atlasPadding` &mdash; Padding of the font atlas, in texels.
    - `weight` &mdash; The weight term of the shader: the larger of the normal and the bold weight, over four.
    - **Returns** &mdash; A width from zero to one.

---

## IdEntry

```csharp
public sealed class IdEntry
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleIconSet.cs</small>

Nested in `TurnHerald.UI.BattleIconSet`.

Icon of one skill or status identity.

**Fields**

`public Sprite Icon`

:   Icon shown for the identity.

`public string Id`

:   Stable skill or status identity text.

---

## KindEntry

```csharp
public sealed class KindEntry
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleIconSet.cs</small>

Nested in `TurnHerald.UI.BattleIconSet`.

Default icon of one action kind.

**Fields**

`public Sprite Icon`

:   Icon shown for the kind.

`public BattleActionKind Kind`

:   Action kind the icon stands for.

---

## SkinAnchor

```csharp
public enum SkinAnchor
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Where a HUD region attaches inside the safe area.

| Value | Meaning |
| --- | --- |
| `TopLeft` | Top-left safe-area point with a matching pivot. |
| `TopCenter` | Horizontal center of the safe area's top edge. |
| `TopRight` | Top-right safe-area point with a matching pivot. |
| `MiddleLeft` | Vertical center of the safe area's left edge. |
| `MiddleCenter` | Center point of the safe area. |
| `MiddleRight` | Vertical center of the safe area's right edge. |
| `BottomLeft` | Bottom-left safe-area point with a matching pivot. |
| `BottomCenter` | Horizontal center of the safe area's bottom edge. |
| `BottomRight` | Bottom-right safe-area point with a matching pivot. |

---

## SkinBarTokens

```csharp
public struct SkinBarTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

A value bar: health, shield, resource, cast, or gauge.

**Fields**

`public float CornerRadius`

:   The bar's intended corner radius in reference pixels. What is actually drawn is the radius on `Track` and `Fill`, since those are the surfaces that reach the shader; the shipped bars set all three to the same value, so change them together when reshaping a bar.

`public float DeltaCatchUpSeconds`

:   Seconds the ghost holds at the previous value before catching up. The ghost only appears when the value falls, and this duration passes through `SkinMotionTokens.Scale`, so zero here, a zero `SkinMotionTokens.MotionScale`, or `SkinMotionTokens.ReduceMotion` each suppress it.

`public Color DeltaColor`

:   Colour of the trailing ghost that marks the value just lost.

`public SkinSurfaceTokens Fill`

:   The surface masked to the current value. The trailing ghost is built from it too, recoloured to `DeltaColor` and stripped of its glow. Only the fill colour is cut by the value; a stroke on this surface still traces the whole bar, so use `Track` for the outline and leave the fill's stroke transparent unless that is the look you want.

`public float Height`

:   Bar height in reference pixels. It is also the layout height the bar requests, so the rows around it move when this changes.

`public Color SegmentColor`

:   Colour the tick marks are blended toward. Its alpha controls how strongly they cut in, and a fully transparent colour draws none at all whatever `SegmentCount` says. The ticks go onto both `Track` and `Fill`, so they stay aligned as the value moves.

`public int SegmentCount`

:   Tick marks drawn across the bar. Zero draws one continuous bar.

`public SkinSurfaceTokens Track`

:   The surface drawn across the bar's full width, showing what the value is measured against. It sits behind both the ghost and the fill, so its own glow is largely hidden and its stroke is what gives the bar its outline.

**Methods**

`public SkinBarTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy, with `Track` and `Fill` sanitized in turn; this instance is unchanged.

---

## SkinContrast

```csharp
public static class SkinContrast
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/SkinContrast.cs</small>

Contrast of text against what it is drawn on, computed the way the web content guidelines do (relative luminance of the sRGB
colours), so a token can be checked, and corrected, by a number instead of by eye.

The team colours of a skin were picked for bars and rings, where a mid-tone reads well. The same colour set as the name of a
combatant over a dark card is 2.4 to 3.1 to one, under the 4.5 to one that text a player reads mid-turn needs, so text takes
the team hue lightened just far enough instead of the raw colour.

**Properties**

`public static Color BrightStage`

:   A bright stage, which the card of a plate is judged against as well as `ReferenceStage`: a lit sky or a pale wall behind the combatant. Text that reads on the card over both reads on it over every stage between them.

`public static Color ReferenceStage`

:   The stage as the card of a plate is judged against: a mid grey. The card is translucent, so what shows through is whatever the stage has behind it; the card is held to its contrast over a stage neither as dark as the darkest backdrop nor as light as a flash.

**Fields**

`public const float MinimumTextRatio`

:   Least contrast, as a ratio, for text a player has to read to play: the name of a combatant and the value of its health.

**Methods**

`public static Color Ensure(Color foreground, Color background, float minimumRatio)`

:   Moves a colour as little as it takes to reach a contrast: toward white when that gets there, toward black when the background is light, so the hue the author chose is kept as far as the contrast allows.

    - `foreground` &mdash; The wanted colour of the text.
    - `background` &mdash; The opaque colour behind it.
    - `minimumRatio` &mdash; The contrast to reach.
    - **Returns** &mdash; The foreground itself when it already reaches the ratio; otherwise the nearest colour on the way to white or black that does, or the better end when neither does.

`public static Color EnsureOnCard(Color wanted, Color cardFill, bool linearBlend, float minimumRatio)`

:   The colour for text on a translucent card: the wanted colour moved as little as it takes to reach a contrast against the card over `ReferenceStage` and against the card over `BrightStage` as the screen blends it.

    - `wanted` &mdash; The colour the text is asked for.
    - `cardFill` &mdash; The translucent fill of the card the text stands on.
    - `linearBlend` &mdash; Whether the project renders in linear colour space; see `Over(Color, Color, bool)`.
    - `minimumRatio` &mdash; The contrast to reach on both.
    - **Returns** &mdash; The wanted colour when it reaches the ratio on both; otherwise the nearest colour toward white or black that does, or the one that does best on the worse of the two when none does.

`public static Color EnsureOverBoth(Color foreground, Color first, Color second, float minimumRatio)`

:   Like `Ensure`, for text that can fall on either of two backgrounds, such as a value drawn across a bar where one part of it sits on the fill and the rest on the empty track.

    - `foreground` &mdash; The wanted colour of the text.
    - `first` &mdash; One opaque background.
    - `second` &mdash; The other opaque background.
    - `minimumRatio` &mdash; The contrast to reach on both.
    - **Returns** &mdash; The foreground when it reaches the ratio on both; otherwise the nearest colour toward white or black that does; otherwise the end that does best on the worse background.

`public static float Luminance(Color color)`

:   Relative luminance of a colour in zero through one; alpha is ignored.

    - `color` &mdash; An sRGB colour.
    - **Returns** &mdash; The luminance defined by the sRGB transfer curve and the Rec. 709 weights.

`public static Color Over(Color top, Color bottom)`

:   Lays a translucent colour over an opaque one.

    - `top` &mdash; The translucent colour; its alpha is the share it covers.
    - `bottom` &mdash; What it is laid over; treated as opaque.
    - **Returns** &mdash; The opaque result.

`public static Color Over(Color top, Color bottom, bool linearBlend)`

:   Lays a translucent colour over an opaque one the way the screen blends it. A project that renders in linear colour space blends the light, not the sRGB values, so a dark translucent card over a bright stage comes out lighter there than the same card in a gamma project: 12% of a bright sky seen through a near-black card is sRGB 80, not 45.

    - `top` &mdash; The translucent sRGB colour; its alpha is the share it covers.
    - `bottom` &mdash; The sRGB colour it is laid over; treated as opaque.
    - `linearBlend` &mdash; True to blend as a linear colour space project does; false blends the sRGB values, as `Over(Color, Color)` does.
    - **Returns** &mdash; The opaque sRGB result.

`public static float Ratio(Color a, Color b)`

:   The contrast ratio of two opaque colours, from one to twenty-one.

    - `a` &mdash; One colour.
    - `b` &mdash; The other colour; the order does not matter.
    - **Returns** &mdash; The lighter luminance plus 0.05 over the darker plus 0.05.

---

## SkinEasing

```csharp
public enum SkinEasing
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

The easing curve applied to a skinned transition.

| Value | Meaning |
| --- | --- |
| `Linear` | Constant rate; no easing. |
| `EaseIn` | Accelerates from rest. |
| `EaseOut` | Decelerates into rest. |
| `EaseInOut` | Accelerates then decelerates. |
| `BackOut` | Overshoots slightly then settles. |

---

## SkinFillMode

```csharp
public enum SkinFillMode
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

How a skinned surface fills its rectangle.

| Value | Meaning |
| --- | --- |
| `Flat` | A single flat colour. |
| `LinearGradient` | A two-stop linear gradient along `SkinSurfaceTokens.GradientAngleDegrees`. |
| `RadialGradient` | A two-stop radial gradient from the surface centre. |

---

## SkinFloatingNumberTokens

```csharp
public struct SkinFloatingNumberTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Rise-and-fade numbers for damage, healing, and shields.

**Fields**

`public float CriticalFadeOutSeconds`

:   Seconds a critical number takes to fade out. Zero takes the shipped value, 0.4 seconds.

`public float CriticalLifetimeSeconds`

:   Lifetime a critical number has instead of `LifetimeSeconds`. Zero takes the shipped value, 1.25 seconds.

`public float CriticalScale`

:   Multiplies `FontSize` for `FloatingNumberStyle.Critical` only; every other style draws at the base size.

`public const float DefaultCriticalFadeOutSeconds`

:   Shipped length of the fade out of a critical number, in seconds.

`public const float DefaultCriticalLifetimeSeconds`

:   Shipped lifetime of a critical number, in seconds.

`public const float DefaultFadeInSeconds`

:   Shipped length of the fade in, in seconds.

`public const float DefaultFadeOutSeconds`

:   Shipped length of the fade out, in seconds.

`public const float DefaultOutlinePixels`

:   Shipped thickness of the outline, in reference pixels.

`public const float DefaultReducedCriticalLifetimeSeconds`

:   Shipped lifetime of a critical number when motion is reduced, in seconds.

`public const float DefaultReducedFadeSeconds`

:   Shipped length of the fades when motion is reduced, in seconds.

`public const float DefaultReducedLifetimeSeconds`

:   Shipped lifetime of a number when motion is reduced, in seconds.

`public float FadeInSeconds`

:   Seconds a number takes to fade in, ease-out. Zero takes the shipped value, 0.1 seconds.

`public float FadeOutSeconds`

:   Seconds the end of the lifetime is spent fading out, ease-out. Zero takes the shipped value, 0.3 seconds.

`public int FontSize`

:   Size every number is drawn at before `CriticalScale` is applied. Numbers are drawn on their own world-space canvas over the stage, not in the HUD, so this is independent of `SkinTypographyTokens` and needs to be much larger than body text to read at the same distance.

`public float HorizontalScatter`

:   Horizontal spread in reference pixels so stacked hits stay readable. The offset is derived from the spawn position rather than a random draw, so it never touches RNG the simulation could observe. Zero stacks the numbers.

`public float LifetimeSeconds`

:   Seconds a number stays visible, from the first frame of its fade in to the last of its fade out. A second is what a player needs to read a number and to see which hit it belongs to; the 0.6 seconds it used to take left a number at full opacity for about 0.3 of them. `SkinMotionTokens.ReduceMotion` swaps it for `ReducedLifetimeSeconds` instead of removing the number, so a hit is never silent.

`public Color OutlineColor`

:   Colour of the outline; its opacity is ignored, the outline is always solid. A colour with zero alpha, which is what an asset saved before this existed holds, takes the shipped ink, a near black. Number colours are raised until they reach `FloatingNumberLegibility.MinimumRatio` against whichever ink this resolves to.

`public float OutlinePixels`

:   Thickness, in reference pixels, of the dark outline every number is drawn with. The outline is what makes a number read on any stage: the fill is held to `FloatingNumberLegibility.MinimumRatio` against it, and the outline stands out from a stage that is too bright or too dark for the fill alone. Zero takes the shipped value, 4 pixels; the least that is ever drawn is one pixel.

`public float ReducedCriticalLifetimeSeconds`

:   Seconds a critical number stays visible when motion is reduced. Zero takes the shipped value, 1.3 seconds.

`public float ReducedFadeSeconds`

:   Seconds a number fades in and out when motion is reduced. A fade moves nothing, so it stays. Zero takes the shipped value, 0.15 seconds.

`public float ReducedLifetimeSeconds`

:   Seconds a number stays visible when motion is reduced. The number does not rise or pop then, so it is the time to read that is kept, not the quarter second that used to cut it short. Zero takes the shipped value, 1 second.

`public float RiseDistance`

:   How far a number travels upward from where it was spawned, in reference pixels, over the whole of `LifetimeSeconds`. The number fades out over the second half of that time regardless, so a long rise reads as slower rather than as lingering longer.

`public SkinEasing RiseEasing`

:   Shapes the rise over the number's lifetime. It moves the position only; the fade always runs on the same schedule, so easing changes where the number is when it starts disappearing. `SkinEasing.BackOut` carries the number past `RiseDistance` before settling back, which is worth knowing if the rise is tuned to clear a nameplate exactly.

**Methods**

`public SkinFloatingNumberTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy; this instance is unchanged. `RiseEasing` is left as authored.

---

## SkinLayoutProfile

```csharp
public enum SkinLayoutProfile
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Which band composition a layout is authored for. The three shipped
profiles keep the same band heights and move only what has to move, so a
project does not re-author a HUD per device.

| Value | Meaning |
| --- | --- |
| `Wide` | 16:9 and wider-but-not-ultrawide. |
| `Ultrawide` | 21:9 and wider. |
| `Portrait` | Taller than it is wide. |

---

## SkinMaterialPool

```csharp
public sealed class SkinMaterialPool : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/SkinMaterialPool.cs</small>

Reference-counted material pool for skinned surfaces, owned by a component
rather than by static state.

The Presentation assembly forbids static fields that can retain a
`UnityEngine.Object`, because such a cache survives a domain
reload and a scene unload and then hands out destroyed materials. Anchoring
the pool to the canvas root gives every material a real owner: when the
interface goes away, so do its materials.

The shader is loaded from Resources rather than found by name so it
survives build shader stripping without the buyer editing Always Included
Shaders. If it cannot load, callers fall back to the default UI material,
which draws a plain quad instead of a magenta error surface.

**Properties**

`public int CachedMaterialCount`

:   Live cached material count; useful in tests and profiling.

`public bool IsShaderAvailable`

:   True when the skinned-surface shader is available.

**Fields**

`public const string ShaderName`

:   Shader name, used as a secondary lookup.

`public const string ShaderResourcePath`

:   Resources path of the skinned-surface shader.

**Methods**

`public Material Acquire(SkinMaterialRequest request)`

:   Returns a material for `request`, sharing an existing one when the parameters match exactly.

    - `request` &mdash; The immutable request to validate and execute.
    - **Returns** &mdash; A shared reference-counted material for the request, or null when the shader is unavailable.

`public void Clear()`

:   Destroys every pooled material. Safe to call repeatedly.

`public static SkinMaterialPool EnsureFor(Component owner)`

:   Finds the pool owning `owner`, creating one on the nearest canvas root when absent. Returns null only when the owner is not in a scene.

    - `owner` &mdash; Scene component whose nearest parent pool or Canvas host should own materials.
    - **Returns** &mdash; The existing parent pool, a new pool on the Canvas or owner object, or null for a null owner.

`public void Release(Material material)`

:   Drops one reference to a pooled material.

    - `material` &mdash; Material previously acquired from this pool; foreign or null materials are ignored.

---

## SkinMotionTokens

```csharp
public struct SkinMotionTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Transition timings. Every duration scales by `MotionScale`.

**Fields**

`public SkinEasing BarEasing`

:   Shapes that travel. It applies to the fill only; the ghost behind it always catches up at a constant rate, which is what keeps the gap between the two readable.

`public float BarTransitionSeconds`

:   How long a bar takes to travel to a new value, before scaling. Once `Scale` reduces it to zero the bar snaps instead, and the trailing ghost is skipped with it, so a reduced-motion player sees the new value but not the amount just lost.

`public float MotionScale`

:   Multiplies every duration handed out by `Scale`. Zero snaps every change instantly.

`public float PanelFadeSeconds`

:   How long a panel takes to fade in, before scaling. The result banner uses it; at zero the banner appears at full opacity on the frame it is shown rather than never appearing.

`public float PipPopSeconds`

:   How long a status pip takes to pop in, before scaling. Offered for hosts that animate their own pip strip; the shipped combatant plate adds and removes pips outright and does not read it.

`public float PulseScale`

:   Scale a combatant token reaches at the peak of a pulse. The pulse rises and falls within `PulseSeconds`, so this is a peak rather than a resting size and a token is never left enlarged. Values close to 1 still register: the shipped Minimal Mono skin pulses at 1.04.

`public float PulseSeconds`

:   How long a whole pulse takes, out and back, before scaling. Once `Scale` reduces it to zero the token is returned to its rest scale immediately, so a pulse requested under reduced motion cannot leave a token stuck at `PulseScale`.

`public bool ReduceMotion`

:   Skip decorative motion. `Scale` then returns zero for every duration, so values snap instead of animating, while floating numbers stay briefly visible so nothing is missed. Drive this from a player accessibility setting.

`public float TimelineShiftSeconds`

:   How long the timeline takes to settle after the running order changes, before scaling. Offered for hosts that animate their own timeline; the shipped strip repaints in place and does not read it.

**Methods**

`public static float Ease(SkinEasing easing, float t)`

:   Maps a normalized 0..1 progress value through the selected easing curve. Input and output are clamped for presentation use only.

    - `t` &mdash; Progress from 0 to 1; anything outside that range is clamped first.
    - `easing` &mdash; Linear, smooth-step, cubic-out, or back-out curve applied to normalized time.
    - **Returns** &mdash; Eased progress. Every curve stays within 0..1 except `SkinEasing.BackOut`, which rises above 1 near the end and is what gives it its overshoot, so a caller that lerps with this result must tolerate values past the target.

`public SkinMotionTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy; this instance is unchanged. `ReduceMotion` and `BarEasing` are left as authored.

`public float Scale(float seconds)`

:   The effective duration for `seconds` under this skin.

    - `seconds` &mdash; The unscaled duration the animation would like.
    - **Returns** &mdash; `seconds` multiplied by `MotionScale`, never negative, and zero whenever `ReduceMotion` is set. Treat a zero result as an instruction to snap rather than animate.

---

## SkinPaletteTokens

```csharp
public struct SkinPaletteTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

The semantic colour roles a skin assigns once and reuses everywhere.

**Fields**

`public Color Accent`

:   The colour the interface uses to point at something: the selected skill button and its glow, the next timeline entry, status pips, and the scheduler gauge while it fills. It appears more often than any other accent, so it is the single value that most changes a skin's character.

`public Color AccentAlt`

:   Secondary accent. The cast bar, the resource bar, and resource floating numbers use it.

`public Color AllyHealth`

:   Health fill of the player's team on the stage plates. Alpha zero, which is what a skin authored before this token existed deserializes to, keeps the plate on `AllyTeam`.

`public Color AllyTeam`

:   Tints the name plate of a combatant on the player's team. The stage decides which team that is by matching each team against the player team id it was given, so with no player team set every combatant is tinted `EnemyTeam` instead.

`public Color AllyText`

:   Colour of the name of a player's combatant on its plate, when the skin has one distinct from `AllyTeam`. Alpha zero, which is what a skin authored before this token existed deserializes to, keeps the name on `AllyTeam`. Either way the plate lightens the name to the contrast text needs against its card.

`public Color Background`

:   The colour behind everything else. The shipped skins build the stage backdrop as a radial gradient from it to a darker shade of itself, and reuse it for the empty part of a bar track and for segment ticks, so it sets how deep the HUD reads overall rather than only the scene edges.

`public Color Border`

:   The stroke colour panels and bars fall back to when nothing more specific applies. A selected or focused widget swaps it for `Accent`, which is what makes selection read at a glance.

`public Color EnemyHealth`

:   Health fill of opposing teams on the stage plates. Alpha zero keeps the plate on `EnemyTeam`.

`public Color EnemyTeam`

:   Tints the name plate of every combatant not on the player's team. Only the plate label takes the tint; bars keep the colours the skin gave them, so health still reads the same on both sides of the field.

`public Color EnemyText`

:   The same for the name of every opposing combatant; alpha zero keeps `EnemyTeam`.

`public Color Negative`

:   Reads as bad news: damage numbers and the defeat banner.

`public Color Positive`

:   Reads as good news: healing numbers, the health bar, and the victory banner.

`public Color Shield`

:   Shield and barrier amounts: the shield bar, shield numbers, and a roster row that is holding shield.

`public Color Surface`

:   The resting colour of a HUD panel. Its alpha is carried through to the panel surface, so a translucent value lets the stage read through the interface; the tooltip surface forces the same colour opaque so text over a busy stage stays legible.

`public Color SurfaceRaised`

:   The colour that lifts something out of a panel: a roster row, a skill button, the next timeline entry, and the +N overflow status pip all use it, so it needs enough contrast against `Surface` to be read as a state change rather than as decoration.

`public Color TextMuted`

:   The recessive text colour: a dead combatant's name, the target caption under a skill button, the tooltip's target row, and the order number of timeline entries that are not next. It still has to be read, so keep it clearly distinguishable from `TextSecondary`.

`public Color TextPrimary`

:   The colour of anything the player is meant to read first: combatant names, headline text, bar readouts, and floating numbers that carry no semantic colour of their own.

`public Color TextSecondary`

:   The colour of text that supports a primary label rather than competing with it: log lines, the tooltip's chance and timing rows, and roster detail. The tooltip's cost row is drawn in `AccentAlt` instead, so a price still reads as its own thing.

`public Color Warning`

:   Reads as caution: critical-hit numbers and the concession banner.

---

## SkinRegionStretch

```csharp
public enum SkinRegionStretch
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

How a HUD region behaves on each axis: pinned at its authored size, or
stretched to the full width or height of the safe area.

Stretching is what makes a band. A pinned region floats at an anchor with
a pixel offset, which is individually reasonable and collectively
arbitrary; a stretched region shares an edge with the screen and with
every other region docked into the same band, so the composition holds at
any aspect ratio without re-authoring an offset.

| Value | Meaning |
| --- | --- |
| `None` | Pinned at the authored size on both axes. |
| `Horizontal` | Full-bleed across the safe-area width. |
| `Vertical` | Full-bleed down the safe-area height, with the authored width kept and the vertical offset read as a top and bottom inset. |
| `Both` | Full-bleed on both axes, inset by `SkinRegionTokens.Offset`. |

---

## SkinRegionTokens

```csharp
public struct SkinRegionTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Where one HUD region sits. Every region is independently placeable so a
customer can move the whole interface without editing a prefab.

**Fields**

`public SkinAnchor Anchor`

:   The point of the safe area the region hangs from. It becomes the region's anchor and its pivot at once, so the region grows away from that corner and stays put on screens of any aspect. `Offset` is then measured inward from it.

`public Vector2 Offset`

:   Distance from the anchor in reference pixels, always measured inward, so the same numbers keep their meaning when the region is re-anchored to another corner. See `InwardOffset` for the signed form a RectTransform wants.

`public float Scale`

:   Extra scale for this region alone. Zero or negative is read as 1, so an unset value never scales a region out of sight.

`public Vector2 Size`

:   Region size in reference pixels. Zero on an axis leaves that axis alone, so the region sizes to its content.

`public SkinRegionStretch Stretch`

:   Whether the region is pinned at its authored size or stretched to the full width or height of the safe area. A stretched axis reads `Offset` as an inset from both edges of that axis and ignores `Size` on it. That is what turns a region into a band: it shares an edge with the screen, so panels docked into it line up with each other at every aspect ratio instead of drifting apart.

`public bool Visible`

:   Whether the interface builds this region. A hidden region is never created rather than created and disabled, so switching it off costs nothing at runtime and its view is simply skipped when the interface repaints. This is how a host drops a block of the HUD it does not want without editing a prefab.

**Methods**

`public static Vector2 AnchorPoint(SkinAnchor anchor)`

:   The normalized anchor point for `anchor`.

    - `anchor` &mdash; Named safe-area location to convert into normalized coordinates.
    - **Returns** &mdash; The matching point with (0,0) at the bottom left and (1,1) at the top right, ready to use as a RectTransform anchor and pivot. A value outside the enum falls back to the bottom right.

`public static SkinRegionTokens At(SkinAnchor anchor, Vector2 offset, Vector2 size)`

:   A visible region anchored at `anchor`.

    - `offset` &mdash; Inward distance from the anchor in reference pixels.
    - `size` &mdash; Size in reference pixels; zero on an axis sizes to content.
    - `anchor` &mdash; Safe-area edge or corner that fixes both region anchors and pivot.
    - **Returns** &mdash; A visible region at scale 1.

`public static SkinRegionTokens Band(SkinAnchor anchor, float height, float sideInset = 0f, float edgeOffset = 0f)`

:   A visible full-bleed horizontal band of `height` reference pixels, hung from the top or bottom of the safe area.

    - `anchor` &mdash; Edge the band hangs from. Only the vertical half is read, so any of the three top anchors gives a top band and any of the three bottom anchors gives a bottom band.
    - `height` &mdash; Band height in reference pixels.
    - `sideInset` &mdash; Left and right inset in reference pixels. Zero is true full bleed, which is what the shipped gauge rail uses.
    - `edgeOffset` &mdash; Distance inward from that edge in reference pixels. Zero sits the band flush against the edge; a positive value stacks it above a band that is already there, which is how the log strip caps the command deck.
    - **Returns** &mdash; A visible, horizontally stretched region at scale 1.

`public Vector2 InwardOffset()`

:   Converts `Offset` into a signed anchored position so positive values always move a region inward from its anchor.

    - **Returns** &mdash; `Offset` with its sign flipped on each axis whose anchor sits at the far edge. A centred axis keeps the raw value, where positive still means right and up.

`public SkinRegionTokens Sanitized()`

:   Copies the region with nonnegative dimensions and a scale capped at two. A nonpositive scale becomes one; other fields are retained.

    - **Returns** &mdash; A presentation copy with those clamps applied. This method does not validate finite values or modify the source region.

`public SkinRegionTokens ScaledBand(float scale)`

:   Clamps every token into its supported range.

    - `scale` &mdash; Factor from `CompiledSkinLayout.BandScale`. One, or anything outside a sane range, returns this region untouched.
    - **Returns** &mdash; A clamped copy; this instance is unchanged. A zero or negative `Scale` becomes 1, and a negative `Size` axis becomes zero.

---

## SkinShape

```csharp
public enum SkinShape
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

The silhouette a skinned surface draws.

| Value | Meaning |
| --- | --- |
| `RoundedRect` | A rounded rectangle honouring the corner radius. |
| `Circle` | A circle inscribed in the shorter rectangle axis. |
| `Capsule` | A capsule: fully rounded on the shorter axis. |
| `Hexagon` | A hexagon inscribed in the rectangle. |
| `Diamond` | A diamond inscribed in the rectangle. |
| `Chamfer` | A rectangle with its corners cut off at 45 degrees rather than rounded. |

---

## SkinStagePresenceTokens

```csharp
public struct SkinStagePresenceTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

How the stage stages its combatants: the falloff between depth ranks, the
contact shadow every body stands on, and the one warm key light.

Draw order alone does not make a scene. A formation whose seats are at
correct coordinates and correct sorting still reads as a diagram, because
nothing tells the eye which body is near and which is far - every
silhouette is the same size, the same brightness, and touches nothing.
These tokens are what turn that arrangement into a photograph of a fight.

Rank is depth, and it is read from the formation rather than authored:
seats sharing a ground line share a rank, and rank rises going away from
the camera. A flat arrangement therefore has one rank and no falloff at
all, which is the right answer for it.

**Fields**

`public Color ContactShadowColor`

:   Colour of the contact shadow. It is a colour rather than plain black because a shadow on a lit stage carries the bounce of whatever it sits on, and pure black on a coloured backdrop reads as a hole.

`public float ContactShadowFlatness`

:   The shadow's height as a fraction of its width. Low values read as a high camera looking down a shallow stage, which is the shipped framing; at 1 the shadow is a circle and the stage reads top-down.

`public float ContactShadowOpacity`

:   How opaque the contact shadow is against the backdrop.

`public float ContactShadowWidth`

:   Width of a combatant's contact shadow as a fraction of that combatant's own sprite width, so one value serves bodies of every size. Zero removes the shadow. Without one a painted character floats: there is no evidence it is standing on the same ground as anybody else, and no amount of correct positioning supplies that evidence.

`public bool Enabled`

:   Whether the stage stages at all. Off leaves every combatant at one size, one brightness, and no shadow - the pre-staging look - without the host having to neutralize four separate tokens to get there.

`public Color KeyLightColor`

:   The single key light every combatant is lit by, tinting bodies toward it most strongly at the front rank and falling off with depth. One light, deliberately. Two lights need a direction each and turn a skin into a lighting rig; one warm key against a cool backdrop is the whole of what this presentation needs to stop looking flat.

`public float KeyLightStrength`

:   How far the front rank is tinted toward `KeyLightColor`. Zero leaves art exactly as painted, which is what a project with its own lighting wants.

`public float RankDarkening`

:   How much luminance each rank loses against the one in front of it, compounding the same way `RankScale` does. Scale alone is ambiguous - a smaller silhouette can be a smaller character. Darkening is what makes it distance, because atmosphere takes light out of everything behind the front line. The line and depth layouts hold it to 8% per rank, because their combatants stand on one ground line rather than at different distances; the legacy layout applies it as authored.

`public float RankScale`

:   How much smaller each rank is than the one in front of it. Applied per rank, so the second rank back is this squared. Below about 0.8 the back rank stops reading as further away and starts reading as smaller creatures; at 1 there is no depth cue left. The shipped value sits in the middle of that window. Only the legacy formation layout applies it. The line and depth layouts draw every rank at one scale and size combatants by population or by the horizon of the stage instead.

**Methods**

`public SkinStagePresenceTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy; this instance is unchanged. `Enabled` and both colours are left as authored.

`public float ScaleForRank(int rank)`

:   The size multiplier for a combatant standing at `rank`.

    - `rank` &mdash; Depth rank, 0 at the front. Negative values are treated as the front.
    - **Returns** &mdash; `RankScale` raised to `rank`, or exactly 1 when staging is off, so a caller can multiply unconditionally.

`public Color TintForRank(Color tint, int rank)`

:   Lights and depth-fades one combatant's tint for its rank.

    - `tint` &mdash; The combatant's own tint, normally white for unmodified art.
    - `rank` &mdash; Depth rank, 0 at the front. Negative values are treated as the front.
    - **Returns** &mdash; The tint pulled toward `KeyLightColor` and then darkened for depth. Alpha is carried through untouched, so this composes with a death fade rather than fighting it. Staging off returns `tint` unchanged.

---

## SkinStatusPipTokens

```csharp
public struct SkinStatusPipTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

The status pip strip drawn above a combatant.

**Fields**

`public int MaximumVisible`

:   Pips drawn before the strip overflows. Past this many statuses the last visible pip becomes a +N pip counting the ones not shown, so the strip never grows wider than this.

`public bool ShowStackCounts`

:   Allows a count to be drawn inside a pip. On the shipped combatant plate only the overflow pip carries one, reading +N for every status the strip has no pip of its own for. The overflow pip takes the place of the last visible one, so N runs one higher than the count past `MaximumVisible`. Turning this off leaves that pip blank, so the strip still shows that something is hidden but not how much.

`public float Size`

:   Edge length of one pip in reference pixels. It also fixes the height of the strip and the size of the stack-count digits, which are derived from it, so a small pip stays legible rather than carrying unreadable text.

`public float Spacing`

:   Gap between neighbouring pips in reference pixels. It widens the strip without widening the pips, so together with `Size` and `MaximumVisible` it decides how much room the strip takes above a combatant.

`public SkinSurfaceTokens Surface`

:   Pip surface. Its shape, stroke, and glow are drawn as authored, but the fill is replaced when the pip is drawn: `SkinPaletteTokens.Accent` for a status pip, `SkinPaletteTokens.SurfaceRaised` for the overflow pip.

**Methods**

`public SkinStatusPipTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy, with `Surface` sanitized in turn; this instance is unchanged.

---

## SkinSurfaceGraphic

```csharp
public sealed class SkinSurfaceGraphic : MaskableGraphic
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/SkinSurfaceGraphic.cs</small>

Draws one `SkinSurfaceTokens` as a uGUI graphic through the
TurnHerald skinned-surface shader. Every panel, button, bar, gauge, and
status pip in the HUD is one of these, so restyling the interface means
changing token values rather than swapping prefabs or textures.

The mesh is padded beyond the layout rect so glow and shadow can bleed
outside the shape without being clipped. Padding is excluded from layout,
so a glowing widget still occupies exactly its `RectTransform`.

**Properties**

`public float FillAmount`

:   Filled fraction in [0,1]. Bars and gauges animate this; other surfaces leave it at 1.

`public bool FillVertical`

:   True when `FillAmount` runs bottom-to-top.

`public float Padding`

:   Padding in reference pixels added around the rect so glow and shadow are not clipped by the quad.

`public SkinSurfaceTokens Surface`

:   The surface tokens this graphic draws.

**Methods**

`public void Apply(SkinSurfaceTokens value)`

:   Updates apply on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `value` &mdash; Shape, fill, stroke, glow, and shadow tokens to sanitize and draw.

`public void ApplySegments(int count, Color color)`

:   Applies segment ticks, used by segmented bars.

    - `color` &mdash; Shader color used for separators between filled segments.
    - `count` &mdash; Requested segment count, clamped to zero through 32.

`public void SetFillColors(Color primary, Color secondary)`

:   Replaces only the fill colours, keeping shape and glow.

    - `primary` &mdash; Replacement first gradient stop.
    - `secondary` &mdash; Replacement second gradient stop.

`public void SetGlow(Color color, float radius, float intensity)`

:   Replaces only the glow, keeping shape and fill.

    - `color` &mdash; Replacement outer-glow color.
    - `intensity` &mdash; Replacement glow multiplier sanitized to the supported shader range.
    - `radius` &mdash; Replacement glow radius in reference pixels.

---

## SkinSurfaceTokens

```csharp
public struct SkinSurfaceTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Fill, stroke, and glow for one skinned surface. Every skinned widget
resolves to one of these, so a customer restyles the whole HUD by editing
a handful of surfaces rather than hunting individual prefabs.

**Fields**

`public float CornerRadius`

:   Corner treatment in reference pixels: the fillet radius under `SkinShape.RoundedRect` and the cut length under `SkinShape.Chamfer`. Every other shape ignores it. The shader clamps it to half the shorter axis, so an over-large value settles into a capsule or a diamond instead of distorting the shape.

`public Color FillColor`

:   The near gradient stop, and the entire fill under `SkinFillMode.Flat`. A linear gradient starts from it at the leading edge and a radial gradient starts from it at the centre, so this is the colour a surface reads as whichever fill mode is chosen.

`public Color FillColorSecondary`

:   The far gradient stop. `SkinFillMode.Flat` ignores it and draws `FillColor` alone.

`public SkinFillMode FillMode`

:   Flat, linear-gradient, or radial-gradient sampling used by the surface shader.

`public Color GlowColor`

:   Halo colour. Its alpha is one of the three switches on the glow, so a fully transparent colour suppresses the halo however generous `GlowRadius` and `GlowIntensity` are. The halo falls off outside the silhouette only, so it never washes out the fill.

`public float GlowIntensity`

:   Multiplies the glow mask. A glow needs a non-zero `GlowRadius`, a non-zero intensity, and a `GlowColor` carrying alpha before anything is drawn at all; values above 1 widen the solid core of the halo, which reads as bloom without a post-processing stack.

`public float GlowRadius`

:   How far the halo reaches beyond the silhouette, in reference pixels. The mesh is padded by this distance so the halo is not clipped by the quad, and the padding is excluded from layout, so a widget that glows still occupies exactly its RectTransform and does not push its neighbours around.

`public float GradientAngleDegrees`

:   Direction of a `SkinFillMode.LinearGradient` fill, in degrees anticlockwise from screen right: 0 runs `FillColor` to `FillColorSecondary` left to right, 90 runs bottom to top. The flat and radial modes ignore it.

`public Color ShadowColor`

:   Drop-shadow colour. Its alpha both gates and scales the shadow: a fully transparent colour draws nothing whatever `ShadowRadius` and `ShadowOffset` say, and it is also what stops a shadowless surface from paying for shadow padding.

`public Vector2 ShadowOffset`

:   Displacement of the shadow from the surface in reference pixels, with positive x to the right and positive y upward. The offset is added to `ShadowRadius` when the mesh is padded, so a far-thrown shadow is drawn in full rather than cut off at the quad edge.

`public float ShadowRadius`

:   Drop-shadow softness in reference pixels. Zero, or a fully transparent `ShadowColor`, draws no shadow.

`public SkinShape Shape`

:   The silhouette every part of the surface is measured against: fill, stroke, glow, and shadow all follow it. The shape is cut from a signed distance field inside the shader rather than built from geometry, so switching shapes costs no extra vertices and needs no sprite or mask.

`public Color StrokeColor`

:   Border colour. It is drawn over the fill as a band hugging the inside of the silhouette, and it is not masked by a partial fill, so a bar built on a stroked surface keeps a complete outline however low its value runs.

`public float StrokeWidth`

:   Border thickness in reference pixels, drawn inside the silhouette so it never enlarges the surface. Zero, or a fully transparent `StrokeColor`, draws no border.

**Methods**

`public static SkinSurfaceTokens Flat(Color fill, float cornerRadius = 0f)`

:   A flat, strokeless, glowless surface in `fill`.

    - `cornerRadius` &mdash; Corner radius in reference pixels; zero gives square corners.
    - `fill` &mdash; Single color assigned to both surface gradient stops.
    - **Returns** &mdash; A rounded-rect surface with no stroke, glow, or shadow, ready to be built on.

`public SkinSurfaceTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy; this instance is unchanged. `GradientAngleDegrees` wraps into 0..360 rather than clamping, and the colours are left exactly as authored.

`public SkinSurfaceTokens WithFill(Color fill)`

:   Returns this surface with its fill replaced by `fill`.

    - `fill` &mdash; Replacement color written to both gradient stops on the returned copy.
    - **Returns** &mdash; A copy with both gradient stops set to `fill`, so a gradient surface reads as flat until a second stop is set again.

`public SkinSurfaceTokens WithGlow(Color color, float radius, float intensity)`

:   Returns this surface with its glow replaced.

    - `radius` &mdash; Glow radius in reference pixels, measured outward from the silhouette.
    - `intensity` &mdash; Glow strength; above 1 the halo reads as bloom.
    - `color` &mdash; Replacement outer-glow color on the returned token copy.
    - **Returns** &mdash; A copy carrying the new glow. The values are stored as given, so call `Sanitized` if they came from outside the supported ranges.

---

## SkinTargetingTokens

```csharp
public struct SkinTargetingTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

How a target pick is expressed. Two fields, because the interesting
decision is not which of the four presets to use - it is whether to let the
package pick for you.

None of this changes what is legal. Legality stays with the resolver, so a
project can swap presets, or hand the choice to its players as an
accessibility setting, without touching content or invalidating a replay.

**Fields**

`public bool AdaptToDevice`

:   Move to the preset the device and party size call for. A preset that adapts is worth more on a store page than four a buyer has to configure. Off honours `Preset` verbatim, which is what a project with one target platform wants.

`public TargetingPreset Preset`

:   The preset a pick is expressed with. With `AdaptToDevice` on this is the starting point rather than the last word.

**Methods**

`public static SkinTargetingTokens Default()`

:   The shipped default: reticle, adapting to the device.

    - **Returns** &mdash; Reticle with adaptation enabled.

---

## SkinTypographyTokens

```csharp
public struct SkinTypographyTokens
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/BattleSkinTokens.cs</small>

Type sizing and treatment. Fonts stay optional so no font is redistributed.

**Fields**

`public int BodySize`

:   Size of the interface's ordinary text: roster names, skill names, and the tooltip's damage preview.

`public int CaptionSize`

:   Size of small supporting text, and the busiest of the three sizes: it covers combatant plates, bar readouts, log lines, timeline entries, and tooltip cost and timing rows. Several regions derive their row heights from it, so raising it grows those rows rather than overflowing them.

`public TMP_FontAsset DisplayFont`

:   Optional display font for combatant names on the stage plates. Left empty, names use `Font`, so a skin authored before this token existed is unchanged.

`public TMP_FontAsset Font`

:   Optional font. Left empty, the skin falls back to Unity's built-in runtime font, so a skin never depends on a font asset the package would have to redistribute.

`public int HeadingSize`

:   Size of titles. The result banner scales it up further for its headline, so a large value here grows the end-of-battle text faster than it grows a tooltip title.

`public int LabelSize`

:   Size of a tracked, uppercase label: ACTING, TARGET, NOW, CAST, and the card footers. These are read as shapes rather than as words, so they sit between caption and heading and are always drawn with letter spacing. Zero means "derive": the size settles midway between `BodySize` and `HeadingSize`, so a skin authored before this token existed still gets a sensible value rather than the minimum.

`public float LineSpacing`

:   Multiplies the gap between lines of a wrapped label. Most HUD text is a single line, so this mainly affects the feedback log and tooltip body.

`public int NameSize`

:   Size of a combatant's name on the stage nameplate. It is the largest type a player reads mid-turn without stopping, so it is deliberately a step above `BodySize` rather than sharing it. Zero derives it from `HeadingSize`.

`public Color OutlineColor`

:   Colour of that outline. It is read only while `UseOutline` is set, and it should oppose the text colour rather than match the panel behind it: the shipped dark skins outline in black, the neon skin in its own near-black backdrop colour.

`public int TitleSize`

:   Size of the skill announcement banner that crosses the stage on perform. It is display type: it exists to be seen from across a room for half a second, not to be read carefully. Zero derives it from `HeadingSize`.

`public bool UseOutline`

:   Adds a one-pixel contrast outline to every label the skin builds, which is what keeps text readable where it sits directly over the stage. The outline is attached when a label is created, so a skin swapped at runtime applies it on the rebuild rather than to labels already on screen. The two light shipped skins leave it off; their text is already dark against pale panels.

**Methods**

`public SkinTypographyTokens Sanitized()`

:   Clamps every token into its supported range.

    - **Returns** &mdash; A clamped copy; this instance is unchanged. `Font`, `UseOutline`, and `OutlineColor` are left as authored.

---

## WorldFade

```csharp
public struct WorldFade
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/WorldFade.cs</small>

An opacity (or any level between zero and one) that moves toward a target with an ease-out, on whatever clock the caller
advances it with.

It holds no clock of its own: the presenter's presentation clock, a test's manual step or a capture's fixed step all drive it
through `Advance`, so a pause holds it and a speed change scales it. A new target set while it moves starts from
where it is, so a reversal never jumps.

**Properties**

`public bool IsAnimating`

:   True while the level is still moving.

`public float Target`

:   The level the fade is heading for, or has reached.

`public float Value`

:   The level now, between zero and one.

**Methods**

`public bool Advance(float deltaSeconds)`

:   Moves the level along by `deltaSeconds` of the caller's clock.

    - `deltaSeconds` &mdash; Elapsed time; zero or less changes nothing.
    - **Returns** &mdash; True when the level changed.

`public void FadeTo(float level, float seconds)`

:   Starts moving toward `level` from the current level.

    - `level` &mdash; Target level; clamped to zero through one.
    - `seconds` &mdash; How long the move takes; zero or less snaps.

`public void Snap(float level)`

:   Puts the level at `level` at once and stops any fade.

    - `level` &mdash; New level; clamped to zero through one.

---

## WorldFadeTiming

```csharp
public static class WorldFadeTiming
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Skin/WorldFade.cs</small>

How long the things the world draws take to come and go.

Plates, target brackets, ground rings, region fills and the dim that pushes the uninvolved back used to switch on and off
in the frame the state changed, while the dock and the turn ribbon already settled over 130 to 230 milliseconds. A mark
that blinks next to a panel that glides reads as a fault in the mark. Everything the world shows or hides now shares one
curve and one duration, so the stage and the interface move as one thing.

Reduced motion keeps the fade and drops everything else: a fade moves nothing, and a mark that still appears and
disappears in a single frame is exactly the flash a player who asked for less motion does not want either.

**Fields**

`public const float MaximumSeconds`

:   Longest a fade is ever allowed to take, whatever the motion scale.

`public const float ReducedSeconds`

:   Seconds a fade takes while the skin reduces motion: a short fade, not a snap.

`public const float Seconds`

:   Seconds one fade takes at the skin's full motion scale. Ease-out.

`public const float SwapInShare`

:   Share of one fade that the new look takes to arrive when a plate changes shape. Out and in together stay within `MaximumSeconds`.

`public const float SwapOutShare`

:   Share of one fade that the old look takes to leave when a plate changes shape; the new look takes `SwapInShare`.

**Methods**

`public static float For(SkinMotionTokens motion)`

:   The duration of one world fade under a skin's motion tokens.

    - `motion` &mdash; Motion tokens of the skin the element is drawn with.
    - **Returns** &mdash; `ReducedSeconds` while motion is reduced, zero when the motion scale is zero (the element snaps, as every other skinned duration does), and otherwise `Seconds` scaled and capped at `MaximumSeconds`.

---
