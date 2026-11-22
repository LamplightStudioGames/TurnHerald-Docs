# Interface and widgets

57 types in this area.

!!! abstract "On this page"
    [BattleDockBox](#battledockbox) &middot; [BattleDockCard](#battledockcard) &middot; [BattleDockCardLayout](#battledockcardlayout) &middot; [BattleDockCardMode](#battledockcardmode) &middot; [BattleDockChoice](#battledockchoice) &middot; [BattleDockIcons](#battledockicons) &middot; [BattleDockMedallion](#battledockmedallion) &middot; [BattleDockMember](#battledockmember) &middot; [BattleDockMemberLayout](#battledockmemberlayout) &middot; [BattleDockMetrics](#battledockmetrics) &middot; [BattleDockModel](#battledockmodel) &middot; [BattleDockParticipant](#battledockparticipant) &middot; [BattleDockPhase](#battledockphase) &middot; [BattleDockRect](#battledockrect) &middot; [BattleDockResourceBar](#battledockresourcebar) &middot; [BattleDockResourceKind](#battledockresourcekind) &middot; [BattleDockShapes](#battledockshapes) &middot; [BattleDockSide](#battledockside) &middot; [BattleDockText](#battledocktext) &middot; [BattleEventNarrator](#battleeventnarrator) &middot; [BattleNumberFormat](#battlenumberformat) &middot; [BattleUiCommandChoice](#battleuicommandchoice) &middot; [BattleUiRoot](#battleuiroot) &middot; [BattleViewCost](#battleviewcost) &middot; [BattleViewEstimate](#battleviewestimate) &middot; [BattleViewEstimateKind](#battleviewestimatekind) &middot; [BattleViewExecution](#battleviewexecution) &middot; [BattleViewResource](#battleviewresource) &middot; [BattleViewStatus](#battleviewstatus) &middot; [BattleViewTargetScope](#battleviewtargetscope) &middot; [BattleViewTimelineEntry](#battleviewtimelineentry) &middot; [DecisionOptions](#decisionoptions) &middot; [DecisionShapeCompiler](#decisionshapecompiler) &middot; [DisplayStringTable](#displaystringtable) &middot; [DisplayStringTableProvider](#displaystringtableprovider) &middot; [FeedbackLogView](#feedbacklogview) &middot; [GeneratedUiRoot](#generateduiroot) &middot; [IBattlePortraitSource](#ibattleportraitsource) &middot; [ResultBannerView](#resultbannerview) &middot; [SafeAreaFitter](#safeareafitter) &middot; [SkillCommandShape](#skillcommandshape) &middot; [SkillTitleView](#skilltitleview) &middot; [SkillTrayView](#skilltrayview) &middot; [SkinnedTokenPlate](#skinnedtokenplate) &middot; [SkinnedValueBar](#skinnedvaluebar) &middot; [SkinnedWidgetFactory](#skinnedwidgetfactory) &middot; [StatusRosterView](#statusrosterview) &middot; [TargetPickerView](#targetpickerview) &middot; [TargetShape](#targetshape) &middot; [TimelineStripView](#timelinestripview) &middot; [TokenPlateDisplay](#tokenplatedisplay) &middot; [TooltipData](#tooltipdata) &middot; [TooltipPanelView](#tooltippanelview) &middot; [TransportBarView](#transportbarview) &middot; [UiPortraitFacing](#uiportraitfacing) &middot; [UiStatusEntry](#uistatusentry) &middot; [UiTimelineEntry](#uitimelineentry)

## BattleDockBox

```csharp
public readonly struct BattleDockBox
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

A rectangle in pixels measured from the top-left corner of the card it is placed in.

**Constructors**

`public BattleDockBox(float x, float y, float width, float height)`

:   Creates a box.

    - `x` &mdash; Left edge.
    - `y` &mdash; Top edge.
    - `width` &mdash; Width.
    - `height` &mdash; Height.

**Properties**

`public float Bottom`

:   Bottom edge.

`public float Height`

:   Height.

`public float Right`

:   Right edge.

`public float Width`

:   Width.

`public float X`

:   Left edge.

`public float Y`

:   Top edge.

**Methods**

`public bool Overlaps(BattleDockBox other)`

:   Tests whether two boxes share any area; touching edges do not count.

    - `other` &mdash; Box to compare with.
    - **Returns** &mdash; True when the interiors intersect.

---

## BattleDockCard

```csharp
public sealed class BattleDockCard
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

The action card of the dock.

**Properties**

`public BattleViewAction Action`

:   Selected action; null unless `Mode` is Action.

`public BattleDockParticipant Actor`

:   The acting combatant of a Prompt, Executing or Waiting card; null in Action mode and when hidden.

`public IReadOnlyList<BattleDockResourceBar> ActorResources`

:   Resource bars of the active actor on the Prompt card, at most three.

`public IReadOnlyList<BattleViewStatus> AppliedStatuses`

:   Statuses the action applies.

`public BattleDockResourceKind CostKind`

:   Resource family of the first cost.

`public string CostText`

:   Cost text such as "3 EN"; empty for a free action.

`public string Description`

:   Authored summary when the host supplied one, otherwise the instruction for the current step.

`public BattleViewEstimateKind EstimateKind`

:   Kind of the estimate shown in `EstimateText`.

`public string EstimateText`

:   Text of the estimate for the first chosen target, or the generic estimate; empty when the host published none.

`public bool HasSummary`

:   True when `Description` is the authored one-line summary of the action rather than the instruction.

`public string Instruction`

:   The instruction for the current step: what to choose, that the command is ready, or, when the action cannot be used, why. Always set in Action mode.

`public bool IsRefused`

:   True when the last choice or Confirm was refused, by the dock or by the battle (`BattleViewSession.Error` is set): `Instruction` then holds that answer, to be drawn as a warning where the player looks, rather than on the stage. Set on the prompt and on the card of a chosen action.

`public bool IsUnavailable`

:   True when the chosen action cannot be used right now; `Instruction` then holds the reason, to be drawn as a warning rather than as a step.

`public IReadOnlyList<BattleDockMarked> Marked`

:   The combatants the action marks on the stage when that is more than one: all the legal targets of a rule that chooses for the player (a row, a side, everyone, a random draw) or the targets the player has picked so far. Empty for none or one, which `TargetLine` carries. At most `BattleDockCardLayout.MaximumMarkedCells`, less one place for the overflow count when there are more.

`public int MarkedHidden`

:   How many marked combatants do not fit in `Marked`; the card draws a "+N" cell for them.

`public BattleDockCardMode Mode`

:   Whether the card is hidden, shows the prompt, or shows an action.

`public string ScopeText`

:   Phrase naming who the action reaches; empty when unclassified.

`public string TargetLine`

:   Names and health of the chosen targets; empty until one is chosen.

`public BattleDockSide TargetSide`

:   Side of the combatant `TargetLine` names, relative to the viewing team; neutral when the line is empty or the state carries no teams.

`public IReadOnlyList<BattleDockParticipant> Targets`

:   Combatants an Executing card names as reached, at most three, each with its team color.

`public string Title`

:   Title: the action label.

---

## BattleDockCardLayout

```csharp
public sealed class BattleDockCardLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

The arrangement of the action card in each of its modes, shared by both adapters. Every measure is a card-local pixel counted from
the top-left corner. The content of a mode is one block centered vertically, and a mode with a pinned footer (the chips of an
action) spreads its text lines evenly between the header and the footer, so a card taller than its content, as on a 16:10 canvas,
shares the spare height evenly instead of leaving an empty band at the foot.

**Properties**

`public BattleDockBox ActionIcon`

:   The icon in front of the action line of a card that shows an action in progress.

`public BattleDockBox Caption`

:   The caption under the title of a waiting card, or the action line of a card that shows an action in progress.

`public float ChipsTop`

:   Distance of the chip row from the top of the card.

`public float ContentBottom`

:   Bottom of the lowest drawn content, used to check that nothing is left empty at the foot.

`public float ContentTop`

:   Top of the highest drawn content.

`public BattleDockBox Cost`

:   The cost, right-aligned on the line of the title of an action card.

`public BattleDockBox Divider`

:   The hairline under the header of an action card.

`public BattleDockBox Hint`

:   The hint of a prompt card.

`public BattleDockBox IconFrameBox`

:   The frame of the action icon of an action card.

`public BattleDockBox[] MarkedCells`

:   The places of the marked targets of an action card, row by row; empty when fewer than two combatants are marked.

`public BattleDockBox Medallion`

:   The actor medallion; empty on an action card.

`public BattleDockBox Resources`

:   The row of resource bars of a prompt card.

`public BattleDockBox Summary`

:   The first body line of an action card: its one-line description or the instruction.

`public BattleDockBox TargetLine`

:   The second body line of an action card: who the action will hit, or the instruction.

`public float TextLeft`

:   Left edge of the text column beside the medallion.

`public float TextWidth`

:   Width of the text column beside the medallion.

`public BattleDockBox Title`

:   The title: the action of an action card, the actor elsewhere.

**Fields**

`public const float ActorMedallion`

:   Diameter of the actor medallion of a prompt or a waiting card.

`public const float CaptionHeight`

:   Height of a caption line in the 28 px display size.

`public const float ChipGap`

:   Space between chips.

`public const float ChipHeight`

:   Height of a chip.

`public const float ExecutionMedallion`

:   Diameter of the actor medallion of a card that shows an action in progress.

`public const float IconFrame`

:   Side of the action icon frame.

`public const float LineHeight`

:   Height of a body line in the 22 px size.

`public const float MarkedBarRoom`

:   Room kept free at the foot of a cell of the single row for its thin health bar, so the name stands above the bar.

`public const int MarkedColumns`

:   Marked targets per row of the card.

`public const float MarkedRowHeight`

:   Height of a row of marked targets when there are two rows, which use the small face.

`public const float MarkedSingleRowHeight`

:   Height of the row of marked targets when there is one row: a line of the small face and, under it, the room of the thin health bar (`MarkedBarRoom`), inside the frame of the cell.

`public const int MaximumMarkedCells`

:   Most places the card lists marked targets in: two rows of three. A larger set shows one place less and a +N place.

`public const float Padding`

:   Margin around the content of the card.

`public const float ResourceRowHeight`

:   Height of the row of resource bars of the prompt card.

`public const float TitleHeight`

:   Height of a title line in the 36 px display size; the line of that face is about 48.5 px.

**Methods**

`public static float ChipLeft(float width, int count, int index)`

:   Left edge of a chip of a row.

    - `width` &mdash; Card width in pixels.
    - `count` &mdash; Number of chips, at least one.
    - `index` &mdash; Index of the chip, from zero.
    - **Returns** &mdash; The left edge in pixels.

`public static float ChipWidth(float width, int count)`

:   Width of one chip of a row, so that the row spans the card between its paddings.

    - `width` &mdash; Card width in pixels.
    - `count` &mdash; Number of chips, at least one.
    - **Returns** &mdash; The chip width in pixels.

`public static BattleDockCardLayout ForAction(float width, float height, float costWidth, int bodyLines, bool hasChips, int markedCells = 0)`

:   Arranges the card of a chosen command.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - `costWidth` &mdash; Width reserved for the cost text; zero for a free action.
    - `bodyLines` &mdash; Number of body lines, zero to two.
    - `hasChips` &mdash; True when a row of preview chips is pinned to the foot.
    - `markedCells` &mdash; Places for marked targets, zero or one for none; two or more replace the second body line with a row of places, or two rows from the fourth on.
    - **Returns** &mdash; The arrangement.

`public static BattleDockCardLayout ForExecution(float width, float height, bool hasActionIcon, bool hasTargets)`

:   Arranges the card of an action in progress: who acts, what it does, and the chips of who it reaches.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - `hasActionIcon` &mdash; True when the action has an icon, drawn in front of its name.
    - `hasTargets` &mdash; True when a row of target chips follows.
    - **Returns** &mdash; The arrangement.

`public static BattleDockCardLayout ForPrompt(float width, float height, bool hasActor, int resourceCount)`

:   Arranges the card of a pending decision with no command chosen: the active actor, its resources and the instruction.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - `hasActor` &mdash; False when the state names no actor; the hint then fills the card.
    - `resourceCount` &mdash; Number of resource bars, zero to three.
    - **Returns** &mdash; The arrangement.

`public static BattleDockCardLayout ForWaiting(float width, float height)`

:   Arranges the card that shows who acts next: the actor and a caption.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - **Returns** &mdash; The arrangement.

---

## BattleDockCardMode

```csharp
public enum BattleDockCardMode
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

State of the action card.

| Value | Meaning |
| --- | --- |
| `Hidden` | Nothing to show, as after the battle has ended; the card collapses instead of drawing an empty panel. |
| `Prompt` | A decision is pending and no command is chosen; the card shows the active actor and the instruction. |
| `Action` | A command is chosen; the card shows its details and preview. |
| `Executing` | An action is being played; the card shows who acts, the action and its targets. |
| `Waiting` | No decision is pending and no action is known yet; the card shows who acts next. |

---

## BattleDockChoice

```csharp
public sealed class BattleDockChoice
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

One row of the command or target list.

**Properties**

`public BattleViewAction Action`

:   The action behind a command row; null for a target row.

`public BattleViewCombatant Combatant`

:   The combatant behind a target row; null for a command row.

`public BattleDockResourceKind CostKind`

:   Resource family of the first cost of a command, used to color the cost text.

`public string Detail`

:   Secondary text on the right of the row: the cost of a command. A target row has none; its health is the mini bar.

`public bool Enabled`

:   False when the actor cannot pay the cost of the command. The row is then not a control at all.

`public bool HasHealth`

:   True when the row shows a mini health bar under its name, which is the case for a target row of a known combatant.

`public float HealthFraction`

:   Health of a target row as a fraction of its maximum, from zero to one; zero without a combatant.

`public StableId Id`

:   Action or combatant identity.

`public bool IsUnavailable`

:   True for a command that has no way to be used right now (nobody it could reach). The row is drawn like one that cannot be paid for, but it stays a control: choosing it shows the reason on the card, and Confirm stays off. Always false for a target row.

`public string Label`

:   Primary text of the row.

`public bool Selected`

:   True for the chosen command or target.

`public BattleDockSide Side`

:   Side of a target row's combatant relative to the viewing team, which decides the color of its health bar; neutral for a command row.

---

## BattleDockIcons

```csharp
public static class BattleDockIcons
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleDockIcons.cs</small>

Resolves the icons of the dock layout from a theme's `BattleIconSet`. Both native adapters use it, so a command,
status or resource shows the same icon in uGUI and in UI Toolkit. A theme without an icon set yields no icons and the views
draw text instead.

**Methods**

`public static BattleActionKind KindOf(BattleViewAction action)`

:   Classifies a command for the per-kind icon fallback from its identity and target rule.

    - `action` &mdash; Command to classify.
    - **Returns** &mdash; The kind whose icon a command without its own icon receives.

`public static bool TryGetAction(BattleTheme theme, BattleViewAction action, out Sprite icon)`

:   Finds the icon of a command.

    - `theme` &mdash; Active theme; null or without an icon set yields none.
    - `action` &mdash; Command to illustrate.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when an icon exists.

`public static bool TryGetResource(BattleTheme theme, StableId id, BattleDockResourceKind kind, out Sprite icon)`

:   Finds the icon of a resource.

    - `theme` &mdash; Active theme; null or without an icon set yields none.
    - `id` &mdash; Stable resource identity.
    - `kind` &mdash; Resource family.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when an icon exists.

`public static bool TryGetStatus(BattleTheme theme, BattleViewStatus status, out Sprite icon)`

:   Finds the icon of a status.

    - `theme` &mdash; Active theme; null or without an icon set yields none.
    - `status` &mdash; Status to illustrate.
    - `icon` &mdash; Receives the icon, or null.
    - **Returns** &mdash; True when an icon exists.

---

## BattleDockMedallion

```csharp
public sealed class BattleDockMedallion
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

One circular entry of the turn ribbon.

**Properties**

`public int HiddenCount`

:   How many entries this +N medallion stands for; zero for an ordinary medallion.

`public StableId Id`

:   Combatant identity; invalid for the +N medallion and for legacy label-only entries.

`public bool IsCurrent`

:   True for the combatant whose turn it is, an opposing combatant included: the one whose action is being played, the one the player is deciding for, or, while nothing is played, the one whose cast lands before anything else can happen. It carries the NOW tab and is drawn larger.

`public bool IsFeatured`

:   True for the one medallion drawn larger than the rest: the current actor while an action is played, otherwise the next actor.

`public bool IsNext`

:   True for the actor who comes after the current turn, which carries the NEXT tab. Outside a turn it is the first actor of the order, and it is drawn larger when no actor is current.

`public bool IsOverflow`

:   True for the +N medallion.

`public string Monogram`

:   Letters drawn when no portrait exists, or the +N text of the overflow medallion.

`public string Name`

:   Display name; empty for the +N medallion.

`public BattleDockSide Side`

:   Side of the combatant relative to the viewing team.

`public string Tab`

:   Text of the tab under the medallion: NOW for the current actor, NEXT for the next one, empty for every other.

---

## BattleDockMember

```csharp
public sealed class BattleDockMember
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

One member of the party panel.

**Properties**

`public BattleViewCombatant Combatant`

:   The combatant projection.

`public float HealthFraction`

:   Health as a fraction of the maximum, from zero to one.

`public string HealthText`

:   Health text such as "120 / 120".

`public bool IsActive`

:   True for the member whose decision is pending.

`public bool IsDefeated`

:   True when the member has no health left.

`public IReadOnlyList<BattleDockResourceBar> Resources`

:   At most three resource bars, drawn on one line.

`public string ShieldText`

:   Shield text such as "+20"; empty without a shield.

`public IReadOnlyList<BattleViewStatus> Statuses`

:   Statuses carried by the member.

`public string ValueText`

:   The text of the health column: the health text, followed by the shield when there is one.

---

## BattleDockMemberLayout

```csharp
public sealed class BattleDockMemberLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

The arrangement of one party member card, shared by both adapters. Every text and every bar owns its own column or its own line,
so a health value can never run across a bar and the resource icons never touch a number. All measures are card-local pixels.

**Properties**

`public BattleDockBox HealthBar`

:   The health bar.

`public int Lines`

:   Number of text lines of the card, two or three.

`public BattleDockBox Name`

:   Line one: the name; it ends before the status icons and the value.

`public BattleDockBox NameInk`

:   The ink of the name: the band its capitals and ascenders occupy inside `Name`, as wide as the box. The line box of the name is taller than its letters (the UI Toolkit label clips at its box, so the box cannot be cut to the letters), and the distance of a frame to a name is the distance to its letters.

`public BattleDockBox Portrait`

:   The portrait medallion.

`public BattleDockBox[] ResourceBars`

:   Bar of each resource, in order; empty when the resources are not drawn.

`public BattleDockBox[] ResourceIcons`

:   Icon of each resource, in order; empty when the resources are not drawn.

`public bool ShowsResources`

:   True when the resources are drawn; a card too short for a third line leaves them to the party panel's detail.

`public BattleDockBox Statuses`

:   Line one, left of the value: the status icons, drawn right to left (third line in the two-column grid). Empty when the member carries none.

`public BattleDockBox Value`

:   The health value in its own right-aligned column, on the name line (the bar line in the two-column grid); the line is tall enough for its numerals.

`public BattleDockBox ValueInk`

:   The ink of the health digits inside `Value`, as wide as the column; see `NameInk`.

`public int VisibleStatuses`

:   How many of the requested status icons fit; a narrow card keeps the name at least 60 px wide and drops the rest.

**Fields**

`public const float MinimumIcon`

:   Smallest side an icon of a framed card is drawn at when the room runs short, in reference pixels: smaller than the icon of any other card, never gone.

`public const float NameInkAbove`

:   Where the capitals and ascenders of the name stand above the vertical center of its line, in reference pixels, measured on both themes (display faces, 22 px type).

`public const float NameInkBelow`

:   Where the baseline of the name stands below the vertical center of its line, in reference pixels. Descenders hang below it, into the gap before the next line.

`public const float OrnamentClearance`

:   Distance, in reference pixels, that the ink of a framed card keeps from the ornament its theme declares. The brief is four reference pixels measured on the screen; the rest is for the rounding of the pixel grid, which can take most of a pixel at the scales of the four tested resolutions (a canvas unit is 0.95 reference pixels at 1920 by 1200).

`public const float RightInset`

:   Distance kept between the right end of the health value and the edge of the card. The frame of the active member carries an inner ornament along its right edge, so the digits stop 14 px short of the card: clear of it in the uGUI sprite, and in the UI Toolkit adapter, which draws the same card, at the same place. A frame whose ornament reaches deeper than that says so (`BattleDockInsets`) and the digits stop `OrnamentClearance` beyond it instead.

`public const float ValueInkAbove`

:   Where the top of the health digits stands above the vertical center of the value column, in reference pixels (18 px numerals).

`public const float ValueInkBelow`

:   Where the foot of the health digits stands below the vertical center of the value column, in reference pixels.

**Methods**

`public static BattleDockMemberLayout Compute(float width, float height, bool compact, int resourceCount, int statusIcons, float valueWidth)`

:   Computes the arrangement of a member card that has no ornament to keep out of.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - `compact` &mdash; True in the two-column grid, where the resources move to a third line.
    - `resourceCount` &mdash; Number of resource bars, at most three.
    - `statusIcons` &mdash; Number of status icons on the first line.
    - `valueWidth` &mdash; Width reserved for the health value.
    - **Returns** &mdash; The computed layout.

`public static BattleDockMemberLayout Compute(float width, float height, bool compact, int resourceCount, int statusIcons, float valueWidth, BattleDockInsets ornament)`

:   Computes the arrangement of a member card whose frame carries an ornament. The content keeps `OrnamentClearance` from the ornament on every side that has one: the right end of the row stops short of it, the first line moves down until the letters of the name stand clear of the ornament at the top, and the line of bars and icons moves up until it stands clear of the one at the foot, and when the card is too short for both the icons of the row (never a font, never a bar, nothing is left out) get smaller, down to `MinimumIcon`. A side declared zero has no ornament and keeps the arrangement of a row without one. The card keeps its height and everything stays inside it. An empty declaration gives the arrangement of `Compute(float, float, bool, int, int, float)` to the pixel.

    - `width` &mdash; Card width in pixels.
    - `height` &mdash; Card height in pixels.
    - `compact` &mdash; True in the two-column grid, where the resources move to a third line.
    - `resourceCount` &mdash; Number of resource bars, at most three.
    - `statusIcons` &mdash; Number of status icons on the first line.
    - `valueWidth` &mdash; Width reserved for the health value.
    - `ornament` &mdash; How far the ornament of the frame reaches into the card, from each edge.
    - **Returns** &mdash; The computed layout.

`public static BattleDockInsets InsetOf(BattleDockInsets declared, bool isActive)`

:   The ornament a row of the party panel keeps its content clear of: what the theme declares for the active row, and nothing for the others. Both adapters ask here, so which rows carry the inset is decided in this one place.

    - `declared` &mdash; What the theme declares for its active row (`BattleTheme` ActiveRowInset).
    - `isActive` &mdash; True for the row of the member whose turn it is.
    - **Returns** &mdash; The ornament the row has to keep clear of.

---

## BattleDockMetrics

```csharp
public static class BattleDockMetrics
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

The geometry of the dock layout, shared by the uGUI and UI Toolkit adapters so both place every region in the same
proportions. Everything is expressed in a 1920 by 1080 reference space and as fractions of it, so the same numbers hold at
1280 by 720, 1366 by 768, 1920 by 1080 and 1920 by 1200 without shrinking type or hiding information.

**Properties**

`public static float Footprint01`

:   The share of the screen height taken by the event strip and the dock together, from the top of the strip to the bottom edge.

**Fields**

`public static readonly BattleDockRect Cancel`

:   Cancel control, right end of the strip.

`public static readonly BattleDockRect Card`

:   Center region: the action card.

`public const int ChoiceRowsInOneColumn`

:   Most button rows kept in one column. Buttons keep full-size type, so a list only splits into columns past this many rows.

`public static readonly BattleDockRect Commands`

:   Left region: command list, replaced by the target list while a target is chosen. Four rows of 53 px.

`public static readonly BattleDockRect Concede`

:   Concede control, left end of the strip. A quiet outline control: smaller than confirm and cancel, on the same line.

`public static readonly BattleDockRect Confirm`

:   Confirm control, right end of the strip.

`public const float ControlDarkenShare`

:   How far the fill of Confirm or Cancel goes toward black while it is pressed, from zero to one.

`public const float ControlHoverSeconds`

:   Seconds Confirm and Cancel take to light up under the pointer, or to be pressed, in a straight line: the length of the color fade of a uGUI button, and the same in both adapters.

`public const float ControlLightenShare`

:   How far the fill of Confirm or Cancel goes toward white under the pointer or with the focus, from zero to one.

`public const float DisabledRowAlpha`

:   Opacity an unavailable command or target row keeps of its fill, from zero to one.

`public const float DisabledRowFrameDash`

:   Length of one dash of the frame of a command row that cannot be used, in reference pixels.

`public const float DisabledRowFrameGap`

:   Shortest gap between two dashes of that frame, in reference pixels.

`public const float DisabledRowFrameThickness`

:   Thickness of the dashed frame of a command row that cannot be used, in reference pixels. Both adapters draw it on the pixel grid, rounded to whole device pixels and never thinner than one.

`public const float DisabledRowShade`

:   Brightness an unavailable command or target row keeps of its fill, from zero to one. Its label does not fade: the label of a cost that cannot be paid takes the quiet text color, and that of a command with nobody to reach keeps the foreground.

`public static readonly BattleDockRect Dock`

:   Whole dock frame at the bottom of the screen: 8 px above the bottom edge, two 6 px paddings around the 212 px regions.

`public const float FadeFloorAlpha`

:   Opacity the new content of a region starts from when it replaces the old one, from zero through one. It is above zero so that no frame shows the region empty while the fade runs.

`public static readonly BattleDockRect Feedback`

:   One-line event text inside the strip.

`public const float FontBody`

:   Type scale: body text and numbers.

`public const float FontHeading`

:   Type scale: command labels and member names in emphasis.

`public const float FontSmall`

:   Type scale: secondary numbers and status text. Nothing essential is smaller.

`public const float FontTitle`

:   Type scale: the action card title and the result banner.

`public const float HealthBarThickness`

:   Thickness of a party health bar in reference pixels.

`public const float HoverEdgeThickness`

:   Thickness of the lit hover border and of the focus ring of a command and of Concede, in reference pixels.

`public const float HoverGlowAlpha`

:   Opacity of the faint glow inside a hovered command, from zero to one.

`public const float HoverLift`

:   Distance a hovered command rises, in reference pixels.

`public const float HoverSeconds`

:   Duration of the hover, press and focus transitions of a command, and of the focus ring of Concede, in seconds; ease-out.

`public const float IconSize`

:   Side of a status or resource icon in reference pixels.

`public const int MaximumColumns`

:   Most columns used before rows start to shrink.

`public const float MaximumFootprint01`

:   Share of the screen height that the event strip, the gap and the dock together may take, measured from the top of the strip to the bottom edge.

`public const int MaximumMedallions`

:   Most medallions drawn before the remainder collapses into a +N medallion.

`public const float MedallionGap`

:   Space between neighboring medallions.

`public const float MedallionSize`

:   Diameter of an ordinary turn-order medallion.

`public const float MotionSeconds`

:   Duration of an ordinary interface transition in seconds; ease-out, never blocking input.

`public const float NextScale`

:   Scale applied to the next actor's medallion.

`public const float NextTabHeight`

:   Height of the NEXT tab in reference pixels.

`public const float NextTabWidth`

:   Width of the NEXT tab in reference pixels.

`public const float NumeralWidthPerPoint`

:   Estimated width of a run of digits and separators, per character and per point of font size. Condensed numerals stay under it.

`public static readonly BattleDockRect Party`

:   Right region: the party panel. Four rows of 53 px, or three rows of about 71 px in the two-column grid.

`public const float PortraitBacklightAlpha`

:   Opacity of the light behind a portrait, from zero to one: bright enough that the darkest painted face reads against it.

`public const float PortraitLiftAlpha`

:   Opacity of the radial exposure lift over a portrait, from zero to one. It lifts the shadows without burning the lights.

`public const float PortraitRimAlpha`

:   Opacity of the thin inner rim light drawn along the edge of a portrait, from zero to one.

`public const float PortraitRimFraction`

:   Thickness of the inner rim light as a fraction of the medallion diameter.

`public const float PortraitRimWhiteMix`

:   Share of the way from the portrait's side color to white at which the inner rim light is drawn, from zero to one.

`public const float PortraitVeilAlpha`

:   Opacity of the flat veil that lifts the blacks of a portrait evenly, from zero to one.

`public const float PressShadeAlpha`

:   Opacity of the dark veil over a pressed command, from zero to one.

`public const float ReducedFadeSeconds`

:   Length of the fade of new content in a region (the list, the card, the strip, the controls) under reduced motion, in seconds. Reduced motion keeps this fade and drops every displacement, so a change of content is still a soft change and never a jump.

`public const float ReducedMotionSeconds`

:   Longest fade under reduced motion, in seconds.

`public const float ReferenceHeight`

:   Reference height in pixels.

`public const float ReferenceWidth`

:   Reference width in pixels.

`public const float ResourceBarThickness`

:   Thickness of a party resource bar in reference pixels.

`public static readonly BattleDockRect Result`

:   Result banner, centered over the stage.

`public static readonly BattleDockRect Ribbon`

:   Turn ribbon, top center. Holds the medallions and the NEXT tab.

`public const float RibbonAdvanceSeconds`

:   The longest a change of the turn ribbon takes, in seconds. The medallion that leaves fades where it stands, the ones that stay slide to their new places and the one that enters appears once the row has made room for it, in that order. A change that needs fewer of those steps ends sooner; none takes longer than this.

`public const float RibbonCenterY`

:   Vertical center of every medallion inside `Ribbon`, in reference pixels from its top edge.

`public const float RibbonCrossfadeOverlap`

:   How much of the fade out of a medallion the fade in of the one that replaces it overlaps under reduced motion, from zero through one. Reduced motion cannot slide the medallions to their new places, so a place of the row is replaced where it stands. With zero the old one is gone before the new one begins and the ribbon is all but empty for a moment (the medallions fall to a twentieth of their opacity, on average, in every change); with one, the value, the two change together over one reduced fade, the old one staying as it is under the new one until it is covered. The motion that slides keeps its three steps, one after the other, and does not read this.

`public const float RibbonEnterSeconds`

:   Length of the fade of a medallion that enters the ribbon, in seconds, once nothing that stays is in its way.

`public const float RibbonExitSeconds`

:   Length of the fade of a medallion that leaves the ribbon, in seconds: a linear fade, never a step of more than half the opacity in a frame at 30 fps.

`public const float RibbonFadeScale`

:   Share of its diameter a medallion has at the far end of its fade: the one that leaves shrinks to this much while it fades out and the one that enters grows from it to all of it, from zero through one. Under reduced motion nothing changes size.

`public const float RibbonFrameSeconds`

:   The frame, in seconds, at which the ribbon keeps the promise of `RibbonFrameShare`: 30 frames a second.

`public const float RibbonFrameShare`

:   The most of a ribbon step (`RibbonStep`) a medallion moves in one frame of `RibbonFrameSeconds`, from zero through one. A medallion that would have to travel farther than the slide can cover at that pace fades out and in again instead of sliding.

`public const float RibbonLineOverhang`

:   How far the line behind the medallions runs past the first and the last one, in reference pixels.

`public const float RibbonSlideSeconds`

:   Length of the slide of the medallions that stay, and of the growth of the featured one, in seconds, both with the same ease-out.

`public const float RibbonStep`

:   Distance between the centers of two neighboring ordinary medallions of the ribbon, in reference pixels: a diameter and a gap. It is the ruler of the ribbon's motion, and both adapters lay the row out in it at every resolution, so a step is the same number of pixels in uGUI and in UI Toolkit.

`public const float RibbonTabFadeSeconds`

:   Length of the fade of a tab text going out, and then of the one coming in, in seconds. A text that is born on a medallion waits until the same text has gone out of the medallion that had it, which takes at most this long, so the ribbon never shows two NEXT or two NOW at once.

`public const float RibbonTabOverlap`

:   How far the tab of a medallion rises over its lower edge: the center of the tab stands this far above that edge, in reference pixels.

`public const float RibbonTabPlateFloor`

:   Opacity the plate behind a tab keeps, from zero through one, while one text takes the place of another: the plate follows the more visible of the two texts and never goes below this, so it is not gone between them and never an empty box at full strength. Below the opacity at which a text still reads (a tenth), the plate is under half.

`public const float RowInset`

:   Margin kept around a command row inside its slot of the grid, in reference pixels.

`public const int RowsPerColumn`

:   Most rows a column of commands, targets or party members holds before a column is added.

`public static readonly BattleDockRect Strip`

:   Strip above the dock that carries the event line and the confirm, cancel and concede controls.

`public const float StripExitShare`

:   Share of `FadeSeconds` that the sentence on the event strip takes to leave: the old sentence is gone before the next one begins to come in, so no frame carries two. The sentence that comes in takes the rest.

`public const float TargetBarThickness`

:   Thickness of the mini health bar under a target name in reference pixels.

**Methods**

`public static int ChoiceColumnsFor(int count)`

:   Columns of a command or target list: one up to five rows, two up to ten, then three.

    - `count` &mdash; Number of buttons to place.
    - **Returns** &mdash; The column count, at least one.

`public static int ChoiceRowsFor(int count)`

:   Rows of a command or target list; a short list keeps the height of four rows so rows never jump.

    - `count` &mdash; Number of buttons to place.
    - **Returns** &mdash; The row count, at least one.

`public static int ColumnsFor(int count)`

:   Columns used to lay out a number of rows without paging: one up to four, two up to eight, then three.

    - `count` &mdash; Number of entries to place.
    - **Returns** &mdash; The column count, at least one.

`public static int DisabledRowFrameDashes(float length, float dash, float gap, out float step)`

:   How the dashes of the frame of a command row that cannot be used lie along one edge: the first starts at the start of the edge and the last ends at its end, with even gaps of at least `DisabledRowFrameGap` between them.

    - `length` &mdash; Length of the edge, in the units of `dash` and `gap`.
    - `dash` &mdash; Length of one dash.
    - `gap` &mdash; Shortest gap.
    - `step` &mdash; Distance from the start of one dash to the start of the next; the length of the edge when there is one.
    - **Returns** &mdash; The number of dashes, at least one; a single dash covers an edge shorter than two dashes and a gap.

`public static float FadeSeconds(bool reduceMotion)`

:   Length of the fade of new content in a region.

    - `reduceMotion` &mdash; True when the theme asks for reduced motion.
    - **Returns** &mdash; `ReducedFadeSeconds` under reduced motion, otherwise `MotionSeconds`.

`public static void LayoutRibbon(bool[] isNext, out float[] centers, out float[] sizes)`

:   Computes the horizontal placement of the turn-ribbon medallions.

    - `isNext` &mdash; One flag per medallion; a next-actor medallion is drawn larger.
    - `centers` &mdash; Receives each medallion's center, in reference pixels from the left edge of `Ribbon`.
    - `sizes` &mdash; Receives each medallion's diameter in reference pixels.

`public static void LayoutRibbon(bool[] isFeatured, int count, float[] centers, float[] sizes)`

:   Computes the same placement as `LayoutRibbon(bool[], out float[], out float[])` into arrays the caller owns, so a view that asks for it on every redraw allocates nothing. The medallions are laid out in a row, a gap apart, centered in `Ribbon`; the larger ones take more room.

    - `isFeatured` &mdash; One flag per medallion; the featured medallion is drawn larger. Read up to `count`.
    - `count` &mdash; How many medallions to place; at most the length of every array.
    - `centers` &mdash; Receives each center, in reference pixels from the left edge of `Ribbon`.
    - `sizes` &mdash; Receives each diameter in reference pixels.

`public static float NumeralWidth(int characters, float fontSize)`

:   Estimates the width a short numeric text needs, so its column can be reserved before it is drawn.

    - `characters` &mdash; Number of characters in the text.
    - `fontSize` &mdash; Font size in reference pixels.
    - **Returns** &mdash; The reserved width in reference pixels, with a small margin.

`public static int RowsFor(int count)`

:   Rows reserved by a layout of a number of entries; a short list keeps the height of a full column so rows never jump.

    - `count` &mdash; Number of entries to place.
    - **Returns** &mdash; The row count, at least `RowsPerColumn` for a single column.

`public static BattleStageBounds StageBounds()`

:   The normalized, bottom-left rectangle the formation may use: below the ribbon and above the strip. Its bottom, at 66.9% of the height from the top, stands the feet at 65.1% (703 px at 1080) and leaves 76 px (7%) above the strip, which the bars under the feet, the ground ring of a target and the world numbers need: 69 px from the bars to the strip at 1080, 35 at 720. Both adapters take this rectangle, so the formation stands on one line in both.

    - **Returns** &mdash; Stage reservation of the dock layout.

`public static float StripEnterSeconds(bool reduceMotion)`

:   Length of the fade-in, with an ease-out, of the sentence that comes onto the event strip: what `FadeSeconds` leaves after `StripExitSeconds`.

    - `reduceMotion` &mdash; True when the theme asks for reduced motion.
    - **Returns** &mdash; The length in seconds, from no opacity to full.

`public static float StripExitSeconds(bool reduceMotion)`

:   Length of the fade-out of the sentence that leaves the event strip: `StripExitShare` of `FadeSeconds`.

    - `reduceMotion` &mdash; True when the theme asks for reduced motion.
    - **Returns** &mdash; The length in seconds, from full opacity to none.

---

## BattleDockModel

```csharp
public sealed class BattleDockModel
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

Everything the dock layout draws, derived once from a `BattleViewSession` by pure code so the uGUI and UI Toolkit
adapters render identical content. The model reads the immutable state and the local selection and changes neither.

**Properties**

`public string BannerError`

:   The error of the session that the card does not carry, for the banner of the stage to show: empty while a decision is shown, since the prompt or the card of the chosen action answers a refusal itself (`BattleDockCard.IsRefused`).

`public BattleDockCard Card`

:   The action card.

`public IReadOnlyList<BattleDockChoice> Commands`

:   Command rows of the pending actor.

`public string FeedbackText`

:   The latest event sentence, or an empty string.

`public bool OffersConfirmation`

:   True when Confirm and Cancel may be offered: only while a decision is pending.

`public IReadOnlyList<BattleDockMember> Party`

:   Members of the viewing team; defeated members stay.

`public BattleDockPhase Phase`

:   Which part of a turn the dock is in.

`public IReadOnlyList<BattleDockMedallion> Ribbon`

:   Turn-ribbon medallions: the next seven entries, then a +N medallion when more remain.

`public bool ShowTargets`

:   True when the command list is replaced by the target list.

`public IReadOnlyList<BattleDockChoice> Targets`

:   Target rows; empty unless the chosen command asks the player to pick targets.

`public IReadOnlyList<BattleDockMedallion> UpNext`

:   While no decision is pending, the actors that follow, in turn order, at most four. They replace the command list so the left column of the dock always carries something to read; empty during a decision and after the battle.

`public StableId ViewingTeam`

:   Viewing team identity, or invalid for legacy label-only states.

**Methods**

`public static BattleDockModel Create(BattleViewSession session)`

:   Builds the model for the current state and selection of a session.

    - `session` &mdash; Session supplying the state and local selection; null yields an empty model.
    - **Returns** &mdash; A new immutable-by-convention model.

`public static IReadOnlyList<BattleViewStatus> StatusesOf(BattleViewCombatant combatant)`

:   Statuses of a combatant: the structured entries, or the legacy preformatted list split into label-only entries.

    - `combatant` &mdash; Combatant to read; null yields none.
    - **Returns** &mdash; The statuses in display order.

---

## BattleDockParticipant

```csharp
public sealed class BattleDockParticipant
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

One combatant named by the card of an action in progress.

**Properties**

`public BattleViewCombatant Combatant`

:   The projection of the combatant when the state carries it; otherwise null.

`public StableId Id`

:   Combatant identity.

`public string Name`

:   Display name.

`public BattleDockSide Side`

:   Side relative to the viewing team: the color of the rim and of the name.

---

## BattleDockPhase

```csharp
public enum BattleDockPhase
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

Which part of a turn the dock is in.

| Value | Meaning |
| --- | --- |
| `Decision` | A decision is pending: commands, targets and the action card are interactive. |
| `Executing` | An action or an opposing turn is being played. |
| `Waiting` | No decision is pending and nothing is playing yet. |
| `Ended` | The battle has a result. |

---

## BattleDockRect

```csharp
public readonly struct BattleDockRect
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

A rectangle in the 1920 by 1080 reference space of the dock layout, measured in pixels from the top-left corner.

**Constructors**

`public BattleDockRect(float x, float y, float width, float height)`

:   Creates a reference-space rectangle.

    - `x` &mdash; Left edge in reference pixels.
    - `y` &mdash; Top edge in reference pixels.
    - `width` &mdash; Width in reference pixels.
    - `height` &mdash; Height in reference pixels.

**Properties**

`public float Bottom`

:   Bottom edge in reference pixels.

`public float Bottom01`

:   Bottom edge as a fraction of the reference height, counted from the top.

`public float Height`

:   Height in reference pixels.

`public float Height01`

:   Height as a fraction of the reference height.

`public float Left01`

:   Left edge as a fraction of the reference width.

`public float Right`

:   Right edge in reference pixels.

`public float Right01`

:   Right edge as a fraction of the reference width.

`public float Top01`

:   Top edge as a fraction of the reference height, counted from the top.

`public float Width`

:   Width in reference pixels.

`public float Width01`

:   Width as a fraction of the reference width.

`public float X`

:   Left edge in reference pixels.

`public float Y`

:   Top edge in reference pixels.

---

## BattleDockResourceBar

```csharp
public sealed class BattleDockResourceBar
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

A resource bar of a party row.

**Properties**

`public string Code`

:   Short code such as EN or FO, used as the accessible name of the icon.

`public BattleDockResourceKind Kind`

:   Resource family.

`public BattleViewResource Resource`

:   The structured resource value.

---

## BattleDockResourceKind

```csharp
public enum BattleDockResourceKind
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

Resource families that receive a themed color and icon.

| Value | Meaning |
| --- | --- |
| `Energy` | Energy, drawn in the theme's energy color. |
| `Focus` | Focus, drawn in the theme's focus color. |
| `Other` | Any other pool, drawn in the neutral accent. |

---

## BattleDockShapes

```csharp
public static class BattleDockShapes
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleDockShapes.cs</small>

Generates the plain white shapes the dock layout falls back to when a theme supplies no sprite: a disc for portrait masks and
medallion backs, a ring for medallion borders, a soft glow that lights a portrait from behind and a nine-slice hairline frame that
outlines a hovered or focused command. Each call returns a new sprite that the caller owns and releases with
`Release`; nothing is cached statically.

**Methods**

`public static Sprite CreateDisc(int size)`

:   Creates a white, antialiased disc.

    - `size` &mdash; Edge length in pixels, at least 8.
    - **Returns** &mdash; A new sprite owned by the caller.

`public static Sprite CreateFrame(int size, int thickness)`

:   Creates a white, hollow, nine-slice rectangle: a hairline frame whose border keeps its thickness at any size.

    - `size` &mdash; Edge length in pixels, at least 8.
    - `thickness` &mdash; Frame width in pixels, at least one and less than a third of the size. It is also the sliced border.
    - **Returns** &mdash; A new sprite owned by the caller, with its border set so an image of type sliced draws the frame at that thickness.

`public static Sprite CreateGlow(int size)`

:   Creates a white radial glow: opaque in the middle, fading smoothly to nothing at the edge of the disc.

    - `size` &mdash; Edge length in pixels, at least 8.
    - **Returns** &mdash; A new sprite owned by the caller.

`public static Sprite CreateRing(int size, float thickness)`

:   Creates a white, antialiased ring.

    - `size` &mdash; Edge length in pixels, at least 8.
    - `thickness` &mdash; Ring width in pixels, at least one.
    - **Returns** &mdash; A new sprite owned by the caller.

`public static void Release(Sprite sprite)`

:   Destroys a sprite created by this class together with its texture.

    - `sprite` &mdash; Sprite to release; null is ignored.

---

## BattleDockSide

```csharp
public enum BattleDockSide
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

Which side a turn-order medallion or target belongs to, relative to the viewing team.

| Value | Meaning |
| --- | --- |
| `Ally` | The viewing team. |
| `Enemy` | An opposing team. |
| `Neutral` | Team membership is unknown, as for legacy label-only data. |

---

## BattleDockText

```csharp
public static class BattleDockText
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

The sentences of the dock layout. Both adapters take their wording from here, so the two renderings read the same.

**Fields**

`public const string ChooseATarget`

:   Instruction while one target is still needed.

`public const string ChooseAnAction`

:   Shown on the action card before any command is chosen.

`public const string Next`

:   Label of the tab under the next actor's medallion.

`public const string NoLegalTarget`

:   What the card says of an action that cannot be used for want of a target, when the author wrote no sentence of their own.

`public const string Now`

:   Label of the tab under the medallion of the combatant whose turn it is: the one whose action is being played, or the one the player is deciding for.

`public const string ReadyToConfirm`

:   Instruction while the command is complete.

`public const float TwoLetterMonogramSize`

:   Largest medallion, in reference pixels, that still shows two letters; smaller ones show the first letter only so a fallback never overflows.

`public const string UpNext`

:   Caption of the card that shows who acts after the current action.

**Methods**

`public static string ChooseTargets(int missing)`

:   Instruction for a command that still needs targets.

    - `missing` &mdash; How many more targets are required; at least one.
    - **Returns** &mdash; A short sentence such as "Choose a target" or "Choose 2 targets".

`public static string Estimate(BattleViewEstimate estimate)`

:   Text of an estimate chip.

    - `estimate` &mdash; Estimate to describe; null yields an empty string.
    - **Returns** &mdash; Text such as "Est. damage 38-52".

`public static string Monogram(string name)`

:   Two-letter-at-most monogram drawn on a medallion when no portrait exists.

    - `name` &mdash; Display name; null or blank yields a question mark.
    - **Returns** &mdash; The initials of the first two words, upper-cased.

`public static string MonogramFor(string monogram, float size)`

:   The letters a medallion of a given size can hold.

    - `monogram` &mdash; Full monogram of one or two letters, or the +N text of an overflow medallion.
    - `size` &mdash; Medallion diameter in reference pixels.
    - **Returns** &mdash; The monogram itself for a large medallion or an overflow count; otherwise its first letter.

`public static string ResourceCode(StableId id, string label)`

:   Short resource code drawn beside an amount: EN for energy, FO for focus, otherwise the first two letters.

    - `id` &mdash; Stable resource identity.
    - `label` &mdash; Display label of the resource.
    - **Returns** &mdash; An upper-case code of at most two characters.

`public static BattleDockResourceKind ResourceKindOf(StableId id, string label)`

:   Classifies a resource by its identity or label.

    - `id` &mdash; Stable resource identity.
    - `label` &mdash; Display label of the resource.
    - **Returns** &mdash; Energy, focus or other.

`public static string Scope(BattleViewTargetScope scope)`

:   Phrase that names who an action reaches.

    - `scope` &mdash; Classification of the target rule.
    - **Returns** &mdash; The phrase, or an empty string when the rule is not classified.

---

## BattleEventNarrator

```csharp
public static class BattleEventNarrator
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleEventNarrator.cs</small>

Turns one battle event into a sentence a player can read.

The feedback log used to render an event's raw type id followed by the
actor in brackets - `scheduler.combatant-ready [Clockwork Rival]` -
which is an engineer's log line shown to a customer as if it were game
text. The values needed to say it properly were always there: the event
carries the actor, the target, the skill, and the amount, and the display
string table has names for all of them.

Nothing here is authoritative. It reads an event that has already
happened and produces text; it resolves nothing, computes nothing, and
cannot change a hash. An event shape it does not recognise falls back to
the labelled type id, so a project that adds its own events still gets a
readable line rather than an empty one.

**Methods**

`public static string Describe(BattleEvent battleEvent, DisplayStringTable labels)`

:   Writes one log line for `battleEvent`.

    - `battleEvent` &mdash; The event to describe. Null returns an empty string.
    - `labels` &mdash; Display names for the ids in the event. Null, or an id the table does not carry, falls back to the raw id text, which is what keeps an unlabelled project readable rather than blank.
    - **Returns** &mdash; One sentence, already capitalised and punctuated. Never null.

`public static bool IsPlayerFacing(BattleEvent battleEvent)`

:   Whether an event belongs in the log a PLAYER reads. The engine emits its own bookkeeping alongside the things that happen in the fiction, and the log printed all of it. Roughly two lines in five were "command.accepted - Ember Vanguard", "reaction.suppressed - Pale Adept", or "Action Completed - Sable Ranger" -- engine vocabulary shown to a customer, burying the four lines that actually told them they were losing. Everything filtered here is still in the event stream, still in replays, and still shown in full by the Workbench; it is only kept out of the player's log.

    - `battleEvent` &mdash; The event to judge. Null is not player-facing.
    - **Returns** &mdash; True when the event is worth a line in the battle log.

---

## BattleNumberFormat

**Start here**

```csharp
public static class BattleNumberFormat
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleNumberFormat.cs</small>

Turns the simulation's fixed-point types into player-facing text.

`Fixed64` and `Chance64` deliberately expose only
raw scaled integers, because their `ToString` feeds canonical
encoding and must never drift. A tooltip that printed those directly would
show "50000" instead of "5" and "875000" instead of "87.5%", so display
formatting belongs here in the presentation layer.

Every conversion is integer arithmetic. No float ever touches a value that
could be mistaken for an authoritative number.

**Fields**

`public const int AmountDecimals`

:   Maximum decimal places shown for a fixed-point amount.

**Methods**

`public static string Amount(Fixed64 value)`

:   Formats a fixed-point amount, trimming trailing zeros: 5, 5.5, 5.25.

    - `value` &mdash; Signed fixed-point battle amount to render without culture-dependent separators.
    - **Returns** &mdash; Invariant decimal text with insignificant fractional zeroes removed.

`public static string AmountRange(Fixed64 minimum, Fixed64 maximum)`

:   Formats a range as "12" when both ends match, otherwise "10-14".

    - `maximum` &mdash; Upper fixed-point preview bound.
    - `minimum` &mdash; Lower fixed-point preview bound.
    - **Returns** &mdash; One rounded amount when bounds match, otherwise a hyphenated minimum-to-maximum range.

`public static string Percent(Chance64 value)`

:   Formats a chance as a percentage, trimming trailing zeros: 100%, 87.5%, 0.05%.

    - `value` &mdash; Million-scale probability to convert into percentage units.
    - **Returns** &mdash; Invariant percentage text with up to four fractional digits and no trailing zeroes.

`public static string Ticks(int ticks)`

:   Formats a tick count as a short duration, "12t".

    - `ticks` &mdash; Signed simulation tick count.
    - **Returns** &mdash; Invariant integer text followed by the `t` tick suffix.

`public static string WholeAmount(Fixed64 value)`

:   Formats a fixed-point amount rounded to a whole number, which is what damage and healing readouts usually want.

    - `value` &mdash; Signed fixed-point battle amount to round to the nearest integer.
    - **Returns** &mdash; Invariant whole-number text rounded with the simulation value's integer conversion.

---

## BattleUiCommandChoice

```csharp
public readonly struct BattleUiCommandChoice
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleUiRoot.cs</small>

A player-chosen command the driver (not the UI) will submit.

**Constructors**

`public BattleUiCommandChoice(StableId actorId, bool isConcede, StableId? skillId, FrozenList<StableId> targets)`

:   Records one choice for the driver to act on.

    - `actorId` &mdash; Pending human actor that owns the choice.
    - `isConcede` &mdash; True for a concession, which carries no skill.
    - `skillId` &mdash; Chosen skill, or null for concession.
    - `targets` &mdash; Target ids the player picked. Null becomes empty, and empty leaves exact target resolution to the driver.

**Properties**

`public StableId ActorId`

:   The combatant the command is for. It is taken from the pending decision rather than from whoever clicked, so it always matches the actor the engine is waiting on.

`public bool IsConcede`

:   True when the player conceded instead of picking a skill. Such a choice carries no `SkillId` and no `Targets`.

`public StableId? SkillId`

:   The skill the player picked; null when the choice is a concession.

`public FrozenList<StableId> Targets`

:   The targets the player picked, never null. Empty means the driver still owns target resolution; the shipped tray always raises choices empty.

---

## BattleUiRoot

**Start here**

```csharp
public sealed class BattleUiRoot : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleUiRoot.cs</small>

The battle interface. It offers the pending actor's legal command shapes,
surfaces the timeline, roster, feedback log, tooltips, and terminal
results verbatim from snapshots and events, and raises a plain C# event
with the chosen command for the DRIVER to submit.

It submits nothing, resolves no targets exactly, and invokes no simulation
or preview API; tooltips are supplied to it as computed
`TooltipData` values.

Every colour, size, font, animation timing, and region position comes from
a `BattleSkinPreset`, so the whole interface restyles from one
asset with no prefab editing. With no preset assigned it falls back to the
shipped default skin rather than rendering unstyled boxes.

**Properties**

`public CompiledSkinLayout ActiveLayout`

:   The layout actually in use, which is the skin's layout adapted to the current screen shape. Read this rather than `Skin.Layout` when you need to know where the interface really is, because a portrait screen stacks the bands and drops the side cells.

`public DecisionOptions CurrentDecision`

:   The decision currently on offer, or `DecisionOptions.None` when there is nothing to decide. Never null, so it can be read without a guard between battles.

`public IReadOnlyList<string> FeedbackLines`

:   The retained feedback log, oldest line first. A live view, capped at `MaximumFeedbackLines` by dropping the oldest lines.

`public string InputUnavailableMessage`

:   Empty, because shortcuts are available in this build.<br>Compilation condition: `#if ENABLE_LEGACY_INPUT_MANAGER`.

`public string InputUnavailableMessage`

:   Display-ready explanation of why the keyboard shortcuts are missing and which project setting restores them. Empty in builds that have them.<br>Compilation condition: `#else (matching #if ENABLE_LEGACY_INPUT_MANAGER)`.

`public bool IsChoosingTarget`

:   True while the player is choosing targets for a skill.

`public bool IsResultShown`

:   Whether the result banner is currently up. A `ShowResult` call whose result is null, not yet terminal, or carries no result id clears this again, which is what makes the call safe to repeat every frame.

`public BattleUiCommandChoice? LastCommandChoice`

:   The most recent choice raised through `CommandChosen`. Null until the player has chosen once, and never cleared afterwards.

`public bool LegacyInputAvailable`

:   Classic input is available; the demo polls it here.<br>Compilation condition: `#if ENABLE_LEGACY_INPUT_MANAGER`.

`public bool LegacyInputAvailable`

:   The legacy input manager is disabled. The tray remains fully clickable through the graphic raycaster, so only the number-key shortcuts are unavailable; nothing throws.<br>Compilation condition: `#else (matching #if ENABLE_LEGACY_INPUT_MANAGER)`.

`public IReadOnlyList<SkillCommandShape> OfferedSkills`

:   The skill shapes the tray is offering, in the order the decision supplied them. Empty whenever no actor is pending.

`public IReadOnlyList<StableId> OfferedTargets`

:   The candidates currently on offer in the picker, or an empty list when no target is being chosen.

`public bool OffersConcede`

:   Whether a concede button is offered. This is exactly the condition under which `ChooseConcede` raises anything, so a custom tray can use it to decide whether to draw the button at all.

`public IReadOnlyList<StableId> PickedTargets`

:   The picks made so far, in pick order. A live view of the interface's own list, emptied as soon as the pick is committed or abandoned.

`public bool PresentationVisible`

:   Shows only this view's owned visuals without disabling a shared host object.

`public StableId? ResultId`

:   The id of the surfaced result, or null while none is shown. This is the simulation's own result id, not a display string; use the label table to turn it into text.

`public string ResultText`

:   One-line text form of the surfaced result, with the winning team appended when there is one. Empty while no result is shown. The banner draws its own labels; this string is for logs and tests.

`public CompiledBattleSkin Skin`

:   The resolved skin this interface draws with.

`public Vector2 StageInsets`

:   The share of the screen the interface's full-width bands claim, as a (top, bottom) pair of fractions. This is what makes the protected stage a fact rather than an intention: `BattleStageFrame` reads it instead of carrying its own margins, so a skin that grows its rail cannot silently start drawing over the combatants.

`public IReadOnlyList<UiStatusEntry> StatusEntries`

:   The surfaced status rows, in snapshot order. A live view, rebuilt in place by every `UpdateStatus` call.

`public StableId? TargetingSkillId`

:   The skill targets are being chosen for, or null while none is.

`public IReadOnlyList<StableId> TimelineActors`

:   The actors on the timeline strip, in the order they were supplied. This is a live view of the interface's own list, so copy it if you need it to survive the next update.

`public RectTransform TransportMount`

:   A mount point for host-supplied controls such as the sample's scenario picker, placed by the skin's transport region.

`public Vector2 ViewportSize`

:   The size the interface is actually being drawn into. This is deliberately not `Screen`. A canvas can be smaller than the screen, can belong to a camera rendering into a texture, and in batch mode reports 640x480 whatever the render target really is - so a layout that switches on Screen switches on the wrong thing and cannot be checked at any resolution but the one the window happens to be. The canvas's own rect follows the real target, so it is what decides.

    - **Returns** &mdash; The canvas rect when it has one, then the camera's pixel rect, and only then the screen - each fallback used only when the one before it has not been established yet.

**Fields**

`public const int MaximumFeedbackLines`

:   Section 10 cap: feedback log lines retained.

**Events**

`public event Action<BattleUiCommandChoice> CommandChosen`

:   Raised when the player chooses a command; never submitted here.

**Methods**

`public void AppendFeedback(BattleEvent battleEvent, DisplayStringTable labels)`

:   Appends one feedback line from an event (bounded log).

    - `battleEvent` &mdash; The event to describe; null appends nothing. Its type id, plus the actor id when the event carries one, become the line.
    - `labels` &mdash; Display names for those ids. Any id the table does not cover, and every id at all when this is null, is written as the raw id text.

`public void ApplySkin(BattleSkinPreset preset)`

:   Replaces the skin and rebuilds the interface. Safe to call at runtime, which is what lets the Skin Browser preview a look live.

    - `preset` &mdash; The look to adopt, or null to fall back to the shipped default skin.

`public bool BeginTargeting(StableId skillId)`

:   Opens the target picker for one offered skill. It declines, and returns false, whenever there is nothing to pick: an automatic-selection resolver, a skill that requires no ids, a skin with the picker region hidden, or no supplied candidate list. A caller that gets false should raise the choice with no targets, which leaves resolution to the driver as it always did.

    - `skillId` &mdash; The offered skill to pick targets for.
    - **Returns** &mdash; True when the picker is now on screen.

`public void BindStage(BattleStage2D stage)`

:   Hands the interface the stage the reticle should sit on. The presenter calls this when it binds; a project driving the interface without a presenter can call it too, and leaving it unset simply means the cursor treatment falls back to the button row.

    - `stage` &mdash; The stage whose tokens the reticle points at.

`public void CancelTargeting()`

:   Abandons the pick in progress and puts the skill tray back. Safe to call when no target is being chosen.

`public void ChooseConcede()`

:   Raises a concession command for the driver. Silently does nothing unless the pending decision actually offers concession.

`public void ChooseSkill(StableId skillId, IReadOnlyList<StableId> targets)`

:   Raises the chosen-skill command for the driver. The UI submits nothing; it only surfaces the player's intent.

    - `skillId` &mdash; The skill the player picked. Nothing is raised while no actor is pending, and the id is not re-checked against the offer.
    - `targets` &mdash; Exact targets, copied into the choice. Null or empty hands target resolution to the driver, which is what the shipped tray does.

`public void ClearDecision()`

:   Clears any offered decision.

`public void ClearTargetCandidates()`

:   Forgets every supplied candidate list. Call it before supplying the lists for a new decision so a combatant that has since died cannot linger in the picker.

`public void ConfirmTargets()`

:   Commits the current picks and raises the skill choice. Does nothing while fewer targets are picked than the skill requires.

`public void Initialize()`

:   Builds the uGUI tree. Explicit so EditMode tests can call it. Awake already calls it, and a second call does nothing.

`public void MoveReticle(int delta)`

:   Steps the reticle to the next or previous candidate, wrapping at both ends. Does nothing under a preset that has no cursor.

    - `delta` &mdash; How many candidates to move; negative steps back.

`public void PickPointedTarget()`

:   Picks whoever the reticle is currently over. This is the confirm half of the cursor treatment; the direction keys are the other half.

`public void PickTarget(StableId combatantId)`

:   Picks or unpicks one combatant. Ignored unless a target is being chosen and the id is one of the offered candidates, so it is safe to wire straight to a click on a stage token. A single-target skill commits on the pick itself; a multi-target skill accumulates picks until `ConfirmTargets` is called.

    - `combatantId` &mdash; The combatant the player pointed at.

`public void SetCombatantPortrait(StableId combatantId, Sprite portrait)`

:   Supplies the portrait a combatant's rail chip crops its face from.

    - `combatantId` &mdash; Combatant the art belongs to.
    - `portrait` &mdash; The sprite to crop, or null to drop one already supplied. The interface never loads art itself, so a combatant with no portrait draws a chip with a plain surface instead.

`public void SetCombatantPortrait(StableId combatantId, Sprite portrait, FormationFacing sourceFacing, FormationFacing desiredFacing)`

:   Supplies a portrait and its authored and displayed directions.

    - `combatantId` &mdash; Combatant the art belongs to.
    - `portrait` &mdash; The sprite to crop, or null to remove it.
    - `sourceFacing` &mdash; Direction encoded by the unmirrored sprite.
    - `desiredFacing` &mdash; Direction this portrait should face on the rail.

`public void SetCombatantPortrait(StableId combatantId, Sprite portrait, FormationFacing sourceFacing, FormationFacing desiredFacing, UiPortraitCrop crop)`

:   Supplies explicit facing and a rail-only normalized crop.

    - `combatantId` &mdash; Combatant receiving the portrait.
    - `portrait` &mdash; Portrait sprite, or null to clear it.
    - `sourceFacing` &mdash; Direction encoded by the source sprite.
    - `desiredFacing` &mdash; Direction shown by the rail.
    - `crop` &mdash; Finite normalized crop, or default for legacy framing.

`public void SetCombatantPortrait(StableId combatantId, Sprite portrait, FormationFacing sourceFacing, UiPortraitCrop crop)`

:   Supplies a crop while retaining current team auto-facing.

    - `combatantId` &mdash; Combatant receiving the portrait.
    - `portrait` &mdash; Portrait sprite, or null to clear it.
    - `sourceFacing` &mdash; Direction encoded by the source sprite.
    - `crop` &mdash; Finite normalized crop, or default for legacy framing.

`public void SetCombatantPortrait(StableId combatantId, Sprite portrait, FormationFacing sourceFacing)`

:   Supplies a portrait with its authored direction while letting the timeline choose the displayed direction from its current team state. This overload is used by UI-only presenters that have no stage token.

    - `combatantId` &mdash; Combatant the art belongs to.
    - `portrait` &mdash; The sprite to crop, or null to remove it.
    - `sourceFacing` &mdash; Direction encoded by the unmirrored source sprite.

`public void SetPlayerTeam(StableId teamId)`

:   Names the team the rail and the health bars should read as "ours". Presentation only: it updates team colors and refreshes portraits whose displayed direction is derived from the team row. Explicit portrait destinations remain fixed.

    - `teamId` &mdash; The player's team. The default id makes every combatant read as an opponent, which is the honest answer when no perspective was supplied.

`public void SetTargetCandidates(StableId skillId, IReadOnlyList<StableId> candidates)`

:   Supplies the combatants one offered skill may legally hit. The driver reads these from the skill's registered target resolver - the same object the engine consults - and hands them in, which is what keeps the picker from offering a target the engine would then refuse. A skill nothing was supplied for is picked for by the driver exactly as it was before the picker existed.

    - `skillId` &mdash; The offered skill the list belongs to.
    - `candidates` &mdash; Legal picks in display order; null or empty leaves target resolution to the driver.

`public void SetTooltip(TooltipData tooltip)`

:   Updates set tooltip on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `tooltip` &mdash; Already-computed tooltip text. Ignored unless its skill id is valid, and it replaces any tooltip previously stored for that skill.

`public void ShowDecision(DecisionOptions options)`

:   Offers exactly the legal command shapes the snapshot exposes.

    - `options` &mdash; The shapes to offer; null withdraws the offer, as `ClearDecision` does.

`public void ShowResult(BattleResultState result, DisplayStringTable labels)`

:   Surfaces a terminal result verbatim (all five kinds).

    - `result` &mdash; The result to show. Null, not yet terminal, or carrying no result id all hide the banner instead, so this may be called every frame.
    - `labels` &mdash; Display names for the result and winning team ids. Uncovered ids, and all ids when this is null, are shown as raw id text.

`public void Tick(float presentationDeltaSeconds)`

:   Advances interface animation by a visual delta. The driver forwards its presentation delta here so pause and speed apply to the HUD exactly as they do to the stage.

    - `presentationDeltaSeconds` &mdash; Presentation seconds since the last call. Zero or negative freezes animation clocks while still refreshing layout and target anchors.

`public bool TryGetTooltip(StableId skillId, out TooltipData tooltip)`

:   Returns the tooltip previously supplied for a skill.

    - `tooltip` &mdash; The stored tooltip, or the default value when none was supplied.
    - `skillId` &mdash; Skill identity previously supplied to `SetTooltip`.
    - **Returns** &mdash; True when `SetTooltip` has stored data for this skill.

`public void UpdateStatus(BattleSnapshot snapshot, DisplayStringTable labels)`

:   Rebuilds the status panel from the snapshot.

    - `snapshot` &mdash; Source of health, shields, and status counts; null empties the panel. It is only read, never advanced.
    - `labels` &mdash; Display names for the rows. Null keeps the table from an earlier call, so labels never have to be resupplied.

`public void UpdateTimeline(FrozenList<DecisionEntry> decisions)`

:   Mirrors the currently-ready decision entries as the timeline.

    - `decisions` &mdash; Ready entries to mirror, kept in the order supplied; null or empty clears the strip. Only each entry's actor is read.

`public void UpdateTimeline(IReadOnlyList<StableId> order)`

:   Mirrors a full turn order onto the rail, soonest first.

    - `order` &mdash; Actors in the order they will act. Null or empty clears the rail. The order is drawn exactly as given: the interface neither sorts it nor asks a scheduler anything.

---

## BattleViewCost

```csharp
public sealed class BattleViewCost
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewActionDetails.cs</small>

Immutable resource price of one action.

**Constructors**

`public BattleViewCost(StableId resourceId, string label, int amount)`

:   Creates a read-only cost; a null label becomes empty.

    - `resourceId` &mdash; Stable resource identity that pays the cost.
    - `label` &mdash; Display label of the resource.
    - `amount` &mdash; Amount spent, at least zero.

**Properties**

`public int Amount`

:   Amount spent.

`public string Label`

:   Display label of the resource.

`public StableId ResourceId`

:   Stable identity of the resource that pays the cost.

---

## BattleViewEstimate

```csharp
public sealed class BattleViewEstimate
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewActionDetails.cs</small>

An estimate the host chose to publish for an action. The projection shipped with the package publishes none, because the
simulation exposes no side-effect-free estimator; a host that owns one can supply values and the views will show them.

**Constructors**

`public BattleViewEstimate(StableId targetId, BattleViewEstimateKind kind, int minimum, int maximum)`

:   Creates a read-only estimate.

    - `targetId` &mdash; Combatant the estimate applies to, or an invalid id when it applies to every target.
    - `kind` &mdash; Damage or healing.
    - `minimum` &mdash; Lowest expected amount, at least zero.
    - `maximum` &mdash; Highest expected amount, not below the minimum.

**Properties**

`public BattleViewEstimateKind Kind`

:   Damage or healing.

`public int Maximum`

:   Highest expected amount.

`public int Minimum`

:   Lowest expected amount.

`public StableId TargetId`

:   Combatant the estimate applies to; invalid means every target.

---

## BattleViewEstimateKind

```csharp
public enum BattleViewEstimateKind
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewActionDetails.cs</small>

Whether an estimate describes lost or restored health.

| Value | Meaning |
| --- | --- |
| `Damage` | Health the target is expected to lose. |
| `Healing` | Health the target is expected to regain. |

---

## BattleViewExecution

```csharp
public sealed class BattleViewExecution
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

What the stage is showing right now while no decision is pending: who acts, with which action, and on whom. While the stage plays
nothing and the next thing the engine does is a cast landing, it is that cast, with nobody reached yet: the turn is already its owner's.

**Constructors**

`public BattleViewExecution(StableId actorId, StableId actionId, string actionLabel, FrozenList<StableId> targetIds = null)`

:   Creates the description of an action in progress.

    - `actorId` &mdash; Acting combatant.
    - `actionId` &mdash; Action in progress.
    - `actionLabel` &mdash; Display label of the action.
    - `targetIds` &mdash; Combatants the action has reached so far; null means none are known yet.

**Properties**

`public StableId ActionId`

:   Action in progress.

`public string ActionLabel`

:   Display label of the action.

`public StableId ActorId`

:   Acting combatant.

`public FrozenList<StableId> TargetIds`

:   Combatants the action has reached so far.

---

## BattleViewResource

```csharp
public sealed class BattleViewResource
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Immutable, renderer-independent value of one combatant resource pool.

**Constructors**

`public BattleViewResource(StableId id, string label, int value, int maximum)`

:   Creates a read-only resource value; a null label becomes empty.

    - `id` &mdash; Stable resource identity.
    - `label` &mdash; Display label.
    - `value` &mdash; Current amount.
    - `maximum` &mdash; Maximum amount.

**Properties**

`public float Fraction`

:   Current amount as a fraction of the maximum, clamped to zero through one; zero when the maximum is not positive.

`public StableId Id`

:   Stable resource identifier.

`public string Label`

:   Display label.

`public int Maximum`

:   Maximum amount.

`public int Value`

:   Current amount.

---

## BattleViewStatus

```csharp
public sealed class BattleViewStatus
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Immutable, renderer-independent status carried by one combatant.

**Constructors**

`public BattleViewStatus(StableId id, string label, int stacks = 1)`

:   Creates a read-only status entry; a null label becomes empty.

    - `id` &mdash; Stable status definition identity.
    - `label` &mdash; Display label.
    - `stacks` &mdash; Stack count, at least one.

`public BattleViewStatus(StableId id, string label, int stacks, int turns)`

:   Creates a read-only status entry with the duration a command applies; a null label becomes empty.

    - `id` &mdash; Stable status definition identity.
    - `label` &mdash; Display label.
    - `stacks` &mdash; Stack count, at least one.
    - `turns` &mdash; The duration, in turns of its owner, that the command applies; zero for none to show. Never negative.

**Properties**

`public StableId Id`

:   Stable status definition identifier.

`public string Label`

:   Display label.

`public int Stacks`

:   Number of stacks applied.

`public int Turns`

:   The duration, in turns of its owner, that the command applies; 0 on the current statuses of a combatant (`BattleViewCombatant.StatusEntries`) and for a duration that is not counted in the owner's turns. With independent stacks every application keeps its own clock: this is the duration applied, never a remaining one.

---

## BattleViewTargetScope

```csharp
public enum BattleViewTargetScope
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewActionDetails.cs</small>

Who an action reaches, in terms a player reads rather than the identity of the resolver that decides it.

| Value | Meaning |
| --- | --- |
| `Unspecified` | The projection did not classify the target rule; views show no scope phrase. |
| `SingleEnemy` | One opposing combatant picked by the player. |
| `SingleAlly` | One allied combatant picked by the player. |
| `Self` | The acting combatant only. |
| `AllEnemies` | Every opposing combatant. |
| `AllAllies` | Every allied combatant. |
| `Everyone` | Every combatant on both sides. |
| `RandomEnemy` | Opposing combatants drawn at random. |
| `RandomAlly` | Allied combatants drawn at random. |
| `RandomAny` | Combatants of either side drawn at random. |
| `FormationRow` | One formation row. |
| `FormationSide` | One side of the field. |
| `SingleAny` | A picked combatant whose team is not constrained. |

---

## BattleViewTimelineEntry

```csharp
public sealed class BattleViewTimelineEntry
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Immutable, renderer-independent turn-order entry for one combatant.

**Constructors**

`public BattleViewTimelineEntry(StableId id, string name, StableId teamId, bool isNext)`

:   Creates a read-only turn-order entry; a null name becomes empty.

    - `id` &mdash; Stable combatant identity, or invalid for legacy label-only data.
    - `name` &mdash; Display name.
    - `teamId` &mdash; Stable team identity, or invalid for legacy label-only data.
    - `isNext` &mdash; Whether this combatant is the next actor.

`public BattleViewTimelineEntry(StableId id, string name, StableId teamId, bool isNext, bool isCurrent)`

:   Creates a read-only turn-order entry that can also say whose turn is being played; a null name becomes empty.

    - `id` &mdash; Stable combatant identity, or invalid for legacy label-only data.
    - `name` &mdash; Display name.
    - `teamId` &mdash; Stable team identity, or invalid for legacy label-only data.
    - `isNext` &mdash; Whether this combatant is the next actor.
    - `isCurrent` &mdash; Whether this combatant is the one whose action the stage is playing right now.

**Properties**

`public StableId Id`

:   Stable combatant identifier; invalid for legacy label-only data.

`public bool IsCurrent`

:   True for the combatant whose turn is being played on the stage right now, an opposing combatant included. At most one entry of a timeline carries it, and it is the first.

`public bool IsNext`

:   True for the combatant that acts next. At most one entry of a timeline carries it; while an action is played it is the one after `IsCurrent`.

`public string Name`

:   Display name.

`public StableId TeamId`

:   Stable team identifier; invalid for legacy label-only data.

---

## DecisionOptions

```csharp
public sealed class DecisionOptions
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DecisionShape.cs</small>

The complete set of legal command shapes for one pending decision:
filtered granted skills plus whether concession is offered. This is a
display projection, never a submission.

**Constructors**

`public DecisionOptions(bool hasActor, StableId actorId, bool canConcede, IReadOnlyList<SkillCommandShape> skills)`

:   Creates an option set. A null skill list becomes an empty one, so a caller never has to null-check `Skills`.

    - `hasActor` &mdash; False for the "nothing to decide" set; see `None`.
    - `canConcede` &mdash; Whether a concede command may be offered alongside the skills.
    - `actorId` &mdash; Pending actor, or the default ID when absent.
    - `skills` &mdash; Legal skills; null becomes an empty list.

**Properties**

`public StableId ActorId`

:   The combatant every entry in `Skills` belongs to, and the one whose command the engine will serve next.

`public bool CanConcede`

:   Whether a concede command may be offered alongside the skills. It reports only that the compiled content registers the concede command at all, so it does not vary from actor to actor within a battle.

`public bool HasActor`

:   Whether a decision is actually pending. It is the flag to test before reading `ActorId`, which carries the default ID in the empty set rather than any meaningful combatant.

`public static DecisionOptions None`

:   The empty set - no actor, no concession, no skills. Returned whenever there is nothing for a player to decide.

`public IReadOnlyList<SkillCommandShape> Skills`

:   The skills the actor may use at this moment, ordered by skill ID so a given decision always lays out the same way. Never null. A granted skill that is on cooldown, unaffordable, or restricted by a status is absent altogether rather than present and marked unusable, so a tray that draws greyed-out entries has to keep its own list of what the actor was granted.

---

## DecisionShapeCompiler

```csharp
public static class DecisionShapeCompiler
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DecisionShape.cs</small>

Pure compiler of legal command shapes from a snapshot and compiled
catalog. It offers a granted skill only when the snapshot-visible
cooldowns, resource costs, restriction tags, and visible interrupt-target
preconditions allow it, and it reads the target shape from the compiled target contract. It performs no exact
re-resolution and calls no engine mutator or preview API.

**Methods**

`public static DecisionOptions Compile(BattleSnapshot snapshot, CompiledAuthoringCatalog catalog)`

:   Builds the option set for the decision at the head of the snapshot's queue. Only that first entry is considered, and only when it is human-controlled, because it is the one the engine serves next. A granted skill is offered only when the snapshot shows no live cooldown for it, every resource cost is affordable from the actor's current pools, no status on the actor restricts one of the skill's tags, and its target resolver is registered. Interrupt skills also require a currently interruptible cast among their eligible targets. Concession is offered when the compiled content registers the concede command at all.

    - `snapshot` &mdash; State to read; nothing in it is mutated.
    - `catalog` &mdash; Compiled content the granted skills and target contracts are read from.
    - **Returns** &mdash; `DecisionOptions.None` for a null argument, an empty or non-human decision queue, a missing or dead actor, or a combatant definition the catalog does not contain; otherwise the legal shapes, ordered by skill id so the same decision always lays out the same way.

---

## DisplayStringTable

**Start here**

```csharp
public sealed class DisplayStringTable
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DisplayStringTable.cs</small>

A non-authoritative map from stable id to display text. Compiled
snapshots carry no labels (they are excluded from B3 compilation and
hashes), so the driver supplies this table from authoring
`DisplayLabel` metadata or a shipped serialized string table. The
table never enters any hash and never affects a simulation output.

**Constructors**

`public DisplayStringTable(IEnumerable<KeyValuePair<StableId, string>> pairs = null)`

:   Copies the supplied labels into a table. The pairs are read once here, so the table does not observe later changes to the source.

    - `pairs` &mdash; Id-to-label pairs; entries with an invalid id or a null label are dropped, and a repeated id keeps the last label. Null builds an empty table.

**Properties**

`public int Count`

:   How many ids carry a label. Pairs the constructor dropped as invalid, and repeats collapsed onto one id, are not counted, so a total below the number of pairs supplied is how those losses show up.

`public static DisplayStringTable Empty`

:   An empty table; every lookup falls back to the raw id.

**Methods**

`public string GetOrId(StableId id)`

:   Returns the label for an id, or the raw id text as a fallback.

    - `id` &mdash; Content identity to resolve, with its canonical text serving as the fallback.
    - **Returns** &mdash; The mapped non-empty label, or the raw stable-ID text when no label is available.

`public bool TryGet(StableId id, out string text)`

:   Looks up the label for an id without falling back to it.

    - `text` &mdash; The label, or null when the id is invalid or unlabelled.
    - `id` &mdash; Valid content identity whose localized or authored label is requested.
    - **Returns** &mdash; True when a label was found.

---

## DisplayStringTableProvider

```csharp
public abstract class DisplayStringTableProvider : ScriptableObject
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DisplayStringTableProvider.cs</small>

Serialized, project-owned source of non-authoritative display labels.
Runtime hosts request a fresh immutable table when a battle is bound;
labels never enter simulation state, hashes, checkpoints, or replays.

**Methods**

`public abstract DisplayStringTable Build()`

:   Builds a display table from this provider's serialized source.

    - **Returns** &mdash; A display table containing the provider's authored labels.

---

## FeedbackLogView

```csharp
public sealed class FeedbackLogView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/FeedbackLogView.cs</small>

The rolling battle log. It shows the most recent lines newest-last and
fades older entries so the newest line reads first.

The owning `BattleUiRoot` keeps the authoritative bounded line
list; this view only draws a window onto its tail, so the 512-line cap is
enforced in exactly one place.

**Fields**

`public const int VisibleLines`

:   Lines drawn at once. The log itself retains far more.

**Methods**

`public void Apply(IReadOnlyList<string> allLines)`

:   Draws the tail of `allLines`. The newest line is fully opaque and older ones fade toward the muted role.

    - `allLines` &mdash; The whole log, oldest first; only the last `VisibleLines` entries are drawn. Null or empty clears every row.

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the panel. Explicit so EditMode tests can drive it. A second call stores the new skin but does not restyle widgets already built.

    - `battleSkin` &mdash; Skin to draw with; null falls back to the shipped default.

---

## GeneratedUiRoot

```csharp
public sealed class GeneratedUiRoot : MonoBehaviour
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUGUI/GeneratedUiRoot.cs</small>

Records the view that owns a generated dynamic subtree across serialization and cloning.

!!! note "Remarks"
    Authored semantic slots remain outside this subtree. Cloning a view with an external root does not transfer ownership of the original controls.

**Properties**

`public bool HasOwnerBinding`

:   True after this subtree has been assigned to a view, including after that view is removed.

`public UguiBattleView Owner`

:   The view allowed to reuse and release this generated subtree, or null once that view is gone. A view that was removed and then restored on the same object, as an undo does, is recognized as the owner again.

---

## IBattlePortraitSource

**Extension point** &mdash; implement this yourself to change behaviour

```csharp
public interface IBattlePortraitSource
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/IBattlePortraitSource.cs</small>

Supplies combatant portraits to a native view. The host implements it once and both the uGUI and the
UI Toolkit adapter draw from it, so portraits never depend on the technology that renders them.

**Methods**

`public bool TryGetPortrait(StableId combatant, out Sprite sprite, out Rect normalizedCrop, out bool flipX)`

:   Looks up the portrait of a combatant.

    - `combatant` &mdash; Stable identity of the combatant.
    - `sprite` &mdash; Receives the source sprite when a portrait exists; otherwise null.
    - `normalizedCrop` &mdash; Receives the visible window of the sprite in normalized coordinates with a bottom-left origin, ready to use as a UV rectangle.
    - `flipX` &mdash; Receives whether the portrait must be mirrored horizontally to face the way the combatant faces on stage.
    - **Returns** &mdash; True when a portrait exists; false when the view should draw its monogram fallback.

---

## ResultBannerView

```csharp
public sealed class ResultBannerView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/ResultBannerView.cs</small>

The terminal result banner. It surfaces all five terminal kinds (victory,
defeat, draw, concession, and the stalled result) and tints itself by
outcome so the end state reads instantly.

It displays the result it is handed and decides nothing about the outcome.

**Properties**

`public bool IsShown`

:   True while the banner is displayed.

**Methods**

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the banner. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin to draw with; null falls back to the shipped default.

`public void Hide()`

:   Hides the banner.

`public void Show(StableId resultId, string headlineText, string detailText)`

:   Shows a terminal result. `headlineText` and `detailText` are already-localized display strings.

    - `resultId` &mdash; Terminal result id. It only picks the tint; an id the package does not ship still displays, in the neutral accent.
    - `detailText` &mdash; Second line; when null or empty the line is hidden rather than left blank.
    - `headlineText` &mdash; Primary result line, such as Victory or Defeat; null displays an empty headline.

`public void Tick(float deltaSeconds)`

:   Advances the fade-in by a visual delta.

    - `deltaSeconds` &mdash; Positive visual-frame duration consumed by the remaining fade time.

---

## SafeAreaFitter

```csharp
public sealed class SafeAreaFitter : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/SafeAreaFitter.cs</small>

Insets a `RectTransform` to the device safe area so HUD
regions never land under a notch, a punch-hole camera, or a home
indicator. It re-applies only when the screen or safe area actually
changes, so it costs nothing on desktop.

The whole HUD sits inside one of these, which means every skin region is
automatically safe-area correct without the buyer positioning anything
twice.

**Properties**

`public Rect AppliedNormalizedArea`

:   The normalized safe area currently applied.

**Methods**

`public bool Apply(int screenWidth, int screenHeight, Rect safeAreaPixels)`

:   Applies a safe area explicitly. Public and parameterised so EditMode tests can verify inset maths without a device.

    - `safeAreaPixels` &mdash; Device-safe rectangle expressed in bottom-left-origin screen pixels.
    - `screenHeight` &mdash; Full render-target height in pixels.
    - `screenWidth` &mdash; Full render-target width in pixels.
    - **Returns** &mdash; `true` after valid normalized anchors are applied; otherwise `false` for zero screen dimensions or an empty area.

---

## SkillCommandShape

```csharp
public sealed class SkillCommandShape
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DecisionShape.cs</small>

One legal skill command shape offered to the pending actor.

**Constructors**

`public SkillCommandShape(StableId skillId, TargetShape target)`

:   Pairs a skill with the target shape its resolver declares.

    - `skillId` &mdash; Valid compiled skill identity represented by this command option.
    - `target` &mdash; Targeting rule the skill resolver requires before command submission.

**Properties**

`public StableId SkillId`

:   The skill this shape stands for, and the ID to carry in the command once the player commits to it.

`public TargetShape Target`

:   What this skill's resolver will accept: how many target IDs the command may carry and which combatants qualify. Read it to decide how many picks to collect before the command is submittable.

---

## SkillTitleView

```csharp
public sealed class SkillTitleView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/SkillTitleView.cs</small>

The skill title card: the name of what is being performed, announced as it
happens and gone again a moment later.

It draws with the same surface and typography tokens as every other region,
so it inherits whichever skin is applied without any per-skin work. Like the
result banner, it displays what it is handed and decides nothing.

**Properties**

`public float Alpha`

:   Current alpha, which is what a test can assert the fade against.

`public string CurrentTitle`

:   The text currently displayed, empty when the card is resting.

`public bool IsShown`

:   True while the card is on screen, fading counted as shown.

**Methods**

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the card. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin to draw with; null falls back to the shipped default.

`public void Hide()`

:   Takes the card down immediately.

`public void Show(string displayName, float holdSeconds, float fadeInOutSeconds)`

:   Announces a skill. Calling it again while a card is up replaces it and restarts the hold, so a fast chain of skills reads as the latest one rather than queueing cards the player will never see.

    - `displayName` &mdash; Already-localized skill name; empty hides the card.
    - `holdSeconds` &mdash; Total seconds on screen, fades included. Zero or less hides the card.
    - `fadeInOutSeconds` &mdash; Fade time at each end, clamped to half the hold.

`public void Tick(float deltaSeconds)`

:   Advances the fade and the hold on the presentation clock, so pause and speed reach the card the same way they reach everything else.

    - `deltaSeconds` &mdash; Elapsed presentation seconds; zero or less does nothing.

---

## SkillTrayView

```csharp
public sealed class SkillTrayView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/SkillTrayView.cs</small>

The command tray offered to a pending human actor: one button per legal
skill shape plus concede.

It raises plain C# events carrying the player's choice and submits
nothing. Target resolution, legality, and submission all stay with the
driver and the engine, which is what keeps the presenter-purity contract
intact while still giving the player something clickable.

**Properties**

`public int VisibleButtonCount`

:   Buttons currently visible.

**Fields**

`public const float CardHeight`

:   Height of one skill card in reference pixels. The command deck is 280 tall, a 46-pixel log strip caps it, and the actor prompt takes a line above the cards, which is what leaves 196 rather than the 216 a card would take if it had the band to itself.

`public const float CardIconSize`

:   Edge of the icon plate in a card's top-left corner.

`public const float CardWidth`

:   Width of one skill card in reference pixels.

`public const float ConcedeCardWidth`

:   Width of the narrower concede card in reference pixels.

`public const int MaximumButtons`

:   Buttons drawn before the tray stops adding more.

`public const float MaximumCardWidth`

:   Widest a single card is allowed to grow when few skills are offered, in reference pixels. Without a ceiling a one-skill decision would hand the whole deck to one button.

**Events**

`public event Action ConcedeChosen`

:   Raised when the player concedes. Never submitted here.

`public event Action<StableId> SkillChosen`

:   Raised when the player picks a skill. Never submitted here.

`public event Action SkillFocusCleared`

:   Raised when the pointer leaves every skill button.

`public event Action<StableId> SkillFocused`

:   Raised when the pointer enters a skill button.

**Methods**

`public void Apply(DecisionOptions options, DisplayStringTable labels)`

:   Offers exactly the shapes in `options`. An empty or non-human decision hides the tray entirely. Does nothing before `Build` has run, and never offers more than `MaximumButtons` skills however many are legal.

    - `labels` &mdash; Display names for the actor and skill ids; null, or an id the table does not carry, falls back to the raw id text.
    - `options` &mdash; Current actor's legal skill and target shapes used to populate the tray.

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the tray. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin every widget in the tray is drawn from; null falls back to `BattleSkinDefaults.Default`. Only the first call builds the widget tree - a later call stores the skin and returns.

`public void ClearSelection()`

:   Clears every button highlight.

`public void SetSelected(StableId skillId)`

:   Highlights the button for `skillId`.

    - `skillId` &mdash; Skill identity whose pooled button receives the selected visual state.

---

## SkinnedTokenPlate

```csharp
public sealed class SkinnedTokenPlate : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Widgets/SkinnedTokenPlate.cs</small>

The floating plate above one combatant: name, health, shield, cast
progress, scheduler gauge, and status pips.

It lives on a world-space canvas parented to the token, so it tracks the
token with no per-frame screen projection and works with any camera setup
the buyer already has. Everything it draws comes from values handed to it;
it reads no simulation state and computes nothing authoritative.

**Properties**

`public TokenPlateDisplay Display`

:   How much of the plate is currently drawn.

`public TokenPlateDisplay DrawnDisplay`

:   What the canvas draws right now. It differs from `Display` only while a plate fades out the look it is leaving.

`public float EffectivePresence`

:   How opaque the plate is on the screen right now, from 0 to 1: `Presence` times the opacity the stage gives the whole interface of the world, which a theme swap lowers while it dips the HUD. It equals `Presence` at rest.

`public bool HasWorldTopOverride`

:   True when a caller has supplied a world-space top edge.

`public bool IsAboveHead`

:   True when the full plate stands above the head of a selected target.

`public bool IsBuilt`

:   True once `Build` has run.

`public float Presence`

:   How opaque the plate is drawn right now, from 0 to 1, by its own fade. It follows `Display` over the length of a fade and does not move with the opacity the stage gives the whole interface of the world; `EffectivePresence` is what is on the screen.

`public bool ValueHasOutline`

:   True when the value of health is drawn with a dark outline, because no single text colour reads on the fill and on the track at once.

`public float ValueSize`

:   Size of the value of a combatant's health, in reference pixels, at the scale the plate is drawn at now.

`public int VisiblePipCount`

:   Status pips currently visible.

**Fields**

`public const float BarOnlyHeight`

:   Height of the bare health bar drawn under a combatant, in reference pixels. Tall enough to stay at least 8 pixels high at 720p.

`public const float BarOnlyWidth`

:   Width of the bare health bar drawn under a combatant, in reference pixels.

`public const float BarOutlineWidth`

:   Thickness of the dark outline around the bare health bar, in reference pixels: 1.3 to 2 screen pixels at the scales a plate is drawn at.

`public const float CriticalHealthFraction`

:   Health fraction below which a combatant reads as in danger. The bar does not change colour there, because colour already means which side you are on. Instead its border lights and its fill pulses, which is a second channel rather than an overloaded one.

`public const int DefaultSortingOrder`

:   Builds the plate. Explicit so EditMode tests can construct one with no scene and no camera.

    - `battleSkin` &mdash; Skin the plate is dressed from; null falls back to the package default.
    - `unitsPerPixel` &mdash; World units one reference pixel is worth. It scales the whole plate, so `PlateWidth` only means 132 world units at a value of one.
    - `verticalOffsetPixels` &mdash; Height above the token in reference pixels. It is scaled by `unitsPerPixel` too, so the plate keeps its distance as the plate is resized.

`public const float MinimumBarOnlyWidth`

:   Narrowest the bare health bar is ever drawn, in reference pixels.

`public const float MinimumSelectedWidth`

:   Narrowest canvas of the plate of a selected target, in reference pixels. At the size the value of health is drawn at it holds nine characters ("999 / 999") and the name is cut with an ellipsis instead of the plate growing back over a neighbour.

`public const float MinimumValuePixels`

:   Least size, in screen pixels at 1080p, of the value of a combatant's health (the "90 / 90"). It is read mid-turn to decide who to hit, so it is held to the same floor as the interface's essential text instead of the caption size of the skin, which a plate scaled down with its stage drew at 15.

`public const float PlateWidth`

:   Plate width in reference pixels.

`public const float SelectedBarHeight`

:   Height of the health bar of a plate drawn above a selected target, which carries its value inside the bar.

`public const float SelectedPlateWidth`

:   Width of the plate drawn above a selected target, in reference pixels.

`public const float ValueOutlinePixels`

:   Thickness, in reference pixels, of the dark outline drawn around the value of health when no single colour reads on the fill and the track.

**Methods**

`public void ApplyState(int health, int maximumHealth, int shieldAmount, int statusCount, bool isDead)`

:   Mirrors health, shield, and status counts onto the plate. Does nothing until `Build` has run.

    - `health` &mdash; Current health, used only to derive the bar's fraction.
    - `maximumHealth` &mdash; Denominator for both the health and shield bars. Zero or less empties the health bar and hides the shield, since neither has a scale to be drawn against.
    - `shieldAmount` &mdash; Absorb remaining, drawn as a share of `maximumHealth` and clamped there. Zero hides the shield bar.
    - `statusCount` &mdash; Total statuses on the combatant, not the number of pips to draw. Anything beyond the skin's visible limit collapses into a single overflow pip.
    - `isDead` &mdash; Draws the health bar empty and mutes the name regardless of `health`.

`public void Build(CompiledBattleSkin battleSkin, float unitsPerPixel, float verticalOffsetPixels)`

:   Creates the plate's world-space canvas, backing, labels and bars once. Later calls retain the existing hierarchy and replace only the stored skin reference.

    - `battleSkin` &mdash; Skin used for initial typography and styling, or null for the default skin.
    - `unitsPerPixel` &mdash; Local world-space scale applied to each canvas pixel during the first build.
    - `verticalOffsetPixels` &mdash; Initial vertical offset from the parent origin, in canvas pixels scaled by unitsPerPixel.

`public Color CardBackdrop()`

:   The card the plate's text stands on, as it looks over the stage the card is judged against: its translucent fill laid over `SkinContrast.ReferenceStage`. The contrast of the name and of the side readout is held against this colour and against `CardBackdropOverBrightStage`.

    - **Returns** &mdash; The opaque colour behind the name of the combatant.

`public Color CardBackdropOverBrightStage()`

:   The card as it looks over a bright stage in this project: its translucent fill laid over `SkinContrast.BrightStage` and blended in the colour space the project renders in. It is the lightest the text of the plate is expected to stand on.

    - **Returns** &mdash; The opaque colour behind the name of the combatant over a bright stage.

`public void ClearHealthColor()`

:   Returns the health bar to the team tint after `SetHealthColor`.

`public void ClearWorldTopOverride()`

:   Restores the last ground-relative placement after a world-top override.

`public void FinishAnimations()`

:   Completes every bar transition at once, as a skipped beat does.

`public static float OutlinePixels(float outlineWidth, float fontSize)`

:   Thickness in reference pixels of the outline a label draws.

    - `outlineWidth` &mdash; Outline width of the label, 0 to 1.
    - `fontSize` &mdash; Font size of the label in reference pixels.
    - **Returns** &mdash; The thickness in reference pixels.

`public void Pulse(Transform target)`

:   Starts a scale pulse that always returns to rest. The previous implementation set a scale and never restored it, so tokens grew permanently every time they acted.

    - `target` &mdash; Transform to scale, normally the token root; null pulses this plate's own transform. A zero motion scale in the skin restores rest scale at once instead of animating.

`public static float SelectedBarHeightFor(float valueSize)`

:   Height of the bar of a selected target, in reference pixels, tall enough to hold a value of the given size.

    - `valueSize` &mdash; Font size of the value in reference pixels.
    - **Returns** &mdash; At least `SelectedBarHeight`.

`public float SelectedHeightReference()`

:   Height of the canvas of the plate of a selected target, in reference pixels, with the rows it shows now: the name, the bar that holds the value, and the shield, cast, gauge and status rows that are wanted.

    - **Returns** &mdash; The height in reference pixels.

`public void SetBarOnlyHeightMinimum(float heightPixels)`

:   Sets the least height of the bare health bar, in reference pixels, so the bar stays readable at the resolution it is drawn at instead of shrinking with a small sprite. Zero or less restores `BarOnlyHeight`.

    - `heightPixels` &mdash; Least height of the bare bar.

`public void SetBarOnlyWidthLimit(float widthPixels)`

:   Limits the width of the bare health bar, in reference pixels, so a narrow combatant or a crowded line gets a bar that fits under it. Zero or less restores `BarOnlyWidth`; a limit never makes the bar wider than that.

    - `widthPixels` &mdash; Widest the bare bar may be.

`public void SetCast(float fraction, bool visible)`

:   Shows cast progress in [0,1], or hides the bar.

    - `fraction` &mdash; Normalized cast completion forwarded to the cast bar when visible.
    - `visible` &mdash; Whether the cast-progress row participates in layout.

`public void SetCeiling(float? localY)`

:   Gives the whole plate of a selected target a highest allowed top edge, so it stays inside the stage instead of reaching into the turn ribbon above it. The value is relative to the token root, in token-local units; null removes the ceiling.

    - `localY` &mdash; Highest allowed top edge of the plate, or null.

`public void SetDisplay(TokenPlateDisplay plateDisplay, bool standAboveHead)`

:   Chooses how much of the plate is drawn and where it stands. A selected target gets the whole plate above its head with the value inside the bar; every other combatant gets a bare bar under its feet, or nothing when its health is shown elsewhere. `Display` and `IsAboveHead` answer at once. What the canvas draws follows on the presentation clock: a plate that appears fades in, one that goes fades out, and one that changes look fades the old look out and the new one in, within 250 milliseconds in all. A plate that has never been advanced has no clock to fade on and changes at once.

    - `plateDisplay` &mdash; How much of the plate to draw.
    - `standAboveHead` &mdash; True to place a full plate above the head instead of under the feet.

`public void SetFloor(float? localY)`

:   Gives the plate a lowest allowed edge, so it stays inside the free area of the stage instead of reaching into the interface below it. The value is relative to the token root, in token-local units; null removes the floor.

    - `localY` &mdash; Lowest allowed bottom edge of the plate, or null.

`public void SetGauge(float fraction, bool visible)`

:   Shows the scheduler gauge in [0,1], or hides it.

    - `fraction` &mdash; Normalized scheduler readiness forwarded to the gauge bar.
    - `visible` &mdash; Whether the scheduler gauge participates in layout.

`public void SetGroundPlacement(float widthPixels, float groundLinePixels, float overlapPixels, float unitsPerPixel)`

:   Moves the plate to a combatant's ground line and sizes it to their art. A nameplate pinned to a fixed offset above the token origin worked only while every combatant was the same 84-pixel square. Once they are painted illustrations of different heights, the plate has to follow the body it belongs to or it ends up across somebody's chest.

    - `widthPixels` &mdash; Width to draw at, in reference pixels. It is widened to 1.4 times the art so the name has room beside the readout, and floored at `PlateWidth` so a narrow combatant still gets a legible plate. Zero or less keeps the current width.
    - `groundLinePixels` &mdash; Where the combatant's feet are, relative to the token origin, in reference pixels. Art pivoted at its feet reports zero here.
    - `overlapPixels` &mdash; How far the plate's top edge rises above that ground line. A small positive value tucks the plate under the body it belongs to.
    - `unitsPerPixel` &mdash; World units one reference pixel is worth.

`public void SetGroundPlacement(float widthPixels, float groundLinePixels, float overlapPixels, float unitsPerPixel, float centreXPixels)`

:   Places the plate using the visual ground line and its horizontal centre, both relative to the token root. The four-argument overload remains the compatibility path for callers that use the token origin.

    - `widthPixels` &mdash; Width to draw in reference pixels; zero keeps the current width.
    - `groundLinePixels` &mdash; Visual ground line relative to the token origin.
    - `overlapPixels` &mdash; How far the plate rises over the visual ground line.
    - `unitsPerPixel` &mdash; World units per reference pixel.
    - `centreXPixels` &mdash; Visual ground centre relative to the token origin.

`public void SetHeadPlacement(float headLine)`

:   Tells the plate where the head of its combatant is, so it can stand above it. The line is relative to the token root, in reference pixels, like the ground line.

    - `headLine` &mdash; Top of the combatant's visible art relative to the token origin, in reference pixels.

`public void SetHealthColor(Color fill)`

:   Gives the health bar a fill of its own instead of the team tint. The name keeps the team tint.

    - `fill` &mdash; Fill color of the living health bar.

`public void SetLabel(string text)`

:   Updates set label on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `text` &mdash; Combatant display name written to the plate; null becomes empty.

`public void SetPresentationScale(float screenPixelsPerReferencePixel, float floorFactor = 1f)`

:   Tells the plate how large it is drawn on the screen, so the value of a health bar keeps its floor when the stage is smaller than the one the plate was authored for. The token passes the share of its reference size the plate follows the stage down to.

    - `screenPixelsPerReferencePixel` &mdash; Screen pixels one reference pixel is drawn at; anything above 1 counts as 1.
    - `floorFactor` &mdash; Multiple of the 18-pixel floor the value is held to, from the height of the screen; 1 up to 1080 pixels.

`public void SetSelectedFit(float shiftPixels, float widthPixels)`

:   Moves the whole plate of a selected target sideways and narrows it, so it stands clear of the painted body of a neighbour. The stage solves it once per layout; the plate is born where it stands and neither value is animated.

    - `shiftPixels` &mdash; Sideways offset from the centre of the owner, in reference pixels; positive is right.
    - `widthPixels` &mdash; Width of the canvas in reference pixels, never below `MinimumSelectedWidth`; zero or less keeps the natural width.

`public void SetSelectionHighlight(bool actor, bool target)`

:   Highlights this plate for actor or target selection without changing its authored type scale. The border changes colour and width over the length of a world fade once the plate has a clock, instead of switching.

    - `actor` &mdash; Whether the plate represents the current actor.
    - `target` &mdash; Whether the plate represents a selectable target.

`public void SetSortingOrder(int order)`

:   Puts this plate on a specific order, still above the bodies.

    - `order` &mdash; Canvas sorting order to draw the plate at.

`public void SetTeamTint(Color tint)`

:   Tints the plate for a team. Keeps ally and enemy readable at a glance without requiring per-combatant art.

    - `tint` &mdash; Colour applied to the combatant's name label; the bars keep the colours the skin gave them.

`public void SetWorldTopOverride(Vector3? worldTop)`

:   Pins the plate's top edge to a world-space point. The authored canvas size and typography remain unchanged; only the plate position moves. Pass `null` to restore the normal ground-relative placement.

    - `worldTop` &mdash; World-space position of the plate top edge, or null to cancel the override.

`public void SetWorldTopOverride(Vector3? worldTop, float unitsPerPixel, float widthPixels)`

:   Sets a world-top override while cancelling token scale for authored plate sizing.

    - `worldTop` &mdash; World-space top edge, or null to restore ground placement.
    - `unitsPerPixel` &mdash; World units per authored pixel. Parent scaling is cancelled on both axes.
    - `widthPixels` &mdash; Optional authored width; zero preserves the current width.

`public void StopPulse()`

:   Cancels this plate's neutral pulse and restores its resting scale.

`public Color TextOnCard(Color wanted)`

:   The colour a text of this plate takes on its card: the wanted colour, held to the contrast of text read to play over a mid and over a bright stage.

    - `wanted` &mdash; The colour the text is asked for, such as the text token of the team.
    - **Returns** &mdash; The colour the plate draws the text in.

`public void Tick(float deltaSeconds)`

:   Advances plate animation. Driven by the presenter's visual clock so pause and speed apply, and so tests can step it deterministically.

    - `deltaSeconds` &mdash; Positive presentation-clock duration applied to all bars and the impact pulse.

`public Color ValueFill()`

:   The colour the bar under the readout is drawn at the moment: its fill, or the muted tone of a combatant that is down.

    - **Returns** &mdash; The fill colour the value inside the bar is drawn on.

`public Color ValueOutlineColor()`

:   The colour of the outline around the value of health when it has one: darker than any bar.

    - **Returns** &mdash; The opaque dark colour.

`public static float ValueSizeFor(float captionSize, float screenPixelsPerReferencePixel, float floorFactor = 1f)`

:   Size, in reference pixels, that puts the value of a combatant's health at `MinimumValuePixels` on the screen: the caption size of the skin, or whatever the scale a plate is drawn at needs to reach the floor, whichever is larger.

    - `captionSize` &mdash; Caption size of the skin, in reference pixels.
    - `screenPixelsPerReferencePixel` &mdash; Screen pixels one reference pixel of the plate is drawn at, 1 or less.
    - `floorFactor` &mdash; How many times the 18-pixel floor applies: 1 up to a 1080-pixel screen, in proportion to the height above it.
    - **Returns** &mdash; The font size in reference pixels.

`public Color ValueTrack()`

:   The colour of the empty part of the health bar, as the value inside the bar is also drawn on it.

    - **Returns** &mdash; The opaque track colour, laid over the card it is on.

---

## SkinnedValueBar

```csharp
public sealed class SkinnedValueBar : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Widgets/SkinnedValueBar.cs</small>

A skinned value bar: track, an optional trailing ghost showing the value
just lost, the live fill, and an optional numeric readout.

The bar animates toward its target rather than snapping, which is what
makes a hit legible at a glance. All motion is presentation-only and
derives from the skin, so `Reduce Motion` or a zero
`Motion Scale` makes every change instant without touching this code.

**Properties**

`public float DisplayedFraction`

:   The fraction currently drawn, in [0,1].

`public bool IsAnimating`

:   True while the fill is still moving toward its target.

`public SkinSurfaceGraphic Outline`

:   The dark outline drawn around the bar, or null while it has none.

`public TMP_Text Readout`

:   The numeric readout, or null when the bar was built without one.

`public float TargetFraction`

:   The fraction the bar is animating toward, in [0,1].

**Methods**

`public void Build(CompiledBattleSkin skin, SkinBarTokens barTokens, bool withReadout)`

:   Builds the bar's children. Explicit rather than done in Awake so EditMode tests can construct and drive a bar with no scene.

    - `barTokens` &mdash; Fill, ghost, track, border, glow, and animation tokens for this bar role.
    - `skin` &mdash; Compiled surface, typography, and motion tokens shared by the widget hierarchy.
    - `withReadout` &mdash; Whether to create centered numeric text over the fill.

`public void FinishAnimation()`

:   Completes any fill and ghost transition at once, leaving the bar at its target value.

`public void SetFillAlpha(float alpha)`

:   Fades the fill without changing its colour, which is what lets a critical bar breathe while still reading as its team's colour.

    - `alpha` &mdash; Opacity in zero to one applied to the fill graphic only.

`public void SetFillColor(Color primary)`

:   Replaces the fill colour, keeping shape, glow, and geometry.

    - `primary` &mdash; Replacement primary and secondary fill color.

`public void SetFraction(float fraction)`

:   Animates toward `fraction`. A decrease leaves a ghost at the previous value that catches up shortly after, so the player can see how much was just taken.

    - `fraction` &mdash; Target fill in normalized units; values outside zero to one are clamped.

`public void SetFractionImmediate(float fraction)`

:   Snaps to `fraction` with no animation.

    - `fraction` &mdash; Immediate fill and ghost value, clamped to zero through one.

`public void SetOutline(bool visible, Color color, float width)`

:   Draws, or takes away, a dark outline around the whole bar. A bare bar stands on the stage with nothing behind it, and its own track is only a shade darker than a stone floor, so the bar needs an edge of its own to be read there. The outline is drawn outside the bar's rect, above the fill and under the readout, so the bar keeps the size it was laid out at.

    - `visible` &mdash; Whether the outline is drawn.
    - `color` &mdash; Colour of the outline; it should be darker than any floor.
    - `width` &mdash; Thickness in reference pixels.

`public void SetReadout(string text)`

:   Sets the numeric readout text, if the bar has one.

    - `text` &mdash; Numeric or status text to display; null becomes empty.

`public void SetTrackStrokeColor(Color stroke)`

:   Replaces the track's border colour, keeping every other value. This is the channel a bar uses to say "in danger" without touching its fill, which already means something else: on a team-coloured health bar the fill says whose side you are on, so the warning has to arrive somewhere other than the fill.

    - `stroke` &mdash; Replacement border colour for the bar's track.

`public void SetUnknown()`

:   Shows an empty bar for a value nobody knows yet, such as a combatant whose health has not arrived. The next real fraction is drawn as it is instead of animating up from this placeholder.

`public void Tick(float deltaSeconds)`

:   Advances the bar's animation. Driven by the presenter's visual clock rather than `Update` so pause and speed apply consistently and so tests can step it deterministically.

    - `deltaSeconds` &mdash; Positive presentation-clock duration applied to fill and delayed ghost transitions.

---

## SkinnedWidgetFactory

```csharp
public static class SkinnedWidgetFactory
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Widgets/SkinnedWidgetFactory.cs</small>

Builds the skinned uGUI primitives the HUD is assembled from. Centralising
construction here is what lets the whole interface restyle from a
`CompiledBattleSkin`: no widget hardcodes a colour, a size, or
a font, and nothing depends on a shipped prefab.

**Methods**

`public static HorizontalLayoutGroup AddHorizontalLayout(RectTransform rect, float spacing, RectOffset padding, TextAnchor alignment = TextAnchor.MiddleCenter)`

:   Adds a horizontal layout group with skin-consistent spacing.

    - `alignment` &mdash; Placement of the non-expanding child row within available space.
    - `padding` &mdash; Left, right, top, and bottom content inset assigned to the group.
    - `rect` &mdash; Rect receiving the new HorizontalLayoutGroup component.
    - `spacing` &mdash; Reference-pixel gap between consecutive children.
    - **Returns** &mdash; A non-expanding horizontal layout group using the requested alignment.

`public static ContentSizeFitter AddVerticalFitter(RectTransform rect)`

:   Adds a content-size fitter so a region can size to content. A fitter measures `ILayoutElement` components on its OWN object, so `rect` must already carry the layout group whose content it should follow. On a rect with no layout group the preferred height resolves to zero and the region collapses.

    - `rect` &mdash; Rect already carrying the layout elements whose preferred height should drive it.
    - **Returns** &mdash; A new ContentSizeFitter constrained only to vertical preferred size.

`public static VerticalLayoutGroup AddVerticalLayout(RectTransform rect, float spacing, RectOffset padding)`

:   Adds a vertical layout group with skin-consistent spacing.

    - `padding` &mdash; Left, right, top, and bottom content inset assigned to the group.
    - `rect` &mdash; Rect receiving the new VerticalLayoutGroup component.
    - `spacing` &mdash; Reference-pixel gap between consecutive children.
    - **Returns** &mdash; A width-expanding, content-height vertical group aligned to the upper left.

`public static void ApplyRegion(RectTransform rect, SkinRegionTokens region)`

:   Anchors a rect inside its parent according to a skin region, so a customer can move any HUD block by editing the preset alone.

    - `rect` &mdash; HUD region whose anchors, pivot, position, optional size, and scale are updated.
    - `region` &mdash; Compiled safe-area anchor, inward offset, size, stretch, and visibility-independent scale.

`public static TMP_Text CreateLabel(string name, Transform parent, CompiledBattleSkin skin, int fontSize, Color color, TextAnchor alignment)`

:   Creates a label using the skin's typography.

    - `alignment` &mdash; Horizontal and vertical text placement within the label rect.
    - `color` &mdash; Initial text color.
    - `fontSize` &mdash; Font size in reference pixels.
    - `name` &mdash; Unity hierarchy name assigned to the label GameObject.
    - `parent` &mdash; Transform that receives the new label child.
    - `skin` &mdash; Compiled font, line spacing, and optional outline settings.
    - **Returns** &mdash; A non-raycast, rich-text-disabled uGUI Text configured from the skin.

`public static RectTransform CreateRect(string name, Transform parent)`

:   Creates a child object with a `RectTransform`.

    - `name` &mdash; Unity hierarchy name assigned to the new child GameObject.
    - `parent` &mdash; Transform that owns the new rect while preserving local coordinates.
    - **Returns** &mdash; The RectTransform of a new child GameObject.

`public static SkinSurfaceGraphic CreateSurface(string name, Transform parent, SkinSurfaceTokens tokens)`

:   Creates a transient, non-raycast surface and applies its visual tokens immediately.

    - `name` &mdash; Unity hierarchy name assigned to the surface GameObject.
    - `parent` &mdash; Transform that receives the new non-raycast surface child.
    - `tokens` &mdash; Shape, fill, stroke, glow, and shadow settings applied immediately.
    - **Returns** &mdash; A new drawable surface with RectTransform, CanvasRenderer, and SkinSurfaceGraphic.

`public static void Fill(RectTransform rect, float inset = 0f)`

:   Stretches a rect to fill its parent with an optional uniform inset.

    - `inset` &mdash; Uniform inward offset in reference pixels; zero reaches every parent edge.
    - `rect` &mdash; Child rect whose anchors and offsets are rewritten to stretch.

`public static LayoutElement IgnoreLayout(RectTransform rect)`

:   Excludes `rect` from its parent's layout group, keeping the anchors it was given. Used for panel backgrounds that must stretch across a region whose children are otherwise laid out in a row or column.

    - `rect` &mdash; Background or overlay rect to exempt from its parent's layout calculation.
    - **Returns** &mdash; A new LayoutElement with `ignoreLayout` enabled.

---

## StatusRosterView

```csharp
public sealed class StatusRosterView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/StatusRosterView.cs</small>

The combatant roster: one row per combatant with name, health bar, shield
readout, and status count. Rows are pooled and reused, so a long battle
allocates nothing per update.

It mirrors supplied `UiStatusEntry` values verbatim and reads
no simulation state.

**Properties**

`public int VisibleRowCount`

:   Rows currently visible.

**Fields**

`public const int MaximumRows`

:   Rows drawn before the rest collapse into a count on the last one. The roster docks into a fixed cell of the command deck, and the stage above it is protected, so it has a real ceiling rather than a preference. Past this many combatants the last row reports how many are not shown, which is more honest than a list that quietly runs off the top of its own panel.

**Methods**

`public void Apply(IReadOnlyList<UiStatusEntry> entries, DisplayStringTable labels)`

:   Rebuilds the roster from supplied entries, one row per entry in the order given. Rows are added as the roster grows and hidden, not destroyed, as it shrinks.

    - `entries` &mdash; Rows to draw; null or empty hides every row.
    - `labels` &mdash; Name source; null falls back to `DisplayStringTable.Empty`, which shows raw ids.

`public void Apply(IReadOnlyList<UiStatusEntry> entries, DisplayStringTable labels, StableId allyTeamId)`

:   Rebuilds the roster, colouring each health bar by whether the combatant is on `allyTeamId`.

    - `entries` &mdash; Rows to draw; null or empty hides every row.
    - `labels` &mdash; Name source; null falls back to `DisplayStringTable.Empty`, which shows raw ids.
    - `allyTeamId` &mdash; The team drawn as ours. The default id makes every row read as an opponent, which is the honest answer when no perspective was supplied.

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the panel. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin to draw with; null falls back to the shipped default.

`public void Tick(float deltaSeconds)`

:   Advances row bar animation by a visual delta.

    - `deltaSeconds` &mdash; Non-negative visual-frame duration used to advance every pooled value bar.

---

## TargetPickerView

```csharp
public sealed class TargetPickerView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/TargetPickerView.cs</small>

The target picker: one button per combatant the chosen skill may legally
hit, plus confirm and back.

It is the second half of choosing an action, and it is deliberately built
the same way as the skill tray - pooled buttons, skinned surfaces, plain
C# events - so a project restyles or replaces it exactly as it does the
tray. It decides nothing: the candidate list is handed to it, and pressing
a button raises an event for the interface to act on.

**Properties**

`public int VisibleButtonCount`

:   Candidate buttons currently visible.

**Fields**

`public const int MaximumButtons`

:   Legacy compatibility constant. The picker no longer truncates its candidates; every supplied candidate is placed in the scrolling row.

**Events**

`public event Action Cancelled`

:   Raised when the player backs out to the skill tray.

`public event Action Confirmed`

:   Raised when the player commits the picks made so far.

`public event Action<StableId> TargetChosen`

:   Raised when the player presses one candidate. Never submitted here.

**Methods**

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the picker. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin every widget is drawn from; null falls back to `BattleSkinDefaults.Default`. Only the first call builds the widget tree - a later call stores the skin and returns.

`public void Hide()`

:   Takes the picker down.

`public void SetCandidatesVisible(bool visible)`

:   Shows or hides the candidate buttons while leaving the prompt up. The Direct preset picks on the stage, so the row would be a second way to do the same thing taking up the deck. The prompt still has to be there: it is the part that tells the player where to point.

    - `visible` &mdash; Whether the row of candidate buttons is drawn.

`public void SetPicked(IReadOnlyList<StableId> picked)`

:   Highlights exactly the candidates in `picked`.

    - `picked` &mdash; The ids picked so far; null or empty clears every highlight.

`public void Show(string prompt, IReadOnlyList<StableId> candidates, bool allowsMultiple, DisplayStringTable labels, IReadOnlyList<UiStatusEntry> status)`

:   Offers exactly the candidates it is handed.

    - `prompt` &mdash; The line above the buttons, such as "Fireball: choose 1 enemy". Shown verbatim, so it is the caller's job to localize it.
    - `candidates` &mdash; The combatants that may be picked, in the order to draw them. Null or empty hides the picker, because a picker offering nothing is a dead end the player cannot leave.
    - `allowsMultiple` &mdash; True when the skill takes more than one target, which is what puts the Confirm button on screen. A single-target skill commits on the pick itself and needs no confirmation step.
    - `labels` &mdash; Display names for the candidates; null, or an id the table does not carry, falls back to the raw id text.
    - `status` &mdash; Current health rows used for the readout under each name. Null draws the names alone.

`public bool TryGetCandidate(int index, out StableId combatantId)`

:   Reports which combatant one visible button stands for.

    - `index` &mdash; Zero-based position in the drawn row.
    - `combatantId` &mdash; The candidate at that position, or the default id.
    - **Returns** &mdash; True when a visible button exists at that position.

---

## TargetShape

```csharp
public readonly struct TargetShape
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/DecisionShape.cs</small>

The display-only shape of a skill's target request, taken from the
compiled target contract. It describes what the player may pick; it is
never the engine's exact target resolution.

**Constructors**

`public TargetShape(TargetTeamRelation relation, TargetLifeState lifeState, int minimumTargets, int maximumTargets, int maximumResolvedTargets, bool actorMayAppear, bool automaticSelection)`

:   Creates a shape from an already-resolved target contract. It copies the declared limits as given and validates nothing.

    - `relation` &mdash; Allowed team relation to the actor.
    - `lifeState` &mdash; Allowed living/dead state.
    - `minimumTargets` &mdash; Fewest ids a command must carry.
    - `maximumTargets` &mdash; Most ids a command may carry.
    - `maximumResolvedTargets` &mdash; Most combatants the resolver may finally reach, which can exceed `maximumTargets` when one pick spreads.
    - `actorMayAppear` &mdash; Whether the acting combatant is itself a legal pick.
    - `automaticSelection` &mdash; Whether a command carrying no ids is legal, leaving the pick to the resolver.

`public TargetShape(TargetTeamRelation relation, TargetLifeState lifeState, int minimumTargets, int maximumTargets, int maximumResolvedTargets, bool actorMayAppear, bool automaticSelection, StableId resolverId)`

:   Copies target-count limits and pick policy with the resolver identity used for stage previews. Values are retained without validation; this shape neither resolves targets nor authorizes a command.

    - `relation` &mdash; Allowed team relation to the actor.
    - `lifeState` &mdash; Allowed living/dead state.
    - `minimumTargets` &mdash; Fewest ids a command must carry.
    - `maximumTargets` &mdash; Most ids a command may carry.
    - `maximumResolvedTargets` &mdash; Most combatants the resolver may finally reach.
    - `actorMayAppear` &mdash; Whether the acting combatant is itself a legal pick.
    - `automaticSelection` &mdash; Whether a command carrying no ids is legal.
    - `resolverId` &mdash; The target resolver's implementation id. The interface uses it to pick how the affected set should be DRAWN -- a whole-team scrim reads differently from a row band or a single ring -- and for nothing else.

**Properties**

`public bool ActorMayAppear`

:   Whether the acting combatant is itself a legal pick.

`public bool AutomaticSelection`

:   Whether a command carrying no ids is legal, leaving the pick to the resolver.

`public TargetLifeState LifeState`

:   Which life state a pick must be in. Copied from the compiled contract in the same way as `Relation`, and equally not re-derived here.

`public int MaximumResolvedTargets`

:   Most combatants the resolver may finally reach; can exceed `MaximumTargets` when one pick spreads.

`public int MaximumTargets`

:   Most ids a command may carry.

`public int MinimumTargets`

:   Fewest ids a command must carry.

`public TargetTeamRelation Relation`

:   Which combatants the skill may reach, relative to the acting combatant's team. It is the resolver's declared eligibility copied verbatim, so it is sound for shading legal picks but is not the check the engine performs when the command arrives.

`public StableId ResolverId`

:   Which resolver produced this shape, or the default id when the shape was built without one. Presentation-only: it decides how the affected set is drawn and never what is legal.

---

## TimelineStripView

```csharp
public sealed class TimelineStripView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/TimelineStripView.cs</small>

The turn-order rail: one chip per upcoming actor, left to right, with the
actor about to act raised, accented, and marked NOW.

This is the product's namesake and the one element present in every frame
of every encounter, so it is a full-bleed band rather than a strip in a
corner. A chip is a portrait, a team-coloured rim, a health underline, and
up to three status pips: four answers in one glance, which is what makes
the rail something a player plans against instead of something they
occasionally read.

Chips slide to their new positions rather than cutting. A chip that jumps
reads as a bug in the scheduler; a chip that slides reads as the feature
the scheduler is.

**Properties**

`public bool IsShifting`

:   True while chips are still sliding toward a new order.

`public int VisibleChipCount`

:   Chips currently visible.

**Fields**

`public const float ActingChipSize`

:   Edge of the acting chip in reference pixels.

`public const float ChipGap`

:   Gap between chips in reference pixels.

`public const float ChipSize`

:   Edge of a resting chip in reference pixels.

`public const int ComfortableChips`

:   Chips past which the rail shrinks rather than wrapping.

`public const float CrowdedChipSize`

:   Edge of a chip once the rail is crowded, in reference pixels.

`public const float HeaderGutter`

:   Clearance held on the left of the band for the "TURN ORDER" title, in reference pixels. Named because the header, the chip row and the hairline all have to agree about it, and it used to be written out three times as a literal.

`public const int MaximumChipPips`

:   Status pips drawn on one chip before the rest are dropped.

`public const int MaximumChips`

:   Chips drawn before the strip stops adding more.

`public const float OverflowReachPixels`

:   Room the trailing "+n" counter needs past the last chip, in reference pixels.

`public const float TransportGutter`

:   Clearance held on the right of the band for the transport cluster, in reference pixels.

**Methods**

`public void Apply(IReadOnlyList<StableId> actors, DisplayStringTable labels)`

:   Rebuilds the rail from the supplied actor order, with no side, health, or status information. Kept for hosts that only have an order to give.

    - `actors` &mdash; Decision order as the simulation reported it, soonest first: index 0 is the chip raised and marked NOW. Entries past `MaximumChips` collapse into a trailing counter, and null is treated as an empty order.
    - `labels` &mdash; Display names for the actors. A missing entry falls back to the actor's identifier, and null is treated as an empty table.

`public void Apply(IReadOnlyList<UiTimelineEntry> entries, DisplayStringTable labels, IReadOnlyDictionary<StableId, Sprite> portraits)`

:   Rebuilds the rail from full chip entries.

    - `entries` &mdash; Decision order, soonest first. Entries past `MaximumChips` collapse into a trailing counter rather than wrapping to a second line; null is an empty order.
    - `labels` &mdash; Display names for the actors; a missing entry falls back to the raw identifier.
    - `portraits` &mdash; Art to crop each chip's face from, keyed by combatant. Null, or a combatant with no entry, draws a chip with textual initials instead.

`public void Apply(IReadOnlyList<UiTimelineEntry> entries, DisplayStringTable labels, IReadOnlyDictionary<StableId, Sprite> portraits, IReadOnlyDictionary<StableId, UiPortraitFacing> portraitFacings)`

:   Rebuilds the rail and uses explicit portrait direction metadata when available. Entries without metadata retain the legacy rule: source art is right-facing and enemy chips are mirrored toward the player.

    - `entries` &mdash; Decision order, soonest first.
    - `labels` &mdash; Display names for the actors.
    - `portraits` &mdash; Art to crop for each combatant.
    - `portraitFacings` &mdash; Optional authored and displayed direction per portrait.

`public void Apply(IReadOnlyList<UiTimelineEntry> entries, DisplayStringTable labels, IReadOnlyDictionary<StableId, Sprite> portraits, IReadOnlyDictionary<StableId, UiPortraitFacing> portraitFacings, IReadOnlyDictionary<StableId, UiPortraitCrop> portraitCrops)`

:   Rebuilds the rail with optional per-combatant crop metadata.

    - `entries` &mdash; Decision order, soonest first.
    - `labels` &mdash; Display names for the actors.
    - `portraits` &mdash; Portrait sprites keyed by combatant.
    - `portraitFacings` &mdash; Optional authored and displayed directions.
    - `portraitCrops` &mdash; Optional finite normalized crops; invalid/default values use legacy framing.

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the rail. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin the chips are dressed from; null falls back to the package default.

`public void Tick(float deltaSeconds)`

:   Advances the slide that follows a reorder. Driven by the presenter's visual clock, so pause and speed apply to the rail exactly as they do to the stage, and a reduced-motion skin snaps instead.

    - `deltaSeconds` &mdash; Positive presentation-clock duration. Non-positive values are ignored.

`public bool TryGetPortraitFrameLayout(StableId combatantId, out Vector3 scale, out Vector2 position, out Vector2 size)`

:   Reads the pooled portrait transform for visual diagnostics.

    - `combatantId` &mdash; Visible combatant whose pooled chip is queried.
    - `scale` &mdash; Local portrait scale, including facing mirror.
    - `position` &mdash; Local crop position inside the chip mask.
    - `size` &mdash; Local source image size before masking.
    - **Returns** &mdash; True when the combatant currently has a visible portrait.

`public bool TryGetPortraitFrameScale(StableId combatantId, out Vector3 scale)`

:   Reads the current portrait transform for a visible combatant. This is a presentation observer for editor previews and diagnostics; it does not expose or mutate the chip's private hierarchy.

    - `combatantId` &mdash; Combatant whose visible portrait is queried.
    - `scale` &mdash; Local portrait scale, or zero when no portrait is visible.
    - **Returns** &mdash; True when a visible portrait for the id exists.

---

## TokenPlateDisplay

```csharp
public enum TokenPlateDisplay
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Widgets/SkinnedTokenPlate.cs</small>

How much of a combatant's plate is drawn.

| Value | Meaning |
| --- | --- |
| `Full` | The whole plate: backing card, name, health readout, bars and status pips. |
| `BarOnly` | Only the health bar, bare, directly under the combatant's feet. |
| `Hidden` | Nothing is drawn; the combatant's health is shown somewhere else. |

---

## TooltipData

```csharp
public readonly struct TooltipData
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/TooltipData.cs</small>

A passive tooltip value computed by the DRIVER through the public preview
surface (`BattleFormulaService.Preview` /
`PreviewStatusApplication`, `FormulaPreview`, and
`IEffectResolver.Plan`) and handed to the UI verbatim. The UI stores
and displays it; it never invokes a simulation or preview API itself.

**Constructors**

`public TooltipData(StableId skillId, string costText, string timingText, string targetShapeText, bool hasPreview, Fixed64 previewMinimum, Fixed64 previewMaximum, Chance64 hitChance, Chance64 criticalChance, Chance64 statusChance)`

:   Captures one already-computed tooltip. Null text arguments are stored as empty strings, so a consumer never needs a null check.

    - `hasPreview` &mdash; True when the driver ran a numeric preview. While it is false the shipped tooltip panel hides the amount range and the hit and critical figures, and shows only the status chance.
    - `costText` &mdash; Driver-authored localized cost line; null hides the row.
    - `criticalChance` &mdash; Conditional critical probability for a landed use.
    - `hitChance` &mdash; Probability that the previewed use lands.
    - `previewMaximum` &mdash; Highest amount a landed use can produce.
    - `previewMinimum` &mdash; Lowest amount a landed use can produce.
    - `skillId` &mdash; Skill identity this tooltip must remain associated with.
    - `statusChance` &mdash; Probability that the accompanying status application succeeds.
    - `targetShapeText` &mdash; Driver-authored localized target-rule line; null hides the row.
    - `timingText` &mdash; Driver-authored localized timing line; null hides the row.

**Properties**

`public string CostText`

:   The cost line, worded and localised entirely by the driver. Nothing in the package parses it back, and an empty string hides the row rather than drawing a blank one.

`public Chance64 CriticalChance`

:   Odds of a critical on a use that lands. The shipped panel leaves the figure out altogether when it is impossible instead of printing zero, so a skill that cannot crit costs no tooltip space.

`public bool HasPreview`

:   True when the amount range and hit and critical figures are worth drawing.

`public Chance64 HitChance`

:   Odds that the use lands at all, meaningful only while `HasPreview` is true.

`public Fixed64 PreviewMaximum`

:   Highest amount a use that lands can produce. It equals `PreviewMinimum` when the formula has no spread, which is how a caller can decide to print one figure instead of a range.

`public Fixed64 PreviewMinimum`

:   Lowest amount a use that lands can produce. A miss is reported by `HitChance` rather than by this bound, and the value stands for nothing while `HasPreview` is false.

`public StableId SkillId`

:   The skill this value was computed for, so a tray entry can tell whether the tooltip it holds still belongs to the skill it draws.

`public Chance64 StatusChance`

:   Odds that the accompanying status applies. It comes from a separate preview call from the amount figures, so it can be worth drawing even while `HasPreview` is false - a pure status skill has odds but no amount range.

`public string TargetShapeText`

:   The line describing who the skill may be aimed at, worded by the driver. An empty string hides the row.

`public string TimingText`

:   The timing line, worded by the driver. An empty string hides the row.

**Methods**

`public static TooltipData TextOnly(StableId skillId, string costText, string timingText, string targetShapeText)`

:   A skill with no numeric preview still carries its cost, timing, and targeting copy.

    - `costText` &mdash; Driver-authored localized cost line.
    - `skillId` &mdash; Skill identity associated with the text-only tooltip.
    - `targetShapeText` &mdash; Driver-authored localized target-rule line.
    - `timingText` &mdash; Driver-authored localized timing line.
    - **Returns** &mdash; Tooltip data with numeric preview disabled and all amounts and chances set to zero.

---

## TooltipPanelView

```csharp
public sealed class TooltipPanelView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/TooltipPanelView.cs</small>

The skill tooltip: cost, timing, target shape, and the driver-computed
preview figures.

It renders a `TooltipData` value verbatim and calls no preview
or simulation API itself, which is what keeps the UI on the passive side
of the presenter contract.

**Properties**

`public bool IsShown`

:   True while a tooltip is displayed.

**Methods**

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the panel. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin the panel is dressed from; null falls back to the package default. The panel is left hidden.

`public void Hide()`

:   Hides the tooltip.

`public void Show(string title, TooltipData tooltip)`

:   Shows `tooltip` under `title`. Does nothing until `Build` has run.

    - `title` &mdash; Heading text, normally the skill's display name; null shows an empty heading.
    - `tooltip` &mdash; Values the driver already computed. Rows whose text is empty are hidden, the amount range and hit chance appear only when the value carries a preview, and the critical and status chances are each left out while impossible.

---

## TransportBarView

```csharp
public sealed class TransportBarView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/Regions/TransportBarView.cs</small>

Scenario picker, seed field, and playback controls, drawn with the skin.

This replaces an `OnGUI`/`GUI.skin.box` overlay. Immediate-mode
chrome is fine for an internal harness but it is the first thing a buyer
sees, it cannot be skinned, it ignores the canvas scaler, and it does not
exist on a touch device. Everything here is real uGUI and therefore
scales, skins, and works on mobile.

Pause, speed, and skip are presentation-only. They scale or halt the
visual clock and never a simulation value, so the same
(scenario, scheduler, formation, seed) tuple still reproduces identical
hashes.

**Events**

`public event Action NextRequested`

:   Raised when the player selects the next scenario.

`public event Action PauseToggled`

:   Raised when the player toggles pause.

`public event Action PreviousRequested`

:   Raised when the player selects the previous scenario.

`public event Action SkipRequested`

:   Raised when the player skips queued visuals.

`public event Action SpeedCycled`

:   Raised when the player cycles playback speed.

`public event Action<string> StartRequested`

:   Raised with the seed text when the player starts a battle.

**Methods**

`public void Build(CompiledBattleSkin battleSkin)`

:   Builds the bar. Explicit so EditMode tests can drive it.

    - `battleSkin` &mdash; Skin the bar is dressed from; null falls back to the package default.

`public void SetPaused(bool paused)`

:   Reflects the current pause state on the toggle.

    - `paused` &mdash; The state the host is now in, not the action to offer: true captions the button Resume.

`public void SetScenario(string text)`

:   Updates set scenario on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `text` &mdash; Name to show; null or empty shows a dash rather than a blank gap.

`public void SetSeedText(string text)`

:   Updates set seed text on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `text` &mdash; Seed characters written into the transport's editable field without submitting them.

`public void SetSpeed(float multiplier)`

:   Reflects the current playback speed.

    - `multiplier` &mdash; Visual speed multiplier, captioned as-is with an x suffix. Displaying it is all this does; the host owns the cycle order.

`public void SetStatus(string text)`

:   Updates set status on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `text` &mdash; Runtime lifecycle message shown beside the transport controls; null becomes empty.

---

## UiPortraitFacing

```csharp
public readonly struct UiPortraitFacing
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleUiRoot.cs</small>

Describes the direction painted into a portrait and the direction the
presentation wants that portrait to face. Keeping these values with the
portrait, rather than deriving a flip from team membership, lets an ally
illustration authored facing left remain left-facing on a left-facing
formation slot.

**Constructors**

`public UiPortraitFacing(FormationFacing source, FormationFacing desired)`

:   Records the source and displayed directions of one portrait.

    - `source` &mdash; Direction in which the source artwork is painted.
    - `desired` &mdash; Direction the portrait should face in this UI.

**Properties**

`public FormationFacing Desired`

:   Direction the portrait is presented toward.

`public bool IsMirrored`

:   Whether the source must be mirrored to reach the desired direction.

`public FormationFacing Source`

:   Direction encoded by the source portrait.

---

## UiStatusEntry

```csharp
public readonly struct UiStatusEntry
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleUiRoot.cs</small>

One combatant's surfaced status-panel row.

**Constructors**

`public UiStatusEntry(StableId combatantId, int health, int maximumHealth, int shield, int statusCount, bool isDead)`

:   Records one row exactly as the snapshot reported it.

    - `combatantId` &mdash; Compiled combatant identity used for label and token lookup.
    - `health` &mdash; Current authoritative health reported by the snapshot.
    - `isDead` &mdash; Whether the snapshot marks the combatant as dead.
    - `maximumHealth` &mdash; Positive health capacity used to calculate the roster-bar fraction.
    - `shield` &mdash; Current shield amount displayed alongside health.
    - `statusCount` &mdash; Number of active statuses represented by roster pips.

`public UiStatusEntry(StableId combatantId, int health, int maximumHealth, int shield, int statusCount, bool isDead, StableId teamId)`

:   Records one row, including the team that decides its colour.

    - `combatantId` &mdash; Compiled combatant identity used for label and token lookup.
    - `health` &mdash; Current authoritative health reported by the snapshot.
    - `isDead` &mdash; Whether the snapshot marks the combatant as dead.
    - `maximumHealth` &mdash; Positive health capacity used to calculate the roster-bar fraction.
    - `shield` &mdash; Current shield amount displayed alongside health.
    - `statusCount` &mdash; Number of active statuses represented by roster pips.
    - `teamId` &mdash; Team the combatant belongs to, compared against the interface's player team to pick a bar colour.

**Properties**

`public StableId CombatantId`

:   Which combatant the row was built from. Look the display name up from this id; the row itself carries no text.

`public int Health`

:   Health exactly as the snapshot reported it; the row itself never interpolates. The roster's health bar eases toward the fraction this implies, and snaps only when the skin scales bar motion to zero, so the drawn bar can trail this value until `BattleUiRoot.Tick` advances it.

`public bool IsDead`

:   True when the snapshot no longer counts the combatant as living. Dead combatants keep their row, so the panel does not reshuffle as a battle thins out.

`public int MaximumHealth`

:   The health ceiling from the same snapshot, for drawing `Health` as a fraction.

`public int Shield`

:   Remaining shield summed over every shield the combatant owns.

`public int StatusCount`

:   How many status entries the snapshot lists for this combatant.

`public StableId TeamId`

:   The team this combatant fights for, or the default id when the row was built without one. It carries no simulation meaning here: it exists so the health bar can read as ours or theirs before any text is parsed.

---

## UiTimelineEntry

```csharp
public readonly struct UiTimelineEntry
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UI/BattleUiRoot.cs</small>

One chip on the turn-order rail: who acts, whose side they are on, how much
of them is left, and whether they are still standing.

The rail is the element the product is named after, and a chip carrying only
a name answers one question out of four. This carries the other three, so a
single glance at the rail tells a player what is coming and whether it
matters.

**Constructors**

`public UiTimelineEntry(StableId combatantId, bool isAlly, float healthFraction, int statusCount, bool isDead)`

:   Records one chip from values the interface was already given.

    - `combatantId` &mdash; Combatant the chip stands for; also the portrait lookup key.
    - `healthFraction` &mdash; Remaining health in zero to one, drawn as the chip's underline.
    - `isAlly` &mdash; Whether the chip takes the ally rim or the enemy rim.
    - `isDead` &mdash; Whether the chip is greyed and struck through rather than removed.
    - `statusCount` &mdash; How many statuses ride the chip, capped when drawn.

**Properties**

`public StableId CombatantId`

:   The combatant this chip stands for.

`public float HealthFraction`

:   Remaining health in zero to one, already clamped.

`public bool IsAlly`

:   True when the chip belongs to the player's team.

`public bool IsDead`

:   True when the combatant is down. The chip stays in place regardless.

`public int StatusCount`

:   Active status count, already floored at zero.

---
