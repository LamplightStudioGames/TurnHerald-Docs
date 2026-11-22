# Other

90 types in this area.

!!! abstract "On this page"
    [AudioArtBinding](#audioartbinding) &middot; [AudioBinding](#audiobinding) &middot; [BattleBarMotion](#battlebarmotion) &middot; [BattleCancelRelay](#battlecancelrelay) &middot; [BattleDockCardReading](#battledockcardreading) &middot; [BattleDockInsets](#battledockinsets) &middot; [BattleDockListsReading](#battledocklistsreading) &middot; [BattleDockMarked](#battledockmarked) &middot; [BattleDockMarkedReading](#battledockmarkedreading) &middot; [BattleDockMemberReading](#battledockmemberreading) &middot; [BattleDockRibbonMotion](#battledockribbonmotion) &middot; [BattleDockRibbonReading](#battledockribbonreading) &middot; [BattleDockRibbonVisual](#battledockribbonvisual) &middot; [BattleDockStripMotion](#battledockstripmotion) &middot; [BattleDockStripReading](#battledockstripreading) &middot; [BattleDockTargetRowReading](#battledocktargetrowreading) &middot; [BattleFeedbackLayout](#battlefeedbacklayout) &middot; [BattleHudDesign](#battlehuddesign) &middot; [BattleLayoutIdentity](#battlelayoutidentity) &middot; [BattlePresentationLabel](#battlepresentationlabel) &middot; [BattlePresentationProfile](#battlepresentationprofile) &middot; [BattleProfileCatalog](#battleprofilecatalog) &middot; [BattleRulesPreset](#battlerulespreset) &middot; [BattleRuntimeCheckpoint](#battleruntimecheckpoint) &middot; [BattleRuntimeController](#battleruntimecontroller) &middot; [BattleRuntimeEndReason](#battleruntimeendreason) &middot; [BattleRuntimeEndedEvent](#battleruntimeendedevent) &middot; [BattleRuntimeEventsEvent](#battleruntimeeventsevent) &middot; [BattleRuntimeFailedEvent](#battleruntimefailedevent) &middot; [BattleRuntimeFailure](#battleruntimefailure) &middot; [BattleRuntimeHumanControlRequirement](#battleruntimehumancontrolrequirement) &middot; [BattleRuntimeOperationResult](#battleruntimeoperationresult) &middot; [BattleRuntimePacing](#battleruntimepacing) &middot; [BattleRuntimeSeedPolicy](#battleruntimeseedpolicy) &middot; [BattleRuntimeSnapshotCause](#battleruntimesnapshotcause) &middot; [BattleRuntimeSnapshotEvent](#battleruntimesnapshotevent) &middot; [BattleRuntimeStartedEvent](#battleruntimestartedevent) &middot; [BattleRuntimeState](#battleruntimestate) &middot; [BattleRuntimeUnityEvent](#battleruntimeunityevent) &middot; [BattleRuntimeValueResult](#battleruntimevalueresult) &middot; [BattleStageBounds](#battlestagebounds) &middot; [BattleTheme](#battletheme) &middot; [BattleThemeContrast](#battlethemecontrast) &middot; [BattleUiCommandTranslationResult](#battleuicommandtranslationresult) &middot; [BattleUiCommandTranslator](#battleuicommandtranslator) &middot; [BattleUiTechnology](#battleuitechnology) &middot; [BattleViewAction](#battleviewaction) &middot; [BattleViewBehaviour](#battleviewbehaviour) &middot; [BattleViewCombatant](#battleviewcombatant) &middot; [BattleViewCommand](#battleviewcommand) &middot; [BattleViewIntent](#battleviewintent) &middot; [BattleViewIntentKind](#battleviewintentkind) &middot; [BattleViewProjection](#battleviewprojection) &middot; [BattleViewRoster](#battleviewroster) &middot; [BattleViewSession](#battleviewsession) &middot; [BattleViewState](#battleviewstate) &middot; [BattleWarmUp](#battlewarmup) &middot; [BattleWarmUpCurtain](#battlewarmupcurtain) &middot; [BattleWarmUpPlan](#battlewarmupplan) &middot; [BattleWarmUpReport](#battlewarmupreport) &middot; [BattleWarmUpStep](#battlewarmupstep) &middot; [CustomMechanicsRegistryProvider](#custommechanicsregistryprovider) &middot; [CustomShieldEffectResolver](#customshieldeffectresolver) &middot; [DemoIdleSheet](#demoidlesheet) &middot; [DisplayStringTableAsset](#displaystringtableasset) &middot; [Entry](#entry) &middot; [ForecastRequest](#forecastrequest) &middot; [ForecastResult](#forecastresult) &middot; [ForecastStopReason](#forecaststopreason) &middot; [GeneratedUiText](#generateduitext) &middot; [IBattleFeedbackLayout](#ibattlefeedbacklayout) &middot; [IBattlePointerBlocker](#ibattlepointerblocker) &middot; [IBattleStageInformationLayout](#ibattlestageinformationlayout) &middot; [IBattleStageLayout](#ibattlestagelayout) &middot; [IBattleView](#ibattleview) &middot; [IInteractiveBattleView](#iinteractivebattleview) &middot; [LowestHealthAllyTargetResolver](#lowesthealthallytargetresolver) &middot; [Pair](#pair) &middot; [ParticleArtBinding](#particleartbinding) &middot; [SessionEndState](#sessionendstate) &middot; [TargetCandidateQuery](#targetcandidatequery) &middot; [TargetPreview](#targetpreview) &middot; [TargetTreatment](#targettreatment) &middot; [TargetingPreset](#targetingpreset) &middot; [TokenArtBinding](#tokenartbinding) &middot; [ToolkitBattleView](#toolkitbattleview) &middot; [TurnHeraldDemoBootstrap](#turnheralddemobootstrap) &middot; [UguiBattleView](#uguibattleview) &middot; [UiPortraitCrop](#uiportraitcrop) &middot; [VfxBinding](#vfxbinding)

## AudioArtBinding

```csharp
public sealed class AudioArtBinding
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/TurnHeraldDemoBootstrap.cs</small>

Nested in `TurnHerald.Presentation.Demo.TurnHeraldDemoBootstrap`.

Binds a recipe audio key (an sfx-* clip name) to art.

**Fields**

`public string AudioKey`

:   Recipe audio key whose clip is being bound.

`public AudioClip Clip`

:   Audio clip played for the bound recipe key.

---

## AudioBinding

```csharp
public sealed class AudioBinding
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeController.cs</small>

Nested in `TurnHerald.Runtime.BattleRuntimeController`.

Maps one presentation audio key to a Unity audio clip.

**Fields**

`public AudioClip Clip`

:   The clip played for the key, or null for an intentional no-op.

`public string Key`

:   The presentation recipe's audio key.

---

## BattleBarMotion

```csharp
public sealed class BattleBarMotion
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleBarMotion.cs</small>

The motion of the bars of a battle view: a bar slides from the value it shows to the value it is given instead of jumping, over
`BattleDockMetrics.MotionSeconds` with the ease-out of the rest of the dock. Both native adapters use this one object,
so a health bar moves the same way in uGUI and in UI Toolkit.

A view that redraws its bars from scratch asks `Track` what fraction to draw now, hands the element it drew to
`Bind`, and applies `HandleAt` and `ValueAt` after each `Advance`. A bar the view
has never drawn appears at its value, with no slide; a bar given a new value while it is sliding continues from where it is.
Nothing is allocated while no bar moves.

**Properties**

`public int Count`

:   How many bars are known to this object.

`public int MovingCount`

:   How many bars are sliding right now.

`public float Seconds`

:   How long a bar takes to reach a new value, in seconds. It starts as `BattleDockMetrics.MotionSeconds`.

**Methods**

`public int Advance(float seconds)`

:   Moves every sliding bar forward. Call it with the view's own clock. The bars it moved are then read with `HandleAt` and `ValueAt` until the next call.

    - `seconds` &mdash; Elapsed seconds; zero or less moves nothing.
    - **Returns** &mdash; How many bars changed their fraction, the ones that arrived included.

`public void BeginPass()`

:   Starts a drawing pass: every bar is marked as not drawn yet. Bars still unmarked at `EndPass` are forgotten, so a bar that left the screen does not keep a handle to an element that is gone.

`public void Bind(string key, object handle)`

:   Hands over the element the view drew for a bar, which `HandleAt` returns after the bar moves.

    - `key` &mdash; Identity the bar was tracked with.
    - `handle` &mdash; The element drawn: a rectangle, a visual element, whatever the adapter resizes.

`public void Clear()`

:   Forgets every bar.

`public float DisplayedOf(string key)`

:   The fraction a bar shows now.

    - `key` &mdash; Identity the view gave the bar.
    - **Returns** &mdash; The displayed fraction, or -1 when the bar is not known.

`public void EndPass()`

:   Ends a drawing pass and forgets the bars it did not draw.

`public int FinishAll()`

:   Takes every sliding bar to its value, as a skip does. The bars it moved are read as after `Advance`.

    - **Returns** &mdash; How many bars changed their fraction.

`public object HandleAt(int index)`

:   The element of a bar that changed in the last `Advance`.

    - `index` &mdash; Zero through the count that call returned, less one.
    - **Returns** &mdash; The handle given to `Bind`, or null.

`public bool IsMoving(string key)`

:   Whether the bar with this key is sliding.

    - `key` &mdash; Identity the view gave the bar.
    - **Returns** &mdash; True while it has not reached its value.

`public float TargetOf(string key)`

:   The fraction a bar is sliding toward.

    - `key` &mdash; Identity the view gave the bar.
    - **Returns** &mdash; The value the bar will show once it arrives, or -1 when the bar is not known.

`public float Track(string key, float target, bool snap)`

:   Says what fraction a bar has to reach and returns what to draw now. A bar not seen before is drawn at its value; a bar whose value changed starts from the fraction it shows, whatever that is, and slides to the new one; a bar whose value did not change is drawn where it is, which is the value itself or a point of the slide it is in.

    - `key` &mdash; Identity of the bar, stable across redraws, such as `hp:` followed by a combatant.
    - `target` &mdash; The fraction the bar has to reach, clamped to zero through one.
    - `snap` &mdash; True to show the value at once, as reduced motion does: the bar stops sliding and takes the value.
    - **Returns** &mdash; The fraction to draw now.

`public float ValueAt(int index)`

:   The fraction of a bar that changed in the last `Advance`.

    - `index` &mdash; Zero through the count that call returned, less one.
    - **Returns** &mdash; The fraction to apply to the element.

---

## BattleCancelRelay

```csharp
public sealed class BattleCancelRelay : MonoBehaviour, ICancelHandler
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUGUI/BattleCancelRelay.cs</small>

Routes the active input module's cancel event without depending on a particular input package.

**Fields**

`public BattleViewBehaviour Owner`

:   View that receives the cancel intent, or null when the relay is inactive.

**Methods**

`public void OnCancel(BaseEventData eventData)`

:   Routes a cancel navigation event to the owning battle view when gamepad input is enabled.

    - `eventData` &mdash; Event data consumed when the owner handles the cancel intent.

---

## BattleDockCardReading

```csharp
public readonly struct BattleDockCardReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

What the action card draws at this instant; the marked targets it lists are read with it, as `BattleDockMarkedReading`.

**Constructors**

`public BattleDockCardReading(BattleDockCardMode mode, string title, string actionLine, string targetLine, float opacity)`

:   Creates a reading.

    - `mode` &mdash; What the card was drawn as.
    - `title` &mdash; The heading text: the action in `BattleDockCardMode.Action`, the actor in the other modes.
    - `actionLine` &mdash; The first line under the heading: the description or instruction of the action, the summary of the card in the other modes.
    - `targetLine` &mdash; The line that names who the action reaches; empty when the card draws none.
    - `opacity` &mdash; The opacity of the card on the screen.

**Properties**

`public string ActionLine`

:   The first line under the heading: the description or instruction of the action in `BattleDockCardMode.Action`, the summary line of the card in the other modes; empty when none is drawn.

`public BattleDockCardMode Mode`

:   What the card was drawn as: hidden, a prompt, an action, an execution or a wait.

`public float Opacity`

:   The opacity of the card on the screen, from zero through one, with the fade of its content and the visibility of its panel: zero for a card that is hidden.

`public string TargetLine`

:   The line that names the targets chosen; empty when the card draws none.

`public string Title`

:   The heading text: the label of the action in `BattleDockCardMode.Action`, the actor in the other modes; empty when none is drawn.

---

## BattleDockInsets

```csharp
public struct BattleDockInsets
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockMetrics.cs</small>

How far the ornament of a frame reaches into the card it frames, from each of the four edges, in reference pixels: the area of the
art that the content of the card has to stay out of. The frame art is the theme's, and what it puts inside the card differs from
one theme to the next (a double line, corner diamonds, crescents along the ends), so a theme declares it and the layout keeps
`BattleDockMemberLayout.OrnamentClearance` beyond it. Nothing declared, which is `None` and the default,
leaves the arrangement of the card exactly as it was before the theme could say anything.

**Constructors**

`public BattleDockInsets(float left, float right, float top, float bottom)`

:   Creates the declaration of an ornament.

    - `left` &mdash; Depth from the left edge.
    - `right` &mdash; Depth from the right edge.
    - `top` &mdash; Depth from the top edge.
    - `bottom` &mdash; Depth from the bottom edge.

**Properties**

`public bool IsEmpty`

:   True when nothing is declared: every depth is zero or less.

`public static BattleDockInsets None`

:   The declaration of a frame with no ornament to keep out of.

**Fields**

`public float Bottom`

:   Depth of the ornament from the bottom edge of the card, in reference pixels.

`public float Left`

:   Depth of the ornament from the left edge of the card, in reference pixels.

`public float Right`

:   Depth of the ornament from the right edge of the card, in reference pixels.

`public float Top`

:   Depth of the ornament from the top edge of the card, in reference pixels.

---

## BattleDockListsReading

```csharp
public readonly struct BattleDockListsReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

How opaque the two lists of the left panel are on the screen; the one that is not showing is zero.

**Constructors**

`public BattleDockListsReading(float actionOpacity, float targetOpacity)`

:   Creates a reading.

    - `actionOpacity` &mdash; Opacity of the list of commands (or of the actors that follow).
    - `targetOpacity` &mdash; Opacity of the list of targets.

**Properties**

`public float ActionOpacity`

:   The opacity of the list of commands, or of the actors that follow while no decision is pending, on the screen; zero while the target list takes its place.

`public float TargetOpacity`

:   The opacity of the list of targets on the screen; zero while it is not showing.

---

## BattleDockMarked

```csharp
public sealed class BattleDockMarked
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockModel.cs</small>

One combatant the chosen action marks on the stage, listed on the card with its health.

**Properties**

`public BattleViewCombatant Combatant`

:   The projection of the combatant when the state carries it; otherwise null.

`public float HealthFraction`

:   Health as a fraction of the maximum, from zero to one.

`public string HealthText`

:   Health text such as "90 / 90"; empty when the state does not carry the combatant.

`public StableId Id`

:   Combatant identity.

`public string Name`

:   Display name.

`public BattleDockSide Side`

:   Side relative to the viewing team: the color of the name and of the health bar.

---

## BattleDockMarkedReading

```csharp
public readonly struct BattleDockMarkedReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

One cell of the combatants an action marks, as the action card draws it.

**Constructors**

`public BattleDockMarkedReading(StableId id, string name, string valueText, float barFraction, bool isOverflow)`

:   Creates a reading.

    - `id` &mdash; The combatant the cell stands for; invalid for the overflow cell.
    - `name` &mdash; The name drawn in the cell, or the text of the overflow cell.
    - `valueText` &mdash; The health text drawn in the cell, such as `90 / 90`; empty for the overflow cell.
    - `barFraction` &mdash; How much of the health bar is drawn, from zero through one.
    - `isOverflow` &mdash; True for the cell that counts the combatants that did not fit.

**Properties**

`public float BarFraction`

:   How much of the health bar of the cell is drawn now, from zero through one; zero for the overflow cell.

`public StableId Id`

:   The combatant of the cell; invalid for the overflow cell.

`public bool IsOverflow`

:   True for the cell that counts the combatants that did not fit.

`public string Name`

:   The name drawn in the cell; for the overflow cell its text, such as `+2 more`.

`public string ValueText`

:   The health text drawn in the cell; empty for the overflow cell and for a combatant the state does not carry.

---

## BattleDockMemberReading

```csharp
public readonly struct BattleDockMemberReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

One member of the party panel as it is drawn now, with the health bar at the fraction that is on the screen this frame.

**Constructors**

`public BattleDockMemberReading(StableId id, float healthFraction, string valueText)`

:   Creates a reading.

    - `id` &mdash; The combatant of the row.
    - `healthFraction` &mdash; How much of the health bar is drawn now, from zero through one.
    - `valueText` &mdash; The text of the health column, such as `120 / 120` or `90 / 120 +20`.

**Properties**

`public float HealthFraction`

:   How much of the health bar is drawn now, from zero through one: the point a slide to a new value has reached on this frame, not the value it is going to.

`public StableId Id`

:   The combatant of the row.

`public string ValueText`

:   The text of the health column as drawn: it takes the new value at once while the bar slides.

---

## BattleDockRibbonMotion

```csharp
public sealed class BattleDockRibbonMotion
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockRibbonMotion.cs</small>

The choreography of the turn ribbon, shared by the uGUI and UI Toolkit adapters so the ribbon moves the same way in both: a view
hands it the new ribbon, steps it on its own clock and applies what it reads, a visual at a time, and does nothing else.

A change of the ribbon plays in three steps, never one over another. First what leaves fades where it stands (and shrinks a
little): a medallion that is no longer on the ribbon, and one that stepped back in the queue, which is the combatant that has
just acted going to the end. Then what stays slides to its new place and takes its new size with one ease-out, which is where the
featured medallion grows. Last, what enters fades in at its place, and only once nothing that stays is still on the way
through it: the instant is worked out from the slides, so no two medallions stand over each other in any frame, whatever the
ribbon is. The tab hangs from its medallion and goes where it goes; a tab text is replaced by a fade out and then a fade in.

The choreography starts from what is drawn now, never from where the last change was going, so a change that arrives in the
middle of another one takes nothing by a jump. Under reduced motion nothing slides or changes size, and the row keeps its left
end where it was instead of being centered again, so its places do not move when it gets shorter or longer: every place is
replaced where it stands, over one reduced fade (`BattleDockMetrics.FadeSeconds`), and only the far end of the row
gains or loses a medallion, by a fade. At a place, the medallion that was there stays as it is under the one that comes in
and is taken away when it is covered, so the ground never shows through the two and the ribbon is never empty or faint in
between. A tab text that the place goes on showing (the NOW of a turn that passes, the NEXT beside it) is handed over as it
is and does not blink; a text that changes goes out in the first half of the fade and the new one comes in in the other half.
A change that arrives while another is playing is taken at once, like any other: what was coming in is kept under what
comes in now, so two changes a frame apart read as one. A row that no longer fits from where it begins is moved back just
enough, and a row taken at once is centered again.
A ribbon that has no visual to come from (the first one, or one after an empty one that has faded out) is drawn at once, and so
is every change when the view is not played.

Nothing is allocated while the ribbon is still or while it moves; a change allocates only the visuals it creates.

**Constructors**

`public BattleDockRibbonMotion()`

:   Creates the choreography of the dock's turn ribbon.

**Properties**

`public int Count`

:   How many visuals are to be drawn now, the ones fading out included.

`public float Duration`

:   Seconds the change in course takes in all; at most `BattleDockMetrics.RibbonAdvanceSeconds`.

`public float Elapsed`

:   Seconds the change in course has been playing.

`public bool IsMoving`

:   True while a change is still playing: something is moving, fading or about to.

`public float LineLeft`

:   Left end of the line behind the medallions, in reference pixels from the left edge of `BattleDockMetrics.Ribbon`.

`public float LineOpacity`

:   Opacity of the line behind the medallions, from zero through one: zero while the ribbon is empty.

`public float LineRight`

:   Right end of the line behind the medallions, in the same measure as `LineLeft`.

`public int Version`

:   Changes whenever a visual is born, retired or put in another order, which is when a view looks again at which nodes it has.

**Methods**

`public bool Advance(float seconds)`

:   Moves the change in course forward by a step of the view's clock.

    - `seconds` &mdash; Elapsed seconds; zero or less, or not a number, moves nothing. A step longer than what is left ends the change.
    - **Returns** &mdash; True while there is still movement.

`public void Clear()`

:   Forgets every visual, as a view does that lets go of its tree; they are all retired.

`public void Finish()`

:   Ends the change in course in this very call: every visual stands where the layout puts it, and what was leaving is retired.

`public bool Retarget(IReadOnlyList<BattleDockMedallion> items, bool animate, bool reduceMotion)`

:   Hands the choreography the ribbon that is to be drawn. A ribbon equal to the one it already has (the same medallions in the same places, sizes and tabs) changes nothing and does not restart a change in course, so a view can ask on every redraw.

    - `items` &mdash; The entries of the ribbon in order, as `BattleDockModel.Ribbon` gives them; null is an empty ribbon.
    - `animate` &mdash; False to take the new ribbon at once, as a view does that is not played, is being drawn for the first time or is changing its theme; any change in course is finished too.
    - `reduceMotion` &mdash; True when the theme asks for reduced motion: what changed fades out and in instead of sliding or growing.
    - **Returns** &mdash; True when the ribbon is not the one the choreography had.

---

## BattleDockRibbonReading

```csharp
public readonly struct BattleDockRibbonReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockRibbonMotion.cs</small>

What a view draws of one visual at one instant, in screen pixels, read back from the nodes the view drew rather than from the
choreography: a test or a recording reads it to see what the player saw. Horizontal measures run from the horizontal center of
the ribbon region, to the right; vertical ones run down from its top edge. Add the screen position of the region to get a
position on the screen. `ScreenScale` is how many screen pixels one reference pixel of
`BattleDockMetrics` is on that screen, so a measure divided by it is the number the choreography works in: the step
of the ribbon is `BattleDockMetrics.RibbonStep` of them in both adapters at every resolution.

**Constructors**

`public BattleDockRibbonReading(int serial, string key, StableId id, bool isOverflow, bool isLeaving, float centerX, float centerY, float diameter, float opacity, string tabText, float tabOpacity, string previousTabText, float previousTabOpacity, float tabPlateOpacity, float tabOffsetX, float tabOffsetY, float feature, float screenScale)`

:   Creates a reading.

    - `serial` &mdash; Number of the visual, which tells it from another of the same key.
    - `key` &mdash; Key of the visual.
    - `id` &mdash; Combatant behind it.
    - `isOverflow` &mdash; True for the +N medallion.
    - `isLeaving` &mdash; True while it fades out.
    - `centerX` &mdash; Center, to the right of the center of the region, in pixels.
    - `centerY` &mdash; Center, below the top of the region, in pixels.
    - `diameter` &mdash; Diameter in pixels.
    - `opacity` &mdash; Opacity as drawn, with every group above the node counted.
    - `tabText` &mdash; Text of the tab.
    - `tabOpacity` &mdash; Opacity of that text as drawn.
    - `previousTabText` &mdash; Text on its way out.
    - `previousTabOpacity` &mdash; Opacity of that text as drawn.
    - `tabPlateOpacity` &mdash; Opacity of the plate behind the tab as drawn.
    - `tabOffsetX` &mdash; Horizontal distance from the center of the medallion to the center of its tab.
    - `tabOffsetY` &mdash; Vertical distance from the center of the medallion to the center of its tab.
    - `feature` &mdash; How much of the featured look (thick ring and glow) is drawn, from zero through one.
    - `screenScale` &mdash; Screen pixels in one reference pixel; one when the view does not know its size on the screen.

**Properties**

`public float CenterX`

:   Center, in pixels to the right of the horizontal center of the ribbon region.

`public float CenterY`

:   Center, in pixels below the top edge of the ribbon region.

`public float Diameter`

:   Diameter in pixels.

`public float Feature`

:   How much of the featured look (the thick ring and the glow) is drawn, from zero through one, as the view set it on its nodes.

`public StableId Id`

:   The combatant behind the medallion; invalid for the +N medallion.

`public bool IsLeaving`

:   True while the medallion fades out where it stood.

`public bool IsOverflow`

:   True for the +N medallion.

`public string Key`

:   Key of the visual (see `BattleDockRibbonVisual.Key`).

`public float Opacity`

:   Opacity as drawn: that of the node times every group above it.

`public float PreviousTabOpacity`

:   Opacity of that text as drawn, counting the medallion.

`public string PreviousTabText`

:   Text of the tab on its way out, or empty.

`public float ScreenScale`

:   Screen pixels in one reference pixel, which turns every measure back into the reference pixels the choreography works in.

`public int Serial`

:   Number of the visual (see `BattleDockRibbonVisual.Serial`): the medallion that fades out and the one that fades in at its new place share a key but not a number.

`public bool ShowsNow`

:   Whether this medallion draws a NOW tab in the frame it was read in: its tab, or the one on its way out, reads NOW and is drawn above `ReadableTabOpacity`. A medallion that is leaving counts while its tab is still readable, so the ribbon of the frame in which the turn that ended fades out still says whose turn it was.

`public float TabOffsetX`

:   Horizontal distance, in pixels, from the center of the medallion to the center of its tab.

`public float TabOffsetY`

:   Vertical distance, in pixels, from the center of the medallion to the center of its tab.

`public float TabOpacity`

:   Opacity of the tab text as drawn, counting the medallion.

`public float TabPlateOpacity`

:   Opacity of the plate behind the tab as drawn, counting the medallion.

`public string TabText`

:   Text of the tab, or empty.

**Fields**

`public const float ReadableTabOpacity`

:   The opacity above which a tab text counts as drawn: the faintest a player reads at all.

**Methods**

`public static bool AnyShowsNow(IReadOnlyList<BattleDockRibbonReading> readings, int count)`

:   Whether the ribbon, as the view drew it in this frame, says whose turn it is: any of the readings draws a NOW tab. A ribbon that does not is mid-swap (the tab of one medallion has gone out and the next has not come) or has no turn at all.

    - `readings` &mdash; What `ReadRibbon` of a view filled in.
    - `count` &mdash; How many of them are valid, as `ReadRibbon` returned.
    - **Returns** &mdash; True when a NOW tab is drawn.

`public override string ToString()`

:   &mdash;

---

## BattleDockRibbonVisual

```csharp
public sealed class BattleDockRibbonVisual
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockRibbonMotion.cs</small>

One medallion of the turn ribbon as the choreography wants it drawn at this instant: where it stands, how large and how opaque
it is, and the tab under it. A visual is born when a medallion appears on the ribbon and is retired once it has faded out, so a
view keeps one node for it from the first to the last. A medallion that steps back in the queue is two visuals, the old one
fading out where it stood and a new one with the same `Key` fading in at its new place.

**Properties**

`public float BodyDiameter`

:   The diameter its body is drawn at: the one it is going to, so the body is drawn once and the view only scales it.

`public float CenterX`

:   Horizontal center in reference pixels from the left edge of `BattleDockMetrics.Ribbon`, the unit of `BattleDockMetrics.LayoutRibbon(bool[], out float[], out float[])`.

`public float CenterY`

:   Vertical center in reference pixels from the top edge of the ribbon; it never moves. In the dock it is `BattleDockMetrics.RibbonCenterY`.

`public float Diameter`

:   Diameter now, in reference pixels.

`public float Feature`

:   How much of the featured look the medallion has now, from zero through one: the thick ring and the glow of the medallion that is drawn larger, against the thin ring of the others. It moves from one to the other with the growth of the medallion, by the same ease-out in the same time, so a medallion that becomes the featured one does not change its ring in one frame while its size changes over several. A view draws both looks and fades them against each other by this number.

`public object Handle`

:   Whatever the adapter that draws this visual wants to keep with it, such as its node; the choreography never reads it.

`public bool HasTab`

:   True while a tab, or the last of one, is still to be drawn.

`public StableId Id`

:   The combatant behind the medallion; invalid for the +N medallion and for an entry without an id.

`public bool IsGone`

:   True once the visual was retired; a view puts its node away.

`public bool IsLeaving`

:   True once the medallion is no longer on the ribbon: the visual only fades out where it stands, under the ones that stay.

`public bool IsOverflow`

:   True for the +N medallion.

`public BattleDockMedallion Item`

:   The ribbon entry this visual shows; for a visual that is leaving, the last one it showed.

`public string Key`

:   Who it is: the combatant's id and which of that combatant's places on the ribbon it is (`ember#0`, `ember#1`), so a combatant that appears twice in a long forecast has two keys; `overflow` for the +N medallion; `#3`, the index, for an entry without a valid id. Two visuals can share a key while one fades out and the other fades in.

`public int Occurrence`

:   Which of the places of the same combatant this is, from zero; the index itself for an entry without an id.

`public float Opacity`

:   Opacity now, from zero through one.

`public float PreviousTabOpacity`

:   How much of `PreviousTabText` is shown, from zero through one, counting the opacity of the medallion.

`public string PreviousTabText`

:   The tab text on its way out while `TabText` comes in, or empty. Never both are legible at the same time.

`public float Scale`

:   The factor a view scales the body by: `Diameter` over `BodyDiameter`.

`public int Serial`

:   Number of this visual, unique among the visuals one `BattleDockRibbonMotion` has made; a view names its node after it.

`public float TabOffsetX`

:   The horizontal distance from the center of the medallion to the center of its tab: none, the tab hangs from the same center.

`public float TabOffsetY`

:   The vertical distance from the center of the medallion to the center of its tab, in reference pixels: half a diameter, less the overlap. It follows the diameter while the medallion grows.

`public float TabOpacity`

:   How much of `TabText` is shown, from zero through one, counting the opacity of the medallion. Under reduced motion a medallion that comes in over one that carried the same text at the same place takes the text over as it is, so there the text stays whole while the medallion under it is still coming in.

`public float TabPlateOpacity`

:   How much of the plate behind the tab text is shown, counting the opacity of the medallion: it follows the more visible of the two texts, so it comes in with a tab that is gained and goes out with one that is lost, and while one text takes the place of another it stays at no less than `BattleDockMetrics.RibbonTabPlateFloor`, so it is never an empty box at full strength.

`public string TabText`

:   The tab text the medallion is going to carry: NOW, NEXT or empty.

`public float TargetCenterX`

:   Where its slide ends: the center the layout gives the medallion.

`public float TargetDiameter`

:   Where its growth ends: the diameter the layout gives the medallion.

`public int TargetIndex`

:   Position in the ribbon of the medallion this visual stands for, from zero; minus one once it is leaving.

**Methods**

`public override string ToString()`

:   &mdash;

---

## BattleDockStripMotion

```csharp
public sealed class BattleDockStripMotion
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockStripMotion.cs</small>

The choreography of the event strip: which sentence it carries and how opaque that sentence is, step by step. The strip carries
one sentence at a time. A sentence that arrives takes the one on the strip out first, which fades to nothing in
`BattleDockMetrics.StripExitSeconds`, and only then does the text change and the new sentence come in, with an
ease-out, in `BattleDockMetrics.StripEnterSeconds`: no frame has two sentences with any opacity, which a crossfade
between two texts in one box cannot promise and which the old strip did not (a quarter of the frames of a 25 s recording).

A sentence that has come in is read before it goes: it stays whole on the strip for `HoldSeconds` after its entry,
and the sentences that arrive meanwhile wait for that, in the order they came. At most `WaitingCapacity` wait: the
one that came first keeps its place and the newest takes the other, so a sentence that arrives when none is waiting is shown
unless another follows it within a burst, and the strip is never more than two sentences behind. Sentences that follow one another within
`BurstSeconds` are one burst, and the newest says what the burst came to (a status that lands on three combatants
in the same instant is not read three times). Before this a sentence that arrived while another was coming in sent it out at
once, and three sentences in nine frames were all taken out before the first reached full opacity: none was read. A hold as
long as a sentence takes to read, with only the newest kept, is no answer either: the sentences of a busy action come about
every half second and overtake one another, and the strip never shows the blow of a Meteor that lands on three combatants or the
Burning that follows it.
A sentence the strip takes as it is (the first one, one of a view nobody plays, one of a change of theme) is already read and
carries no hold, and asking for an empty strip takes the sentence out at once: nothing is read in an empty one.

The motion runs on the clock of the view that owns it, never on a transition of a style sheet, so a test or a recording that steps
the clock by hand sees the same frames as a player. It allocates nothing after it has been made: a step moves a few numbers and
the text it carries is a reference to a string the caller gave it.

**Properties**

`public float HoldRemainingSeconds`

:   Seconds still to run of the hold of the sentence on the strip; zero when it is not held.

`public bool IsHolding`

:   True while the sentence that has come in is held whole for its reading time (`HoldSeconds`). The strip is not changing then, but it needs the clock: a view steps it while it is moving or holding, and the sentences that wait, when there are any, wait for the hold to be over.

`public bool IsLeaving`

:   True while `Text` is on its way out and `Target` is waiting to come in.

`public bool IsMoving`

:   True while a sentence is on its way out or on its way in.

`public string Newest`

:   The newest sentence the strip was asked for: the one it ends on. It is `Text` once the strip is at rest.

`public float Opacity`

:   How opaque `Text` is now, from zero through one; zero for an empty strip.

`public string Target`

:   The sentence that takes the strip next: the one that is coming in while `Text` leaves, or that waits for `Text` to be read. It is `Text` when nothing waits.

`public string Text`

:   The sentence the strip carries now: the one on its way out while `IsLeaving`, otherwise the one that is coming in or that stays. Empty when the strip has nothing to say.

`public int Version`

:   A number that grows every time `Text` changes, so a view puts the sentence in its text only when it swaps.

`public int WaitingCount`

:   How many sentences wait behind `Text`, from none through `WaitingCapacity`.

**Fields**

`public const float BurstSeconds`

:   Seconds within which a sentence that follows another one that is still waiting replaces it: the two came together, and the newest says what they came to. A sentence that follows a waiting one later than this joins the line behind it.

`public const float HoldSeconds`

:   Seconds a sentence that has come in stays whole on the strip before the next one may begin to take it out: the time to take it in at a glance. It is counted from the moment the sentence reaches full opacity, and it is the same under reduced motion, which shortens the fades and not the time a person needs for a sentence. It is also the longest hold that keeps up with a busy action: the events of one come about every half second, and a sentence takes `BattleDockMetrics.MotionSeconds` to go out and come in besides, so a longer hold makes the strip fall behind and skip.

`public const int WaitingCapacity`

:   The most sentences that wait behind the one on the strip: the first to arrive and the newest.

**Methods**

`public bool Advance(float seconds)`

:   Moves the change on by a step of the clock. A step longer than the whole change finishes it, and what is left of a step that ends the exit goes into the entry, and what is left of one that ends the entry goes into the hold. When the hold is over and a sentence waits, the sentence on the strip begins to go out with what is left of the step.

    - `seconds` &mdash; Seconds elapsed; zero, negative and not a number change nothing.
    - **Returns** &mdash; True when the text or its opacity may have changed.

`public void Clear()`

:   Forgets everything, as a strip that was never asked: the next sentence it is asked for is taken as it is.

`public void Finish()`

:   Ends the change where it stands: the newest sentence is on the strip, whole, and nothing waits.

`public void Retarget(string sentence, bool animate, bool reduceMotion)`

:   Asks the strip for a sentence. The same sentence as the newest one asked for starts nothing, so a redraw is free. Without `animate` (a view nobody plays or steps, a view that was never drawn, a change of theme) and the first time the strip is asked at all, the sentence is on the strip at once, whole, and whatever was changing or waiting is over. A sentence that comes in while another is being held, or is still coming in, waits for that one to be read (`HoldSeconds`) behind the ones that were already waiting; an empty sentence does not wait.

    - `sentence` &mdash; The sentence the strip has to end on; null or empty for none.
    - `animate` &mdash; True when the change plays; false takes the sentence as it is.
    - `reduceMotion` &mdash; True under reduced motion, which keeps the fades and shortens them to `BattleDockMetrics.ReducedFadeSeconds`.

`public override string ToString()`

:   &mdash;

---

## BattleDockStripReading

```csharp
public readonly struct BattleDockStripReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

What the event strip draws at this instant. It carries one sentence at a time (`BattleDockStripMotion`), so
`Opacity` and `OutgoingOpacity` are never above zero together. Opacities are the ones that reach the
screen: the product of the node of the sentence and of every node above it, the dip of a theme swap included.

**Constructors**

`public BattleDockStripReading(string text, float opacity, string outgoingText, float outgoingOpacity)`

:   Creates a reading.

    - `text` &mdash; The sentence the strip is showing or is about to show.
    - `opacity` &mdash; Its opacity on the screen; zero while it has not come in yet.
    - `outgoingText` &mdash; The sentence on its way out, or empty.
    - `outgoingOpacity` &mdash; Its opacity on the screen; zero when there is none.

**Properties**

`public float Opacity`

:   The opacity of `Text` on the screen, from zero through one.

`public float OutgoingOpacity`

:   The opacity of `OutgoingText` on the screen; zero when there is none.

`public string OutgoingText`

:   The sentence on its way out while `Text` waits to come in; empty when none.

`public string Text`

:   The sentence the strip is showing; while another is on its way out, the one that comes in after it (at no opacity yet). Empty when the strip has nothing to say.

---

## BattleDockTargetRowReading

```csharp
public readonly struct BattleDockTargetRowReading
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleDockReadings.cs</small>

One row of the target list, read while the list is showing.

**Constructors**

`public BattleDockTargetRowReading(StableId id, float barFraction, float listOpacity)`

:   Creates a reading.

    - `id` &mdash; The combatant of the row.
    - `barFraction` &mdash; How much of the mini health bar is drawn, from zero through one; zero for a row that draws none.
    - `listOpacity` &mdash; The opacity of the whole list on the screen.

**Properties**

`public float BarFraction`

:   How much of the mini health bar of the row is drawn now, from zero through one.

`public StableId Id`

:   The combatant of the row.

`public float ListOpacity`

:   The opacity of the whole target list on the screen: the fade of its content, the panel above it and the dip of a theme swap.

---

## BattleFeedbackLayout

```csharp
public static class BattleFeedbackLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Computes a deterministic clear rectangle for presentation feedback.

The routine is renderer- and engine-independent. It clips positive
obstacle intersections to the supplied stage, considers every pair of
resulting x edges, and finds the largest y gap in that vertical slab.
The expected obstacle count is small (normally twelve or fewer), so the
bounded temporary arrays are rebuilt once per call. Callers should cache
the result across frames when geometry is stable; this helper deliberately
does not retain mutable static scratch state.

**Methods**

`public static bool TryFindClearBounds(BattleStageBounds stage, IReadOnlyList<BattleStageBounds> obstacles, out BattleStageBounds bounds)`

:   Finds the largest axis-aligned rectangle inside `stage` that does not positively intersect any obstacle. Obstacles outside the stage are ignored; obstacles crossing its edge are clipped. A touching edge has zero intersection and therefore does not reduce the available area. Ties prefer the rectangle whose centre is closest to the original stage centre, then lexicographic (left, bottom, width, height) order, making results independent of obstacle input ordering.

    - `stage` &mdash; Valid normalized stage bounds.
    - `obstacles` &mdash; Information bands or other occupied bounds.
    - `bounds` &mdash; Receives the largest clear rectangle.
    - **Returns** &mdash; False when the stage is invalid or fully covered.

---

## BattleHudDesign

```csharp
public enum BattleHudDesign
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleHudDesign.cs</small>

Which HUD structure a view draws (the HudDesign of a battle view). The structure decides the framing of the formation, the
plates of the stage and the share of the screen the stage may use; the theme only decides the style. A view reads its design from the
tree it is bound to: the dock frame makes it the Dock, the Overlay marker the Overlay, anything else the Classic panel.

| Value | Meaning |
| --- | --- |
| `Dock` | The dock at the bottom of the screen: commands, action card and party panel in one band, the stage above it. |
| `Classic` | The console panel of the science-fiction layout: the stage on the left, the panel on the right. |
| `Overlay` | The Overlay of the Antlerglow C direction: the stage takes the whole screen, the HUD floats over its corners (the ribbon top left, the party cards top right, the command menu and i... |

---

## BattleLayoutIdentity

```csharp
public enum BattleLayoutIdentity
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

Visual family used for starter palettes and default stage reservations.

| Value | Meaning |
| --- | --- |
| `Fantasy` | Fantasy presentation framing and palette family. |
| `ScienceFiction` | Science-fiction presentation framing and palette family. |

---

## BattlePresentationLabel

```csharp
public sealed class BattlePresentationLabel
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

One display text override owned by a presentation profile.

**Fields**

`public string Id`

:   Stable display identifier looked up by the presentation layer.

`public string Text`

:   Text shown for the identifier.

---

## BattlePresentationProfile

```csharp
public sealed class BattlePresentationProfile : ScriptableObject
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

Authored references only. Runtime and preview never write to this asset.

**Fields**

`public int ActionsPerPage`

:   Maximum number of action choices shown on one page.

`public BattleContentCatalog Catalog`

:   Authoring catalog supplying the encounter and content references.

`public string EncounterId`

:   Stable encounter identifier selected for presentation.

`public BattlePresentationLabel[] Labels`

:   Optional display text overrides; these never affect battle hashes.

`public UnityEngine.Object LayoutAsset`

:   Optional UI Toolkit visual tree asset.

`public BattleRegistryProvider RegistryProvider`

:   Optional registry provider used when the runtime has no explicit provider.

`public BattleRulesPreset RulesPreset`

:   Scheduler preset used to build the runtime catalog.

`public uint Seed`

:   Initial deterministic seed supplied to the battle session.

`public UnityEngine.Object StagePresentation`

:   Optional stage preset validated and consumed by the runtime presentation layer.

`public int TargetsPerPage`

:   Maximum number of target choices shown on one page.

`public BattleUiTechnology Technology`

:   UI technology a host should instantiate for this profile.

`public BattleTheme Theme`

:   Theme values copied into the active view.

`public float TicksPerSecond`

:   Simulation ticks represented by one real second.

`public bool UseGamepad`

:   Enables directional keyboard and controller navigation.

`public bool UseSideInformationBanks`

:   Groups stage information beside the bodies instead of attaching each plate to its feet. The initial bank layout supports three combatants per side.

`public BattleViewBehaviour ViewPrefab`

:   View prefab that owns the profile's UI layout.

`public BattleWarmUp WarmUp`

:   What the battle rehearses while it loads, so the first action of the player does not pay for the first use of the code behind it: the interface (`BattleWarmUp.Dock`), the text of the world (`BattleWarmUp.WorldText`) and the code of the decision on a shadow copy of the battle (`BattleWarmUp.Rehearsal`). Every layer draws off screen, never touches the battle, and is taken away when it is done; it costs some frames of work while the battle loads, before the first decision opens. Every layer is on by default (`BattleWarmUp.All`); `BattleWarmUp.None` makes a battle that rehearses nothing.

---

## BattleProfileCatalog

```csharp
public sealed class BattleProfileCatalog : IDisposable
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleProfileCatalog.cs</small>

Owns the partial runtime catalog required by a presentation profile.
The catalog clone, selected scheduler, and encounters rewired to that
scheduler are runtime-owned; other definitions referenced by the graph
remain shared with the source and must be treated as read-only.

**Constructors**

`public BattleProfileCatalog(BattleContentCatalog source, string encounterId, BattleRulesPreset preset)`

:   Creates a partial runtime catalog for one presentation profile. The nodes this class replaces are isolated; referenced definitions that are not replaced remain shared with the source and are read-only for consumers of the returned catalog.

    - `source` &mdash; Authored catalog to copy.
    - `encounterId` &mdash; Stable encounter identifier to select.
    - `preset` &mdash; Scheduler behavior to apply.

**Properties**

`public BattleContentCatalog Catalog`

:   Runtime-owned catalog containing copied scheduler and encounter nodes. Definitions not replaced while selecting the profile remain shared references to the source catalog and are not safe to edit through this property.

**Methods**

`public void Dispose()`

:   Destroys all runtime-owned catalog copies and releases the catalog.

---

## BattleRulesPreset

```csharp
public enum BattleRulesPreset
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

Choice of Action Order rounds or paused ATB when deriving a profile's runtime catalog.

| Value | Meaning |
| --- | --- |
| `Rounds` | Round-based scheduler with action order. |
| `AtbPause` | Active-time scheduler that pauses while input is requested. |

---

## BattleRuntimeCheckpoint

```csharp
public sealed class BattleRuntimeCheckpoint
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Persistable battle restore point. The battle state is canonical bytes and
the three hashes pin it to one compiled encounter.

**Constructors**

`public BattleRuntimeCheckpoint(StableId encounterId, uint seed, Sha256Digest contentManifestHash, Sha256Digest compiledSnapshotHash, Sha256Digest startRequestHash, byte[] stateBytes)`

:   Creates a restore point, usually from external persisted fields. All identity fields are validated and the state payload is defensively copied.

    - `encounterId` &mdash; Exact encounter the state belongs to.
    - `seed` &mdash; Seed originally used to create the battle.
    - `contentManifestHash` &mdash; Compiled content manifest hash.
    - `compiledSnapshotHash` &mdash; Compiled catalog snapshot hash.
    - `startRequestHash` &mdash; Selected encounter start-request hash.
    - `stateBytes` &mdash; Non-empty canonical battle-state bytes.

**Properties**

`public Sha256Digest CompiledSnapshotHash`

:   The compiled catalog snapshot hash.

`public Sha256Digest ContentManifestHash`

:   The compiled catalog's content manifest hash.

`public StableId EncounterId`

:   The explicit encounter this checkpoint restores.

`public uint Seed`

:   The battle seed.

`public Sha256Digest StartRequestHash`

:   The selected encounter's start-request hash.

**Methods**

`public byte[] GetStateBytes()`

:   Returns a defensive copy of the canonical state bytes.

    - **Returns** &mdash; A new byte array containing the checkpoint's canonical battle state.

---

## BattleRuntimeController

```csharp
public sealed partial class BattleRuntimeController
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeController.Presentation.cs</small>

Coordinates authored presentation profiles, runtime views and optional stage presentation.

**Properties**

`public CompiledAuthoringCatalog ActiveCatalog`

:   The immutable compiled catalog used by the active engine.

`public StableId ActiveEncounterId`

:   The explicit encounter ID bound to the active engine.

`public uint ActiveSeed`

:   The seed bound to the active engine.

`public StagePresentationPlayback ActiveStagePresentation`

:   The isolated stage effects owned by this battle, or null when no preset is configured.

`public BattleViewBehaviour ActiveView`

:   The instantiated presentation view for the active battle, or null before it starts.

`public IAnimationAdapter AnimationAdapter`

:   The animation player, or null to use the shipped one. Set this to drive an Animator or a sprite library from the authored animation keys.

`public IAudioAdapter AudioAdapter`

:   The sound player, or null to use the shipped one. Set this to route battle audio through FMOD, Wwise, or your own mixer instead of the serialized clips.

`public bool AutoAdvance`

:   Whether Update converts elapsed time into fixed integer ticks.

`public BattleContentCatalog Catalog`

:   Serialized catalog used by the no-argument start.

`public DecisionOptions CurrentDecisionOptions`

:   The legal presentation choices for the current human decision, or `DecisionOptions.None` while no battle is active or the engine is not waiting for a human. Reading this property never advances or mutates the authoritative engine.

`public BattleSnapshot CurrentSnapshot`

:   The latest authoritative snapshot, or null before a battle starts.

`public string EncounterId`

:   Serialized encounter ID used by the no-argument start.

`public bool HasBattle`

:   Whether this controller currently owns an authoritative engine.

`public bool IsPaused`

:   True while `Pause` has frozen the battle and its visuals. `State` keeps reporting what the battle itself is doing, because a paused battle is still mid-fight rather than finished.

`public bool IsWarmingUp`

:   True while any layer of the warm-up the profile asked for is still working: the interface playing a decision off screen, or the stage drawing the text of the world. The decision of the battle is on the screen meanwhile; a command the player gives through the interface while the layers run is held and submitted when they end, so the first action never plays over its own rehearsal (a command the host submits itself, with `Submit(BattleUiCommandChoice)`, is never held). A host that wants those first frames unseen keeps its scene transition over the battle until this is false, or puts a `BattleWarmUpCurtain` on the object of the controller, which covers them. Neither covers the frame the battle is started in unless it is on the screen before the call: the transition from before it, the curtain when it was lowered a frame earlier (`BattleWarmUpCurtain.Lower`). False when the profile asks for nothing.

`public bool LogFailuresToConsole`

:   Whether a failed operation is written to the Console. On by default, because a designer who cannot read a `BattleRuntimeOperationResult` has no other channel. Turn it off in a project that surfaces failures its own way through `OnRuntimeFailed`, or in a test that provokes a failure on purpose.

`public bool ManualClock`

:   When true, `Update` leaves everything to the host: it neither ticks the presentation nor advances the battle clock, and the host calls `AdvancePresentation` and `AdvanceTicks` itself with an explicit step. Off by default, which keeps the normal behaviour driven by Unity's frame time. Captures and tests that need an exact step turn it on.

`public BattleRuntimePacing Pacing`

:   When the tick pump is allowed to run. Changing it mid-battle is safe: pacing decides when ticks are requested, never what they produce, and never when the HUD shows a result, which follows the beats being played in either pacing.

`public IPoolAdapter PoolAdapter`

:   The pool the presentation spawns instances through, or null to use the shipped one. Assign an implementation of your own before the battle starts to load art from Addressables or an existing pool; the built-in pool is used for any adapter left null.

`public BattlePresentationProfile PresentationProfile`

:   The authored presentation profile currently selected by this controller.

`public BattleRegistryProvider RegistryProvider`

:   Explicit custom mechanics registry. Assign before starting a battle; a profile provider is used only when this is null.

`public float SpeedMultiplier`

:   The playback multiplier in force, one of `SpeedSteps`. It scales both the battle clock and the visuals, so nothing drifts apart at 4x.

`public BattlePresenter StagePresenter`

:   Optional stage presenter used to render combatants and target previews. It may be assigned only while no battle is active.

`public BattleRuntimeState State`

:   The facade's current lifecycle state.

`public float TicksPerSecond`

:   How many simulation ticks one real second is worth before `SpeedMultiplier` is applied. Values below one are raised to one, because a battle that cannot reach a whole tick never moves.

`public IVfxAdapter VfxAdapter`

:   The effect player, or null to use the shipped one. A host adapter replaces the VFX bindings on this component rather than adding to them.

`public BattleWarmUpReport WarmUpReport`

:   What the warm-up of the active battle asked for and has done so far.

**Fields**

`public const float DefaultTicksPerSecond`

:   The default conversion rate from elapsed seconds to integer ticks.

`public static readonly FrozenList<float> SpeedSteps`

:   The playback multipliers `CycleSpeed` steps through, in order. Speed scales the visual clock and the tick pump together, so a fight watched at 4x still reaches the same result through the same ticks as one watched at 1x.

**Events**

`public event Action<BattleRuntimeEndedEvent> BattleEnded`

:   Raised when the battle reaches a clean end or Stop is called.

`public event Action<BattleRuntimeStartedEvent> BattleStarted`

:   Raised after a new or restored battle is fully bound.

`public event Action<BattleRuntimeEventsEvent> EventsProduced`

:   Raised once per non-empty event batch.

`public event Action<BattleRuntimeFailedEvent> RuntimeFailed`

:   Raised when a configuration or engine failure is contained.

`public event Action<BattleRuntimeSnapshotEvent> SnapshotChanged`

:   Raised after every authoritative snapshot change.

**Methods**

`public BattleRuntimeOperationResult AdvanceOneAction()`

:   Advances the battle to the end of exactly one action instead of a budget of ticks, which is what a turn-based or animation-driven host wants: call it once per attack and let the visuals finish before calling it again. It stops at a human decision without inventing a command. A failed battle answers `BattleRuntimeFailure.BattleNotRunning` without publishing anything.

    - **Returns** &mdash; The resulting lifecycle state and authoritative snapshot.

`public void AdvancePresentation(float seconds)`

:   Advances the presentation by an explicit step, exactly as one `Update` would with that frame time: the stage presenter (beats, bars, numbers, reticle pulse), the world theme crossfade and the active view's own motion. The `BattleWarmUpCurtain` of this controller, if there is one, takes the step too, and with the whole of it: the curtain is a transition, so a paused battle does not hold it. Never advances the simulation.

    - `seconds` &mdash; Elapsed seconds, unscaled; zero or less changes nothing.

`public BattleRuntimeOperationResult AdvanceTicks(int count)`

:   Advances an exact positive integer number of simulation ticks and stops at engine boundaries. Non-positive counts fail without mutation, and a failed battle answers `BattleRuntimeFailure.BattleNotRunning` without publishing anything.

    - `count` &mdash; Positive number of simulation ticks.
    - **Returns** &mdash; The resulting lifecycle state and authoritative snapshot.

`public void ApplyTheme(BattleTheme theme)`

:   Switches the visual theme without stopping the battle. The stage backdrop starts to crossfade in the same call (`BattleStageBackdropRig.DefaultCrossfadeSeconds`, or a dissolve of `BattleStageBackdropRig.ReducedCrossfadeSeconds` when the theme asks for reduced motion: a fade is allowed under Reduce Motion, a cut is the flash it asks to avoid). The native view changes its skin behind a dip of its whole HUD over the same length, started in the same call: the old skin fades out, the view takes the theme while it is invisible and the new skin fades in. The interface the stage draws in the world (nameplates and bare bars, the marks of the target preview and the cue ring under a caster) dips with the HUD, frame by frame, and takes the skin of the theme, its plate policy and its painted marks, and the layout it asks for, in the very frame the view takes the theme, when both are invisible. So the theme of the view and the skin of the world are the new ones only once the HUD has dipped, which takes the view's own clock; a view that is not drawn, has no clock or is a custom one takes the theme and the world takes its skin at once. A skip, a second call, a stop and the end of the battle never leave the world interface on the old skin or below full opacity. Simulation state, the authored profile and the event stream are not touched. Without a battle, the theme is kept and used by the next one.

    - `theme` &mdash; Theme to apply; it is copied. Null returns to the selected profile's own theme.

`public BattleRuntimeValueResult<BattleRuntimeCheckpoint> CaptureCheckpoint()`

:   Captures canonical state plus the hashes required for exact restore. The returned checkpoint owns a defensive copy of its byte payload.

    - **Returns** &mdash; A checkpoint value, or BattleNotRunning/CheckpointInvalid.

`public BattleRuntimeValueResult<byte[]> CaptureReplay()`

:   Captures canonical replay JSON for the active battle using the same scheduler registry that compiled and runs it.

    - **Returns** &mdash; Replay bytes, or BattleNotRunning/ReplayCaptureFailed.

`public void ConfigureBattle(BattleContentCatalog content, string encounter, uint seed)`

:   Configures an explicit catalog without mutating it or starting a battle.

    - `content` &mdash; Authored catalog prepared at StartBattle; it is not modified by this controller.
    - `encounter` &mdash; Stable encounter ID in the supplied catalog.
    - `seed` &mdash; Fixed deterministic seed used by subsequent starts.

`public void ConfigurePresentation(BattlePresentationProfile profile)`

:   Chooses a native or custom view before starting. The authored profile is read-only.

    - `profile` &mdash; Authored view and presentation configuration, or null to use the legacy host.

`public void CycleSpeed()`

:   Moves to the next entry of `SpeedSteps`, wrapping back to the slowest after the fastest.

`public void Pause()`

:   Freezes the battle and everything drawing it. Repeating the call does nothing, and no tick is lost: the clock simply stops accumulating.

`public BattleRuntimeOperationResult Restore(BattleRuntimeCheckpoint checkpoint)`

:   Restores an exact canonical checkpoint against the current catalog. All catalog and encounter hashes must match before state is decoded; a rejected restore leaves an existing battle unchanged.

    - `checkpoint` &mdash; Checkpoint value and canonical state bytes.
    - **Returns** &mdash; The restored state or a typed fail-closed diagnostic.

`public void Resume()`

:   Restarts a paused battle from exactly where it stopped.

`public void SkipVisuals()`

:   Finishes every queued animation now and puts the HUD on the authoritative state in the same call: nothing stays queued and no bar is left sliding. It only compresses visuals, so a player who skips sees the same battle arrive at the same result.

`public BattleRuntimeOperationResult StartBattle()`

:   Starts the serialized encounter with the configured seed policy. Compilation and configuration failures are returned and published; the method does not throw an integration exception or select fallback content.

    - **Returns** &mdash; The resulting lifecycle state, snapshot, and typed failure.

`public BattleRuntimeOperationResult StartBattle(string requestedEncounterId, uint seed)`

:   Starts an explicit authored encounter and seed. Invalid, missing, or unknown IDs fail closed and leave an already active battle unchanged.

    - `requestedEncounterId` &mdash; Exact authored stable-ID text.
    - `seed` &mdash; Unsigned deterministic battle seed.
    - **Returns** &mdash; The resulting lifecycle state, snapshot, and typed failure.

`public BattleRuntimeOperationResult StartBattle(StableId requestedEncounterId, uint seed)`

:   Starts an explicit authored encounter and seed. Unknown content or a failed compile is reported without replacing an active battle.

    - `requestedEncounterId` &mdash; Exact valid authored encounter ID.
    - `seed` &mdash; Unsigned deterministic battle seed.
    - **Returns** &mdash; The resulting lifecycle state, snapshot, and typed failure.

`public BattleRuntimeOperationResult Stop()`

:   Stops and tears down the active battle while returning its last snapshot. Calling Stop without an active battle fails without events.

    - **Returns** &mdash; The stopped state and final snapshot, or BattleNotRunning.

`public BattleRuntimeOperationResult Submit(BattleUiCommandChoice choice)`

:   Submits a UI choice after deterministic command translation. A stale actor, unavailable skill, or unsatisfied target contract is rejected without inventing a different command. A failed battle refuses it with `BattleRuntimeFailure.BattleNotRunning` and publishes nothing.

    - `choice` &mdash; Intent emitted by a battle UI.
    - **Returns** &mdash; The authoritative command result and resulting snapshot.

`public BattleRuntimeOperationResult Submit(BattleCommand command)`

:   Submits an advanced, already-built battle command. Gameplay rejection is returned as `BattleRuntimeFailure.CommandRejected`; fatal invariants move the controller to the failed state, which refuses every later command with `BattleRuntimeFailure.BattleNotRunning` and publishes nothing.

    - `command` &mdash; Exact command for authoritative validation.
    - **Returns** &mdash; The command disposition, resulting state, and snapshot.

`public void UpdateStagePresentation(UnityEngine.Object stagePresentation)`

:   Updates visual recipes, bindings and feel during a battle. Cancels old pending effects and restores their offsets without restarting simulation, replacing its view, or writing to the authored profile.

    - `stagePresentation` &mdash; Optional PresentationStagePreset asset; null clears profile effects. Other object types warn and clear them.

---

## BattleRuntimeEndReason

```csharp
public enum BattleRuntimeEndReason
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Why a normally driven battle stopped advancing.

| Value | Meaning |
| --- | --- |
| `TerminalResult` | The authored win or loss condition became terminal. |
| `NoScheduledWork` | The engine has no remaining scheduled work. |
| `StoppedByHost` | The host called Stop. |

---

## BattleRuntimeEndedEvent

```csharp
public sealed class BattleRuntimeEndedEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Payload raised when driving reaches a clean end.

**Properties**

`public BattleRuntimeEndReason Reason`

:   The clean end reason.

`public BattleSnapshot Snapshot`

:   The last authoritative snapshot.

---

## BattleRuntimeEventsEvent

```csharp
public sealed class BattleRuntimeEventsEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Payload raised for a non-empty event batch.

**Properties**

`public FrozenList<BattleEvent> Events`

:   The non-empty immutable event batch.

---

## BattleRuntimeFailedEvent

```csharp
public sealed class BattleRuntimeFailedEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Payload raised for fail-closed runtime failures.

**Properties**

`public BattleRuntimeFailure Failure`

:   The typed failure category.

`public string Message`

:   Actionable diagnostic detail.

---

## BattleRuntimeFailure

```csharp
public enum BattleRuntimeFailure
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Typed reasons a facade operation can fail without throwing.

| Value | Meaning |
| --- | --- |
| `None` | No failure occurred. |
| `CatalogMissing` | No authoring catalog was assigned. |
| `EncounterIdMissing` | No encounter ID was supplied. |
| `EncounterIdInvalid` | The supplied encounter ID is not valid stable-ID text. |
| `EncounterNotFound` | The explicit encounter is absent from the compiled catalog. |
| `CatalogCompileFailed` | The authoring catalog failed compilation. |
| `RegistryProviderFailed` | The configured registry provider threw while building registries. |
| `HumanControlRequirementNotMet` | The encounter does not satisfy the configured human-control policy. |
| `BattleNotRunning` | The requested operation requires an active battle. |
| `CommandTranslationFailed` | A presentation choice could not be translated into a command. |
| `CommandRejected` | The authoritative engine rejected the submitted command. |
| `CheckpointInvalid` | The supplied or captured checkpoint is malformed. |
| `CheckpointIncompatible` | The checkpoint hashes do not match the compiled content. |
| `RestoreRejected` | The engine rejected the checkpoint state. |
| `ReplayCaptureFailed` | Replay capture could not complete. |
| `FatalInvariant` | The simulation reported a deterministic fatal invariant. |
| `InvalidTickCount` | The requested tick count is not positive. |
| `UnexpectedException` | An unexpected integration exception was contained. |

---

## BattleRuntimeHumanControlRequirement

```csharp
public enum BattleRuntimeHumanControlRequirement
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Optional fail-closed check over the control kinds authored into an
encounter. The controller never rewrites the compiled start request.

| Value | Meaning |
| --- | --- |
| `UseAuthoredControls` | Accept the encounter's authored Human/Automatic assignments. |
| `RequireAtLeastOneHuman` | Require at least one living human-controlled combatant. |
| `RequirePerspectiveTeamHuman` | Require a living human-controlled member on the perspective team. |

---

## BattleRuntimeOperationResult

```csharp
public class BattleRuntimeOperationResult
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Common typed result returned by controller operations.

**Properties**

`public CommandResult CommandResult`

:   The underlying command result for Submit operations.

`public BattleRuntimeFailure Failure`

:   Typed failure, or None on success.

`public string Message`

:   Actionable detail suitable for a log or error panel.

`public BattleSnapshot Snapshot`

:   Authoritative snapshot after the operation, when one exists.

`public BattleRuntimeState State`

:   Controller state after the operation.

`public bool Succeeded`

:   True only when the requested operation completed.

---

## BattleRuntimePacing

```csharp
public enum BattleRuntimePacing
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

How the controller decides when the battle clock may advance. It changes
pacing only: the same encounter and seed still reach the same result
through the same ticks either way.

| Value | Meaning |
| --- | --- |
| `Continuous` | Convert elapsed time into ticks every frame. |
| `WaitForPresentation` | Hold the next tick until the presenter has finished playing every beat it has been handed, so a batch never grows past the action on screen, at the cost of the battle running at th... |

---

## BattleRuntimeSeedPolicy

```csharp
public enum BattleRuntimeSeedPolicy
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

How the no-argument StartBattle operation chooses its seed.

| Value | Meaning |
| --- | --- |
| `Fixed` | Use the serialized fixed seed for every start. |
| `Incrementing` | Add the number of successful starts on this controller to the fixed seed. |

---

## BattleRuntimeSnapshotCause

```csharp
public enum BattleRuntimeSnapshotCause
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Why a snapshot was published through SnapshotChanged.

| Value | Meaning |
| --- | --- |
| `Started` | A new engine published its initial snapshot. |
| `Restored` | A restored engine published its restored snapshot. |
| `CommandSubmitted` | Command submission produced the snapshot. |
| `TicksAdvanced` | Integer tick advancement produced the snapshot. |
| `ActionAdvanced` | One action boundary produced the snapshot. |

---

## BattleRuntimeSnapshotEvent

```csharp
public sealed class BattleRuntimeSnapshotEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Payload raised whenever the authoritative snapshot changes.

**Properties**

`public BattleRuntimeSnapshotCause Cause`

:   The operation that published the snapshot.

`public BattleSnapshot Snapshot`

:   The authoritative snapshot.

---

## BattleRuntimeStartedEvent

```csharp
public sealed class BattleRuntimeStartedEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Payload raised when a battle starts or is restored.

**Properties**

`public StableId EncounterId`

:   The encounter that was bound.

`public bool Restored`

:   True for Restore; false for a new start.

`public uint Seed`

:   The seed that was bound.

`public BattleSnapshot Snapshot`

:   The initial authoritative snapshot.

---

## BattleRuntimeState

```csharp
public enum BattleRuntimeState
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

The runtime facade's externally visible lifecycle.

| Value | Meaning |
| --- | --- |
| `Idle` | No battle has been started. |
| `Running` | The engine can advance without a human command. |
| `AwaitingInput` | The engine is paused at a human decision boundary. |
| `Completed` | The battle reached a clean terminal or no-work outcome. |
| `Stopped` | The host explicitly stopped the battle. |
| `Failed` | A contained failure prevents further automatic driving. |

---

## BattleRuntimeUnityEvent

```csharp
public sealed class BattleRuntimeUnityEvent : UnityEvent
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

Parameterless inspector event paired with the typed C# events.

---

## BattleRuntimeValueResult

```csharp
public sealed class BattleRuntimeValueResult
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeContracts.cs</small>

An operation result that also returns an immutable value.

**Properties**

`public T Value`

:   The captured value on success; default on failure.

---

## BattleStageBounds

```csharp
public readonly struct BattleStageBounds
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

A presentation-only rectangle in normalized screen space, with a bottom-left origin.

**Constructors**

`public BattleStageBounds(float left, float bottom, float width, float height)`

:   Creates normalized bottom-left stage bounds.

    - `left` &mdash; Normalized left edge.
    - `bottom` &mdash; Normalized bottom edge.
    - `width` &mdash; Normalized width.
    - `height` &mdash; Normalized height.

**Properties**

`public float Bottom`

:   Normalized bottom coordinate.

`public float Height`

:   Normalized height.

`public bool IsValid`

:   True when the rectangle is positive and contained in normalized space.

`public float Left`

:   Normalized left coordinate.

`public float Width`

:   Normalized width.

---

## BattleTheme

```csharp
public sealed class BattleTheme
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

Serializable visual values copied by views before they render.

**Fields**

`public Color Accent`

:   Primary action and selection accent color.

`public Sprite AccentBarSprite`

:   Nine-slice bar of accent color along the edge of a selected row. Null draws a flat bar.

`public BattleDockInsets ActiveRowInset`

:   How far the ornament of `SelectionSprite` reaches into the active party row, from each of its four edges, in reference pixels (1920 by 1080): double lines, corner diamonds or crescents that the content of the row has to stay clear of. The row keeps four reference pixels of air beyond it, and when its card is too short for that it makes its icons smaller before it touches anything else. A side left at zero has no ornament (a line along the edge of the card, which every row draws, is not one) and keeps its arrangement. All zero, the default and what a theme saved before this field gets, declares nothing and keeps the row as it was drawn then.

`public Color AllyAccent`

:   Accent of the viewing team: ally rim and medallion ring. Alpha zero falls back to `Accent`.

`public Color AllyHealth`

:   Health fill of allies; never red. Alpha zero falls back to `Positive`.

`public Color AllyText`

:   Color of allied text in the dock: names of allies, the line of the chosen target. A rim can be as dark as the art asks; text must read at 4.5:1. Alpha zero derives it from `AllyAccent` by the smallest step toward `Foreground`.

`public Color Background`

:   Background color used by the view.

`public Sprite BarBackground`

:   Nine-slice white background of resource and health bars, tinted by the view. Null draws a flat bar.

`public Sprite BarFill`

:   Nine-slice white bar fill, tinted by the view. Null draws a flat fill.

`public Sprite BarFrame`

:   Nine-slice hairline frame drawn over bars. Null draws none.

`public Font DisplayFont`

:   Optional display font (TTF or OTF) for UI Toolkit names and headers. The body font is `Font`.

`public UnityEngine.Object DisplayFontAsset`

:   Optional display font asset (a TMP_FontAsset) for names and headers. The body font is `FontAsset`.

`public Color EnemyAccent`

:   Accent of opposing teams. Alpha zero falls back to `Negative`.

`public Color EnemyHealth`

:   Health fill of enemies. Alpha zero falls back to `Negative`.

`public Color EnemyText`

:   Color of hostile text in the dock: names of enemies, an unaffordable cost. Alpha zero derives it from `EnemyAccent` by the smallest step toward `Foreground`.

`public Font Font`

:   Optional legacy Unity font for controls that require one.

`public UnityEngine.Object FontAsset`

:   Optional native font asset consumed by the selected UI technology.

`public float FontSize`

:   Default font size used by native controls created by a view.

`public Color Foreground`

:   Primary readable text and foreground color.

`public FormationLayoutMode FormationLayout`

:   How the formation is laid out on this theme's stage. Line, the default, stands every combatant on one ground line at full scale and sizes them by population. Depth stands two shallow rows with perspective scale and needs a backdrop that declares a horizon and a vanishing point; without them it falls back to Line. Legacy keeps the authored seat positions and the skin's rank scale.

`public Color FrameColor`

:   Hairline and border color of frames. Alpha zero leaves each surface's own border.

`public Sprite FrameSprite`

:   Nine-slice sprite drawn as the frame of panels. Null keeps the flat panel.

`public Sprite GroundRingSprite`

:   Elliptical sprite drawn on the ground under a previewed target. Null uses the procedural ring.

`public BattleIconSet IconSet`

:   Icons for action kinds, skills and statuses. Null shows no icons.

`public BattleLayoutIdentity Identity`

:   Layout family whose colors and framing this theme describes.

`public Sprite MedallionMask`

:   Round white sprite that masks portraits into medallions. Null generates a circle.

`public Sprite MedallionRing`

:   Ring sprite drawn around portrait medallions. Null draws a plain ring.

`public Color Negative`

:   Color used for negative outcomes such as damage.

`public Color NeutralAccent`

:   Accent for neutral emphasis such as selection and the next-actor tab. Alpha zero falls back to `Accent`.

`public Sprite NextMedallionRing`

:   Ring sprite drawn around the next actor's medallion in the turn ribbon. Null scales `MedallionRing`.

`public Sprite OrnamentSprite`

:   Nine-slice ornament sprite for corners, dividers and tabs. Null draws none.

`public int OverlayRibbonPlacesBelow16By9`

:   At most this many places in the turn ribbon of the Overlay HUD on a screen narrower than 16:9 (2 to 5, the +N medallion included); 0 keeps as many as the width holds (five at 16:10). A longer turn order shows its first entries and a +N medallion, as on any screen. For a scene whose set art stands where a full ribbon would end.

`public Color Panel`

:   Panel fill color used by the view.

`public Color Positive`

:   Color used for positive outcomes such as healing.

`public bool ReduceMotion`

:   Requests reduced motion in the presentation layer.

`public Color ResourceEnergy`

:   Energy resource color. Alpha zero falls back to `Positive`.

`public Color ResourceFocus`

:   Focus resource color. Alpha zero falls back to `Accent`.

`public Sprite ReticleSprite`

:   Square sprite of four corner brackets drawn on a selected target. Null uses the procedural ring.

`public Sprite SelectionSprite`

:   Nine-slice frame of the selected command, target or active party member. Null tints `FrameSprite` instead.

`public BattleStageBackdropAsset StageBackdrop`

:   Backdrop that replaces the generated stage gradient. Null keeps the generated backdrop.

`public Material SurfaceMaterial`

:   Optional material used by the view's panel surfaces.

`public Sprite SurfaceSprite`

:   Optional surface sprite used by the view's panels.

`public Sprite TabSprite`

:   Nine-slice tab drawn under the next actor's medallion. Null draws a flat tab.

`public BattleWorldPlateMode WorldPlates`

:   Which plates the combatants on the stage draw. Compact, the default, draws none for the player's side, a bare health bar for every other combatant and the whole plate above the head of a selected target. Standard draws a whole plate under every combatant. A theme saved before the default changed keeps the value it was saved with.

**Methods**

`public BattleTheme Clone()`

:   Returns a shallow copy so a view can adjust values without editing the asset.

    - **Returns** &mdash; A new theme object sharing the referenced Unity assets.

`public static BattleTheme Create(BattleLayoutIdentity identity)`

:   Builds a new theme with the layout family's background, panel, accent, and foreground defaults.

    - `identity` &mdash; Layout family to seed.
    - **Returns** &mdash; A new theme with that family's default colors.

`public Color DockBackdrop()`

:   The opaque color the dock panel shows: `Panel` drawn over `Background`. Essential text is measured against it.

    - **Returns** &mdash; The opaque backdrop of the dock text.

`public bool HasWorldStyle()`

:   True when this theme dresses the stage plates or target marks: a plate policy or painted marks.

    - **Returns** &mdash; True when any plate or mark value is set.

`public bool HasWorldTokens()`

:   True when this theme authors anything the world (plates, floating numbers, target preview, backdrop) should follow. Themes without world tokens leave the world on the package default.

    - **Returns** &mdash; True when a world token is set. The default plate mode is not a token, any other value is: a theme that asks for Standard plates still switches the world on.

`public static bool IsSet(Color color)`

:   Whether a token color is authored; alpha zero means unset.

    - `color` &mdash; Token color to test.
    - **Returns** &mdash; True when the alpha is above zero.

`public Color ResolveAllyAccent()`

:   Ally accent, falling back to `Accent`.

    - **Returns** &mdash; The effective color.

`public Color ResolveAllyHealth()`

:   Ally health fill, falling back to `Positive`.

    - **Returns** &mdash; The effective color.

`public Color ResolveAllyText()`

:   Allied text color: `AllyText` when set, otherwise `ResolveAllyAccent`, lightened until it reads on the dock.

    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`.

`public Color ResolveDisabledFill()`

:   Flat fill of an unavailable control: the background, nearly solid, with no accent, no sprite and no frame.

    - **Returns** &mdash; A translucent color at `BattleThemeContrast.DisabledFillAlpha`.

`public Color ResolveDisabledText()`

:   Color of the label of a command row that cannot be used, for want of a target or of what it costs: the foreground at the opacity that reads `BattleThemeContrast.DisabledTextRatio` against the dock.

    - **Returns** &mdash; An opaque color, dimmer than the foreground and readable on the dock.

`public Color ResolveEnemyAccent()`

:   Enemy accent, falling back to `Negative`.

    - **Returns** &mdash; The effective color.

`public Color ResolveEnemyHealth()`

:   Enemy health fill, falling back to `Negative`.

    - **Returns** &mdash; The effective color.

`public Color ResolveEnemyText()`

:   Hostile text color: `EnemyText` when set, otherwise `ResolveEnemyAccent`, lightened until it reads on the dock.

    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`.

`public Color ResolveHairline()`

:   Color of the one-pixel line of a framed box (a list row, a chip, an icon frame) where the art's own hairline is under a pixel: the frame color at the opacity that stands `BattleThemeContrast.HairlineRatio` above the dock panel.

    - **Returns** &mdash; An opaque color.

`public Color ResolveMutedText()`

:   Color of a text that is present but quiet: the foreground at `BattleThemeContrast.MutedAlpha`, kept above the readable floor.

    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`, and visibly dimmer than the foreground.

`public Color ResolveNeutralAccent()`

:   Neutral accent, falling back to `Accent`.

    - **Returns** &mdash; The effective color.

`public Color ResolveNeutralText()`

:   Neutral text color: `ResolveNeutralAccent`, lightened until it reads on the dock.

    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`.

`public Color ResolveResourceEnergy()`

:   Energy resource color, falling back to `Positive`.

    - **Returns** &mdash; The effective color.

`public Color ResolveResourceFocus()`

:   Focus resource color, falling back to `Accent`.

    - **Returns** &mdash; The effective color.

`public Color ResolveResourceText(BattleDockResourceKind kind)`

:   Text color of a resource amount or code: the resource color, lightened until it reads on the dock.

    - `kind` &mdash; Resource family.
    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`.

`public Color ResolveSideText(BattleDockSide side)`

:   Text color of a side: ally, enemy, or neutral for unknown membership.

    - `side` &mdash; Side of the combatant relative to the viewing team.
    - **Returns** &mdash; An opaque color at least 4.5:1 against `DockBackdrop`.

---

## BattleThemeContrast

```csharp
public static class BattleThemeContrast
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleThemeContrast.cs</small>

WCAG contrast arithmetic for the text of the dock, shared by the theme (which derives readable text colors from its tokens), by
both adapters and by the tests, so the number a test measures is the number the views were built to meet.

**Fields**

`public const float DerivedMargin`

:   Extra ratio that a color derived by the theme aims for above `TextMinimum`, so antialiasing, a scale below one and a stage that shows faintly through a translucent panel never push a derived color under the floor.

`public const float DisabledFillAlpha`

:   Opacity of the flat fill behind an unavailable control: nearly solid, so the text on it reads against a known color.

`public const float DisabledTextRatio`

:   Ratio the label of a command that cannot be used aims for on the dock: the foreground taken down until it reads this much. Dimmer than every other label of the list by about a third of its luminance, so the row reads as one that cannot be used without its color, and still above what a thin face drawn small needs to read 4.5:1 on the raster (the quiet text, at `MutedRatio`, reads about 4:1 on a row of that face).

`public const float HairlineRatio`

:   Ratio the one-pixel border of a framed box has against the dock panel, which is what the line of the art measures at 1080p.

`public const float MutedAlpha`

:   Opacity of the foreground of a text that is present but quiet: a defeated member, an unavailable control.

`public const float MutedRatio`

:   Ratio a quiet text aims for. Well above `TextMinimum` on purpose: a thin face drawn small (Cormorant at 18 px through TextMesh Pro) never reaches full coverage on a stroke, and the pixel that the measure of a capture finds brightest carries about 60% of the color, so a quiet label needs about 8:1 on the token to read 4.5:1 on the screen.

`public const float TextMinimum`

:   Lowest contrast ratio of any essential text of the dock against what it is drawn on.

**Methods**

`public static Pair[] DockTextPairs(BattleTheme theme)`

:   Every essential text color of the dock against its backdrop, as the adapters draw them: the foreground on the dock panel and on the darker inset, the quiet foreground, the ally, enemy and neutral text, the cost and resource text, the controls in both of their states and the target line. Each must reach `TextMinimum`.

    - `theme` &mdash; Theme whose tokens are measured.
    - **Returns** &mdash; The pairs, in a stable order.

`public static float Luminance(Color color)`

:   Relative luminance of a color, from zero for black to one for white; alpha is ignored.

    - `color` &mdash; Color to measure.
    - **Returns** &mdash; The WCAG relative luminance.

`public static Color Over(Color top, Color under)`

:   The color a translucent color shows when it is drawn over an opaque one.

    - `top` &mdash; Color drawn on top; its alpha is the share it covers.
    - `under` &mdash; Color underneath; its alpha is ignored.
    - **Returns** &mdash; The opaque result.

`public static float Ratio(Color text, Color backdrop)`

:   Contrast ratio of a text color against its backdrop, from one to twenty-one.

    - `text` &mdash; Text color; when translucent it is first drawn over the backdrop.
    - `backdrop` &mdash; What the text sits on, taken as opaque.
    - **Returns** &mdash; The WCAG contrast ratio.

`public static Color Readable(Color wanted, Color toward, Color backdrop, float minimum)`

:   A color that keeps the hue of `wanted` and reads against a backdrop: the wanted color itself when it already does, otherwise the smallest step toward `toward` that reaches the ratio.

    - `wanted` &mdash; The color the theme asks for.
    - `toward` &mdash; The light color to move toward, normally the theme's foreground.
    - `backdrop` &mdash; What the text sits on.
    - `minimum` &mdash; Ratio to reach.
    - **Returns** &mdash; An opaque color whose ratio against the backdrop is at least the minimum, or `toward` when even that falls short.

`public static Color TintForRatio(Color tint, Color backdrop, float ratio)`

:   The opaque color a tint takes when drawn over a backdrop at the opacity that gives exactly a contrast ratio against that backdrop: the color of a line that must stand a measured step above the panel it is drawn on.

    - `tint` &mdash; The color to dilute.
    - `backdrop` &mdash; What the line is drawn on.
    - `ratio` &mdash; Ratio to reach.
    - **Returns** &mdash; An opaque color; the tint itself when even the full tint falls short.

---

## BattleUiCommandTranslationResult

```csharp
public sealed class BattleUiCommandTranslationResult
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/BattleUiCommandTranslator.cs</small>

Typed result of translating a presentation choice into a command.

**Properties**

`public BattleCommand Command`

:   The translated command on success; null on failure.

`public string Message`

:   Actionable failure detail, or an empty string on success.

`public bool Succeeded`

:   True when a complete command was produced.

---

## BattleUiCommandTranslator

```csharp
public static class BattleUiCommandTranslator
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/BattleUiCommandTranslator.cs</small>

Turns a UI choice into the exact command shape the engine expects. When
the caller supplies no explicit targets for a resolver that requires
them, this asks that skill's registered `ITargetResolver` who is
eligible and takes the lowest stable IDs from the answer, so a project
whose resolver narrows further than its declared contract gets an
auto-pick its own resolver accepts. Explicit target lists are preserved
verbatim, checked against the same resolver, and remain subject to
authoritative engine validation.

**Methods**

`public static BattleUiCommandTranslationResult Translate(BattleUiCommandChoice choice, BattleSnapshot snapshot, CompiledAuthoringCatalog catalog)`

:   Translates a presentation choice against the current authoritative snapshot and compiled command shapes. It returns a failed result for null context, a stale actor, an unavailable skill, or an unsatisfied target contract; normal validation failures do not throw.

    - `choice` &mdash; Player intent to translate.
    - `snapshot` &mdash; Current authoritative state.
    - `catalog` &mdash; Compiled content used by the battle.
    - **Returns** &mdash; A complete command on success or actionable failure detail.

---

## BattleUiTechnology

```csharp
public enum BattleUiTechnology
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattlePresentationProfile.cs</small>

Native UI backend required by a profile's view prefab.

| Value | Meaning |
| --- | --- |
| `UGUI` | Uses Unity's Canvas-based UI. |
| `UIToolkit` | Uses Unity UI Toolkit. |

---

## BattleViewAction

```csharp
public sealed class BattleViewAction
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

A legal action and the candidate IDs supplied by its actual resolver.

**Constructors**

`public BattleViewAction(StableId id, string label, string description, int minimumTargets, int maximumTargets, bool automaticTargets, FrozenList<StableId> candidates = null, FrozenList<BattleViewCost> costs = null, BattleViewTargetScope targetScope = BattleViewTargetScope.Unspecified, FrozenList<BattleViewStatus> appliedStatuses = null, FrozenList<BattleViewEstimate> estimates = null, string summary = "", string unavailableReason = "")`

:   Creates an action projection; candidates are caller supplied view data and are not validated here.

    - `id` &mdash; Stable action identity.
    - `label` &mdash; Display label.
    - `description` &mdash; Display description.
    - `minimumTargets` &mdash; Minimum manually selected targets.
    - `maximumTargets` &mdash; Maximum manually selected targets.
    - `automaticTargets` &mdash; Whether target selection is automatic.
    - `candidates` &mdash; Projected candidate IDs.
    - `costs` &mdash; Structured resource costs; null means none. The description keeps any preformatted cost text for compatibility.
    - `targetScope` &mdash; Player-readable classification of the target rule.
    - `appliedStatuses` &mdash; Statuses the action applies; null means none or unknown.
    - `estimates` &mdash; Estimates the host chose to publish; null means none.
    - `summary` &mdash; Authored one-line description for the action card; empty when the host has none.
    - `unavailableReason` &mdash; Why the action cannot be used right now, in the words the player reads; empty when it can be used. A text marks the action unavailable: the dock lists it dimmed, the card shows the text where the instruction would be and marks nobody, whatever candidates the action carries, and the session does not confirm it.

**Properties**

`public FrozenList<BattleViewStatus> AppliedStatuses`

:   Statuses the action applies; empty when none or unknown.

`public bool AutomaticTargets`

:   Whether targets are selected automatically.

`public FrozenList<StableId> Candidates`

:   Authoritative candidate IDs from the resolver.

`public FrozenList<BattleViewCost> Costs`

:   Structured resource costs; empty when the action is free or the host supplies none.

`public string Description`

:   Display description.

`public FrozenList<BattleViewEstimate> Estimates`

:   Estimates published by the host; empty when none.

`public StableId Id`

:   Stable action identifier.

`public bool IsUnavailable`

:   True when the action is offered but cannot be used right now. The session does not confirm it, whatever was picked, and the dock draws it dimmed and still lets the player choose it, so the card can say why.

`public string Label`

:   Display label.

`public int MaximumTargets`

:   Maximum manual target count.

`public int MinimumTargets`

:   Minimum manual target count.

`public string Summary`

:   Authored one-line description for the action card; empty when the host has none.

`public BattleViewTargetScope TargetScope`

:   Player-readable classification of the target rule.

`public string UnavailableReason`

:   Why the action cannot be used right now, in the words the player reads; empty when it can be used. The projection fills it from the label table (the entry named after the skill with ".unavailable") or, when the author wrote none, with a plain default.

---

## BattleViewBehaviour

```csharp
public abstract class BattleViewBehaviour : MonoBehaviour, IInteractiveBattleView, IBattlePointerBlocker, IBattleStageLayout, IBattleStageInformationLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleViewBehaviour.cs</small>

Unity lifecycle shell. Native adapters share selection and command semantics.

**Properties**

`public virtual BattleHudDesign HudDesign`

:   The HUD design this view draws, read from the structure it is bound to. The base view answers the design its layout family builds by default: the Dock for the Fantasy family, the Classic panel for the Science Fiction family. The native adapters answer from the tree they draw (the dock frame, the Overlay marker), without binding it.

`public virtual bool IsSwappingTheme`

:   True from `BeginThemeSwap` until the HUD is whole again with the new theme, which is the whole length of the swap, fall and rise. Always false in the base view, which has no dip.

`public virtual bool IsWarmingUp`

:   True while this view is still rehearsing a plan it was given (see `BeginWarmUp`). A view with no rehearsal is never warming up, so a host can wait on this without knowing which adapter it holds.

`public bool ManualClock`

:   When true the view no longer reads the engine clock for its own motion (dock tweens): the host feeds it with `AdvanceMotion` instead. Off by default, which keeps the normal unscaled-time behaviour. Captures and tests that need an exact step turn it on.

`public IBattlePortraitSource PortraitSource`

:   Supplies combatant portraits to this view. The host assigns it once per battle; both native adapters read the same source. Null means no portraits, so the view draws its monogram fallback. Assigning a different source refreshes the view.

`public BattlePresentationProfile Profile`

:   Profile last applied through `Configure`.

`public BattleViewSession Session`

:   Session holding selection, navigation, and command state.

`public abstract BattleUiTechnology Technology`

:   UI technology implemented by this concrete view.

`public BattleTheme Theme`

:   Runtime copy of the active theme.

`public virtual float ThemeSwapOpacity`

:   The opacity the HUD is drawn at because of a theme swap, from zero to one: it follows the dip of `BeginThemeSwap` frame by frame, is zero at the frame `Theme` changes, and is one whenever no swap is in course. A host that draws interface of its own around the view (the stage does, in the world) reads it every frame to dip that interface together with the HUD and to change its skin at the same frame. Always one in the base view, which has no dip.

`public bool UseSideInformationBanks`

:   Optional side information layout requested by the applied profile.

`public virtual string WarmUpFault`

:   Why the last rehearsal was given up, or an empty string when none was. A rehearsal is a courtesy to the first action, so a failure never reaches the player: the view stops, takes its copy away and keeps the reason here for whoever measures or tests it.

**Events**

`public event Action<BattleViewCommand> CommandChosen`

:   Raised when the user confirms a battle command.

**Methods**

`public virtual void AdvanceMotion(float seconds)`

:   Advances the view's own motion by an explicit step. The base view has none.

    - `seconds` &mdash; Elapsed seconds, unscaled.

`public virtual void ApplyTheme(BattleTheme theme)`

:   Copies a theme and refreshes the rendered view, at once. A native view also ends a theme swap in course (see `BeginThemeSwap`): the HUD is whole again in the same call and the theme given here is the one the view keeps, not the one the swap was carrying.

    - `theme` &mdash; Theme to copy, or null for defaults.

`public virtual void BeginThemeSwap(BattleTheme theme, float seconds)`

:   Changes the theme with a dip of the opacity of the whole HUD instead of a cut: the old skin fades out over 40% of `seconds`, the theme changes while the HUD is invisible, and the new skin fades in over the remaining 60% with an ease-out. `Theme` keeps the old theme until the HUD is invisible and holds the new one from then on. The base view has no dip and applies the theme at once, exactly as `ApplyTheme` does, so a view that does not know about the dip keeps working. A native view dips when it is active, has been drawn, `seconds` is greater than zero and it has a clock (the view is played, or stepped through `ManualClock`); in any other case it applies the theme at once too. A second call during a swap replaces the theme it carries. If the theme had not changed yet, the swap goes on as it was; if it had, the HUD falls again from the opacity it has, without a jump. Disabling the view, unbinding it, calling `ApplyTheme` or stepping `AdvanceMotion` by more than the whole swap ends it at once, with the HUD whole.

    - `theme` &mdash; Theme to copy, or null for defaults.
    - `seconds` &mdash; Length of the whole swap, fall and rise together. Zero or less applies the theme at once.

`public virtual bool BeginWarmUp(BattleWarmUpPlan plan)`

:   Starts drawing the plan off screen, one step per step of the view's own motion (`AdvanceMotion`), in a copy of the view that nobody sees and that is taken away when the plan ends. It never touches this view's session, state or tree. The base view has no rehearsal.

    - `plan` &mdash; States and intents of a first decision, made from the data of the battle.
    - **Returns** &mdash; True when the view accepted the plan and is now warming up; false when it cannot rehearse or is busy.

`public virtual bool BlocksStagePointer(float screenX, float screenY)`

:   Checks whether this view consumes a stage pointer at the supplied screen coordinate.

    - `screenX` &mdash; Screen-space horizontal coordinate.
    - `screenY` &mdash; Screen-space vertical coordinate.
    - **Returns** &mdash; Always false in the base view; a concrete view overrides this when its UI blocks the stage.

`public abstract void BuildDefaultLayout(BattleLayoutIdentity identity)`

:   Builds the view's default layout for a layout family.

    - `identity` &mdash; Layout family to author.

`public virtual void BuildDefaultLayout(BattleLayoutIdentity identity, BattleHudDesign design)`

:   Builds the view's default layout for a layout family and a HUD design. The base implementation builds the family's own design (the Dock for Fantasy, the Classic panel for Science Fiction) through `BuildDefaultLayout(BattleLayoutIdentity)`, so that pair draws exactly what the one-argument call draws, and throws `NotSupportedException` for any other pair. The native adapters also build the Overlay for either family.

    - `identity` &mdash; Layout family to author.
    - `design` &mdash; HUD design to build.

`public virtual void CancelWarmUp()`

:   Ends a rehearsal in course at once: the copy of the view is destroyed with everything it made and `IsWarmingUp` is false. A host that is about to destroy the view calls it first, because a view that is destroyed in Edit Mode is not told to disable itself. The base view has no rehearsal.

`public virtual void Configure(BattlePresentationProfile profile)`

:   Retains the supplied profile reference and applies a cloned theme. Null profile or theme inputs use defaults; authored theme values and simulation state are not changed.

    - `profile` &mdash; Profile to apply, or null to use default theme values.

`public void ConfigureStageBounds(BattleStageBounds? bounds)`

:   Configures a view's stage reservation without changing combat state. Null retains host framing.

    - `bounds` &mdash; Normalized bottom-left rectangle to reserve, or null to release the reservation.

`public void HandleIntent(BattleViewIntent intent)`

:   Dispatches a user intent through the view session.

    - `intent` &mdash; Input intent to process.

`public virtual bool OwnsPointerSurface(object surface)`

:   Checks whether this view handles the supplied external pointer surface.

    - `surface` &mdash; Host surface object to inspect.
    - **Returns** &mdash; Always false in the base view; a concrete technology adapter overrides this when it owns the surface.

`public virtual void RefreshBindingsIfNeeded()`

:   Editor hosts call this while the simulation is idle to observe native live reload.

`public void Render(BattleViewState state)`

:   Renders a state snapshot without changing simulation state.

    - `state` &mdash; Latest presentation snapshot.

`public bool TryGetStageBounds(out BattleStageBounds bounds)`

:   Returns the authored stage reservation when enabled.

    - `bounds` &mdash; Receives the normalized bottom-left stage rectangle.
    - **Returns** &mdash; True when this view reserves a valid stage rectangle.

`public abstract string[] ValidateBindings()`

:   Reports missing or invalid bindings needed by this view.

    - **Returns** &mdash; Human-readable validation messages; an empty array means valid.

---

## BattleViewCombatant

```csharp
public sealed class BattleViewCombatant
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Immutable, renderer-independent information shown for one combatant.

**Constructors**

`public BattleViewCombatant(StableId id, string name, string team, int health, int maximumHealth, int shield = 0, string resources = "", string statuses = "", StableId teamId = default, int statusCount = 0, FrozenList<BattleViewResource> resourceValues = null, FrozenList<BattleViewStatus> statusEntries = null)`

:   Creates a read-only combatant projection; null display strings become empty.

    - `id` &mdash; Stable combatant identity.
    - `name` &mdash; Display name.
    - `team` &mdash; Display team label.
    - `health` &mdash; Current health units.
    - `maximumHealth` &mdash; Maximum health units.
    - `shield` &mdash; Current shield units.
    - `resources` &mdash; Preformatted resource text.
    - `statuses` &mdash; Preformatted status text.
    - `teamId` &mdash; Stable team identity, or invalid for legacy label-only data.
    - `statusCount` &mdash; Number of statuses represented by the projection.
    - `resourceValues` &mdash; Structured resource pools; null means none. The preformatted `resources` text is kept for compatibility.
    - `statusEntries` &mdash; Structured statuses; null means none. The preformatted `statuses` text is kept for compatibility.

`public BattleViewCombatant(StableId id, string name, string team, int health, int maximumHealth, int shield, string resources, string statuses, StableId teamId, int statusCount, FrozenList<BattleViewResource> resourceValues, FrozenList<BattleViewStatus> statusEntries, FrozenList<StableId> tags)`

:   Creates a read-only combatant projection that also carries the tags of the combatant's definition; null display strings become empty.

    - `id` &mdash; Stable combatant identity.
    - `name` &mdash; Display name.
    - `team` &mdash; Display team label.
    - `health` &mdash; Current health units.
    - `maximumHealth` &mdash; Maximum health units.
    - `shield` &mdash; Current shield units.
    - `resources` &mdash; Preformatted resource text.
    - `statuses` &mdash; Preformatted status text.
    - `teamId` &mdash; Stable team identity, or invalid for legacy label-only data.
    - `statusCount` &mdash; Number of statuses represented by the projection.
    - `resourceValues` &mdash; Structured resource pools; null means none.
    - `statusEntries` &mdash; Structured statuses; null means none.
    - `tags` &mdash; Tags of the combatant's definition, as compiled; null means none. The list is kept as given, not copied.

**Properties**

`public int Health`

:   Current health.

`public StableId Id`

:   Stable combatant identifier.

`public int MaximumHealth`

:   Maximum health.

`public string Name`

:   Display name.

`public FrozenList<BattleViewResource> ResourceValues`

:   Structured resource pools (id, label, value, maximum); empty for legacy data. `Resources` remains the preformatted summary.

`public string Resources`

:   Preformatted resource summary.

`public int Shield`

:   Current shield.

`public int StatusCount`

:   Number of statuses represented by this projection.

`public FrozenList<BattleViewStatus> StatusEntries`

:   Structured statuses (id, label, stacks); empty for legacy data. `Statuses` remains the preformatted summary.

`public string Statuses`

:   Preformatted status summary.

`public FrozenList<StableId> Tags`

:   Tags of the combatant's definition, as compiled; empty for legacy data and for a projection made with the constructor without tags. Presentation reads them (the affinities a caption names); no built-in rule of the simulation does.

`public string Team`

:   Display team label.

`public StableId TeamId`

:   Stable team identity; invalid means legacy display data.

---

## BattleViewCommand

```csharp
public readonly struct BattleViewCommand
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Immutable command choice forwarded for authoritative validation.

**Constructors**

`public BattleViewCommand(StableId actorId, StableId? skillId, bool isConcede, FrozenList<StableId> targets = null)`

:   Packages actor, skill, concession, and requested targets for host validation; it performs no command legality checks.

    - `actorId` &mdash; Actor whose decision is represented.
    - `skillId` &mdash; Selected skill, or null for concession.
    - `isConcede` &mdash; Whether this is a concession request.
    - `targets` &mdash; Requested target IDs.

**Properties**

`public StableId ActorId`

:   Actor for whom the choice was made.

`public bool IsConcede`

:   Whether this requests concession.

`public StableId? SkillId`

:   Selected skill, or null for concession.

`public FrozenList<StableId> Targets`

:   Requested target IDs.

---

## BattleViewIntent

```csharp
public readonly struct BattleViewIntent
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

A UI gesture; the host still validates the resulting command.

**Constructors**

`public BattleViewIntent(BattleViewIntentKind kind, StableId id = default)`

:   Creates an intent with an optional action or target ID.

    - `kind` &mdash; Interaction requested by the view.
    - `id` &mdash; Action or target identity, when applicable.

**Properties**

`public StableId Id`

:   Action or target identifier.

`public BattleViewIntentKind Kind`

:   Requested interaction kind.

---

## BattleViewIntentKind

```csharp
public enum BattleViewIntentKind
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Interaction intents understood by a battle view session.

| Value | Meaning |
| --- | --- |
| `SelectAction` | Requests that the session select an available skill and clear its current targets. |
| `SelectTarget` | Toggles an eligible target. |
| `Confirm` | Publishes the current selection. |
| `Cancel` | Clears the current selection. |
| `Concede` | Publishes a concession request. |

---

## BattleViewProjection

```csharp
public static class BattleViewProjection
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/BattleViewProjection.cs</small>

The single snapshot-to-UI projection for every native or customer renderer.

**Methods**

`public static BattleViewState Create(BattleSnapshot snapshot, CompiledAuthoringCatalog catalog, DisplayStringTable labels = null, IEnumerable<string> feedback = null, StableId? rosterTeamId = null, StableId? executingActor = null, StableId? executingAction = null, IReadOnlyList<StableId> executingTargets = null)`

:   Projects a battle snapshot and compiled content into read-only HUD rows, available actions, target candidates, timeline labels and a terminal result. Does not submit commands or advance the simulation.

    - `snapshot` &mdash; Authoritative snapshot to present. Null returns the empty view state.
    - `catalog` &mdash; Compiled content used for decision shapes, costs and target candidates. Null returns the empty view state.
    - `labels` &mdash; Optional display-name table; missing names fall back to stable identities.
    - `feedback` &mdash; Optional feedback lines copied into the resulting presentation state.
    - `rosterTeamId` &mdash; Optional viewing-team identity. When omitted, uses the first human-controlled combatant's team, or the first snapshot team for an automatic-only battle; never the current decision actor.
    - `executingActor` &mdash; Combatant whose action the stage is playing, when the host tracks it; reported only while no decision is pending. When nobody's action is played and the next thing the engine does is a cast landing, the projection reports that cast instead.
    - `executingAction` &mdash; Action being played; both this and `executingActor` are needed.
    - `executingTargets` &mdash; Combatants the action has reached so far.
    - **Returns** &mdash; A presentation state with a decision key derived from command sequence and actor identity, or the empty state when required input is absent.

---

## BattleViewRoster

```csharp
public static class BattleViewRoster
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewRoster.cs</small>

Pure grouping helpers for immutable presentation rosters.

**Methods**

`public static FrozenList<FrozenList<BattleViewCombatant>> BuildPages(FrozenList<BattleViewCombatant> combatants, int capacity)`

:   Builds pages containing one team each; teams follow first occurrence and members keep input order.

    - `combatants` &mdash; Source projections; a null source or null entries produces no members.
    - `capacity` &mdash; Positive maximum members per page.
    - **Returns** &mdash; Frozen pages of combatant projections.

`public static int FindActorPage(FrozenList<FrozenList<BattleViewCombatant>> pages, StableId? actorId)`

:   Finds the page containing an actor by exact stable ID, or returns the first page.

    - `pages` &mdash; Roster pages produced by `BuildPages`.
    - `actorId` &mdash; Current decision actor, when one is available.
    - **Returns** &mdash; The zero-based page containing the actor, or zero when no exact match exists.

`public static FrozenList<BattleViewCombatant> ForTeam(BattleViewState state, StableId teamId)`

:   Returns every member with the exact team ID, including defeated members.

    - `state` &mdash; State supplying the roster; null produces an empty result.
    - `teamId` &mdash; Valid stable team identity.
    - **Returns** &mdash; Matching members in source order.

---

## BattleViewSession

```csharp
public sealed class BattleViewSession
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewSession.cs</small>

Shared interaction state survives visual tree reconstruction. Never owns an engine.

**Constructors**

`public BattleViewSession()`

:   Creates an empty selection session; it owns presentation state only.

**Properties**

`public bool CanConfirm`

:   Whether the current selection satisfies local UI constraints. An action the state marks unavailable never does.

`public string Error`

:   Latest host rejection or local selection error.

`public bool IsSubmissionPending`

:   Remains pending until the host rejects or publishes a different decision.

`public BattleViewAction SelectedAction`

:   Currently selected available action, or null.

`public IReadOnlyList<StableId> SelectedTargets`

:   Currently selected eligible targets.

`public BattleViewState State`

:   Current immutable host-provided view state.

**Events**

`public event Action Changed`

:   Raised after state or selection changes.

`public event Action<BattleViewCommand> CommandChosen`

:   Raised when a validated UI selection is published to the host.

**Methods**

`public void Dispatch(BattleViewIntent intent)`

:   Processes an intent locally and forwards only a choice; the host remains authoritative.

    - `intent` &mdash; Interaction to apply to the current selection.

`public void Reject(string error)`

:   Clears the pending submission and records a host rejection.

    - `error` &mdash; Host-provided rejection text; null becomes empty.

`public void UpdateState(BattleViewState state)`

:   Replaces host state and prunes selections no longer available.

    - `state` &mdash; New host snapshot; null selects `BattleViewState.Empty`.

---

## BattleViewState

```csharp
public sealed class BattleViewState
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

A complete read-only view; contains no scene objects or authority to change combat.

**Constructors**

`public BattleViewState(string decisionKey, string heading, StableId? actorId, bool canConcede, FrozenList<BattleViewCombatant> combatants = null, FrozenList<BattleViewAction> actions = null, FrozenList<string> timeline = null, FrozenList<string> feedback = null, string resultText = "", StableId? rosterTeamId = null, FrozenList<BattleViewTimelineEntry> timelineEntries = null, BattleViewExecution execution = null)`

:   Creates an immutable renderer-independent decision snapshot.

    - `decisionKey` &mdash; Host decision identity.
    - `heading` &mdash; Display heading.
    - `actorId` &mdash; Deciding actor, when any.
    - `canConcede` &mdash; Whether concession is offered.
    - `combatants` &mdash; Combatant projections.
    - `actions` &mdash; Available action projections.
    - `timeline` &mdash; Timeline text entries.
    - `feedback` &mdash; Feedback text entries.
    - `resultText` &mdash; Terminal result text.
    - `rosterTeamId` &mdash; Optional valid team identity for roster scoping.
    - `execution` &mdash; Optional description of the action being played while no decision is pending.
    - `timelineEntries` &mdash; Structured turn-order entries. When null they are derived from `timeline` with invalid ids and the first entry marked next; when supplied without `timeline`, the name list is derived from them.

**Properties**

`public FrozenList<BattleViewAction> Actions`

:   Actions currently available to the actor.

`public StableId? ActorId`

:   Actor currently expected to decide, when any.

`public bool CanConcede`

:   Whether concession is currently offered.

`public FrozenList<BattleViewCombatant> Combatants`

:   Read-only combatant projections.

`public string DecisionKey`

:   Host decision identity used to retain or reset selection.

`public BattleViewExecution Execution`

:   The action the stage is playing while no decision is pending, or null when the host does not report one.

`public FrozenList<string> Feedback`

:   Presentation feedback entries.

`public string Heading`

:   Display heading.

`public string ResultText`

:   Terminal result text, when the battle has ended.

`public StableId? RosterTeamId`

:   Optional valid stable team identity for a scoped roster.

`public FrozenList<string> Timeline`

:   Presentation timeline entries as display names, kept for compatibility. `TimelineEntries` carries ids and the next-actor flag.

`public FrozenList<BattleViewTimelineEntry> TimelineEntries`

:   Structured turn-order entries (combatant id, name, team id, next-actor flag), in turn order.

**Fields**

`public static readonly BattleViewState Empty`

:   Empty state used before the first host update.

---

## BattleWarmUp

```csharp
public enum BattleWarmUp
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleWarmUp.cs</small>

What a battle rehearses while it loads, so that the first action of the player does not pay for the first use of the code behind
it. A Mono player compiles each method the first time it runs, the engine's own UI and text code included, so the first command of
a battle used to take longer than the next one. Only running the same path at load removes that cost; warming
glyphs or shaders alone does not. Each layer is a flag, so a measurement can tell which one earned what, and a project can keep the
ones that pay on the platforms it ships to.

Nothing here changes the battle. The rehearsal plays on a copy of the engine, draws in views and canvases that are never on the
screen, and takes all of it away when it is done.

| Value | Meaning |
| --- | --- |
| `None` | Nothing is rehearsed, and the first action pays for the first use of its code. |
| `Dock` | The interface adapter draws, off screen and one state per frame, the decision the first action will go through: the choice of an action, of its targets, the confirmed command, the ... |
| `WorldText` | The presenter draws once, far from the stage, every text the stage writes in the world: the whole plate (name, value, bars), the floating numbers of every style, a critical one and... |
| `Rehearsal` | The code of the decision runs on a shadow copy of the battle: a second engine from the same content and seed is taken to its first human decision, projected, driven through the sel... |
| `All` | Every layer: what a new profile asks for. |

---

## BattleWarmUpCurtain

```csharp
public sealed class BattleWarmUpCurtain : MonoBehaviour
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleWarmUpCurtain.cs</small>

Keeps the first frames of a battle off the screen. While the warm-up of the battle runs
(`BattleRuntimeController.IsWarmingUp`) the curtain covers the whole screen, the stage and the dock together, and when
the warm-up ends it lifts with a fade of `FadeSeconds`. Those first frames are the ones that pay for the code of the
battle running for the first time, so they are the ones that can hitch; with the curtain down, the player sees none of the frames
that follow the one the battle starts in.

The frame the battle starts in is another matter. The curtain falls when the controller says the battle started, inside the call
to `BattleRuntimeController.StartBattle()`, and is first drawn at the end of that frame; the frame itself is the
longest of all, since the views and the stage are built in it, and while it runs the screen goes on showing what was drawn
before it. A host that has nothing of its own over the screen calls `Lower` a frame before it starts the battle, so
that it is the curtain that stands there. That is for a controller the host starts itself: one left on Auto Start starts its
battle in its own first frame, before the host has lowered anything.

Put one on the object of the `BattleRuntimeController` (the Add Component menu, or `AddTo`) before the
battle starts. It draws one full-screen image on a canvas of its own that sits over every other canvas and takes no pointer, so it
touches neither the dock nor the stage: a theme swap, or a view made again, in the middle of the fade changes nothing about it,
and when the fade ends no part of the screen is left at a partial opacity. The canvas is made the first time it is needed, so a
battle that asks for no warm-up pays nothing for the curtain.

It covers only what it should. It stays clear when the profile asks for no warm-up, when the controller has already warmed up the
look of the battle, and, by default, when the controller does not advance the battle by itself
(`BattleRuntimeController.AutoAdvance` is false): such a host decides when the action plays, steps the presentation
when it chooses, and may never step it at all, so a curtain kept down for it could stay down. If the warm-up is still running
after `MaximumCoverSeconds` the curtain lifts anyway. Reduce Motion does not change it: a fade is not motion, and the
player who asked for less of it still gets the fade, not a cut.

The curtain follows the clock of the controller. In a game it steps itself once a frame on unscaled time; when the controller is on
`BattleRuntimeController.ManualClock` it is stepped by `BattleRuntimeController.AdvancePresentation`, with
the stage and the dock, so a test or a recording that steps the presentation by hand steps the fade as well. It allocates nothing
in a frame (the canvas is made once, the first time it is needed), and the first decision of the player is never delayed by it:
the controller holds a command given while the warm-up runs and plays it when the warm-up ends, whatever the curtain is doing.

On a UI Toolkit dock, the panel and the curtain are sorted against each other by their sort orders: give the curtain a
`SortingOrder` above the one of the panel settings of the dock.

**Properties**

`public BattleRuntimeController Controller`

:   The controller whose warm-up the curtain follows. Assigning it makes the curtain follow that controller from now on. When none was assigned, the curtain follows the controller on its own object, or on a parent, once it is enabled.

`public Color CurtainColor`

:   Colour of the curtain; black by default. Its alpha is the opacity of the curtain when it is all the way down.

`public float FadeSeconds`

:   Seconds the curtain takes to go from all the way down to gone, once the warm-up has ended. From 0 (it lifts at once) to 1; a new curtain has `DefaultFadeSeconds`. Reduce Motion does not shorten it.

`public bool IsCovering`

:   True while the curtain is held down: because the warm-up runs, from the start of the battle to the end of the warm-up, or because it was lowered with `Lower` and the battle has not started yet (in either case, no longer than `MaximumCoverSeconds`). It is false during the fade: `Opacity` says where the fade is.

`public bool IsLowered`

:   True from a call to `Lower` that lowered the curtain until the next battle starts or `Raise` is called.

`public float MaximumCoverSeconds`

:   Longest time, in seconds of the curtain's own clock, that it stays down while the warm-up still runs. Past it the curtain lifts although `BattleRuntimeController.IsWarmingUp` is still true; the warm-up goes on, and the battle is seen as it is. Zero or less is no limit. A new curtain has `DefaultMaximumCoverSeconds`.

`public float Opacity`

:   How much of the screen the curtain covers now, from 0 (nothing is drawn) to 1 (all of it, at the opacity of `CurtainColor`).

`public bool RequiresAutoAdvance`

:   True (the default) when the curtain covers only a controller that advances the battle by itself (`BattleRuntimeController.AutoAdvance`), the same host whose first command the controller holds while the warm-up runs. False covers a controller that is advanced by hand too; do it only when that host steps the presentation every frame (`Update` does, or `BattleRuntimeController.AdvancePresentation`), because the warm-up ends as the presentation is stepped and a host that never steps it would never have the curtain lifted but by `MaximumCoverSeconds`.

`public int SortingOrder`

:   Sorting order of the canvas the curtain draws on, `DefaultSortingOrder` by default. A UI Toolkit dock draws in a panel whose sort order is compared with it: the curtain covers the dock only if its order is the higher one.

**Fields**

`public const float DefaultFadeSeconds`

:   Length of the fade, in seconds, that a new curtain has.

`public const float DefaultMaximumCoverSeconds`

:   Longest time, in seconds, that a new curtain stays down while the warm-up still runs.

`public const int DefaultSortingOrder`

:   Sorting order of the canvas of a new curtain: above the canvases a battle interface draws.

`public const string SurfaceName`

:   Name of the object the curtain draws on, under the object that holds the component.

**Methods**

`public static BattleWarmUpCurtain AddTo(BattleRuntimeController controller)`

:   Adds a curtain to the object of `controller` and makes it follow that controller, or returns the one that is already there. Call it before the battle starts: a battle that is already warming up when the curtain is added is covered from then on.

    - `controller` &mdash; The controller whose warm-up is to be covered.
    - **Returns** &mdash; The curtain on the object of the controller.

`public void Advance(float seconds)`

:   Moves the curtain by an explicit step: it takes in whether the warm-up runs now, falls at once if it does, and otherwise lifts by `seconds` of the fade. `BattleRuntimeController.AdvancePresentation` calls it with the step it is given, so a host on `BattleRuntimeController.ManualClock` that steps the presentation steps the curtain too and needs nothing else; call it yourself only when you step the curtain without the controller.

    - `seconds` &mdash; Elapsed seconds, unscaled; zero or less moves nothing but takes in a change of the warm-up.

`public bool Lower()`

:   Lowers the curtain now, before the battle starts, and holds it down until the battle that starts next has warmed up. Use it when nothing of the host covers the screen: the frame in which `BattleRuntimeController.StartBattle()` is called builds the views and the stage and is by far the longest, and the screen shows what was drawn before it for as long as it takes. Lower the curtain, let one frame be drawn, then start the battle: ` controller.ConfigureBattle(catalog, encounterId, seed); // it also turns Auto Start off: the battle starts when you say var curtain = BattleWarmUpCurtain.AddTo(controller); curtain.Lower(); yield return null; // the curtain is drawn if (!controller.StartBattle().Succeeded) curtain.Raise(); ` The controller must not be on Auto Start (its default in the Inspector; `ConfigureBattle` turns it off): such a controller starts the battle by itself in its first frame, before these lines have lowered anything, so that frame is not covered, and the call to `StartBattle` then starts the battle a second time. The fall is a cut, as it is when the battle starts. When the battle starts the curtain goes on as if it had fallen then: it stays down while the warm-up runs, with its whole `MaximumCoverSeconds`, and lifts with the fade; when that battle asks for no warm-up it lifts with the fade at once. Called while a warm-up is already running, it holds nothing: the curtain is down for that warm-up and lifts when it ends, as if `Lower` had not been called. A curtain that is lowered and never sees a battle start lifts after `MaximumCoverSeconds` of its own clock. That clock does not run for a curtain with no longest cover (zero), nor for one whose controller is on `BattleRuntimeController.ManualClock` and is not stepped: call `Raise` there when the battle does not start.

    - **Returns** &mdash; True when the curtain is down. False, with nothing changed, when it would not cover the battle either: it is disabled, it follows no controller, or the controller is advanced by hand and `RequiresAutoAdvance` is true.

`public void Raise()`

:   Lets go of a curtain lowered with `Lower` when the battle did not start after all: it lifts with the fade. It does nothing to a curtain that is down because a warm-up runs.

---

## BattleWarmUpPlan

```csharp
public sealed class BattleWarmUpPlan
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleWarmUpPlan.cs</small>

The script of a rehearsal: states and intents in the order a first decision goes through them, made from the real data of the
encounter by the host. A view plays one step per step of its own clock, so the panel or the canvas draws between steps. The plan
is data only and owns nothing; a view never changes it.

**Constructors**

`public BattleWarmUpPlan(IEnumerable<BattleWarmUpStep> plannedSteps)`

:   Makes a plan from its steps, in order.

    - `plannedSteps` &mdash; Steps to play; null makes an empty plan.

**Properties**

`public int Count`

:   How many steps the plan has.

---

## BattleWarmUpReport

```csharp
public sealed class BattleWarmUpReport
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeController.WarmUp.cs</small>

What the warm-up of a battle did, for a host that measures it or waits on it. It is a snapshot: it does not change after it was
read, and a new one is made by each read of `BattleRuntimeController.WarmUpReport`.

**Properties**

`public string Fault`

:   What went wrong in any layer, one reason after another; empty when nothing did.

`public bool Finished`

:   True when no layer is working any more (also true when nothing was asked for).

`public bool InterfaceStarted`

:   True when the interface accepted the script and rehearsed it.

`public int RehearsalEvents`

:   Events the shadow engine produced.

`public int RehearsalSteps`

:   Steps (states and intents) of the script the interface was given.

`public int RehearsedFlows`

:   Commands, of different shapes, the shadow engine accepted.

`public BattleWarmUp Requested`

:   The layers the profile asked for (`BattleWarmUp.None` when it asked for nothing).

`public bool WorldTextStarted`

:   True when the presenter drew the text of the world.

---

## BattleWarmUpStep

```csharp
public readonly struct BattleWarmUpStep
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleWarmUpPlan.cs</small>

One thing a view is asked to do while it rehearses a decision off screen: show a state, or take a user intent as the player would.

**Properties**

`public BattleViewIntent Intent`

:   The intent to dispatch; meaningful only when `IsIntent` is true.

`public bool IsIntent`

:   True when this step is an intent and not a state.

`public BattleViewState State`

:   The state to render, or null when this step is an intent.

**Methods**

`public static BattleWarmUpStep Do(BattleViewIntent intent)`

:   Makes a step that hands `intent` to the rehearsing view, as a click or a key would.

    - `intent` &mdash; Intent to dispatch through the view's own session.
    - **Returns** &mdash; The step.

`public static BattleWarmUpStep Show(BattleViewState state)`

:   Makes a step that shows `state` as the host would render it.

    - `state` &mdash; State to render; null is treated as the empty state.
    - **Returns** &mdash; The step.

---

## CustomMechanicsRegistryProvider

```csharp
public sealed class CustomMechanicsRegistryProvider : BattleRegistryProvider
```

`TurnHerald.Samples.CustomMechanics` &middot; <small>Samples/CustomMechanics/CustomMechanicsRegistryProvider.cs</small>

Adds the sample shield effect and lowest-health ally target resolver to
the built-in registry set used by authored battles and replay.

---

## CustomShieldEffectResolver

```csharp
public sealed class CustomShieldEffectResolver : IEffectResolver
```

`TurnHerald.Samples.CustomMechanics` &middot; <small>Samples/CustomMechanics/CustomShieldEffectResolver.cs</small>

Creates a shield equal to a configured fraction of missing health.

**Properties**

`public int ContractVersion`

:   Gets the contract version implemented by this resolver.

`public int EffectContractVersion`

:   Gets the effect registry contract version implemented by this resolver.

`public StableId ImplementationId`

:   Gets the stable implementation id used for compatibility checks.

`public StableId ResolverId`

:   Gets the resolver's stable registry id.

**Fields**

`public static readonly StableId Id`

:   Stable registry id for this effect resolver.

`public static readonly StableId PriorityKey`

:   Property key for the shield priority.

`public static readonly StableId RatioKey`

:   Property key for the missing-health fraction to convert into shield.

`public static readonly StableId ShieldKey`

:   Property key for the shield identity to apply.

**Methods**

`public static long CalculateShieldRaw(int missingHealth, Fixed64 ratio)`

:   Calculates the fixed-point shield amount from missing health and a ratio.

    - `missingHealth` &mdash; Positive amount of health missing from the target.
    - `ratio` &mdash; Fixed-point fraction applied to the missing health.
    - **Returns** &mdash; The raw fixed-point shield amount, or zero for non-positive inputs.

`public EffectPlan Plan(EffectPlanningContext context, PropertySet properties)`

:   Plans a shield primitive equal to the target's missing health times the configured ratio.

    - `context` &mdash; Planning context containing the target snapshot and content.
    - `properties` &mdash; Validated effect properties controlling shield id, ratio, and priority.
    - **Returns** &mdash; An effect plan, empty when no shield is needed or validation fails.

`public ValidationReport Validate(EffectValidationContext context, PropertySet properties)`

:   Validates the three required property values and their ranges.

    - `context` &mdash; Content context used to validate the effect.
    - `properties` &mdash; Effect properties, requiring ratio, shield id, and priority.
    - **Returns** &mdash; A valid report or a diagnostic identifying the first contract violation.

---

## DemoIdleSheet

```csharp
public static class DemoIdleSheet
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Demo/DemoIdleSheet.cs</small>

Reads the sample character art, which ships as a grid of idle frames rather than
as a single still so combatants breathe instead of standing frozen.

Everything that dresses a combatant goes through here, because the bound sprite
covers the whole grid: handing it to a token unsliced would put thirty tiny
characters on one formation slot. Art that is not the authored grid - the token
gems, or a buyer's own drawing - is passed through untouched.

Cells are the full authored canvas, so every frame keeps the (0.5, 0) ground-line
pivot and the importer's pixels-per-unit and a combatant neither drifts nor
resizes as it plays.

It holds nothing. An earlier version memoized the sliced frames in a static
dictionary keyed by texture, which is two faults at once: the presentation
assembly forbids static state that can retain a UnityEngine.Object, and the
entries outlived the textures they were keyed on, so every domain reload left
a table of destroyed keys pointing at sprites nothing would ever free. Callers
keep the frames they asked for; the shipped demo already did.

It also lives outside the demo-driver namespace deliberately. That namespace
is exempt from the purity rules because the driver owns a battle engine by
specification, and a sprite utility has no business inheriting an exemption
written for something else - particularly one the layout audit and the
documentation capture both call.

**Fields**

`public const int Columns`

:   Columns in the authored grid.

`public const float FaceCoreShare`

:   Half of the width of the face core, as a fraction of the portrait crop width, on each side of the crop centre.

`public const float FramesPerSecond`

:   Frames per second the grid is authored to play at.

`public const int Rows`

:   Rows in the authored grid.

`public const string TextureNamePrefix`

:   Only art named like the shipped characters is treated as a grid.

**Methods**

`public static bool ConfigureSampleGround(CombatantTokenView token)`

:   Authors a stable foot anchor for the six shipped idle grids without cropping their art. Their full cells include transparent padding below the feet; renderer bounds alone would place shadows and targeting there. Custom art is left untouched and can author its own ground anchor.

    - `token` &mdash; Sample token whose root renderer wears a sliced idle frame.
    - **Returns** &mdash; True when a known sample frame supplied a configured foot anchor.

`public static void DressSampleCombatant(BattlePresenter presenter, StableId combatantId, string definitionId, Sprite restingFrame)`

:   Dresses one combatant with a shipped sample illustration: body art on the stage token, the same frame as its portrait with the authored head crop, and the foot anchor. A character that is not a shipped sample keeps the default bust window.

    - `presenter` &mdash; Presenter that owns the stage tokens; null does nothing.
    - `combatantId` &mdash; Combatant to dress.
    - `definitionId` &mdash; Definition identity or texture name used to find the crop.
    - `restingFrame` &mdash; Resting frame returned by `RestingFrame`.

`public static Sprite RestingFrame(Sprite source)`

:   The frame a combatant rests on: frame zero of the grid, or the sprite itself when it is a plain still. This is what everything that only needs one image - the turn-order rail, a documentation screenshot, a layout measurement - should be given, so a measurement never reads the whole sheet as one combatant.

`public static Sprite[] Slice(Sprite source)`

:   The frames of `source`'s grid, or null when the art is a plain still and should be used exactly as authored.

`public static bool TryGetSamplePortraitCrop(string definitionId, out UiPortraitCrop crop)`

:   The head-and-shoulders window of a shipped sample character, relative to its resting frame, with the origin at the bottom left, inset two pixels from the kit measurement so every window lies strictly inside the frame. The turn ribbon and the party panel of the native views draw their round portraits from it, so a medallion shows a face rather than the middle of a body.

    - `definitionId` &mdash; Combatant definition identity such as `combatant.vanguard`, or a character texture name such as `character-vanguard`.
    - `crop` &mdash; Receives the crop; the unconfigured default when the character is not a shipped sample.
    - **Returns** &mdash; True when the sample character has an authored crop.

---

## DisplayStringTableAsset

```csharp
public sealed class DisplayStringTableAsset : DisplayStringTableProvider
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/DisplayStringTableAsset.cs</small>

The shipped serialized string-table asset the demo driver supplies to the
presenter (specification section 3: display text comes from an explicit
table, never from compiled snapshots, which exclude labels from every
hash). Entries map a stable id to a human display name; the asset is
authored by the Internal presentation-content generator and consumed by
`TurnHeraldDemoBootstrap` through `Build`. It is
non-authoritative data and never enters any battle hash.

**Properties**

`public IReadOnlyList<Entry> Entries`

:   The authored entries in serialized order.

**Methods**

`public override DisplayStringTable Build()`

:   Builds the runtime `DisplayStringTable`. Null entries and invalid ids are skipped defensively. A null label is stored as an empty string; lookups for missing ids fall back to the raw id text inside the table itself.

---

## Entry

```csharp
public sealed class Entry
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/DisplayStringTableAsset.cs</small>

Nested in `TurnHerald.Presentation.Demo.DisplayStringTableAsset`.

One stable-id-to-display-name pair.

**Fields**

`public string Id`

:   Stable id parsed into the table when this entry is valid.

`public string Label`

:   Display text stored for the parsed id; a null value becomes an empty string.

---

## ForecastRequest

```csharp
public sealed class ForecastRequest
```

`TurnHerald.Simulation` &middot; <small>Runtime/Simulation/Forecast/BattleForecast.cs</small>

The three caps that bound one `BattleForecast.Run` call: how
far ahead it may look, and how much work and evidence it may collect
before stopping. The constructor accepts any values; out-of-range caps
are reported by `BattleForecast.Run` as
`ForecastStopReason.FatalInvariant` rather than thrown.

**Constructors**

`public ForecastRequest(int maximumTickDelta, int maximumActions, int maximumEvents)`

:   Creates a forecast bound. All three caps are checked at `BattleForecast.Run` time, not here.

    - `maximumTickDelta` &mdash; Ticks to look ahead of the source engine's current tick, not an absolute tick. Valid range is 0 to `SimulationLimits.ForecastTickDelta`.
    - `maximumActions` &mdash; The most action-terminal events the forecast may pass through. Valid range is 1 to `SimulationLimits.ForecastActions`.
    - `maximumEvents` &mdash; The most events the forecast may collect. Valid range is 1 to `SimulationLimits.ForecastEvents`.

**Properties**

`public int MaximumActions`

:   The cap on `ForecastResult.CompletedActions`: how many action-terminal events the forecast may pass through before it stops with `ForecastStopReason.ActionLimit`.

`public int MaximumEvents`

:   The cap on `ForecastResult.Events` before the forecast stops with `ForecastStopReason.EventLimit`.

`public int MaximumTickDelta`

:   Ticks ahead of the source engine's current tick, not an absolute tick. The forecast derives its absolute horizon by adding this to the source tick.

---

## ForecastResult

```csharp
public sealed class ForecastResult
```

`TurnHerald.Simulation` &middot; <small>Runtime/Simulation/Forecast/BattleForecast.cs</small>

Immutable outcome of one `BattleForecast.Run` call: where the
lookahead stopped, the state and events of the throwaway clone it ran,
and the non-authoritative evidence it produced. Only
`BattleForecast` creates it, and holding it has no effect on
the engine it was forecast from.

**Properties**

`public FrozenList<AiDecisionTrace> AiDecisionTraces`

:   Non-authoritative AI decision evidence from the automatic decisions the clone took. It is outside canonical battle state and hashes.

`public int CompletedActions`

:   How many action-terminal events (action completed, interrupted, or skipped) appear in `Events`, which is the count compared against `ForecastRequest.MaximumActions`.

`public Diagnostic? Diagnostic`

:   The typed reason a cap or invariant ended the run. Set only for `ForecastStopReason.ActionLimit`, `ForecastStopReason.EventLimit`, and `ForecastStopReason.FatalInvariant`; null otherwise.

`public FrozenList<BattleEvent> Events`

:   The events the clone emitted, in emission order. They belong to the forecast alone and are not part of the source engine's event chain.

`public FrozenList<FormulaAttributionTrace> FormulaAttributionTraces`

:   Shorthand for `FormulaAttributions.Traces`.

`public FormulaAttributionTraceBatch FormulaAttributions`

:   Non-authoritative formula evidence produced by the clone, likewise outside canonical battle state and hashes.

`public long OmittedFormulaAttributionTraceCount`

:   Shorthand for `FormulaAttributions.OmittedCount`: how many formula traces were produced but dropped to stay inside the documented result-memory bound.

`public long RequestedHorizonTick`

:   The absolute tick the forecast was asked to reach: the source tick plus `ForecastRequest.MaximumTickDelta`. It records the request, not the outcome; only `ForecastStopReason.HorizonReached` means it was reached. When the request itself was rejected this is the source tick.

`public BattleSnapshot Snapshot`

:   State of the throwaway clone where the lookahead stopped. The source engine's own snapshot, hashes, RNG, and history are unchanged, so this is a prediction and never the authoritative battle state.

`public ForecastStopReason StopReason`

:   Why the lookahead stopped, and the first thing to branch on. Only `ForecastStopReason.HorizonReached` means the whole requested window was covered, and only `ForecastStopReason.Terminal` means the battle itself ended inside it; every other value leaves the rest of the window unknown rather than empty.

---

## ForecastStopReason

```csharp
public enum ForecastStopReason : byte
```

`TurnHerald.Simulation` &middot; <small>Runtime/Simulation/Forecast/BattleForecast.cs</small>

Why one `BattleForecast.Run` call stopped. Caps are
evaluated only at complete emitted boundaries, so a forecast never stops
part-way through an event.

| Value | Meaning |
| --- | --- |
| `HorizonReached` | The forecast reached `ForecastResult.RequestedHorizonTick` with no earlier stop. |
| `UnknownHumanDecision` | The next decision belongs to a human-controlled actor, so the forecast stopped instead of inventing a command. |
| `Terminal` | A terminal battle result was reached, or the source was already terminal. |
| `NoScheduledWork` | The forecast ran out of scheduled work before the horizon without reaching a terminal result. |
| `ActionLimit` | `ForecastRequest.MaximumActions` was reached. |
| `EventLimit` | `ForecastRequest.MaximumEvents` was reached. |
| `FatalInvariant` | The request was null or out of range, the horizon would overflow, or a step failed. |

---

## GeneratedUiText

```csharp
public sealed class GeneratedUiText : MonoBehaviour
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUGUI/GeneratedUiText.cs</small>

Marks adapter-owned text that participates in presentation themes.

!!! note "Remarks"
    Remove this marker to keep a label's authored font and size.

---

## IBattleFeedbackLayout

```csharp
public interface IBattleFeedbackLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Optional presentation-only reservation for feedback that must stay clear
of the stage and its other information bands.

**Methods**

`public bool TryGetFeedbackBounds(out BattleStageBounds bounds)`

:   Returns the normalized rectangle reserved for feedback.

    - `bounds` &mdash; Receives the reserved rectangle when available.
    - **Returns** &mdash; True when a valid reservation is available.

---

## IBattlePointerBlocker

```csharp
public interface IBattlePointerBlocker
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Optional screen-space hit-test owned by a view.

**Methods**

`public bool BlocksStagePointer(float screenX, float screenY)`

:   Returns whether the view blocks a stage pointer at the coordinates.

    - `screenX` &mdash; Screen-space horizontal coordinate.
    - `screenY` &mdash; Screen-space vertical coordinate.
    - **Returns** &mdash; True when the view owns an opaque hit area at those coordinates.

`public bool OwnsPointerSurface(object surface)`

:   Returns whether the supplied surface belongs to this view.

    - `surface` &mdash; Renderer-specific input-surface identity.
    - **Returns** &mdash; True when the surface belongs to this view.

---

## IBattleStageInformationLayout

```csharp
public interface IBattleStageInformationLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Optional presentation-only choice to group combatant information beside the action stage.

**Properties**

`public bool UseSideInformationBanks`

:   True when the view requests side information banks. This does not change formation or simulation coordinates.

---

## IBattleStageLayout

```csharp
public interface IBattleStageLayout
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Optional authored stage reservation. Custom views may retain the host's framing.

**Methods**

`public bool TryGetStageBounds(out BattleStageBounds bounds)`

:   Provides a presentation-only normalized stage reservation that the host may use for camera framing without changing combat.

    - `bounds` &mdash; Receives the reservation when available.
    - **Returns** &mdash; True when authored bounds are available.

---

## IBattleView

```csharp
public interface IBattleView
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Renderer-neutral contract for rendering state and forwarding intents.

**Events**

`public event Action<BattleViewCommand> CommandChosen`

:   Raised when the view publishes a command choice.

**Methods**

`public void HandleIntent(BattleViewIntent intent)`

:   Handles a user intent.

    - `intent` &mdash; Interaction to process.

`public void Render(BattleViewState state)`

:   Replaces the rendered state.

    - `state` &mdash; Immutable state to render.

---

## IInteractiveBattleView

```csharp
public interface IInteractiveBattleView : IBattleView
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleViewState.cs</small>

Optional interaction surface used by a world-space presentation bridge.
It is deliberately separate from `IBattleView` so existing
adapters and custom views do not acquire a new implementation burden.

**Properties**

`public BattleViewSession Session`

:   Shared selection and submission session.

---

## LowestHealthAllyTargetResolver

```csharp
public sealed class LowestHealthAllyTargetResolver : ITargetResolver
```

`TurnHerald.Samples.CustomMechanics` &middot; <small>Samples/CustomMechanics/LowestHealthAllyTargetResolver.cs</small>

Chooses the living targetable ally with the lowest health ratio.

**Properties**

`public int ContractVersion`

:   Gets the contract version implemented by this resolver.

`public StableId ImplementationId`

:   Gets the stable implementation id used for compatibility checks.

`public TargetRequestContract RequestContract`

:   Gets the request contract for automatic selection of up to one living, targetable ally, including the actor, with no manual picks.

`public StableId ResolverId`

:   Gets the resolver's stable registry id.

`public int TargetContractVersion`

:   Gets the target registry contract version implemented by this resolver.

**Fields**

`public static readonly StableId Id`

:   Stable registry id for this target resolver.

**Methods**

`public FrozenList<StableId> GetCandidates(TargetContext context, PropertySet properties)`

:   Returns the living, targetable ally with the lowest Health/MaximumHealth ratio, breaking ties by stable ID.

    - `context` &mdash; Snapshot and actor context used to identify allies.
    - `properties` &mdash; Resolver properties, which must be empty.
    - **Returns** &mdash; One candidate id, or an empty list when the actor or allies are unavailable.

`public static StableId SelectLowestHealthRatio(BattleStateView snapshot, FrozenList<StableId> candidates)`

:   Selects the lowest-health-ratio valid candidate from a snapshot.

    - `snapshot` &mdash; Battle snapshot used to resolve candidate ids.
    - `candidates` &mdash; Candidate ids to compare.
    - **Returns** &mdash; The selected id, or the default id when no candidate remains valid.

`public static StableId SelectLowestHealthRatio(IEnumerable<CombatantState> candidates)`

:   Selects the lowest-health-ratio valid combatant from an enumerable.

    - `candidates` &mdash; Combatants to compare.
    - **Returns** &mdash; The selected id, or the default id when no candidate is valid.

`public ValidationReport Validate(TargetValidationContext context, PropertySet properties)`

:   Validates that this resolver receives no custom properties.

    - `context` &mdash; Targeting context used to validate the request.
    - `properties` &mdash; Resolver properties, which must be empty.
    - **Returns** &mdash; A valid report for an empty property set, otherwise an unknown-property diagnostic.

`public TargetRequestResult ValidateRequested(TargetContext context, PropertySet properties, FrozenList<StableId> requested)`

:   Rejects manual picks and accepts the living, targetable ally with the lowest Health/MaximumHealth ratio, breaking ties by stable ID.

    - `context` &mdash; Snapshot and actor context used to recompute the candidate.
    - `properties` &mdash; Resolver properties, which must be empty.
    - `requested` &mdash; Manual ids supplied by the caller; any non-empty request is rejected.
    - **Returns** &mdash; A rejection for manual requests, otherwise an acceptance containing the computed id or an empty list when no candidate is available.

---

## Pair

```csharp
public readonly struct Pair
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleThemeContrast.cs</small>

Nested in `TurnHerald.UI.BattleThemeContrast`.

One text color of the dock and what it is drawn on, named for a failure message.

**Constructors**

`public Pair(string name, Color text, Color backdrop)`

:   Creates a pair.

    - `name` &mdash; What the text is.
    - `text` &mdash; Text color.
    - `backdrop` &mdash; Backdrop color.

**Properties**

`public Color Backdrop`

:   Backdrop color.

`public string Name`

:   What the text is.

`public float Ratio`

:   Contrast ratio of the pair.

`public Color Text`

:   Text color; translucent colors are measured over the backdrop.

---

## ParticleArtBinding

```csharp
public sealed class ParticleArtBinding
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/TurnHeraldDemoBootstrap.cs</small>

Nested in `TurnHerald.Presentation.Demo.TurnHeraldDemoBootstrap`.

Binds a recipe VFX key (a particle-* sprite name) to art.

**Fields**

`public Sprite ParticleSprite`

:   Sprite used by the particle effect.

`public string VfxKey`

:   Recipe VFX key whose particle sprite is being bound.

---

## SessionEndState

```csharp
public enum SessionEndState
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/TurnHeraldDemoBootstrap.cs</small>

Nested in `TurnHerald.Presentation.Demo.TurnHeraldDemoBootstrap`.

Typed end-of-session states surfaced by the driver.

| Value | Meaning |
| --- | --- |
| `None` | No battle, or the battle is still running. |
| `TerminalResult` | The engine reported a terminal result (victory, defeat, draw, concession, or the stalled result). |
| `NoScheduledWork` | The engine reported no scheduled work remains. |
| `FatalInvariant` | The engine reported a fatal invariant; the driver stops pumping instead of entering an exception loop. |

---

## TargetCandidateQuery

```csharp
public static class TargetCandidateQuery
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/TargetCandidateQuery.cs</small>

Asks a skill's registered target resolver who it may legally hit right
now, and whether one particular pick would be accepted.

It is the single place the interface and the command translator both go
for that answer, which is what keeps the two from disagreeing: a project
that registers a resolver narrower than its declared contract - front row
only, lowest health only, line of fire - narrows the picker and the
auto-pick together, because both ask the same object the engine will ask.

Everything here is a read. The snapshot is projected into the read-only
view the resolver contract already takes, no command is submitted, and no
RNG is drawn, so consulting it can never change a battle.

**Methods**

`public static FrozenList<StableId> GetCandidates(BattleSnapshot snapshot, CompiledAuthoringCatalog catalog, StableId actorId, StableId skillId)`

:   Lists the resolver's candidates after taunt and snapshot-visible interrupt preconditions are applied for `actorId`. Random automatic selection remains authoritative in the simulation.

    - `snapshot` &mdash; Current authoritative state; read, never advanced.
    - `catalog` &mdash; Compiled content and the registry the resolver is looked up in.
    - `actorId` &mdash; The combatant that would use the skill.
    - `skillId` &mdash; The skill whose resolver is consulted.
    - **Returns** &mdash; Candidate ids, ascending and without duplicates. Empty for a missing argument, an unknown skill, an unregistered resolver, or a resolver that threw; an empty result therefore means "offer no picks" rather than "every combatant is legal".

`public static bool ValidateRequest(BattleSnapshot snapshot, CompiledAuthoringCatalog catalog, StableId actorId, StableId skillId, IReadOnlyList<StableId> requested, out string message)`

:   Puts a proposed pick through the resolver check and visible interrupt preconditions. The engine remains authoritative, including random automatic selection and changes after this snapshot.

    - `snapshot` &mdash; Current authoritative state; read, never advanced.
    - `catalog` &mdash; Compiled content and the registry the resolver is looked up in.
    - `actorId` &mdash; The combatant that would use the skill.
    - `skillId` &mdash; The skill whose resolver is consulted.
    - `requested` &mdash; Exactly the ids the command would carry, in pick order. An empty list asks for automatic selection.
    - `message` &mdash; Why the pick would be refused, or an empty string when it would be accepted. It is developer-facing detail, not player-facing text.
    - **Returns** &mdash; True when the resolver and visible preconditions accept the request. Random automatic locks are checked by the engine after selection. A resolver this method cannot reach at all also returns true: the engine remains the authority, and refusing a command the UI merely failed to preview would be worse than letting the engine answer.

---

## TargetPreview

```csharp
public static class TargetPreview
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/TargetPreview.cs</small>

Turns a resolver into the way its affected set should be shown, and a
device into the way a pick should be expressed.

Pure classification over ids the simulation already owns. It adds no
simulation code and reaches no engine: every treatment here is fed by
`TargetCandidateQuery.GetCandidates`, which already exists and
already agrees with the engine. Eight looks, one data source.

**Fields**

`public const int CollapseToSinglePickAt`

:   Below this many candidates a region treatment says nothing. A team scrim drawn around one combatant communicates no more than a reticle would and reads as a bug, which is why a duel collapses to the single-pick look however the resolver is written.

`public const int PerHeadMarkCeiling`

:   Past this many resolved targets, per-head marks stop scaling and the region plus a count does the work instead. Six ticks over six heads is noise; a scrim and the number six is a sentence.

`public const int SlotGridCandidateCeiling`

:   Past this many candidates a side, picking on the stage stops being reliable and the slot grid takes over.

**Methods**

`public static TargetingPreset Adapt(TargetingPreset authored, bool adapt, int candidatesPerSide, bool portrait, bool touch)`

:   The preset a pick should actually be expressed with, given the device and the stage in front of the player. A preset that adapts is worth more than four a buyer has to configure, so the shipped default starts at `TargetingPreset.Reticle` and moves when the situation makes it the wrong tool. A project that wants its authored choice honoured verbatim turns adaptation off.

    - `authored` &mdash; The preset the skin asks for.
    - `adapt` &mdash; False returns `authored` untouched.
    - `candidatesPerSide` &mdash; The largest candidate count on either side.
    - `portrait` &mdash; Whether the stage is taller than it is wide.
    - `touch` &mdash; Whether the device is touch-first.
    - **Returns** &mdash; The preset to drive the pick with.

`public static TargetTreatment ClassifyTreatment(StableId resolverId, TargetLifeState allowedLifeState)`

:   The treatment `resolverId` should be previewed in.

    - `allowedLifeState` &mdash; The life state the resolver accepts. Dead outranks the shape: revive is the one skill that wants a corpse legible, and showing it as an ordinary ally pick is what makes players think it is broken.
    - `resolverId` &mdash; The shipped resolver key, such as `target.one-enemy.v1`.
    - **Returns** &mdash; The matching treatment, or `TargetTreatment.SinglePick` for a resolver this version does not know. A custom resolver therefore gets the reticle rather than nothing, which is wrong in a way a player can see and recover from rather than wrong in a way that looks like a missing feature.

`public static TargetTreatment Degrade(TargetTreatment treatment, int candidateCount)`

:   Degrades a treatment for the party size and stage shape in front of it. Three thresholds decide everything: one candidate, more than `PerHeadMarkCeiling`, and a portrait stage. No per-encounter targeting art, and nothing to re-author when a project changes its party size.

    - `treatment` &mdash; The treatment the resolver classified to.
    - `candidateCount` &mdash; How many combatants the query returned.
    - **Returns** &mdash; The treatment to draw. A region shape with one candidate collapses to the single-pick look; everything else is returned as classified.

`public static bool TakesAPlayerPick(TargetTreatment treatment)`

:   Whether this treatment asks the player to choose, rather than showing them what the resolver has already decided.

    - `treatment` &mdash; The treatment to classify.
    - **Returns** &mdash; True for the three shapes that take a pick. The other five resolve themselves, which is exactly why they still have to be previewed: nothing else will tell the player what is about to be hit.

`public static bool UsesPerHeadMarks(int resolvedCount, bool portrait)`

:   Whether each resolved target gets its own mark, or the region carries a count instead.

    - `resolvedCount` &mdash; How many combatants the shape resolves to.
    - `portrait` &mdash; Whether the stage is taller than it is wide.
    - **Returns** &mdash; False past `PerHeadMarkCeiling`, and false in portrait, where rows run horizontally and a band reads where per-head ticks do not.

---

## TargetTreatment

```csharp
public enum TargetTreatment
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/TargetPreview.cs</small>

The visual language one target shape is previewed in.

There are eight because there are eight kinds of answer a resolver can
give, not because eight looked like a good number. Twelve resolvers ship
and only three of them take a player pick, so a preview built around the
reticle - the interface for exactly one shape - showed the player nothing
at all for the other nine.

| Value | Meaning |
| --- | --- |
| `SinglePick` | One combatant, chosen by the player. |
| `WholeTeam` | A whole side. |
| `Everyone` | Both sides at once. |
| `RandomPool` | N drawn from a pool. |
| `FormationRow` | One formation row, marked at its ground line across the stage. |
| `FormationSide` | One side of the field, filled to a hard vertical edge. |
| `Self` | The actor alone. |
| `DeadTarget` | A corpse, which keeps its greyscale but regains a rim and hit-testing. |

---

## TargetingPreset

```csharp
public enum TargetingPreset
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Runtime/TargetPreview.cs</small>

How a pick is expressed. It never changes what is legal: legality stays
with the resolver, so a project can swap presets - or offer the choice to
its players as an accessibility setting - without touching content or
invalidating a replay.

| Value | Meaning |
| --- | --- |
| `Reticle` | A cursor living on one candidate. |
| `Direct` | Drag from the card onto a body, or tap card then body. |
| `SlotGrid` | A formation-shaped mini map beside the deck. |
| `AutoConfirm` | No pick step: the resolver decides and one button commits. |

---

## TokenArtBinding

```csharp
public sealed class TokenArtBinding
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/TurnHeraldDemoBootstrap.cs</small>

Nested in `TurnHerald.Presentation.Demo.TurnHeraldDemoBootstrap`.

Binds a starter combatant definition id to its generated
token sprite (the token-* art keys from the art manifest).

**Fields**

`public string CombatantDefinitionId`

:   Stable combatant definition id whose token art is being bound.

`public Sprite TokenSprite`

:   Sprite drawn for the combatant's token.

---

## ToolkitBattleView

```csharp
public sealed partial class ToolkitBattleView
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUIToolkit/ToolkitBattleView.Dock.cs</small>

The dock layout of the UI Toolkit adapter: turn ribbon, command list, action card and party panel.

**Properties**

`public override BattleHudDesign HudDesign`

:   The HUD design of the tree this view is bound to: the Overlay for a tree with its marker, the Dock for a tree with the dock frame, the Classic panel for any other. Read without binding: a view that has not bound its tree yet looks at it.

`public bool IsRibbonMoving`

:   True while a change of the turn ribbon is still playing: something on it is sliding, growing or fading. A view that is not enabled is not stepped, so it reports no motion whatever it was doing; the change ends where it stands when the view is drawn, which is also what the engine's OnDisable leads to (Edit Mode does not deliver it to a component that is not ExecuteAlways).

`public bool IsStripMoving`

:   True while the sentence of the event strip is still changing: one is on its way out or another on its way in. A view that is not enabled is not stepped, so it reports no motion; see `IsRibbonMoving`.

`public override bool IsSwappingTheme`

:   True while the HUD of this view is dipping to change its theme: from `BeginThemeSwap` until the opacity of its root is back to full.

`public override bool IsWarmingUp`

:   True from the moment a plan is accepted until the copy of the dock that plays it has been taken away.

`public VisualTreeAsset LayoutAsset`

:   UXML asset used by the UIDocument; assigning it rebinds the live tree.

`public override BattleUiTechnology Technology`

:   Reports the UI Toolkit backend implemented by this replaceable UXML surface.

`public override float ThemeSwapOpacity`

:   The opacity the dip gives the root of the HUD now: the opacity of the dip, one when no swap is in course.

`public VisualElement ViewRoot`

:   Currently bound battle root, or null until the document is available.

`public override string WarmUpFault`

:   The reason the last rehearsal was given up; empty when it was played to its end or never asked for.

**Methods**

`public override void AdvanceMotion(float seconds)`

:   Advances the motion of the dock that this adapter drives itself: the turn ribbon, the bars sliding to their values and the fades of new content.

    - `seconds` &mdash; Elapsed seconds, unscaled.

`public override void ApplyTheme(BattleTheme theme)`

:   Applies the shared theme to the bound UI Toolkit surface at once, and ends a theme swap in course: the HUD is whole in the same call and this theme is the one kept.

    - `theme` &mdash; Theme values to apply.

`public override void BeginThemeSwap(BattleTheme theme, float seconds)`

:   Dips the opacity of the root of this view, which holds the whole HUD, and changes `BattleViewBehaviour.Theme` at the bottom of the dip, when nothing of the HUD is visible. Focus and the selection in course go through that change as they do through `ApplyTheme`. The opacity is written by the clock of the view (`AdvanceMotion`), not by a USS transition. A view that is disabled or has not been drawn yet, one without a clock (it is not played and `BattleViewBehaviour.ManualClock` is off), or a length of zero or less applies the theme at once.

    - `theme` &mdash; Theme to copy, or null for defaults.
    - `seconds` &mdash; Length of the whole swap, fall and rise together. Zero or less applies the theme at once.

`public override bool BeginWarmUp(BattleWarmUpPlan plan)`

:   Accepts a plan to play off screen in a second copy of this dock, one step for each step of `AdvanceMotion`. The copy is made when the dock is on a panel, so a plan given before that waits for it, and is dropped after a while with the reason in `WarmUpFault`.

    - `plan` &mdash; States and intents of a first decision.
    - **Returns** &mdash; True when the plan was accepted; false for an empty plan, one already being played or a view that is not enabled.

`public override bool BlocksStagePointer(float screenX, float screenY)`

:   Tests whether a screen point belongs to an interactive battle surface.

    - `screenX` &mdash; Screen-space horizontal coordinate.
    - `screenY` &mdash; Screen-space vertical coordinate.
    - **Returns** &mdash; True when the picked element is an interactive battle control.

`public override void BuildDefaultLayout(BattleLayoutIdentity identity, BattleHudDesign design)`

:   Builds the default layout of a layout family in a HUD design. The family's own design (the Dock for Fantasy, the Classic panel for Science Fiction) is built by `BuildDefaultLayout(BattleLayoutIdentity)`, the same call as before; the Overlay is built for either family, in code, and is built again whenever the view rebuilds its default layout (a new visual host, an enable).

    - `identity` &mdash; Layout family to author.
    - `design` &mdash; HUD design to build.

`public override void BuildDefaultLayout(BattleLayoutIdentity identity)`

:   Replaces the current UXML tree with an immediately generated default layout. Existing document elements are cleared; when the UIDocument has no root, the method only clears the asset assignment and returns.

    - `identity` &mdash; Layout identity requested by the presentation profile.

`public override void CancelWarmUp()`

:   Ends the rehearsal at once: the copy, its container and its profile are destroyed and the dock is as it was.

`public override void Configure(BattlePresentationProfile profile)`

:   Loads the profile's VisualTreeAsset and forwards the profile settings to the base view.

    - `profile` &mdash; Profile whose layout and theme should be used.

`public override bool OwnsPointerSurface(object surface)`

:   Reports whether the last pointer hit belonged to this view's panel.

    - `surface` &mdash; Panel object previously used for the pointer hit.
    - **Returns** &mdash; True only when the last hit was owned by this view and the supplied panel matches.

`public int ReadCard(out BattleDockCardReading card, List<BattleDockMarkedReading> marked)`

:   Reads what the action card draws at this instant: what it was drawn as, its heading and its two lines as the elements carry them, its opacity on the screen (the fade of its content, the fade of its panel as the card comes or goes, and the dip of a theme swap, all of them written by the clock of the view and none by a style sheet transition), and one entry for each cell of the combatants the action marks, in the order they are drawn: the combatant, the health text, and how much of the health bar is drawn.

    - `card` &mdash; Receives the card.
    - `marked` &mdash; Receives the marked cells; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many cells were read; zero when the card lists none.

`public BattleDockListsReading ReadLists()`

:   Reads how opaque the list of commands and the list of targets are on the screen; the one that is not showing is zero.

    - **Returns** &mdash; The two opacities.

`public int ReadParty(List<BattleDockMemberReading> members)`

:   Reads the party panel: for each member in the order they are drawn, the combatant, how much of the health bar is on the screen at this instant (the point a slide to a new value has reached, not the value it is going to) and the text of the health column.

    - `members` &mdash; Receives the members; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many members were read.

`public int ReadRibbon(List<BattleDockRibbonReading> readings)`

:   Reads what the turn ribbon draws at this instant, from the elements the view drew, in screen pixels: for each medallion, the ones that are fading out included and bottom first, its key, combatant, center, diameter, opacity as drawn (with the opacity of every element above it), the tab text and its opacity, the text going out and its opacity, and where the tab hangs from the medallion. Horizontal measures run from the horizontal center of the ribbon region and vertical ones from its top edge; every reading carries the screen pixels of one panel unit, which divides them back to the reference pixels of `BattleDockMetrics`. The values are the ones the view wrote, so they are there before the panel has laid anything out. Whether a NOW is drawn in this frame is read from the same readings, in both adapters, by `BattleDockRibbonReading.ShowsNow` of each of them or `BattleDockRibbonReading.AnyShowsNow` of the list: a tab that reads NOW, or is on its way out, above the faintest a player reads.

    - `readings` &mdash; Receives the readings; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many medallions were read; zero before the ribbon is drawn.

`public BattleDockStripReading ReadStrip()`

:   Reads what the event strip draws at this instant, from the label the view drew: the sentence it shows with its opacity on the screen (the opacity of every element above it counted, the dip of a theme swap included) and, while a sentence is on its way out, that sentence with its own opacity and the one that follows at none. The strip is one label, so the two opacities are never above zero together. The values are the ones the view wrote, so they are there before the panel has laid anything out.

    - **Returns** &mdash; The reading; empty texts and zero opacities before the strip is drawn.

`public int ReadTargetRows(List<BattleDockTargetRowReading> rows)`

:   Reads the rows of the target list while it is showing: the combatant of each row, how much of its mini health bar is drawn, and the opacity of the whole list on the screen.

    - `rows` &mdash; Receives the rows in the order they are drawn; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many rows were read; zero while the list of commands is the one showing.

`public void Rebind()`

:   Explicit refresh hook for editor previews and custom live-reload hosts.

`public override void RefreshBindingsIfNeeded()`

:   Rebinds when UIDocument or required controls changed.

`public void SetVisualHost(VisualElement host, Action<BattleViewIntent> dispatchIntent = null)`

:   Hosts this view in a dedicated public visual container, or returns to its UIDocument when null. The host owns panel attachment and dimensions; this view owns its children and bindings.

    - `host` &mdash; Dedicated container for the authored layout.
    - `dispatchIntent` &mdash; Optional host routing for visual input, such as preview decision guards.

`public bool TryGetFeedbackBounds(out BattleStageBounds bounds)`

:   Finds a clear feedback rectangle using the currently attached visual tree, including the complete timeline header.

    - `bounds` &mdash; Receives the largest normalized area inside the authored stage reservation that avoids visible HUD panels.
    - **Returns** &mdash; True when layout is ready and a clear area exists. False means feedback must wait or stay hidden.

`public override string[] ValidateBindings()`

:   Validates required UXML names and button types without changing battle state.

    - **Returns** &mdash; Diagnostic messages; an empty array means the required bindings are valid.

---

## TurnHeraldDemoBootstrap

```csharp
public sealed class TurnHeraldDemoBootstrap : MonoBehaviour
```

`TurnHerald.Presentation.Demo` &middot; <small>Runtime/Presentation/Demo/TurnHeraldDemoBootstrap.cs</small>

The runtime demo driver (specification section 9). It compiles the
starter catalog with built-in registries explicitly at load, offers the
scenario picker over the AUTHORED encounter variants (scheduler and
formation choices are inputs to scenario identity, so picking one of the
eight already-compiled encounters IS the scheduler/formation choice; no
preset is ever swapped on a live start), exposes a user-visible seed
field, owns the `BattleEngine`, and runs the continuous
driver loop from ExecutionSteppingV1 section 7: accumulated presentation
time is converted into an integer requested tick count and handed to
`AdvanceTicks`, whose returned events feed the presenter and whose
snapshots are adopted verbatim.

The DRIVER is the single audited engine owner in the Presentation
assembly (specification section 3 rule 1: "The demo's driver object owns
the engine; the presenter only receives values"); the presenter-purity
audit carves out exactly this demo namespace and nothing else. Pause,
speed, and skip affect presentation only: they scale or halt the
presentation-time accumulator and the visual beat clock, never a
simulation value, so the same (scenario, scheduler, formation, seed)
tuple always reproduces the same hashes. Human-decision scenarios must
author the PauseOnInput scheduler policy so presentation speed cannot
shift submission ticks; the shipped starter scenarios are all-Automatic.
`FatalInvariant`, `NoScheduledWork`, and the stalled terminal
result surface as typed end-of-session states without an exception loop.

**Properties**

`public int AtbCompileErrorCount`

:   Error diagnostic count from the ATB load-time compile.

`public bool AtbCompileSucceeded`

:   True when the assigned ATB showcase catalog compiled.

`public int CompileErrorCount`

:   Error diagnostic count from the primary load-time compile.

`public bool CompileSucceeded`

:   True when the primary catalog compiled with zero errors.

`public IReadOnlyList<StableId> EncounterIds`

:   The authored encounter variants offered by the picker.

`public SessionEndState EndState`

:   The typed end-of-session state of the current battle.

`public bool IsBattleRunning`

:   True when a battle exists and has not reached an end state.

`public bool Paused`

:   Presentation-only pause; halts presentation-time accumulation (and therefore tick pumping) without touching state.

`public StableId? SelectedEncounterId`

:   The picker's currently selected encounter variant.

`public float SpeedMultiplier`

:   The active presentation speed step.

`public StableId? TerminalResultId`

:   The terminal result id when `EndState` is `SessionEndState.TerminalResult` (battle.stalled marks a stall surfaced as a clean terminal result).

**Fields**

`public const float BaseTicksPerSecond`

:   Simulation ticks represented by one presentation second at 1x speed.

`public static readonly float[] SpeedSteps`

:   The specification section 9 presentation speed steps.

**Methods**

`public void CompileCatalog()`

:   Explicitly compiles both starter catalogs with built-in registries (specification section 9: compile at load through the same public entry point the Workbench and tests use). The picker then spans the primary catalog's Action Order variants plus the dedicated ATB catalog's variant; each variant remembers its owning compiled catalog because the engine binds scheduler-adjustment support per catalog at creation (specification section 6).

`public void CycleSpeed()`

:   Cycles the presentation speed through 0.5x/1x/2x/4x.

`public void SelectNextEncounter()`

:   Moves the scenario picker forward through the authored variants.

`public void SelectPreviousEncounter()`

:   Moves the scenario picker backward through the authored variants.

`public void SkipAll()`

:   Finishes every queued presentation beat now (visuals only).

`public bool StartBattle(StableId encounterId, uint seedValue)`

:   Creates the engine for one authored encounter variant from the variant's OWNING compiled catalog (primary or ATB) and binds a fresh presenter to its compiled formation layout.

`public bool StartSelectedBattle()`

:   Starts (or restarts) the picker-selected encounter variant with the current seed value. The variant is an authored, already-compiled start; nothing is re-authored or swapped at runtime.

---

## UguiBattleView

```csharp
public sealed partial class UguiBattleView
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUGUI/UguiBattleView.Dock.cs</small>

The dock layout of the uGUI adapter: turn ribbon, command list, action card and party panel.

**Properties**

`public RectTransform CustomRoot`

:   Optional authored subtree containing the required named slots.

`public override BattleHudDesign HudDesign`

:   The HUD design of the tree this view is bound to: the Overlay for a tree with its marker, the Dock for a tree with the dock frame, the Classic panel for any other. Read without binding: a view that has not bound its tree yet looks at it.

`public bool IsRibbonMoving`

:   True while a change of the turn ribbon is still playing: something on it is sliding, growing or fading. A view that is not enabled is not stepped, so it reports no motion whatever it was doing; the change ends where it stands when the view is drawn, which is also what the engine's OnDisable leads to (Edit Mode does not deliver it to a component that is not ExecuteAlways).

`public bool IsStripMoving`

:   True while the sentence of the event strip is still changing: one is on its way out or another on its way in. A view that is not enabled is not stepped, so it reports no motion; see `IsRibbonMoving`.

`public override bool IsSwappingTheme`

:   True while the HUD of this view is dipping to change its theme: from `BeginThemeSwap` until its canvas group is back to full opacity.

`public override bool IsWarmingUp`

:   True from the moment a plan is accepted until the copy of the dock that plays it has been taken away.

`public override BattleUiTechnology Technology`

:   Reports the uGUI backend implemented by this prefab-authored surface.

`public override float ThemeSwapOpacity`

:   The opacity the canvas group of the dip gives the HUD now: the opacity of the dip, one when no swap is in course.

`public override string WarmUpFault`

:   The reason the last rehearsal was given up; empty when it was played to its end or never asked for.

**Methods**

`public override void AdvanceMotion(float seconds)`

:   Advances the motion of the dock (the turn ribbon, the bars, the hovers, the fades of new content) by an explicit step.

    - `seconds` &mdash; Elapsed seconds, unscaled.

`public override void ApplyTheme(BattleTheme theme)`

:   Applies a theme at once and ends a theme swap in course, so the HUD is whole in the same call and this theme is the one kept.

    - `theme` &mdash; Theme to copy, or null for defaults.

`public override void BeginThemeSwap(BattleTheme theme, float seconds)`

:   Dips the opacity of the whole HUD through a canvas group on the root this view binds, and changes `BattleViewBehaviour.Theme` at the bottom of the dip, when nothing of the HUD is visible. Focus and the selection in course go through that change as they do through `ApplyTheme`. The group is never made non-interactable or non-raycastable, so a click during the dip goes to the HUD and not to the stage. A view that is disabled or has not been drawn yet, one without a clock (it is not played and `BattleViewBehaviour.ManualClock` is off), or a length of zero or less applies the theme at once.

    - `theme` &mdash; Theme to copy, or null for defaults.
    - `seconds` &mdash; Length of the whole swap, fall and rise together. Zero or less applies the theme at once.

`public override bool BeginWarmUp(BattleWarmUpPlan plan)`

:   Accepts a plan to play off screen in a second copy of this dock, one step for each step of `AdvanceMotion`. The copy is made once this dock has drawn, so a plan given before that waits for it, and is dropped after a while with the reason in `WarmUpFault`.

    - `plan` &mdash; States and intents of a first decision.
    - **Returns** &mdash; True when the plan was accepted; false for an empty plan, one already being played or a view that is not enabled.

`public override bool BlocksStagePointer(float screenX, float screenY)`

:   Tests whether a screen point falls within a visible raycastable battle slot.

    - `screenX` &mdash; Screen-space horizontal coordinate.
    - `screenY` &mdash; Screen-space vertical coordinate.
    - **Returns** &mdash; True when a visible slot contains the supplied screen point.

`public override void BuildDefaultLayout(BattleLayoutIdentity identity, BattleHudDesign design)`

:   Builds the default layout of a layout family in a HUD design. The family's own design (the Dock for Fantasy, the Classic panel for Science Fiction) is built by `BuildDefaultLayout(BattleLayoutIdentity)`, the same call as before; the Overlay is built for either family, on a canvas of the same size and match as the dock's.

    - `identity` &mdash; Layout family to author.
    - `design` &mdash; HUD design to build.

`public override void BuildDefaultLayout(BattleLayoutIdentity identity)`

:   Generates the built-in responsive uGUI layout under the selected root.

    - `identity` &mdash; Layout identity used to choose the default arrangement.

`public override void CancelWarmUp()`

:   Ends the rehearsal at once: the copy, its container and its profile are destroyed and the dock is as it was.

`public int ReadCard(out BattleDockCardReading card, List<BattleDockMarkedReading> marked)`

:   Reads what the action card draws at this instant: what it was drawn as, its heading and its two lines as the nodes carry them, its opacity on the screen (the fade of its content, the visibility of its panel and the dip of a theme swap), and one entry for each cell of the combatants the action marks, in the order they are drawn: the combatant, the health text, and how much of the health bar is drawn.

    - `card` &mdash; Receives the card.
    - `marked` &mdash; Receives the marked cells; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many cells were read; zero when the card lists none.

`public BattleDockListsReading ReadLists()`

:   Reads how opaque the list of commands and the list of targets are on the screen; the one that is not showing is zero.

    - **Returns** &mdash; The two opacities.

`public int ReadParty(List<BattleDockMemberReading> members)`

:   Reads the party panel: for each member in the order they are drawn, the combatant, how much of the health bar is on the screen at this instant (the point a slide to a new value has reached, not the value it is going to) and the text of the health column.

    - `members` &mdash; Receives the members; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many members were read.

`public int ReadRibbon(List<BattleDockRibbonReading> readings)`

:   Reads what the turn ribbon draws at this instant, from the nodes the view drew, in screen pixels: for each medallion, the ones that are fading out included and bottom first, its key, combatant, center, diameter, opacity as drawn (with every canvas group above it), the tab text and its opacity, the text going out and its opacity, and where the tab hangs from the medallion. Horizontal measures run from the horizontal center of the ribbon region and vertical ones from its top edge; every reading carries the screen pixels of one canvas unit, which divides them back to the reference pixels of `BattleDockMetrics`. Whether a NOW is drawn in this frame is read from the same readings, in both adapters, by `BattleDockRibbonReading.ShowsNow` of each of them or `BattleDockRibbonReading.AnyShowsNow` of the list: a tab that reads NOW, or is on its way out, above the faintest a player reads.

    - `readings` &mdash; Receives the readings; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many medallions were read; zero before the ribbon is drawn.

`public BattleDockStripReading ReadStrip()`

:   Reads what the event strip draws at this instant, from the text node the view drew: the sentence it shows with its opacity on the screen (every canvas group above it counted, the dip of a theme swap included) and, while a sentence is on its way out, that sentence with its own opacity and the one that follows at none. The strip is one node, so the two opacities are never above zero together.

    - **Returns** &mdash; The reading; empty texts and zero opacities before the strip is drawn.

`public int ReadTargetRows(List<BattleDockTargetRowReading> rows)`

:   Reads the rows of the target list while it is showing: the combatant of each row, how much of its mini health bar is drawn, and the opacity of the whole list on the screen.

    - `rows` &mdash; Receives the rows in the order they are drawn; it is cleared first, and is the caller's, so a recording reads every frame without allocating.
    - **Returns** &mdash; How many rows were read; zero while the list of commands is the one showing.

`public void Rebind()`

:   Forces slot discovery again after an authored hierarchy change.

`public bool TryGetFeedbackBounds(out BattleStageBounds bounds)`

:   Finds a clear feedback rectangle from the current HUD geometry, without moving the formation or camera.

    - `bounds` &mdash; Receives the largest normalized area inside the authored stage reservation that avoids visible HUD panels.
    - **Returns** &mdash; True when layout is ready and a clear area exists. False means feedback must wait or stay hidden.

`public override string[] ValidateBindings()`

:   Checks required named slots and reports missing, duplicate or incompatible controls.

    - **Returns** &mdash; Diagnostic messages; an empty array means the authored hierarchy is valid.

---

## UiPortraitCrop

```csharp
public readonly struct UiPortraitCrop : IEquatable<UiPortraitCrop>
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/UiPortraitCrop.cs</small>

Normalized source-space window used only by a portrait presentation.

**Constructors**

`public UiPortraitCrop(float centerX, float centerY, float width, float height)`

:   Creates a finite normalized source-space crop.

    - `centerX` &mdash; Crop center in normalized source coordinates.
    - `centerY` &mdash; Crop center in normalized source coordinates.
    - `width` &mdash; Crop width between .01 and 1.
    - `height` &mdash; Crop height between .01 and 1.

**Properties**

`public Vector2 Center`

:   Normalized bottom-left source coordinate at the crop center.

`public static UiPortraitCrop Default`

:   Unconfigured sentinel that selects the unchanged legacy crop.

`public float Height`

:   Normalized crop height.

`public bool IsConfigured`

:   True when this value contains a configured, finite crop.

`public Vector2 Size`

:   Normalized source-space crop size.

`public float Width`

:   Normalized crop width.

**Methods**

`public bool Equals(UiPortraitCrop other)`

:   Compares crop components exactly, including the unconfigured sentinel.

    - `other` &mdash; Crop value to compare with this value.
    - **Returns** &mdash; True when both crop values have equal components.

`public override bool Equals(object obj)`

:   Compares this crop with another object.

    - `obj` &mdash; Object to compare with this crop.
    - **Returns** &mdash; True when `obj` is an equal `UiPortraitCrop` value.

`public override int GetHashCode()`

:   Returns a hash derived from the crop components.

    - **Returns** &mdash; A hash code for this crop value.

`public static bool IsValid(float centerX, float centerY, float width, float height)`

:   Checks finite values, normalized bounds and containment.

    - `centerX` &mdash; Crop center in normalized source coordinates.
    - `centerY` &mdash; Crop center in normalized source coordinates.
    - `width` &mdash; Crop width between .01 and 1.
    - `height` &mdash; Crop height between .01 and 1.
    - **Returns** &mdash; True when all values are finite and the crop is contained in normalized space.

`public static bool operator !=(UiPortraitCrop left, UiPortraitCrop right)`

:   Compares two crop values for component inequality.

    - `left` &mdash; First crop value.
    - `right` &mdash; Second crop value.
    - **Returns** &mdash; True when any crop component differs.

`public static bool operator ==(UiPortraitCrop left, UiPortraitCrop right)`

:   Compares two crop values for component equality.

    - `left` &mdash; First crop value.
    - `right` &mdash; Second crop value.
    - **Returns** &mdash; True when both crop values have equal components.

---

## VfxBinding

```csharp
public sealed class VfxBinding
```

`TurnHerald.Runtime` &middot; <small>Runtime/Integration/BattleRuntimeController.cs</small>

Nested in `TurnHerald.Runtime.BattleRuntimeController`.

Maps one presentation VFX key to an optional pooled prototype.

**Fields**

`public string Key`

:   The presentation recipe's VFX key.

`public GameObject Prototype`

:   The pooled GameObject prototype, or null for a diagnostic no-op.

---
