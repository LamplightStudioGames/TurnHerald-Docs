# Formations

32 types in this area.

!!! abstract "On this page"
    [AspectRatio](#aspectratio) &middot; [CompiledEncounterFormationLayout](#compiledencounterformationlayout) &middot; [CompiledEncounterFormationTeam](#compiledencounterformationteam) &middot; [CompiledFormationAnchor](#compiledformationanchor) &middot; [CompiledFormationPreset](#compiledformationpreset) &middot; [CompiledFormationSlot](#compiledformationslot) &middot; [FormationArrangement](#formationarrangement) &middot; [FormationArrangements](#formationarrangements) &middot; [FormationFacing](#formationfacing) &middot; [FormationFraming](#formationframing) &middot; [FormationHeightWindow](#formationheightwindow) &middot; [FormationLayoutFallback](#formationlayoutfallback) &middot; [FormationLayoutIssue](#formationlayoutissue) &middot; [FormationLayoutIssueKind](#formationlayoutissuekind) &middot; [FormationLayoutMode](#formationlayoutmode) &middot; [FormationLayoutOptions](#formationlayoutoptions) &middot; [FormationLayoutPlacement](#formationlayoutplacement) &middot; [FormationLayoutResult](#formationlayoutresult) &middot; [FormationLayoutUnit](#formationlayoutunit) &middot; [FormationOccupancy](#formationoccupancy) &middot; [FormationPoint](#formationpoint) &middot; [FormationPresence](#formationpresence) &middot; [FormationPresetDefinition](#formationpresetdefinition) &middot; [FormationSlotDefinition](#formationslotdefinition) &middot; [FormationStageLayout](#formationstagelayout) &middot; [FormationVfxAnchorDefinition](#formationvfxanchordefinition) &middot; [FormationViewport](#formationviewport) &middot; [IStageFloorSource](#istagefloorsource) &middot; [ProjectedFormationPoint](#projectedformationpoint) &middot; [StageFloorPlan](#stagefloorplan) &middot; [StageFloorProp](#stagefloorprop) &middot; [StaticStageFloorSource](#staticstagefloorsource)

## AspectRatio

```csharp
public readonly struct AspectRatio : IEquatable<AspectRatio>
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

The design aspect a formation was authored against, as an exact integer
fraction where `Numerator` is the width term and
`Denominator` the height term. The fraction is never reduced,
so 16/9 and 32/18 are different values. Components outside 1..10,000
(`AuthoringLimits.AspectComponentMaximum`) are reported as a
compile or projection diagnostic rather than rejected here.

**Constructors**

`public AspectRatio(int numerator, int denominator)`

:   Copies the width and height terms without reducing or range-checking the fraction. Compilation reports components outside 1..10,000.

    - `denominator` &mdash; Height term retained verbatim as the fraction's denominator.
    - `numerator` &mdash; Width term retained verbatim as the fraction's numerator.

**Properties**

`public int Denominator`

:   The height term, held to the same 1..`AuthoringLimits.AspectComponentMaximum` range as `Numerator`.

`public int Numerator`

:   The width term of the fraction. Projection and compilation accept 1..`AuthoringLimits.AspectComponentMaximum`; anything else is reported as a diagnostic, so a default-constructed ratio with a zero term fails rather than dividing by zero.

**Methods**

`public bool Equals(AspectRatio other)`

:   Equal only when both terms match, because the fraction is never reduced.

    - `other` &mdash; The value to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override bool Equals(object obj)`

:   Value comparison against a boxed ratio; any other type is never equal.

    - `obj` &mdash; The object to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override int GetHashCode()`

:   Combines both terms; consistent with `Equals(AspectRatio)`.

    - **Returns** &mdash; A deterministic hash code for this value.

---

## CompiledEncounterFormationLayout

```csharp
public sealed class CompiledEncounterFormationLayout
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

The compiled formation for a whole encounter: exactly two teams, plus a
flattened and indexed view of every combatant's seat. This is the object
presentation builds a stage from, and it is fully immutable, so the same
layout can drive a live battle, a headless batch and an editor preview at
once.

**Properties**

`public StableId EncounterId`

:   The encounter this layout was compiled for, carried so a layout handed on its own can still be matched back to the encounter that produced it.

`public FrozenList<FormationOccupancy> Occupancy`

:   Both teams' bindings merged into one list, ascending by combatant id.

`public FrozenSortedIndex<StableId, FormationOccupancy> OccupancyByCombatant`

:   Combatant to seat, as a binary-searchable index over the same records held in `Occupancy`. Use it rather than scanning that list when placing a token or building a start request; every combatant in the encounter has an entry, because an unassigned member fails the compile.

`public FrozenSortedIndex<StableId, StableId> OccupancyBySlot`

:   Seat to occupant: the value is the combatant id standing in that slot, not a full occupancy record. Seats nobody was assigned to are absent.

`public FrozenList<CompiledEncounterFormationTeam> Teams`

:   Both teams, ascending by team id.

---

## CompiledEncounterFormationTeam

```csharp
public sealed class CompiledEncounterFormationTeam
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

One team's half of a compiled encounter layout: the preset it stands in
and which combatant holds which seat. Compilation only succeeds when every
member of the team is assigned to a free seat and all of those seats sit on
one side of the field.

**Properties**

`public FrozenList<FormationOccupancy> Occupancy`

:   This team's combatant-to-seat bindings, ascending by combatant id. Every member is present, because an unassigned member fails the compile.

`public CompiledFormationPreset Preset`

:   A deep copy of the preset the team was compiled against, so the layout stands alone once returned.

`public StableId ResolvedSideId`

:   The one side id shared by every seat this team occupies. Compilation fails if a team's seats disagree, or if both teams resolve to the same side.

`public StableId TeamId`

:   The team this half of the layout belongs to. It is what the two teams of a layout are sorted by, and the two must differ.

---

## CompiledFormationAnchor

```csharp
public readonly struct CompiledFormationAnchor
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

One named attachment point on a compiled slot. Presentation resolves a
beat's VFX position through these, so a slot can offer more than the one
point the combatant stands on. Only the formation compiler creates them,
and `Position` is in the same normalised design space as the
slot's own position.

**Properties**

`public StableId AnchorId`

:   The name a presentation beat asks for this anchor by. It is unique among the anchors of its slot but not across the preset, so two seats may both offer, say, a "muzzle" anchor.

`public FormationPoint Position`

:   Where the anchor sits, in the preset's normalised design space rather than as an offset from the slot, so it is projected exactly as the slot's own position is.

---

## CompiledFormationPreset

```csharp
public sealed class CompiledFormationPreset
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

A validated, immutable formation preset: the seats one team can occupy,
plus the design aspect their coordinates were authored against. Only the
formation compiler creates one, and it stores the slots ascending by slot
id, which is what lets `TryGetSlot` binary search instead of
scanning.

**Properties**

`public AspectRatio DesignAspect`

:   The aspect the slot coordinates were authored for. Projection fits the target viewport to this ratio before mapping any point, so the preset keeps its shape on screens it was not designed for.

`public StableId PresetId`

:   This preset's identity, carried into every `FormationOccupancy` compiled against it so a consumer can tell which preset a seated combatant was placed from.

`public FrozenList<CompiledFormationSlot> Slots`

:   Every seat in the preset, ascending by slot id.

**Methods**

`public bool TryGetSlot(StableId slotId, out CompiledFormationSlot slot)`

:   Looks up one seat by id with a binary search over `Slots`.

    - `slotId` &mdash; Id of the seat to find.
    - `slot` &mdash; The matching seat, or null when the preset declares no such slot.
    - **Returns** &mdash; True when a seat with that id exists.

---

## CompiledFormationSlot

```csharp
public sealed class CompiledFormationSlot
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

One validated seat in a compiled formation preset: where a combatant
stands, which way it faces, how it sorts against the other seats, and
where its anchors are. Only the formation compiler creates these, and
every value on a compiled slot is immutable, so one can be handed to the
stage, an editor preview and a batch run at the same time.

**Properties**

`public FrozenList<CompiledFormationAnchor> Anchors`

:   This seat's anchors, ascending by anchor id, and empty when the slot declares none.

`public FormationPoint ApproachPoint`

:   The point a step-in or approach beat targets, in the same normalised space as `Position`. It is authored per slot rather than derived, so an approach can lead in front of, behind or beside a seat.

`public FormationFacing Facing`

:   Which way the occupant is presented as facing. Compilation rejects any value other than `FormationFacing.Left` or `FormationFacing.Right`, so this is never the enum default.

`public FormationPoint Position`

:   Where the occupant stands, in the preset's normalised design space.

`public StableId RowId`

:   The row this seat belongs to. Rows are a grouping rather than an identity, so several seats normally share one row id, and it is carried through to the combatant's start state where row-based targeting matches on it.

`public StableId SideId`

:   The side of the field this seat sits on. Every seat a team actually occupies must agree on it, which is what stops a team straddling both sides, and it reaches the combatant's start state for side-based targeting.

`public StableId SlotId`

:   This seat's identity, unique within the preset. Encounter assignments name a seat by this id, and it is the key `CompiledFormationPreset.TryGetSlot` searches on.

`public StableId SortingLayerKey`

:   Identifier of the sorting layer this seat belongs to. The package carries it as data only; nothing here assigns it to a Unity sorting layer, so a custom stage decides how to map it.

`public int SortingOrder`

:   Draw order within the sorting layer. The compiler restricts it to -32,768..32,767 (`AuthoringLimits.SortingOrderMinimum` and `AuthoringLimits.SortingOrderMaximum`), so it always fits Unity's own sorting order range.

---

## FormationArrangement

```csharp
public enum FormationArrangement : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationArrangements.cs</small>

The stage shapes a battle can be laid out in.

A formation preset is authored data, so these are not modes the engine
switches between at runtime: they are starting points
`FormationArrangements` can build a preset from, which you then
ship, edit in the Formation Editor, or ignore entirely in favour of placing
every seat by hand.

| Value | Meaning |
| --- | --- |
| `Rank` | One rank per side, standing shoulder to shoulder along a single baseline, in the manner of a party line-up in a 2D dungeon crawler. |
| `Column` | One column per side, stacked up the screen, in the manner of a classic console role-playing game party list. |
| `Stagger` | A column with every second seat pushed toward the centre, so the side reads as a diagonal rather than a straight stack. |
| `Perspective` | Two parallel lines per side, the back one raised and pushed toward the centre so the pair reads as a receding plane. |

---

## FormationArrangements

```csharp
public static class FormationArrangements
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationArrangements.cs</small>

Builds formation presets for the shipped stage arrangements.

The value here is not the coordinates, which anyone could type; it is that
the draw order comes out right. Formation space puts Y at the bottom of the
stage and increases upward, so a seat lower on screen is nearer the camera
and has to be drawn over the seats behind it. Authoring that by hand is easy
to get backwards, and it stays invisible until two silhouettes actually
overlap - by which point the art is in and the formation is hard to change.

**Fields**

`public const int CoordinateMaximum`

:   Normalized coordinate space is 0 to this value on both axes.

`public const int LeftTeamFrontSortingOrder`

:   Sorting order the front seat of the left team receives.

`public const int MaximumSlotsPerSide`

:   Largest number of seats per side these builders will produce.

`public const int RightTeamFrontSortingOrder`

:   Sorting order the front seat of the right team receives.

`public const string SortingLayerKey`

:   Sorting layer key every produced seat carries, matching the shipped starter presets. The compiler rejects an empty key, so this is not optional decoration.

`public const int StaggerInset`

:   How far `FormationArrangement.Stagger` pushes every second seat toward the centre. Wide enough that a broad silhouette still shows an edge past the one in front, narrow enough that the side still reads as one group rather than two.

**Methods**

`public static FormationPresetDefinition Build(string stableIdRaw, FormationArrangement arrangement, int slotsPerSide)`

:   Builds a preset for `arrangement` with `slotsPerSide` seats on each side.

    - `stableIdRaw` &mdash; Stable id for the produced preset.
    - `slotsPerSide` &mdash; Seats per side, 1 to `MaximumSlotsPerSide`.
    - `arrangement` &mdash; Rank, column, staggered-column, or perspective seat geometry to materialize.
    - **Returns** &mdash; A new unsaved preset with deterministic seat coordinates, facing, and front-to-back sorting.

---

## FormationFacing

```csharp
public enum FormationFacing : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationDefinitions.cs</small>

Which way the occupant of a formation slot is presented as facing. It
reaches the battle through presentation only: the built-in 2D stage
mirrors the combatant token's sprite only when the slot facing differs
from its source-art facing (Right by default). Neither name is zero, so
default(FormationFacing) is not a facing at all and preset compilation
rejects any slot carrying a value other than these two.

| Value | Meaning |
| --- | --- |
| `Left` | Faces the formation slot toward decreasing X in projected stage space. |
| `Right` | Faces the formation slot toward increasing X in projected stage space. |

---

## FormationFraming

```csharp
public enum FormationFraming : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationCloseFraming.cs</small>

How the Depth layout frames the formation (`FormationLayoutOptions.Framing`). Wide is the layout as it always was and the
default of every public constructor; Close is the framing the Overlay HUD design asks the stage for. Line and Legacy ignore it.

| Value | Meaning |
| --- | --- |
| `Wide` | The Depth layout as it always was: the group held to 15% of the screen height and a boss to 22-25%. |
| `Close` | The near framing of the Overlay HUD design (Antlerglow C): the group at about a third of the screen height, a boss near half of it, the party anchored at a fifth of the width from ... |

---

## FormationHeightWindow

```csharp
public readonly struct FormationHeightWindow
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

A sprite height window as thousandths of the screen height.

**Constructors**

`public FormationHeightWindow(int minimumPermille, int targetPermille, int maximumPermille)`

:   Creates a window.

    - `minimumPermille` &mdash; Smallest height.
    - `targetPermille` &mdash; Height the average combatant is drawn at.
    - `maximumPermille` &mdash; Largest height.

**Properties**

`public int MaximumPermille`

:   Largest height as a thousandth of the screen height.

`public int MinimumPermille`

:   Smallest height as a thousandth of the screen height.

`public int TargetPermille`

:   Height of the average combatant as a thousandth of the screen height.

---

## FormationLayoutFallback

```csharp
public enum FormationLayoutFallback : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

Why a requested layout mode could not be used and a simpler one took its place.

| Value | Meaning |
| --- | --- |
| `None` | The requested mode was used. |
| `DepthNeedsPerspective` | Depth was requested but the stage declares no horizon, vanishing point and ground line, or the ground line is not below the horizon. |
| `DepthSpriteTooLarge` | Depth was requested but a combatant that is not drawn as a boss has a painted body taller than the 15% of the screen height that perspective scaling is meant for (its whole height ... |
| `CloseNeedsFloor` | Reported only by the Close framing of the Depth layout, which the Overlay HUD design of a later version asks for; no public option selects that framing in this version. |
| `CloseDoesNotFit` | Reported only by the Close framing of the Depth layout (see `CloseNeedsFloor`). |

---

## FormationLayoutIssue

```csharp
public readonly struct FormationLayoutIssue
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

One defect found in a solved layout.

**Constructors**

`public FormationLayoutIssue(FormationLayoutIssueKind kind, StableId combatantId, string propName)`

:   Creates an issue.

    - `kind` &mdash; What is wrong.
    - `combatantId` &mdash; Combatant whose feet are at fault.
    - `propName` &mdash; Name of the prop for `FormationLayoutIssueKind.FootInsideProp`; empty otherwise.

`public FormationLayoutIssue(FormationLayoutIssueKind kind, StableId combatantId, string propName, StableId otherCombatantId)`

:   Creates an issue that involves a second combatant.

    - `kind` &mdash; What is wrong.
    - `combatantId` &mdash; Combatant at fault.
    - `propName` &mdash; Name of the prop for `FormationLayoutIssueKind.FootInsideProp`; empty otherwise.
    - `otherCombatantId` &mdash; The other combatant of `FormationLayoutIssueKind.BodiesOverlap`; the default id otherwise.

**Properties**

`public StableId CombatantId`

:   Combatant whose feet are at fault.

`public FormationLayoutIssueKind Kind`

:   What is wrong.

`public StableId OtherCombatantId`

:   The combatant the body of `CombatantId` overlaps for `FormationLayoutIssueKind.BodiesOverlap`; the default (invalid) id for every other kind.

`public string PropName`

:   Name of the prop that holds the feet, or empty.

---

## FormationLayoutIssueKind

```csharp
public enum FormationLayoutIssueKind : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

A defect the solver found in the standing points it computed.

| Value | Meaning |
| --- | --- |
| `FootAboveFloorBackEdge` | A foot stands above the back edge of the open floor, on the wall or the set behind it. |
| `FootInsideProp` | A foot stands inside a prop of the stage's prop mask. |
| `BodiesOverlap` | Two painted bodies of one side of the Depth layout are closer than the clearance the layout keeps between bodies, or overlap, because the side does not fit the stage even at the sm... |

---

## FormationLayoutMode

```csharp
public enum FormationLayoutMode : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

How a stage turns the seats of a formation into standing points. The seats stay authored data and keep their ids; the mode
decides how the presentation reads them.

| Value | Meaning |
| --- | --- |
| `Line` | The default. |
| `Depth` | Two shallow rows, the back row smaller by perspective from the stage's horizon and vanishing point, standing so that no painted body of a side is on another one: neighbours keep `F... |
| `Legacy` | Legacy. |

---

## FormationLayoutOptions

```csharp
public readonly struct FormationLayoutOptions
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

The knobs of one layout solve.

**Constructors**

`public FormationLayoutOptions(FormationLayoutMode mode, StageFloorPlan floorPlan, int stageShareOfScreenPermille)`

:   Creates options.

    - `mode` &mdash; Layout mode to request.
    - `floorPlan` &mdash; What the stage declares about its floor; null declares nothing.
    - `stageShareOfScreenPermille` &mdash; Height of the stage viewport as a thousandth of the screen height. Sprite heights are fractions of the screen, so this recovers the screen from the viewport. Zero or less uses `DefaultStageShareOfScreenPermille`.

`public FormationLayoutOptions(FormationLayoutMode mode, StageFloorPlan floorPlan, int stageShareOfScreenPermille, int screenHeightPx, StableId playerTeamId)`

:   Creates options that also say how tall the screen really is and which team is the player's.

    - `mode` &mdash; Layout mode to request.
    - `floorPlan` &mdash; What the stage declares about its floor; null declares nothing.
    - `stageShareOfScreenPermille` &mdash; Height of the stage viewport as a thousandth of the screen height. It only matters when `screenHeightPx` is not given. Zero or less uses `DefaultStageShareOfScreenPermille`.
    - `screenHeightPx` &mdash; Height of the whole screen in pixels, when the caller knows it. The layout then sizes everything from it and `FormationLayoutResult.ScreenHeightPx` carries it as given; zero or less recovers the screen height from the viewport and the share, which is off by a pixel or two because the share is a whole number of thousandths.
    - `playerTeamId` &mdash; The team of the player, when the caller knows it; the default id says it does not. See `PlayerTeamId`.

**Properties**

`public int CloseRightLimitPx`

:   With the Close framing: the stage x that no plate of an opposing combatant on the right side may pass, in stage pixels (the left of the button column of the Overlay, less 8 reference pixels, converted and rounded so the limit never moves right); zero keeps only the margin of the viewport. Ignored by every other framing.

`public static FormationLayoutOptions Default`

:   The default: line layout, no declared floor, the dock's stage share.

`public StageFloorPlan FloorPlan`

:   What the stage declares about its floor; null means nothing.

`public FormationFraming Framing`

:   How the Depth layout frames the formation: `FormationFraming.Wide`, as it always did and as every public constructor asks, or `FormationFraming.Close`, the near framing of the Overlay HUD design. Ignored by Line and Legacy.

`public FormationLayoutMode Mode`

:   Layout mode requested.

`public StableId PlayerTeamId`

:   The team of the player, or the default (invalid) id when the caller does not say. With it the Depth layout draws an automatic boss (`FormationPresence.Automatic`) only on the side that opposes the player: a hero alone against two enemies is not a boss unless the author marked it `FormationPresence.Boss`. Without it, or when no unit belongs to that team, either side can have an automatic boss, which is what the layout did before it could be told. The Line layout does not read it.

`public int ScreenHeightPx`

:   Height of the whole screen in pixels, or zero when the caller does not know it and the layout recovers it from the viewport and `StageShareOfScreenPermille`.

`public int StageShareOfScreenPermille`

:   Stage viewport height as a thousandth of the screen height; zero or less means the default. Ignored when `ScreenHeightPx` is given.

**Fields**

`public const int DefaultStageShareOfScreenPermille`

:   The share of the screen height the stage viewport covers when nothing else is known: the 52% the dock layout reserves.

**Methods**

`public FormationLayoutOptions WithCloseRightLimit(int rightLimitPx)`

:   Returns a copy with another limit for the plates of the Close framing.

    - `rightLimitPx` &mdash; Stage x no opposing plate may pass; zero or less keeps only the margin of the viewport.
    - **Returns** &mdash; The new options.

`public FormationLayoutOptions WithFloorPlan(StageFloorPlan floorPlan)`

:   Returns a copy with another floor plan.

    - `floorPlan` &mdash; Floor plan to use.
    - **Returns** &mdash; The new options.

`public FormationLayoutOptions WithFraming(FormationFraming framing)`

:   Returns a copy with another framing.

    - `framing` &mdash; Framing to request.
    - **Returns** &mdash; The new options.

`public FormationLayoutOptions WithMode(FormationLayoutMode mode)`

:   Returns a copy with another mode.

    - `mode` &mdash; Mode to request.
    - **Returns** &mdash; The new options.

`public FormationLayoutOptions WithPlayerTeam(StableId playerTeamId)`

:   Returns a copy that knows which team is the player's.

    - `playerTeamId` &mdash; The team of the player; the default id says the caller does not know.
    - **Returns** &mdash; The new options.

`public FormationLayoutOptions WithScreenHeight(int screenHeightPx)`

:   Returns a copy that knows how tall the screen is.

    - `screenHeightPx` &mdash; Height of the whole screen in pixels; zero or less goes back to recovering it from the viewport and the share.
    - **Returns** &mdash; The new options.

---

## FormationLayoutPlacement

```csharp
public readonly struct FormationLayoutPlacement
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

Where one combatant stands and how big it is drawn.

**Constructors**

`public FormationLayoutPlacement(StableId combatantId, int footX, int footY, int heightPx, int paintedWidthPx, int scalePermille, int rank, int rankCount, int sortingOrder, int row)`

:   Creates a placement.

    - `combatantId` &mdash; Combatant placed.
    - `footX` &mdash; Horizontal position of the feet in stage pixels.
    - `footY` &mdash; Vertical position of the feet in stage pixels.
    - `heightPx` &mdash; Drawn height from the feet to the head line in stage pixels.
    - `paintedWidthPx` &mdash; Drawn width of the painted body in stage pixels.
    - `scalePermille` &mdash; Art scale as a thousandth, or zero when the art was not measured and the stage keeps its own scale.
    - `rank` &mdash; Order from the centre of its side: zero is the front.
    - `rankCount` &mdash; Number of combatants on its side.
    - `sortingOrder` &mdash; Draw order to use.
    - `row` &mdash; Row of the depth layout: zero is the front row. Always zero in the line layout.

`public FormationLayoutPlacement(StableId combatantId, int footX, int footY, int heightPx, int paintedWidthPx, int scalePermille, int rank, int rankCount, int sortingOrder, int row, bool isBoss, int presenceScalePermille)`

:   Creates a placement that says whether the combatant is drawn as a boss.

    - `combatantId` &mdash; Combatant placed.
    - `footX` &mdash; Horizontal position of the feet in stage pixels.
    - `footY` &mdash; Vertical position of the feet in stage pixels.
    - `heightPx` &mdash; Drawn height from the feet to the head line in stage pixels.
    - `paintedWidthPx` &mdash; Drawn width of the painted body in stage pixels.
    - `scalePermille` &mdash; Art scale as a thousandth, or zero when the art was not measured and the stage keeps its own scale.
    - `rank` &mdash; Order from the centre of its side: zero is the front.
    - `rankCount` &mdash; Number of combatants on its side.
    - `sortingOrder` &mdash; Draw order to use.
    - `row` &mdash; Row of the depth layout: zero is the front row.
    - `isBoss` &mdash; True when the combatant is drawn as a boss.
    - `presenceScalePermille` &mdash; How much larger the combatant is drawn than it would be as a standard member of the same formation, as a thousandth; 1000 for a standard member.

**Properties**

`public StableId CombatantId`

:   Combatant placed.

`public int FootX`

:   Horizontal position of the feet in stage pixels.

`public int FootY`

:   Vertical position of the feet in stage pixels, increasing upward.

`public int HeightPx`

:   Drawn height from the feet to the head line in stage pixels: the layout's own measure, which the plates and the art scale follow. The painted body of a unit that declared `FormationLayoutUnit.NaturalPaintedHeightPx` is drawn that tall times `ScalePermille` over a thousand, and that body is what the Depth layout holds to 15% and 22-25%.

`public bool IsBoss`

:   True when the combatant is drawn as a boss: declared with `FormationPresence.Boss`, or alone against a larger group.

`public int PaintedWidthPx`

:   Drawn width of the painted body in stage pixels.

`public int PresenceScalePermille`

:   How much larger the combatant is drawn than it would be as a standard member of the same formation, as a thousandth: 1000 for a standard member, and for a boss the ratio of its height to the height it would have had without the boss rule. The stage scales the bar under a boss with it.

`public int Rank`

:   Order from the centre of its side: zero is the front.

`public int RankCount`

:   Number of combatants on its side.

`public int Row`

:   Row of the depth layout; zero in the line layout.

`public int ScalePermille`

:   Art scale as a thousandth; zero when the art was not measured.

`public int SortingOrder`

:   Draw order to use.

---

## FormationLayoutResult

```csharp
public sealed class FormationLayoutResult
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

The outcome of one layout solve.

**Properties**

`public FormationLayoutFallback Fallback`

:   Why the requested mode was not used, or, with the Close framing, why the framing could not be kept as asked.

`public int GroundLineY`

:   Height of the ground line the feet stand on, in stage pixels.

`public bool HasBoss`

:   True when a combatant is drawn as a boss: declared with `FormationPresence.Boss`, or alone against a larger group (three or more in the line layout, two or more in the depth layout, where only the side that opposes the player can have one when the options say which team that is). A lone boss is drawn larger and centred on its half.

`public IReadOnlyList<FormationLayoutIssue> Issues`

:   Defects found in the solved positions.

`public FormationLayoutMode Mode`

:   Mode that was used; differs from `RequestedMode` only when `Fallback` is not none. The one exception is the Close framing of the Depth layout (no public option selects it in this version): it stays Depth whatever its fallback, so there the mode equals the requested one while `Fallback` says why the framing could not be kept as asked.

`public IReadOnlyList<FormationLayoutPlacement> Placements`

:   One placement per input unit, in input order.

`public int PopulationPerSide`

:   Number of combatants on the larger side; it picks the sprite height from `FormationStageLayout.LineHeights`.

`public FormationLayoutMode RequestedMode`

:   Mode that was asked for.

`public int ScreenHeightPx`

:   Screen height the sizes were taken from, in stage pixels: the height the options carried (`FormationLayoutOptions.ScreenHeightPx`) or, when they carried none, the one recovered from the viewport and its share of the screen, which can be a pixel or two off. The percentages of a receipt are of this height.

**Methods**

`public bool TryGetPlacement(StableId combatantId, out FormationLayoutPlacement placement)`

:   Finds the placement of a combatant.

    - `combatantId` &mdash; Combatant to find.
    - `placement` &mdash; Receives the placement.
    - **Returns** &mdash; True when the combatant was placed.

---

## FormationLayoutUnit

```csharp
public readonly struct FormationLayoutUnit
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

One combatant to place: where its seat projects to and how big its art is.

**Constructors**

`public FormationLayoutUnit(StableId combatantId, StableId teamId, StableId slotId, int sourceX, int sourceY, int sortingOrder, int naturalHeightPx, int naturalPaintedWidthPx, int naturalPaintedOffsetPx = 0, int naturalFaceMinPx = 0, int naturalFaceMaxPx = 0)`

:   Creates a unit.

    - `combatantId` &mdash; Combatant standing in the seat.
    - `teamId` &mdash; Team of the combatant.
    - `slotId` &mdash; Seat the combatant occupies.
    - `sourceX` &mdash; Projected X of the authored seat, in stage pixels.
    - `sourceY` &mdash; Projected Y of the authored seat, in stage pixels, increasing upward.
    - `sortingOrder` &mdash; Authored draw order of the seat.
    - `naturalHeightPx` &mdash; Height of the art from its ground anchor to the head line at scale one, in 1080p-reference pixels; zero when unknown.
    - `naturalPaintedWidthPx` &mdash; Width of the painted body at scale one in the same pixels; zero when unknown.
    - `naturalPaintedOffsetPx` &mdash; How far the middle of the painted body lies right of the ground anchor at scale one, in the same pixels, as the art is drawn on its side (already mirrored when the sprite is flipped).
    - `naturalFaceMinPx` &mdash; Left edge of the face, measured from the middle of the painted body at scale one, as the art is drawn on its side (already mirrored when flipped). Equal to `naturalFaceMaxPx` when unknown.
    - `naturalFaceMaxPx` &mdash; Right edge of the face, measured the same way.

`public FormationLayoutUnit(StableId combatantId, StableId teamId, StableId slotId, int sourceX, int sourceY, int sortingOrder, int naturalHeightPx, int naturalPaintedWidthPx, int naturalPaintedOffsetPx, int naturalFaceMinPx, int naturalFaceMaxPx, FormationPresence presence)`

:   Creates a unit that states how it wants to be drawn against the others.

    - `combatantId` &mdash; Combatant standing in the seat.
    - `teamId` &mdash; Team of the combatant.
    - `slotId` &mdash; Seat the combatant occupies.
    - `sourceX` &mdash; Projected X of the authored seat, in stage pixels.
    - `sourceY` &mdash; Projected Y of the authored seat, in stage pixels, increasing upward.
    - `sortingOrder` &mdash; Authored draw order of the seat.
    - `naturalHeightPx` &mdash; Height of the art from its ground anchor to the head line at scale one, in 1080p-reference pixels; zero when unknown.
    - `naturalPaintedWidthPx` &mdash; Width of the painted body at scale one in the same pixels; zero when unknown.
    - `naturalPaintedOffsetPx` &mdash; How far the middle of the painted body lies right of the ground anchor at scale one, in the same pixels, as the art is drawn on its side.
    - `naturalFaceMinPx` &mdash; Left edge of the face, measured from the middle of the painted body at scale one.
    - `naturalFaceMaxPx` &mdash; Right edge of the face, measured the same way.
    - `presence` &mdash; Whether the combatant is drawn as a boss, as a standard member, or as the layout decides.

`public FormationLayoutUnit(StableId combatantId, StableId teamId, StableId slotId, int sourceX, int sourceY, int sortingOrder, int naturalHeightPx, int naturalPaintedWidthPx, int naturalPaintedOffsetPx, int naturalFaceMinPx, int naturalFaceMaxPx, FormationPresence presence, int naturalPaintedHeightPx)`

:   Creates a unit that also says how tall its painted body is, which is the height the Depth layout holds the group and the boss to.

    - `combatantId` &mdash; Combatant standing in the seat.
    - `teamId` &mdash; Team of the combatant.
    - `slotId` &mdash; Seat the combatant occupies.
    - `sourceX` &mdash; Projected X of the authored seat, in stage pixels.
    - `sourceY` &mdash; Projected Y of the authored seat, in stage pixels, increasing upward.
    - `sortingOrder` &mdash; Authored draw order of the seat.
    - `naturalHeightPx` &mdash; Height of the art from its ground anchor to the head line at scale one, in 1080p-reference pixels; zero when unknown.
    - `naturalPaintedWidthPx` &mdash; Width of the painted body at scale one in the same pixels; zero when unknown.
    - `naturalPaintedOffsetPx` &mdash; How far the middle of the painted body lies right of the ground anchor at scale one, in the same pixels, as the art is drawn on its side.
    - `naturalFaceMinPx` &mdash; Left edge of the face, measured from the middle of the painted body at scale one.
    - `naturalFaceMaxPx` &mdash; Right edge of the face, measured the same way.
    - `presence` &mdash; Whether the combatant is drawn as a boss, as a standard member, or as the layout decides.
    - `naturalPaintedHeightPx` &mdash; Height of the painted body at scale one: from the ground anchor to its highest opaque pixel, in the same pixels. Zero when unknown.

**Properties**

`public StableId CombatantId`

:   Combatant standing in the seat.

`public int NaturalFaceMaxPx`

:   Right edge of the face from the middle of the painted body at scale one.

`public int NaturalFaceMinPx`

:   Left edge of the face from the middle of the painted body at scale one; equal to `NaturalFaceMaxPx` when unknown.

`public int NaturalHeightPx`

:   Art height from the ground anchor to the head line at scale one, in 1080p-reference pixels; zero when unknown.

`public int NaturalPaintedHeightPx`

:   Height of the painted body at scale one, in 1080p-reference pixels: from the ground anchor to the highest pixel that is opaque, which is a little under `NaturalHeightPx` for a figure that leaves empty canvas above its head and a little over it for one that fills its cell. The Depth layout holds the group to 15% of the screen height and a boss to 22-25% in this height, the one a ruler on the screen reads, and keeps `NaturalHeightPx` for everything else. Zero when unknown, and then the layout measures the unit by `NaturalHeightPx`; so does it for a value under 30% or over 120% of that height, which can only be a mistake. The Line layout does not read it.

`public int NaturalPaintedOffsetPx`

:   How far the middle of the painted body lies right of the ground anchor at scale one, in the same pixels.

`public int NaturalPaintedWidthPx`

:   Painted body width at scale one in the same pixels; zero when unknown.

`public FormationPresence Presence`

:   Whether the combatant is drawn as a boss, as a standard member, or as the layout decides. `FormationPresence.Automatic` unless stated.

`public StableId SlotId`

:   Seat the combatant occupies.

`public int SortingOrder`

:   Authored draw order of the seat.

`public int SourceX`

:   Projected X of the authored seat.

`public int SourceY`

:   Projected Y of the authored seat.

`public StableId TeamId`

:   Team of the combatant.

---

## FormationOccupancy

```csharp
public readonly struct FormationOccupancy
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

The resolved binding of one combatant to one seat, with the team, preset,
row and side that seat belongs to copied in so a consumer never has to
walk back to the preset to draw or query a combatant. The compiler
guarantees a combatant appears at most once and that no two combatants
share a slot.

**Properties**

`public StableId CombatantId`

:   The combatant standing in the seat. Every occupancy list is sorted on it and `CompiledEncounterFormationLayout.OccupancyByCombatant` is keyed on it; the seat-first index `CompiledEncounterFormationLayout.OccupancyBySlot` is keyed on the slot id instead and only carries this id as its value. It appears exactly once across the whole layout.

`public StableId PresetId`

:   The preset the seat was taken from, so a consumer holding only this record can still name the layout the combatant was placed by.

`public StableId RowId`

:   The seat's row, copied from the slot. The encounter compiler passes it straight into the combatant's start state, so row-based targeting in the battle matches on this value.

`public StableId SideId`

:   The seat's side, copied from the slot and likewise carried into the combatant's start state for side-based targeting. Every occupancy on a team shares it.

`public StableId SlotId`

:   The seat itself. Look it up in the team's preset to reach the position, facing, sorting values and anchors.

`public StableId TeamId`

:   The team the combatant fights for.

---

## FormationPoint

```csharp
public readonly struct FormationPoint : IEquatable<FormationPoint>
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

A resolution-independent position inside a formation preset. Both
components are integers from 0 to 1,000,000
(`AuthoringLimits.NormalizedCoordinateMaximum`), measured from
the bottom-left corner of the design rectangle, and the compiler rejects
any slot or anchor that falls outside that range. The space is integral on
purpose: projection uses integer arithmetic only, so the same preset lands
on the same pixels on every platform.

**Constructors**

`public FormationPoint(int x, int y)`

:   Copies authored X/Y coordinates in formation reference units. Range and overlap checks occur during compilation.

    - `x` &mdash; Horizontal position, 0 at the design rectangle's left edge.
    - `y` &mdash; Vertical position, 0 at the design rectangle's bottom edge.

**Properties**

`public int X`

:   Horizontal position, 0 at the design rectangle's left edge and `AuthoringLimits.NormalizedCoordinateMaximum` at its right, whatever pixel width the preset is eventually projected into.

`public int Y`

:   Vertical position on the same normalised scale, measured upward from the design rectangle's bottom edge.

**Methods**

`public bool Equals(FormationPoint other)`

:   Equal only when both components match.

    - `other` &mdash; The value to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override bool Equals(object obj)`

:   Value comparison against a boxed point; any other type is never equal.

    - `obj` &mdash; The object to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override int GetHashCode()`

:   Combines both components; consistent with `Equals(FormationPoint)`.

    - **Returns** &mdash; A deterministic hash code for this value.

---

## FormationPresence

```csharp
public enum FormationPresence : byte
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

How a combatant asks to be drawn against the others. It is presentation data of the stage, not of the catalog: it travels with
the token prototype or is set on the stage, and the line and the depth layout both read it.

| Value | Meaning |
| --- | --- |
| `Automatic` | The layout decides. |
| `Boss` | Always drawn as a boss: larger than the formation, and centred on its side when it stands alone. |
| `Standard` | Never drawn as a boss, even alone against a larger group. |

---

## FormationPresetDefinition

**Start here**

```csharp
public sealed class FormationPresetDefinition : StableIdDefinition
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationPresetDefinition.cs</small>

Mutable Unity authoring data. Compilation snapshots every value and returns
engine-independent immutable records; this object is never retained.

**Properties**

`public int DesignAspectDenominator`

:   Denominator of that same authored aspect, under the same bounds.

`public int DesignAspectNumerator`

:   Numerator of the aspect ratio the slot coordinates were authored against. Projection fits the target viewport to this ratio before mapping any point, so the preset keeps its shape on screens it was not designed for. It must be between 1 and `AuthoringLimits.AspectComponentMaximum` to compile.

`public IReadOnlyList<FormationSlotDefinition> Slots`

:   The seats authored on this preset, in authored order. This is the live backing list rather than a copy, and it is null when the preset was built from a null sequence, which compilation reports as an error instead of reading as a preset with no seats.

**Methods**

`public static FormationPresetDefinition CreateTransient(string stableIdRaw, int aspectNumerator, int aspectDenominator, IEnumerable<FormationSlotDefinition> formationSlots, int schemaVersion = CurrentSchemaVersion)`

:   Explicit in-memory construction hook for tests and customer tooling. It creates no asset, GUID, or implicit persistent mutation.

    - `stableIdRaw` &mdash; Preset ID text, stored verbatim. It is not checked here: empty or invalid ID text becomes a compile diagnostic instead.
    - `aspectNumerator` &mdash; Numerator of the design aspect the slots are authored against.
    - `aspectDenominator` &mdash; Denominator of that design aspect.
    - `formationSlots` &mdash; The slots to copy. The copy is bounded, but not trimmed to a valid preset: a sequence longer than `AuthoringLimits.FormationSlotsPerPreset` compiles to a collection-limit error, and null leaves the preset with no slot list at all, which is an error of its own.
    - `schemaVersion` &mdash; Authoring schema version to stamp. Any value other than the current one fails validation rather than being migrated in place.
    - **Returns** &mdash; A new unsaved instance holding a copy of the slots. It belongs to no catalog, so the caller keeps it alive and adds it to one itself.

---

## FormationSlotDefinition

```csharp
public sealed class FormationSlotDefinition
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationDefinitions.cs</small>

Mutable Unity authoring data for one seat in a formation preset: where a
combatant stands, which way it faces, how it sorts against the other
seats, where a step-in beat leads, and which named VFX anchors it offers.
Compilation validates every value and snapshots it into an immutable
`CompiledFormationSlot`; this object is never retained. Its
four id fields are all stored as raw text and every one of them must parse
as a non-empty id, so a half-filled seat fails the preset rather than
compiling to a default.

**Constructors**

`public FormationSlotDefinition()`

:   Creates a seat with empty ids at the origin, facing `FormationFacing.Right` and declaring no anchors, as the inspector does when you add a list entry. Its empty ids fail compilation, so it has to be filled in before the preset builds.

`public FormationSlotDefinition(string slotIdRaw, string rowIdRaw, string sideIdRaw, int normalizedX, int normalizedY, FormationFacing formationFacing, string sortingLayerKeyRaw, int authoredSortingOrder, int normalizedApproachX, int normalizedApproachY, IEnumerable<FormationVfxAnchorDefinition> vfxAnchors)`

:   Creates a seat from authored values. Nothing is validated here: parsing, range and uniqueness checks belong to the deterministic compiler, so a bad value surfaces as a compile diagnostic rather than an exception from this call.

    - `slotIdRaw` &mdash; Seat id text. It must be non-empty, valid id text and unique within the preset; a duplicate is a compile error.
    - `rowIdRaw` &mdash; Grouping id for the row this seat sits in. It must be non-empty, valid id text, but it is shared freely: several seats normally carry the same row id.
    - `sideIdRaw` &mdash; Grouping id for the side of the field this seat sits on. It must be non-empty, valid id text, and every seat a team actually occupies has to agree on it, so a team cannot straddle two sides.
    - `normalizedX` &mdash; Horizontal stand position in normalised design space; see `PositionX`.
    - `normalizedY` &mdash; Vertical stand position in the same space; see `PositionY`.
    - `formationFacing` &mdash; Presented facing. It must be `FormationFacing.Left` or `FormationFacing.Right`; the enum's default value is not valid.
    - `sortingLayerKeyRaw` &mdash; Sorting layer id text, carried as data only. It must be non-empty, valid id text, but the package never assigns it to a Unity sorting layer: a custom stage decides what it maps to.
    - `authoredSortingOrder` &mdash; Draw order within that layer. Compilation restricts it to `AuthoringLimits.SortingOrderMinimum`..`AuthoringLimits.SortingOrderMaximum`, which is Unity's own sorting order range.
    - `normalizedApproachX` &mdash; Horizontal component of the approach point; see `ApproachX`.
    - `normalizedApproachY` &mdash; Vertical component of the approach point; see `ApproachY`.
    - `vfxAnchors` &mdash; Named anchors for this seat. The sequence is copied immediately, so later changes to it do not reach the slot, and enumeration stops one past `AuthoringLimits.VfxAnchorsPerSlot` so an over-long or endless sequence is reported by compilation instead of being read to exhaustion. Passing null leaves `Anchors` null, which compilation treats as an error rather than as an empty list.

**Properties**

`public IReadOnlyList<FormationVfxAnchorDefinition> Anchors`

:   The anchors authored on this seat, in authored order. This is the live backing list rather than a copy, and it is null when the slot was constructed from a null sequence, which compilation reports as an error instead of reading as an empty list.

`public int ApproachX`

:   Horizontal component of the point a step-in or approach beat targets, in the same normalised space as `PositionX`. It is authored rather than derived, so an approach can lead in front of, behind or beside the seat.

`public int ApproachY`

:   Vertical component of the approach point, in the same normalised space as `PositionY`.

`public FormationFacing Facing`

:   Which way the occupant of this seat is presented as facing. It reaches the battle through presentation only, where the built-in 2D stage mirrors the token's sprite only when this differs from its source-art facing (Right by default). It must be one of the two named values, because the enum's default is not a facing and compilation rejects it.

`public int PositionX`

:   Horizontal stand position in the preset's normalised design space, running 0 at the left edge to `AuthoringLimits.NormalizedCoordinateMaximum` at the right. Anything outside that range fails compilation; two seats sharing a position only warn.

`public int PositionY`

:   Vertical stand position in the same normalised space, measured upward from the bottom edge.

`public string RowIdRaw`

:   The authored row id as text, empty when unset.

`public string SideIdRaw`

:   The authored side id as text, empty when unset. Every seat a team occupies must carry the same side id, so this is what decides which side of the field the team lands on.

`public string SlotIdRaw`

:   The authored seat id as text, empty when unset and never null. It is unparsed: compilation turns it into the id assignments and lookups use.

`public string SortingLayerKeyRaw`

:   The authored sorting layer id as text, empty when unset. The package carries it as data only; nothing here assigns it to a Unity sorting layer, so a custom stage decides how to map it.

`public int SortingOrder`

:   Draw order within the sorting layer. Compilation restricts it to -32,768..32,767, which is Unity's own sorting order range.

---

## FormationStageLayout

```csharp
public static class FormationStageLayout
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

The line and depth layouts. All arithmetic is integer, so the same input lands on the same pixels on every platform.

**Fields**

`public const int AutoBossMinimumOpponentsDepth`

:   Opponents a combatant alone on its side must face to be drawn as a boss without declaring it, in the depth layout.

`public const int AutoBossMinimumOpponentsLine`

:   Opponents a combatant alone on its side must face to be drawn as a boss without declaring it, in the line layout.

`public const int BossCentreOffsetPermille`

:   Distance of a lone boss from the centre, as a thousandth of the viewport width.

`public const int BossMaximumHeightPermille`

:   Tallest a boss may be, as a thousandth of the screen height.

`public const int BossScalePermille`

:   How much larger than the others a lone boss is drawn, as a thousandth.

`public const int DefaultBodyAspectPermille`

:   Width-to-height ratio of a painted body, in thousandths, when the art was not measured.

`public const int DefaultGroundAboveBottomPermille`

:   Height of the feet above the stage viewport's bottom when the stage declares no ground line, as a thousandth of the screen height.

`public const int DepthBodyClearancePixels`

:   Clear pixels the depth layout keeps between the painted bodies of one side, at the 1080-pixel reference height; the layout scales it with the screen (never below two pixels). Painted bodies, not sprite cells, because cells are mostly air.

`public const int DepthMaximumNaturalHeightPermille`

:   Tallest art the depth layout accepts at scale one for a member of the group, as a thousandth of the 1080-pixel reference height, and the tallest a member of the group is drawn: 15% of the screen height, measured on its painted body (its whole height to the head line when it does not declare how tall the painted body is). A boss is not held to it; see `DepthBossHeights`.

`public const int DepthMinimumShrinkPermille`

:   Smallest size, as a thousandth, the depth layout shrinks the combatants to when a side does not fit the stage with the clearance between bodies. Past it the side is compressed and `FormationLayoutIssueKind.BodiesOverlap` is reported.

`public const int DepthRowGapPermille`

:   Vertical gap of the depth layout's rows, as a thousandth of the tallest group member's sprite height on the side. The depth layout promises at most 350.

`public const int EdgeMarginPermille`

:   Margin kept free at each side of the viewport, as a thousandth of its width.

`public const int FaceClearancePixels`

:   Clear pixels kept between the face of a combatant and the body of the neighbour that draws over it.

`public const int HalfCentreGapPermille`

:   Half the empty space between the two front combatants, as a thousandth of the viewport width.

`public const int LargeOverlapPermille`

:   Overlap aimed for with six or more combatants a side. The line is longest here, so it is packed a little tighter to stay clear of the edges of the plate.

`public const int MaximumLeanPermille`

:   Furthest the whole formation leans away from the centre of the viewport to keep a side clear of the edge or a prop, as a thousandth of the viewport width.

`public const int MaximumOverlapPermille`

:   Largest neighbour overlap accepted, as a thousandth of the narrower silhouette.

`public const int MaximumRankDarkeningPermille`

:   Heaviest darkening the line layout applies to a combatant behind the front, as a thousandth.

`public const int MediumOverlapPermille`

:   Overlap aimed for with four or five combatants a side.

`public const int MinimumOverlapPermille`

:   Smallest neighbour overlap accepted, as a thousandth of the narrower silhouette.

`public const int PlateClearancePixels`

:   Pixels kept between the canvas of a world plate and the event strip: the dock layout asks for 12 between its visible card and the strip, the card's backing reaches about 6 beyond the canvas, and two more absorb rounding.

`public const int PlateFloorBelowStagePermille`

:   Gap between the stage viewport's bottom and the top of the event strip, as a thousandth of the screen height: where a world bar must stop.

`public const int PropClearancePixels`

:   Clear pixels a foot keeps from a prop on the ground line.

`public const int ReferenceScreenHeight`

:   Reference screen height that natural art heights are measured against.

`public const int TargetOverlapPermille`

:   Overlap of neighbouring silhouettes the line layout aims for with up to three combatants a side, as a thousandth of the narrower silhouette.

`public const int VanishingLeanPermille`

:   How far a receding row of the depth layout leans toward the vanishing point, as a thousandth of the full perspective pull.

**Methods**

`public static int DefaultGroundLineY(FormationViewport viewport, int stageShareOfScreenPermille)`

:   The height of the feet when the stage declares no ground line: just above the bottom of the stage viewport, which the dock layout keeps clear of the event strip.

    - `viewport` &mdash; Stage viewport.
    - `stageShareOfScreenPermille` &mdash; Share of the screen the viewport covers.
    - **Returns** &mdash; Height of the feet in stage pixels.

`public static FormationHeightWindow DepthBossHeights()`

:   Heights of a boss in the depth layout: 22-25% of the screen height, 22.5% for a boss whose art is as tall as the group's. The unit is the painted body, from its lowest to its highest opaque pixel, which is what a ruler laid on the screen reads; the group of the depth layout stays at 15% or less in the same unit. A unit that declares `FormationLayoutUnit.NaturalPaintedHeightPx` is drawn so that its painted body fills the window, and the height from its feet to the head line (`FormationLayoutPlacement.HeightPx`) comes out as much taller as its art leaves canvas empty above the head; a unit that does not is measured by the height to the head line, the most the layout can know of it.

    - **Returns** &mdash; The height window as thousandths of the screen height.

`public static FormationHeightWindow LineHeights(int populationPerSide)`

:   Sprite heights of the line layout by combatants on the larger side: 36-38% of the screen at one, 32-36% at three, 26-28% at four and 22-24% at five and six. The empty stage of the Line preset asked for larger casts than the first measurement of the reference battle screens (about 28% at three); the dock and the event strip give the height back (together at most 26% of the screen). Six a side aims at 22.6% but may go down to 20%: the open floor of the sample stages is the same width on a 16:10 screen as on a 16:9 one while the sprites grow with the height, and the overlap may not pass 25%. Two is interpolated between one and three; seven and more continue the decline.

    - `populationPerSide` &mdash; Combatants on the larger side; values below one use one.
    - **Returns** &mdash; The height window as thousandths of the screen height.

`public static int PlateFloorY(FormationViewport viewport, int stageShareOfScreenPermille)`

:   The lowest height a world plate may reach: the clear space the dock layout wants above the event strip. Bare bars and the whole plates of a stress preview stop here.

    - `viewport` &mdash; Stage viewport.
    - `stageShareOfScreenPermille` &mdash; Share of the screen the viewport covers.
    - **Returns** &mdash; Height in stage pixels.

`public static int ScreenHeight(FormationViewport viewport, int stageShareOfScreenPermille)`

:   Recovers the screen height from the stage viewport height and its share of the screen. The viewport is a whole number of pixels and the share a whole number of thousandths, so the answer can be a pixel or two off the real screen (719 or 721 for 720, 1081 for 1080): a caller that knows the screen height says so in `FormationLayoutOptions.ScreenHeightPx` instead.

    - `viewport` &mdash; Stage viewport.
    - `stageShareOfScreenPermille` &mdash; Share of the screen the viewport covers; zero or less uses the dock's 52%.
    - **Returns** &mdash; Screen height in pixels.

`public static FormationLayoutResult Solve(FormationViewport viewport, FormationLayoutOptions options, IReadOnlyList<FormationLayoutUnit> units)`

:   Places every unit. Line puts all feet on one ground line, sizes them by population, spaces neighbours for an overlap of 15-25% and orders each side from the centre outward. Depth stands two shallow rows with perspective scale, holds the group to 15% of the screen height and a boss to 22-25% in the painted body, and draws an automatic boss only on the side that opposes the player when the options name the player's team. Legacy returns the authored positions untouched.

    - `viewport` &mdash; Stage viewport in pixels.
    - `options` &mdash; Mode, floor plan, screen share, and optionally the real height of the screen and the team of the player.
    - `units` &mdash; Combatants to place with their projected seats and measured art.
    - **Returns** &mdash; One placement per unit, in input order, plus any defect found.

---

## FormationVfxAnchorDefinition

```csharp
public sealed class FormationVfxAnchorDefinition
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationDefinitions.cs</small>

Mutable Unity authoring data for one named point on a formation slot that
a presentation beat can target instead of the slot itself. Compilation
validates every value and snapshots it into an immutable
`CompiledFormationAnchor`; this object is never retained.

**Constructors**

`public FormationVfxAnchorDefinition()`

:   Creates an anchor with an empty id at the origin, as the inspector does when you add a list entry. The empty id fails compilation, so an anchor created this way has to be filled in before the preset builds.

`public FormationVfxAnchorDefinition(string anchorIdRaw, int normalizedX, int normalizedY)`

:   Creates an anchor from authored values. Nothing is validated here: parsing and range checks belong to the deterministic compiler, so an out-of-range or unparsable value surfaces as a compile diagnostic rather than an exception from this call.

    - `anchorIdRaw` &mdash; Anchor id text. It must be non-empty, valid id text and unique among the anchors of its slot, or preset compilation fails. Null is stored as the empty string.
    - `normalizedX` &mdash; Horizontal position in the preset's normalised design space; see `PositionX`.
    - `normalizedY` &mdash; Vertical position in the same space; see `PositionY`.

**Properties**

`public string AnchorIdRaw`

:   The authored anchor id as text, empty when unset. It is never null, and it is unparsed: compilation turns it into the id the stage looks anchors up by.

`public int PositionX`

:   Horizontal position in the preset's normalised design space, running 0 at the left edge to `AuthoringLimits.NormalizedCoordinateMaximum` at the right. Anything outside that range fails compilation.

`public int PositionY`

:   Vertical position in the same normalised space, measured upward from the bottom edge.

---

## FormationViewport

```csharp
public readonly struct FormationViewport : IEquatable<FormationViewport>
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

The screen-space rectangle a formation is projected into, in pixels, with
the origin at `Left`/`Bottom` and Y increasing
upward. Width and height must both be positive or projection fails with a
diagnostic instead of throwing. The projector treats this rectangle as a
bound, not as the frame the slots land in: it first shrinks the rectangle
to the preset's design aspect and centres the result inside it.

**Constructors**

`public FormationViewport(int left, int bottom, int width, int height)`

:   Copies the viewport origin and size in integer pixels. Projection reports non-positive dimensions instead of dividing by them.

    - `left` &mdash; Left edge in pixels.
    - `bottom` &mdash; Bottom edge in pixels; the rectangle grows upward.
    - `width` &mdash; Width in pixels. Projection fails unless positive.
    - `height` &mdash; Height in pixels. Projection fails unless positive.

**Properties**

`public int Bottom`

:   Bottom edge in pixels. The rectangle grows upward from here, so this is the low Y edge rather than the top one.

`public int Height`

:   Height in pixels, under the same positive-value and overflow rules as `Width`.

`public int Left`

:   Left edge in pixels, with X increasing to the right.

`public int Width`

:   Width in pixels. Projection fails with a diagnostic when it is zero or negative, and also when `Left` plus this width would overflow, so a degenerate rectangle never reaches the slot mapping.

**Methods**

`public bool Equals(FormationViewport other)`

:   Equal only when all four edges match.

    - `other` &mdash; The value to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override bool Equals(object obj)`

:   Value comparison against a boxed viewport; any other type is never equal.

    - `obj` &mdash; The object to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override int GetHashCode()`

:   Combines all four edges; consistent with `Equals(FormationViewport)`.

    - **Returns** &mdash; A deterministic hash code for this value.

---

## IStageFloorSource

**Extension point** &mdash; implement this yourself to change behaviour

```csharp
public interface IStageFloorSource
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

Supplies the floor of a stage in the projected pixels of whatever viewport the stage currently uses. The stage asks it again
whenever it lays out, so the answer follows the viewport instead of going stale when the window is resized.

**Methods**

`public StageFloorPlan Resolve(Rect stageWorldRect, float unitsPerPixel)`

:   Resolves the floor for the current stage rectangle.

    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `unitsPerPixel` &mdash; World units per projected pixel.
    - **Returns** &mdash; The plan in projected stage pixels; `StageFloorPlan.None` when the stage declares nothing.

---

## ProjectedFormationPoint

```csharp
public readonly struct ProjectedFormationPoint : IEquatable<ProjectedFormationPoint>
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationModels.cs</small>

A formation point after projection, in the pixel space of the
`FormationViewport` it was fitted into. It is a separate type
from `FormationPoint` so normalised authoring coordinates and
projected screen coordinates cannot be passed for one another by mistake.

**Constructors**

`public ProjectedFormationPoint(int x, int y)`

:   Copies projected X/Y pixel coordinates for a concrete viewport. It carries no transform or scene reference.

    - `x` &mdash; Absolute horizontal pixel coordinate in the destination viewport's space.
    - `y` &mdash; Absolute vertical pixel coordinate in the destination viewport's space.

**Properties**

`public int X`

:   Horizontal pixel position, measured in the same space as the viewport that was projected into and already offset by that viewport's left edge, so it is an absolute coordinate rather than one relative to the formation.

`public int Y`

:   Vertical pixel position, offset by the viewport's bottom edge and increasing upward.

**Methods**

`public bool Equals(ProjectedFormationPoint other)`

:   Equal only when both components match.

    - `other` &mdash; The value to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override bool Equals(object obj)`

:   Value comparison against a boxed point; any other type is never equal.

    - `obj` &mdash; The object to compare with this instance.
    - **Returns** &mdash; True when the supplied value is equal to this value; otherwise false.

`public override int GetHashCode()`

:   Combines both components; consistent with `Equals(ProjectedFormationPoint)`.

    - **Returns** &mdash; A deterministic hash code for this value.

---

## StageFloorPlan

```csharp
public sealed class StageFloorPlan
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

What a stage tells the formation about its floor, resolved into the projected pixels of the stage viewport. A stage declares a
ground line (where the feet of the line layout stand), the back edge of its open floor, an optional horizon and vanishing point
for the depth layout, and the props no foot may stand on. `None` declares nothing.

**Constructors**

`public StageFloorPlan(int? groundLineY, int? floorBackEdgeY, int? horizonY, int? vanishingPointX, IEnumerable<StageFloorProp> floorProps)`

:   Creates a plan. Every position is in projected stage pixels, with Y increasing upward.

    - `groundLineY` &mdash; Height of the line on which the feet stand, or null when the stage declares none.
    - `floorBackEdgeY` &mdash; Height of the back edge of the open floor; no foot may stand above it. Null declares none.
    - `horizonY` &mdash; Height of the horizon the depth layout scales toward, or null when the stage declares none.
    - `vanishingPointX` &mdash; Horizontal position of the vanishing point, or null when the stage declares none.
    - `floorProps` &mdash; Regions where no foot may stand; null is none.

**Properties**

`public int FloorBackEdgeY`

:   Height of the back edge of the open floor in projected stage pixels; meaningful only when `HasBackEdge`.

`public int GroundLineY`

:   Height of the ground line in projected stage pixels; meaningful only when `HasGround`.

`public bool HasBackEdge`

:   True when the stage declares the back edge of its open floor.

`public bool HasGround`

:   True when the stage declares a ground line.

`public bool HasPerspective`

:   True when the stage declares both a horizon and a vanishing point, which the depth layout needs.

`public int HorizonY`

:   Height of the horizon in projected stage pixels; meaningful only when `HasPerspective`.

`public static StageFloorPlan None`

:   A plan that declares nothing. The line layout then stands the feet just above the dock band. Each read returns a new, empty plan, so no state is shared.

`public IReadOnlyList<StageFloorProp> Props`

:   Regions where no foot may stand.

`public int VanishingPointX`

:   Horizontal position of the vanishing point in projected stage pixels; meaningful only when `HasPerspective`.

**Methods**

`public int? FindBlockedX(int y, int fromX, int direction, int toX)`

:   Walks along a horizontal line from a start point and reports where the first prop begins.

    - `y` &mdash; Height of the line in projected stage pixels.
    - `fromX` &mdash; Where the walk starts; a prop that contains the start is skipped first, so a formation may start on a prop that stands in the middle.
    - `direction` &mdash; Negative walks left, positive walks right.
    - `toX` &mdash; Where the walk stops.
    - **Returns** &mdash; The first blocked horizontal position, or null when the line is clear up to `toX`.

`public bool TryFindProp(int x, int y, out StageFloorProp prop)`

:   Finds the first prop that contains a point.

    - `x` &mdash; Horizontal position in projected stage pixels.
    - `y` &mdash; Vertical position in projected stage pixels.
    - `prop` &mdash; Receives the prop, or null.
    - **Returns** &mdash; True when a prop contains the point.

---

## StageFloorProp

```csharp
public sealed class StageFloorProp
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

A region of the stage plate where no foot may stand, such as a staircase, a well or a wall. Points are a closed polygon in
projected stage pixels, the same space as `FormationViewport`.

**Constructors**

`public StageFloorProp(string name, IEnumerable<ProjectedFormationPoint> outline)`

:   Creates a prop from its outline.

    - `name` &mdash; Name shown in diagnostics; null becomes an empty name.
    - `outline` &mdash; Polygon corners in projected stage pixels. Fewer than three corners describe an empty prop that blocks nothing.

**Properties**

`public string Name`

:   Name shown in diagnostics.

`public IReadOnlyList<ProjectedFormationPoint> Outline`

:   Polygon corners in projected stage pixels.

**Methods**

`public bool Contains(int x, int y)`

:   Tests whether a point lies inside the outline, using the even-odd rule.

    - `x` &mdash; Horizontal position in projected stage pixels.
    - `y` &mdash; Vertical position in projected stage pixels, increasing upward.
    - **Returns** &mdash; True when the point is inside the polygon.

---

## StaticStageFloorSource

```csharp
public sealed class StaticStageFloorSource : IStageFloorSource
```

`TurnHerald.Authoring` &middot; <small>Runtime/Authoring/Formation/FormationStageLayout.cs</small>

A floor source that always answers with one fixed plan, for stages whose floor does not depend on the viewport.

**Constructors**

`public StaticStageFloorSource(StageFloorPlan floorPlan)`

:   Creates a source around a fixed plan.

    - `floorPlan` &mdash; Plan to answer with; null answers `StageFloorPlan.None`.

**Methods**

`public StageFloorPlan Resolve(Rect stageWorldRect, float unitsPerPixel)`

:   Returns the fixed plan.

    - `stageWorldRect` &mdash; Ignored.
    - `unitsPerPixel` &mdash; Ignored.
    - **Returns** &mdash; The plan given at construction.

---
