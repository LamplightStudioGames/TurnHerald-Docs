# Stage and tokens

44 types in this area.

!!! abstract "On this page"
    [ArtReach](#artreach) &middot; [BattleBackdropAmbient](#battlebackdropambient) &middot; [BattleBackdropLayer](#battlebackdroplayer) &middot; [BattleBackdropLayerFit](#battlebackdroplayerfit) &middot; [BattlePresenter](#battlepresenter) &middot; [BattleStage2D](#battlestage2d) &middot; [BattleStageBackdrop](#battlestagebackdrop) &middot; [BattleStageBackdropAsset](#battlestagebackdropasset) &middot; [BattleStageBackdropGeometry](#battlestagebackdropgeometry) &middot; [BattleStageBackdropRig](#battlestagebackdroprig) &middot; [BattleStageBloom](#battlestagebloom) &middot; [BattleStageFloorSource](#battlestagefloorsource) &middot; [BattleStageFrame](#battlestageframe) &middot; [BattleStageInformationBank](#battlestageinformationbank) &middot; [BattleStageInformationBankSide](#battlestageinformationbankside) &middot; [BattleStageInformationBanks](#battlestageinformationbanks) &middot; [BattleStageInformationEntry](#battlestageinformationentry) &middot; [BattleStageInformationSide](#battlestageinformationside) &middot; [BattleStageProp](#battlestageprop) &middot; [BattleWorldPlateMode](#battleworldplatemode) &middot; [BattleWorldStyle](#battleworldstyle) &middot; [BeatDeriver](#beatderiver) &middot; [CombatantPuppet](#combatantpuppet) &middot; [CombatantTokenView](#combatanttokenview) &middot; [PresentationBeat](#presentationbeat) &middot; [PresentationBeatContext](#presentationbeatcontext) &middot; [PresentationStagePreset](#presentationstagepreset) &middot; [PresenterBinding](#presenterbinding) &middot; [PuppetActionKind](#puppetactionkind) &middot; [PuppetApproach](#puppetapproach) &middot; [PuppetMotionProfile](#puppetmotionprofile) &middot; [PuppetPose](#puppetpose) &middot; [PuppetShear](#puppetshear) &middot; [StageAnimationBinding](#stageanimationbinding) &middot; [StageAnimationSource](#stageanimationsource) &middot; [StageAudioBinding](#stageaudiobinding) &middot; [StageFrameMode](#stageframemode) &middot; [StagePresentationPlayback](#stagepresentationplayback) &middot; [StageSkillMotionBinding](#stageskillmotionbinding) &middot; [StageVfxBinding](#stagevfxbinding) &middot; [StrikeEffectKind](#strikeeffectkind) &middot; [StrikeEffectLayer](#strikeeffectlayer) &middot; [TargetPreviewView](#targetpreviewview) &middot; [TargetingReticleView](#targetingreticleview)

## ArtReach

```csharp
public struct ArtReach
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/ArtReach.cs</small>

The box around every texel an illustration paints in the frames it shows, as shares of its sprite rectangle, as the art is drawn
(a flipped sprite mirrors it): from the left edge of the rectangle to the left and to the right side of the box, and from its top
edge to the top and to the bottom of the box. It is larger than the painted body wherever the art reaches past it: the faint edge
the painted body leaves out (its metrics are measured at an alpha of 30%), feet drawn a texel or two below the ground line, the
other frames of an idle that sways, or a clip that throws a weapon or antlers forward. Target marks are fitted outside it
(`CombatantTokenView.TryGetMarkBoundsWorld`); the layout and the numbers keep the painted body, and so do the sides and
the width of a plate, which only stands higher over the brackets when they reach higher than the painted head.

**Constructors**

`public ArtReach(float left, float right, float top, float bottom)`

:   Creates a reach from its four sides.

    - `left` &mdash; Share of the width from the left edge of the rectangle to the left side of the box.
    - `right` &mdash; Share of the width from the left edge of the rectangle to the right side of the box.
    - `top` &mdash; Share of the height from the top edge of the rectangle to the top of the box.
    - `bottom` &mdash; Share of the height from the top edge of the rectangle to the bottom of the box.

**Properties**

`public bool IsDeclared`

:   True when the box has an area; the default value declares nothing.

**Fields**

`public float Bottom`

:   Share of the rectangle's height from its top edge to the bottom of the box.

`public float Left`

:   Share of the rectangle's width from its left edge to the left side of the box, as the art is drawn.

`public float Right`

:   Share of the rectangle's width from its left edge to the right side of the box, as the art is drawn.

`public float Top`

:   Share of the rectangle's height from its top edge to the top of the box.

**Methods**

`public ArtReach Clamped()`

:   The same box with every side kept inside the rectangle, or the empty value when it does not declare a box.

`public static ArtReach FromTexels(int left, int right, int top, int bottom, int cellWidth, int cellHeight)`

:   The reach of texels counted on the art: the first painted column and the column after the last one, from the left of the cell, and the first painted row and the row after the last one, from its top, over every frame the art can show.

    - `left` &mdash; First painted column.
    - `right` &mdash; Column after the last painted one.
    - `top` &mdash; First painted row, counted from the top.
    - `bottom` &mdash; Row after the last painted one, counted from the top.
    - `cellWidth` &mdash; Width of the sprite rectangle in texels.
    - `cellHeight` &mdash; Height of the sprite rectangle in texels.
    - **Returns** &mdash; The reach as shares of the rectangle.

`public override string ToString()`

:   &mdash;

---

## BattleBackdropAmbient

```csharp
public sealed class BattleBackdropAmbient
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropAsset.cs</small>

An optional ambient particle prefab placed at an anchor of the stage rectangle.

**Fields**

`public Vector2 Anchor`

:   Anchor inside the stage rectangle: (0,0) is bottom left and (1,1) is top right.

`public GameObject Prefab`

:   Particle prefab such as embers, dust, fireflies or a brazier flame. Use unlit sprite or particle shaders so it renders the same in Built-in and URP.

`public float Scale`

:   Uniform scale applied to the instance.

`public int SortingOrder`

:   Sorting order relative to the rig's base order.

---

## BattleBackdropLayer

```csharp
public sealed class BattleBackdropLayer
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropAsset.cs</small>

One sprite layer of a stage backdrop.

**Fields**

`public BattleBackdropLayerFit Fit`

:   How the sprite is sized against the stage rectangle.

`public Vector2 Offset`

:   Offset from the stage center as a fraction of the stage size.

`public float ParallaxFactor`

:   Parallax factor from zero to one. One keeps the layer fixed in the world, so it never shifts against the stage. Zero pins it to the camera, so it appears still on screen while the camera moves.

`public float Scale`

:   Multiplier applied after fitting.

`public int SortingOrder`

:   Sorting order relative to the rig's base order; higher draws in front.

`public Sprite Sprite`

:   Sprite drawn by the layer. A layer without a sprite is skipped.

`public Color Tint`

:   Color multiplied into the sprite. Its alpha is the layer opacity.

---

## BattleBackdropLayerFit

```csharp
public enum BattleBackdropLayerFit
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropAsset.cs</small>

How a backdrop layer is sized against the stage rectangle.

| Value | Meaning |
| --- | --- |
| `Cover` | Scales the sprite uniformly until it covers the stage rectangle plus the rig overscan. |
| `Native` | Keeps the sprite at its imported size multiplied by the layer scale. |

---

## BattlePresenter

**Start here**

```csharp
public sealed partial class BattlePresenter
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattlePresenter.Puppet.cs</small>

The presenter's half of the procedural motion: it turns the beats of an action into commands for the puppets of the combatants
involved. Everything here is presentation: it reads the beat and the stage, moves drawn bodies, and never touches a battle.

**Properties**

`public int ActiveCriticalNumberCount`

:   Floating numbers on the stage that are drawn as critical (larger and in the skin's critical color).

`public int ActiveFloatingNumberCount`

:   Floating numbers currently on the stage, including ones still playing out their rise. Each returns to the pool as it finishes, and the oldest is retired early rather than exceeding `MaximumFloatingNumbers`.

`public Action CameraShakeCallback`

:   Optional camera-shake sink; visual only, never authoritative.

`public int CameraShakeRequestCount`

:   Camera shakes requested since `Bind`. Counted whether or not `CameraShakeCallback` is set.

`public static StableId CastFizzledLabelId`

:   The label that says a cast ended without doing anything.

`public static StableId CastInterruptedLabelId`

:   The label that says a cast was broken off.

`public int ForcedInstantBeatCount`

:   Beats that were finished instantly because the queue had already reached `MaximumQueuedBeats`. A non-zero count means visuals were compressed to keep up, never that the battle changed. Cleared by `Bind`.

`public bool IsIdle`

:   True when no beat is playing and none are queued, so the visuals and the HUD have caught up with every event handed in so far. A pending decision opens on the HUD only from the moment this is true.

`public bool IsWarmingUp`

:   True from the moment the world text is drawn for the warm-up until the throwaway widgets that drew it are gone.

`public static StableId MagicSkillTag`

:   A skill tagged with this is a spell and does not close the distance.

`public bool ManualClock`

:   When true the target preview pulse is stepped by `Tick(float,bool)` instead of by the engine clock, so a host that drives time itself (a capture, a test) moves every part of the presentation with one explicit step. Off by default.

`public static StableId MeleeSkillTag`

:   A skill tagged with this is a melee attack: the attacker walks up to its target.

`public IList<IPerformBeatModule> PerformModules`

:   The perform modules driving the moment a skill lands, run in list order as each phase begins. This is the seam the shipped effects are built on and the one a project extends: add a module, drop one, reorder them, or replace the set entirely. The presenter contains anything a module throws, so a project's own module cannot stop a battle from playing. The list starts empty and, unless the built-in perform feel is switched off in the inspector, the shipped set is installed on the first tick. Registering your own modules before then keeps them, and their order, exactly as you built them: only a kind that is missing is added.

`public StableId PlayerTeamId`

:   The team treated as the player's for ally/enemy tinting. Presentation only. Left unset, the first team in the compiled layout is used, which matches how the shipped encounters order their teams.

`public static StableId ProjectileSkillTag`

:   A skill tagged with this launches something at its target and does not close the distance.

`public PuppetMotionProfile PuppetMotion`

:   The numbers of the procedural motion: wind-up, advance, squash, hit stop, knock-back, fall and breath. A copy is kept and clamped, so a value out of range cannot break a pose.

`public bool PuppetMotionEnabled`

:   Whether the presenter moves the painted bodies at all. On by default: every body breathes, attackers wind up and strike, and the struck and the fallen react. Off draws the bodies still and leaves their motion to the project.

`public int QueuedBeatCount`

:   Beats waiting behind the one currently playing. It never passes `MaximumQueuedBeats`, because reaching that cap completes the oldest beat instantly to make room, so a count that sits near the cap means the visuals are trailing the engine rather than that events are being lost.

`public static StableId RangedSkillTag`

:   A skill tagged with this does not close the distance.

`public bool ReduceMotion`

:   Whether the session or its skin currently reduces presentation motion.

`public float Speed`

:   Presentation-only playback speed multiplier (visual). A negative value clamps to zero, which freezes the visuals rather than reversing them.

`public static StableId SpellSkillTag`

:   A skill tagged with this is cast, not struck, and does not close the distance.

`public BattleStage2D Stage`

:   The stage this presenter created and owns, or null until `Bind` has run.

`public FormationLayoutMode StageLayoutMode`

:   The formation layout the stage was asked for. Line is the default.

`public int StageScreenHeightPx`

:   Height of the whole screen in pixels, when whoever frames the stage knows it; zero means it does not, and the layout recovers it from the viewport and `StageShareOfScreenPermille`, a pixel or two off at some sizes. `BattleStageFrame` gives it. The value applies at the next rebuild of the stage.

`public int StageShareOfScreenPermille`

:   Height of the stage viewport as a thousandth of the screen height; zero or less means the 52% the dock layout reserves. The line layout sizes combatants as a fraction of the screen, and the stage only knows its own viewport, so whoever frames the stage says how much of the screen it covers. `BattleStageFrame` does it. The value applies at the next rebuild of the stage.

`public Rect StageWorldRect`

:   Where the stage lands in world space, in units, for the current viewport and scale. Tokens are placed in world space directly rather than under this transform, so a camera framed on this rectangle sees the whole formation wherever the presenter object itself sits. The setup wizard frames the scene camera from this value, so the framing is authored here rather than copied by hand into a scene.

`public static StableId SupportSkillTag`

:   A skill tagged with this helps its target and does not move its user.

`public float UnitsPerPixel`

:   World units per stage pixel, falling back to `DefaultUnitsPerPixel` when the serialized value is zero or negative, which is the coercion `BattleStage2D.Build` applies anyway.

`public FormationViewport Viewport`

:   The pixel rectangle the formation is projected into, read straight from the serialized stage fields. `SetViewport` writes those fields, so a `BattleStageFrame` that reframes the stage at runtime shows up in the inspector instead of hiding behind it.

`public string WarmUpFault`

:   The reason the last `WarmUpWorldText` gave up; empty when it ran to its end or was never asked for.

`public float WorldInterfaceOpacity`

:   The opacity last given to `SetWorldInterfaceOpacity`; one when the interface of the world is whole.

`public CompiledBattleSkin WorldSkin`

:   The skin the stage draws with when the presenter has no legacy interface root, or null for the package default.

`public BattleWorldStyle WorldStyle`

:   How the stage is currently dressed apart from its skin: plate policy and target marks.

**Fields**

`public const float DefaultUnitsPerPixel`

:   World units one stage pixel is worth when the serialized scale is left at zero or below. It repeats `BattleStage2D.Build`'s own fallback so a presenter nobody has touched frames exactly as before.

`public const float FloatingNumberSpacingSeconds`

:   Least gap, in seconds, between two numbers appearing over the same combatant. They stack with it, never on one frame.

`public const int MaximumFloatingNumbers`

:   Section 10 cap: floating numbers concurrently visible.

`public const int MaximumFloatingNumbersPerTarget`

:   Floating numbers one combatant shows at the same time. A third hit waits for the first to finish instead of piling a third number onto the head, so the stack stays readable.

`public const int MaximumQueuedBeats`

:   Section 10 cap: queued beats per presenter.

`public const int MaximumQueuedFloatingNumbers`

:   Numbers waiting for their combatant to free a place. Past this the newest one joins the last waiting number of its combatant.

`public const float ReducedNumberSpacingSeconds`

:   Least gap, in seconds of presentation time, between the births of two floating numbers anywhere on the stage while motion is reduced. Reduced motion plays no phase, so without it every number of a batch would appear in one frame. With it each number is read before the next arrives, in the order of the events, and a number that has to wait holds the beats behind it, so the HUD (which takes the result of an event when its number is born) never runs ahead of the numbers.

`public const float ReducedTurnSpacingSeconds`

:   The least time, in seconds, a turn stays the one being played under reduced motion. The beats of a turn are fired in one step there, so a turn with no number (a cast that starts, a skipped action) would come and go in a single frame: its sentence on the strip, the current turn on the HUD and the cue on its actor would never be read. Once somebody's turn has opened, nothing that belongs to another turn is played and the stage is not idle until this time has passed.

**Methods**

`public void AdoptSnapshot(BattleSnapshot snapshot)`

:   Adopts an authoritative snapshot for resync/skip and display. With nothing queued the HUD and the stage take it at once. While beats are still playing it is kept as the state they end on, and the HUD reaches it when the last beat is done: the HUD follows the events being played, not the end of the batch.

    - `snapshot` &mdash; State to mirror onto the stage and HUD. It is read, never advanced or mutated; a null snapshot is accepted and updates nothing.

`public void Bind(PresenterBinding presenterBinding)`

:   Rebuilds the stage from an explicit binding and reconnects its optional interactive HUD. Clears queued visual beats and resets playback without changing the simulation.

    - `presenterBinding` &mdash; Required compiled content, layout, recipes, adapters, pool, labels and optional UI. Retained until the next binding; null throws.

`public PuppetActionKind ClassifySkill(StableId? skillId)`

:   How the user of a skill moves. An explicit choice from `SetSkillMotion` wins. Otherwise a skill tagged melee is melee; one tagged ranged, magic, spell or projectile is ranged; one tagged support stays in place; one with a cast time or that reaches several targets (at random, across a row, or all at once) is ranged because there is no one place to walk to; a skill that picks one target, whoever picks it, is melee. An event with no skill (a status ticking) moves nobody.

    - `skillId` &mdash; The skill of the event, or null.
    - **Returns** &mdash; Melee, ranged or in place; never `PuppetActionKind.Auto`.

`public void ConfigureSkillMotions(IReadOnlyList<StageSkillMotionBinding> motions)`

:   Replaces the skill motions a stage preset authored. Earlier ones from a preset are removed first; motions stated with `SetSkillMotion` are kept unless the preset names the same skill.

    - `motions` &mdash; The preset's statements, or null to clear them.

`public void ConfigureStageFeel(PerformFeelPreset feel)`

:   Chooses the profile's fallback feel. An explicit inspector preset or host-installed module keeps precedence. Only automatically installed modules are replaced; their camera and body offsets reset first.

    - `feel` &mdash; Session-owned fallback feel; null returns to the presenter's default policy.

`public void EnqueueEvents(IReadOnlyList<BattleEvent> events)`

:   Derives and enqueues one beat per event (host step result).

    - `events` &mdash; Events from one engine step, in the order the engine produced them. A null list, and any null entry, is skipped. Once the queue reaches `MaximumQueuedBeats` the oldest beat is completed instantly to make room instead of being dropped, which increments `ForcedInstantBeatCount`.

`public void EnqueueEvents(IReadOnlyList<BattleEvent> events, IReadOnlyList<FormulaAttributionTrace> formulaTraces)`

:   Derives and enqueues one beat per event, and reads which damage was critical from the formula evidence of the same step. The engine does not write a critical flag on its damage events; the evidence it returns beside them does record a critical multiplier step, and the attribution hash an event carries names the evidence it stands for. A hit whose evidence has that step plays as a critical: `PresentationBeatContext.IsCritical` is true and its number is the critical one.

    - `events` &mdash; Events from one engine step, in the order the engine produced them; null and null entries are skipped.
    - `formulaTraces` &mdash; The formula attribution traces the same step returned, or null when the host has none.

`public void EnqueueEvents(IReadOnlyList<BattleEvent> events, IReadOnlyList<FormulaAttributionTrace> formulaTraces, IReadOnlyList<BattleSnapshot> afterEach)`

:   Derives and enqueues one beat per event, as the overload without snapshots does, and hands the HUD the state each event left behind. The HUD then shows that state in the phase of the beat that plays the event's result, instead of showing the end of the whole batch at once: a bar moves when the blow lands, the strip reads each event as it plays, and a decision opens only once the last beat is done. Without the snapshots the HUD still ends on the right state, but it changes once, with the last event.

    - `events` &mdash; Events from one engine step, in the order the engine produced them; null and null entries are skipped.
    - `formulaTraces` &mdash; The formula attribution traces the same step returned, or null when the host has none.
    - `afterEach` &mdash; The authoritative snapshot right after each event, such as `AdvanceTicksResult.EventSnapshots`, or null when the host has none. It needs one entry per event, and an entry may be null.

`public StableId? FindSkillOf(BattleEvent battleEvent)`

:   The skill an event belongs to. An event that names its skill says so; a damage or healing event names its effect entry instead, and an entry belongs to one skill of the compiled content.

    - `battleEvent` &mdash; The event to read; null has no skill.
    - **Returns** &mdash; The skill, or null when the event names neither a skill nor an entry the content knows.

`public int InstallBuiltInPerformModules(PerformFeelPreset feel, Camera camera, SkillTitleView titleView)`

:   Registers the shipped perform moment in one call: the skill title announcement, the focus pull, the body shake, and - when a camera is supplied - the camera shake and push-in, plus the bloom, vignette, and backdrop blur for whichever of those optional components the camera carries. This is the wiring the demo scene does by hand, offered as one line so a battle assembled from the shipped facade does not read flatter than the demo a buyer watched before purchasing. It adds only modules of a kind that is not registered yet, so calling it twice, or calling it after adding a module of your own, cannot double an effect. The first tick calls it for you with the serialized feel, camera, and no card, so calling it explicitly is only needed to pass a different preset, a different camera, or a card of your own. `PerformModules` stays open afterwards: drop one, reorder them, or add your own alongside.

    - `feel` &mdash; How hard the moment hits. Null uses the shipped defaults rather than zeroes, so the effects are visible without an asset being authored.
    - `camera` &mdash; The camera the shake and the push-in drive. Null registers the modules that need no camera and skips the rest.
    - `titleView` &mdash; The card the skill name is announced on. Null builds one over the bound interface, and skips the announcement when there is no interface to build it on.
    - **Returns** &mdash; How many modules were added.

`public bool IsCriticalHit(ulong eventSequence)`

:   Whether the damage event with this battle-wide sequence was read as critical from formula evidence handed to `EnqueueEvents(IReadOnlyList{BattleEvent}, IReadOnlyList{FormulaAttributionTrace})`. The last few thousand are remembered.

    - `eventSequence` &mdash; The event's `EventSequence`.
    - **Returns** &mdash; True when the presenter played, or will play, that hit as a critical.

`public void RebindEffects(PresentationRecipeSet recipes, IAnimationAdapter animation, IVfxAdapter vfx, IAudioAdapter audio, PresentationLog log = null)`

:   Replaces visual recipes and effect adapters without rebuilding the stage or HUD. Pending old effects are cancelled, not replayed. The snapshot, interactive subscriptions, selection and pool stay intact.

    - `recipes` &mdash; Replacement visual recipe set; must satisfy PresenterBinding's content contract.
    - `animation` &mdash; Adapter receiving animation keys from future phases.
    - `vfx` &mdash; Adapter receiving effect keys and participant anchors from future phases.
    - `audio` &mdash; Adapter receiving one-shot sound keys from future phases.
    - `log` &mdash; Replacement warning log, or null to retain the current binding's log.

`public void ResetPerformModules()`

:   Puts every module's effect back. Called on teardown and whenever playback is skipped, because a module that has dimmed the stage or moved the camera would otherwise leave it that way.

`public void SetCombatantArt(StableId combatantId, Sprite art)`

:   Gives one combatant its illustration, on the stage and on the rail at once. Existing source-facing metadata is preserved. Newly configured tokens default to right-facing source art; use the explicit overload when the imported illustration points elsewhere.

    - `combatantId` &mdash; The combatant to dress. Unknown ids are ignored.
    - `art` &mdash; The illustration, or null to strip it back to the lettered fallback. The same sprite becomes the bust crop on that combatant's turn-order chip, so a project assigns art once rather than twice.

`public void SetCombatantArt(StableId combatantId, Sprite art, FormationFacing sourceArtFacing)`

:   Gives a combatant art whose source orientation is supplied by the project. The direction is retained by the token and shared with the turn-order portrait, so stage art and the legacy rail never acquire independent mirror rules.

    - `combatantId` &mdash; The combatant to dress.
    - `art` &mdash; The source illustration, or null to clear it.
    - `sourceArtFacing` &mdash; Direction encoded by the unmirrored source sprite.

`public void SetCombatantArt(StableId combatantId, Sprite bodyArt, FormationFacing sourceArtFacing, Sprite portraitSprite, UiPortraitCrop portraitCrop)`

:   Assigns body art and an optional independent rail portrait crop.

    - `combatantId` &mdash; Combatant to dress.
    - `bodyArt` &mdash; Stage sprite, preserving the body's ground anchor.
    - `sourceArtFacing` &mdash; Direction encoded by the stage sprite.
    - `portraitSprite` &mdash; Optional independent rail sprite; body art is reused when null.
    - `portraitCrop` &mdash; Finite normalized crop, or default for exact legacy framing.

`public void SetCombatantPresence(StableId id, FormationPresence presence)`

:   Tells the presenter how a combatant is to be drawn against the others, whatever its token prototype says: `FormationPresence.Boss` always draws it as a boss, `FormationPresence.Standard` never does, and `FormationPresence.Automatic` lets the layout decide. The choice is kept by the presenter, so it holds before the presenter is bound, and it survives a new binding, a change of viewport and a teardown. A bound stage is laid out again at once.

    - `id` &mdash; The combatant the choice is for; an invalid id is ignored.
    - `presence` &mdash; How the combatant is to be drawn.

`public void SetReducedMotion(bool value)`

:   Applies a session preference to beats, stage and numbers without changing skin assets or battle state. A custom HUD applies its own matching policy. Existing perform modules reset when reduction is enabled. Effects already started outside those modules remain the host's responsibility.

    - `value` &mdash; Session preference, combined with the authored skin preference.

`public void SetSkillMotion(StableId skillId, PuppetActionKind kind)`

:   States how one skill moves its user, overriding what the presenter would decide from the skill's tags.

    - `skillId` &mdash; The skill.
    - `kind` &mdash; How its user moves; `PuppetActionKind.Auto` removes the override.

`public void SetStageLayout(FormationLayoutMode mode, IStageFloorSource floor)`

:   Chooses how the formation is laid out and what floor it stands on. May be called before `Bind` and while a battle runs: combatants move, resize and reorder in place and no combat state is touched. Line stands every combatant on one ground line at full scale, sized by population; Depth stands two shallow rows with perspective scale and needs a stage that declares a horizon and vanishing point; Legacy keeps the authored seat positions.

    - `mode` &mdash; Layout to use.
    - `floor` &mdash; What the stage declares about its floor, or null to stand the feet just above the dock band.

`public void SetViewport(FormationViewport value)`

:   Sets the stage viewport; rebuilds the stage when bound.

    - `value` &mdash; Pixel rectangle the formation is projected into. Written to the serialized stage fields even when the presenter is not bound yet, so the next `Bind` uses it and the inspector shows it.

`public void SetWorldInterfaceOpacity(float opacity)`

:   Gives the interface the stage draws in the world one opacity: the nameplates and bare health bars, the marks of the target preview (brackets, reticle, ground ring, region fill and row band) and the cue ring under a caster. A theme swap uses it to dip that interface together with the HUD of the view. The value multiplies what each element already draws and never replaces its own fade, so a plate in the middle of its fade goes on with it, only dimmer. Bodies, shadows, the dim that pushes the uninvolved back and floating numbers that are already alive are not touched. One is the normal value. It may be called at any time; `Bind` and `Teardown` return it to one, because a battle starts and ends with its interface whole.

    - `opacity` &mdash; Opacity from zero to one; values outside are clamped and NaN is taken as one.

`public void SetWorldSkin(CompiledBattleSkin skin)`

:   Chooses the skin that nameplates, floating numbers and the target preview follow when the HUD is a native view rather than the legacy interface root, which keeps supplying its own skin. May be called before `Bind` and again while a battle runs: nameplates, the generated backdrop and the target preview restyle in place, numbers that appear afterwards use the new skin, and no combat state changes.

    - `skin` &mdash; The skin to follow, or null to return to the package default.

`public void SetWorldStyle(BattleWorldStyle style)`

:   Chooses the plate policy and the painted target marks of the stage. May be called before `Bind` and while a battle runs: plates and marks change in place and no combat state, position or scale is touched.

    - `style` &mdash; The style to follow, or null to return to `BattleWorldStyle.Standard`.

`public void SkipAll()`

:   Finishes every queued beat immediately (visuals only). The HUD takes the authoritative state in the same call.

`public void Teardown()`

:   Releases pooled instances and clears playback state.

`public void Tick(float presentationDeltaSeconds)`

:   Advances beats and adapters by presentation delta seconds.

    - `presentationDeltaSeconds` &mdash; Elapsed seconds, unscaled: `Speed` is applied on top, so a host passes its frame delta straight in. Zero or less does nothing, which is how a host implements pause.

`public void Tick(float presentationDeltaSeconds, bool reduceMotion)`

:   Advances visual beat playback using the current speed and motion preference. An unbound, paused or nonpositive-delta call leaves playback and the motion preference unchanged; simulation time is never advanced here.

    - `presentationDeltaSeconds` &mdash; Elapsed seconds, unscaled. Zero or less, or a zero `Speed`, preserves pause.
    - `reduceMotion` &mdash; Whether to compress beats, suppress new decorative effects and keep stage feedback static. A compressed beat plays all its phases in one tick; only the floating numbers keep a pace, `ReducedNumberSpacingSeconds` apart, and a number that has to wait holds the beats behind it and the HUD with them.

`public bool TryGetPortraitCrop(StableId combatantId, out UiPortraitCrop crop)`

:   Finds the crop registered for a combatant's portrait by `SetCombatantArt`.

    - `combatantId` &mdash; The combatant to look up.
    - `crop` &mdash; Receives the registered crop, or the unconfigured default.
    - **Returns** &mdash; True when a configured crop exists.

`public bool TryGetPortraitSprite(StableId combatantId, out Sprite sprite)`

:   Finds the independent portrait sprite registered for a combatant, supplied apart from its body art.

    - `combatantId` &mdash; The combatant to look up.
    - `sprite` &mdash; Receives the registered portrait sprite, or null.
    - **Returns** &mdash; True when a portrait sprite was registered.

`public bool WarmUpWorldText()`

:   Draws once, far from every camera, every text this stage writes in the world, with the skin of the stage: a whole plate (name, value, bars), a bare bar, a floating number of each style, a critical one and a status word. The fonts first make the glyphs of printable ASCII and read their ligature, kerning and mark tables, and the canvases are updated at once, so the first plate and the first number of a battle find the text code compiled and the fonts loaded. The widgets are taken away after two steps of `Tick(float, bool)`; nothing is added to the stage, to the pool or to any combatant, and the battle is not touched.

    - **Returns** &mdash; True when the widgets were drawn and are waiting to be taken away; false when the presenter is not bound, is already warming up, or could not draw (the reason is in `WarmUpFault`).

---

## BattleStage2D

```csharp
public sealed class BattleStage2D : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStage2D.cs</small>

A neutral 2D battle stage. It maps normalized formation space to stage
space with the documented aspect-fit rule by reusing
`FormationLayoutCompiler.Project`, spawns one
`CombatantTokenView` per compiled occupancy through the pool
adapter, and resolves slot/approach/anchor positions for beats. No
transform ever feeds back into anything authoritative.

**Properties**

`public int DepthRankCount`

:   How many distinct depth ranks the last `Build` found. One means a flat arrangement, which is a legitimate answer and the reason nothing scales or fades on a rank formation.

`public bool ExternalBackdropActive`

:   True when an external backdrop, such as a layered theme backdrop, owns the area behind the combatants. The generated gradient and floor ellipse are then hidden and not rebuilt. Setting it back to false shows them again.

`public StageFloorPlan FloorPlan`

:   The floor the last layout was solved against, in projected stage pixels.

`public bool GeneratedBackdropVisible`

:   True when the generated gradient backdrop exists and is visible.

`public FormationLayoutMode LayoutMode`

:   The layout mode in use: `FormationLayoutMode.Line` by default. It differs from the requested mode when Depth was asked for and the stage declares no perspective or the art is too large; `LayoutResult` says why.

`public FormationLayoutResult LayoutResult`

:   The last solved layout, or null when no combatant is on the stage or the legacy layout is in use.

`public Func<object, bool> OwnsPointerSurface`

:   Optional identity filter for UI surfaces already covered by PointerBlocked. Other interfaces keep their normal raycast blocking.

`public Camera PickCamera`

:   The camera clicks are unprojected through. Left unset, the stage uses `Camera.main`, which is what the shipped setups have.

`public IReadOnlyDictionary<StableId, StageTokenPlacement> Placements`

:   Every token the last `Build` produced, keyed by combatant. Each entry carries the projected slot and approach points along with the slot's facing and sorting data, so a caller can read where a combatant stands without going through its transform.

`public BattleWorldPlateMode PlateMode`

:   Which plates the combatants draw; see `CombatantTokenView.SetPlatePolicy`.

`public Func<Vector2, bool> PointerBlocked`

:   Optional host screen-space HUD hit-test evaluated before stage picking. Binding a presenter preserves this callback.

`public FormationLayoutMode RequestedLayoutMode`

:   The layout mode the stage was asked for. The mode in use can differ; see `LayoutMode`.

`public int StageScreenHeightPx`

:   Height of the whole screen in pixels, when whoever frames the stage knows it; zero means it does not, and the layout recovers it from the viewport and `StageShareOfScreenPermille`. The share is a whole number of thousandths and the viewport is rounded, so the recovered height can be a pixel or two off (719 or 721 for 720); the height given here is used as it is.

`public int StageShareOfScreenPermille`

:   Share of the screen height the stage viewport covers, in thousandths. Sprite heights are fractions of the screen, so the stage recovers the screen height from the viewport with it. The default is the 52% the dock layout reserves.

`public StrikeEffectLayer StrikeEffects`

:   The layer that draws what joins the author of a blow to a target it does not touch: the link, the mark on the body and the wave of a blow at several. Made the first time it is asked for, as a child of the stage, and stepped by the stage.

`public int TokenCount`

:   How many tokens are currently spawned. It can be lower than the layout's occupancy count without that being an error: a team whose formation fails to project is skipped with a warning, while an occupancy whose slot is missing from the preset or whose pool returns nothing is skipped silently.

`public float TokenPickRadiusPixels`

:   How near a click has to land, in formation pixels, before it counts as hitting a combatant. It is measured against the token's slot point, so it is a radius around where the combatant stands rather than the bounds of whatever art is on top of it.

`public bool TokenPickingEnabled`

:   Whether the stage watches for clicks on its tokens at all. Turn it off for a project that reads its own input; with no listener attached the watch already costs nothing.

`public float TokenScale`

:   How far combatant art is scaled to fit the stage it was given. Art has a fixed world size, so a stage smaller than the box it was drawn for does not shrink it - the combatants simply run off the edges, which is what a 3v3 of painted characters did in portrait. Scaling by the tighter of the two axes keeps a whole formation on the stage at any shape without re-authoring a single slot, and leaves the authoring reference untouched at exactly 1. The legacy layout draws every token at this scale. The line and depth layouts size combatants by population or by the horizon from the art they measure, and use this scale only for tokens whose art has not been measured yet, such as the fallback card.

`public IReadOnlyDictionary<StableId, CombatantTokenView> Tokens`

:   Every spawned token by combatant id, for a caller that has to walk the whole field rather than look one combatant up. Read only, and the instances belong to the pool: reposition or tint one and you must put it back, because the stage will not recompute it.

`public float UnitsPerPixel`

:   World units one projected formation pixel is worth on this stage. Exposed because anything drawn against a combatant -- a targeting cursor, a host's own marker -- has to be sized in the same currency the stage placed that combatant in, and guessing it produces a widget that looks right at one resolution only.

`public FormationViewport Viewport`

:   The viewport the current layout was projected against, as handed to `Build`. Nothing re-projects on its own, so a change of screen size means building again.

**Fields**

`public const int BackdropSortingOrder`

:   Sorting order the stage backdrop is drawn at, far below any token.

`public const float RankGroupingFraction`

:   How far apart two ground lines have to be, as a fraction of the projected stage height, before they count as different depth ranks. Some slack is required rather than optional: a formation's seats are authored in integer normalized space and then projected through an aspect fit, so two seats meant to share a ground line arrive a fraction of a pixel apart and would otherwise be staged as two ranks with an invisible size difference between them.

`public const float ReferenceStageHeight`

:   Height of that same authoring box.

`public const float ReferenceStageWidth`

:   The stage box combatant art is authored against, in projection pixels: a 1920-wide screen with the shipped bands taken off the top and bottom.

`public const string TokenPoolKey`

:   Pool key used for spawned combatant tokens when no per-combatant prototype has been registered. One prototype under this key serves every combatant.

**Events**

`public event Action<StableId> TokenClicked`

:   Raised when the player clicks a combatant on the stage. It is a report, not a command: the stage never decides what a click means, which is what lets the same click pick a target, open an inspector, or do nothing at all depending on who is listening.

**Methods**

`public void Build(CompiledEncounterFormationLayout layout, IPoolAdapter pool, FormationViewport viewport, PresentationLog log = null, float unitsPerPixel = 0.01f)`

:   Projects the layout at `viewport` and spawns the token set. Explicit; the stage never scans the scene.

    - `layout` &mdash; Compiled team formations and combatant-to-slot occupancies to project and spawn.
    - `log` &mdash; Optional log-once ledger for projection or missing-art warnings.
    - `pool` &mdash; Instance pool supplying shared or combatant-specific token objects.
    - `unitsPerPixel` &mdash; Positive conversion from projected formation pixels to Unity world units; invalid values use 0.01.
    - `viewport` &mdash; Integer projection rectangle applied independently to each team preset.

`public void Clear()`

:   Releases every token back to the pool and clears state.

`public bool ClearCombatantPresence(StableId combatantId)`

:   Removes what `SetCombatantPresence` told the stage about a combatant, so its token prototype decides again, and lays the stage out again.

    - `combatantId` &mdash; Combatant to forget.
    - **Returns** &mdash; True when the stage had something to forget.

`public void FinishBarAnimations()`

:   Completes every health, shield, cast and gauge bar transition, and every fade of a plate or of a dim, at once.

`public FormationPresence GetCombatantPresence(StableId combatantId)`

:   How a combatant is drawn against the others: what the stage was told for it, else what its token prototype carries, else Automatic.

    - `combatantId` &mdash; Combatant to ask about.
    - **Returns** &mdash; The presence the layout is solved with.

`public bool IsPointerOccluded(Vector2 screenPoint)`

:   Tests semantic HUD occlusion and raycasts from other UI surfaces.

    - `screenPoint` &mdash; Pointer position in screen pixels supplied to host/native hit tests and the current EventSystem.
    - **Returns** &mdash; True when either semantic blocker accepts the point or an unowned UI raycast hit remains; false when no surface blocks stage picking.

`public void RelayoutTokens()`

:   Solves the layout again from the authored seats and the art currently worn, then moves, scales and orders every token. Call it after art or ground anchors change, because the line is sized from the measured art.

`public void SetCombatantPresence(StableId combatantId, FormationPresence presence)`

:   Tells the stage how a combatant is to be drawn against the others, whatever its token prototype says: `FormationPresence.Boss` always draws it as a boss, `FormationPresence.Standard` never does, `FormationPresence.Automatic` lets the layout decide. The choice belongs to the stage and not to the token, so it survives `Clear` and a token reused for another combatant does not inherit it. The stage is laid out again.

    - `combatantId` &mdash; Combatant the choice is for; an invalid id is ignored.
    - `presence` &mdash; How the combatant is to be drawn.

`public void SetLayout(FormationLayoutMode mode, IStageFloorSource floor)`

:   Chooses how the formation is laid out and what floor it stands on, and applies it to the combatants already on the stage without respawning them. Line is the default.

    - `mode` &mdash; Line, Depth or the legacy authored-position layout.
    - `floor` &mdash; What the stage declares about its floor; null declares nothing, and the feet stand just above the dock band.

`public void SetPlateMode(BattleWorldPlateMode mode)`

:   Changes the plate policy of every spawned token and of tokens spawned later.

    - `mode` &mdash; Plate policy.

`public void SetPlateSelection(IReadOnlyList<StableId> selected)`

:   Names the combatants a target preview or pick selected. Under the compact policy the whole plate above the head belongs to a lone target: when two or more combatants are selected at once their plates would stand on top of each other, so none of them gets it and each keeps what it draws unselected (an opponent its bare bar, a player's combatant nothing).

    - `selected` &mdash; Selected combatants; null or empty clears the selection.

`public void SetPresentation(CompiledBattleSkin battleSkin, DisplayStringTable labelTable, StableId allyTeamId)`

:   Supplies the skin and label table used to dress spawned tokens with nameplates, bars, and status pips. Call before `Build`. Optional: without it tokens still mirror state onto their properties, which is what the headless tests assert against.

    - `allyTeamId` &mdash; Team identity whose spawned token plates receive the ally tint.
    - `battleSkin` &mdash; Compiled skin used to build token plates; null leaves tokens headless.
    - `labelTable` &mdash; Combatant ID labels used on token plates; null selects an empty table.

`public void SetPuppetMotion(PuppetMotionProfile motion, bool enabled, bool reduceMotion)`

:   Chooses the procedural motion every token of this stage plays, or switches it off. It reaches the tokens already standing and every token spawned afterwards. The presenter calls this; the stage never starts a motion of its own.

    - `motion` &mdash; The numbers the motion follows; null uses the shipped values.
    - `enabled` &mdash; False draws every body with its own renderer and never moves it.
    - `reduceMotion` &mdash; True to play only short fades.

`public void Tick(float presentationDeltaSeconds)`

:   Advances token plate animation by a visual delta.

    - `presentationDeltaSeconds` &mdash; Positive presentation-clock duration forwarded to every spawned token plate.

`public void TickPuppets(float presentationDeltaSeconds)`

:   Advances the procedural motion of every token by presentation time. The presenter calls it once per tick, after it has started that tick's motions.

    - `presentationDeltaSeconds` &mdash; Positive presentation-clock duration.

`public static string TokenPoolKeyFor(StableId combatantId)`

:   The pool key that gives one combatant its own body: `presentation.token.`. Register a prototype under this key and that combatant spawns from it; register nothing and it falls back to `TokenPoolKey`, so a project can give art to some combatants and not others. The stage only looks for the specific key when the pool can be asked whether it holds one, because `IPoolAdapter.Acquire` is allowed to fabricate an empty instance for an unknown key rather than returning null, and a fallback built on null would silently spawn blank tokens instead.

    - `combatantId` &mdash; The combatant whose prototype is wanted.
    - **Returns** &mdash; `presentation.token.` for exact prototype registration.

`public bool TryGetAnchorWorld(StableId combatantId, PresentationVfxAnchorKind kind, StableId? anchorId, out Vector3 world)`

:   Resolves a beat anchor to stage space for a combatant.

    - `anchorId` &mdash; Named VFX anchor when `kind` is Anchor; otherwise ignored.
    - `combatantId` &mdash; Spawned combatant whose compiled placement supplies the handle.
    - `kind` &mdash; Standing slot, approach point, or named anchor to resolve.
    - `world` &mdash; Receives the projected handle converted to stage-world units, or zero on failure.
    - **Returns** &mdash; True when the operation succeeds; otherwise false.

`public bool TryGetToken(StableId combatantId, out CombatantTokenView token)`

:   Returns the spawned token for a combatant, if present.

    - `combatantId` &mdash; Combatant identity used as the stage token dictionary key.
    - `token` &mdash; Receives the active pooled token view, or null when the combatant was not spawned.
    - **Returns** &mdash; True when the operation succeeds; otherwise false.

`public bool TryPickTokenAtScreen(Vector2 screenPoint, Camera camera, out StableId combatantId)`

:   Projects a pointer through `camera` and picks the nearest token on the stage plane. Input-system integrations can call this directly without depending on TurnHerald input packages.

    - `screenPoint` &mdash; Screen-space pointer position in pixels.
    - `camera` &mdash; Camera that produced the screen point.
    - `combatantId` &mdash; Picked combatant, or the default id.
    - **Returns** &mdash; True when the pointer reaches a token.

`public bool TryPickTokenAtWorld(Vector3 worldPoint, out StableId combatantId)`

:   Finds the combatant standing nearest a point on the stage.

    - `worldPoint` &mdash; The point to test, in world space, and only its x and y are read. Tokens are placed at world positions rather than under this transform, so this is measured against those positions directly.
    - `combatantId` &mdash; The combatant found, or the default id when none is near enough.
    - **Returns** &mdash; True when a combatant stands within `TokenPickRadiusPixels` of the point. Ties resolve to the lowest id so the same click always picks the same combatant.

`public bool TryProjectScreenToStage(Vector2 screenPoint, Camera camera, out Vector3 worldPoint)`

:   Projects one screen point onto the world-space stage plane at z = 0. A ray/plane intersection works for orthographic and perspective cameras, including cameras rotated away from the world z axis.

    - `screenPoint` &mdash; Screen-space pointer position in pixels.
    - `camera` &mdash; Camera that produced the screen point.
    - `worldPoint` &mdash; Intersection on the stage plane.
    - **Returns** &mdash; True when the camera ray reaches the stage plane.

`public void UpdateFromSnapshot(BattleSnapshot snapshot)`

:   Mirrors current snapshot state onto every token.

    - `snapshot` &mdash; Authoritative snapshot supplying health, shields, statuses, and death state for each spawned combatant.

---

## BattleStageBackdrop

```csharp
public sealed class BattleStageBackdrop : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageBackdrop.cs</small>

Optional background blur for the perform moment. **Off by default and never required.**

While a skill performs, everything behind the battle stage softens so the eye stays on
the participants. The shipped `FocusPerformModule` does the same job by
tinting non-participants, which costs nothing and works everywhere; this is the richer
alternative for a project that wants the background itself to go out of focus.

It renders the scene a second time, without TurnHerald's own content, into a
half-resolution RenderTexture, softens that through bilinear blits, and shows the
result on a quad behind the stage. This uses a secondary camera rather than
`OnRenderImage`; verify capture and blit behavior in your project's render pipeline.

**Only the background is blurred.** The capture hides the stage tokens and the battle
interface for the duration of its own render, so the participants are never in the
blurred image and never ghost behind their sharp selves.

The blur is live rather than a snapshot: it is re-rendered each frame while
`Strength` is above zero, so anything still moving behind the wash stays
readable. At zero it releases everything it allocated and costs nothing at all.

To enable: add it to the battle camera. Drive `Strength` yourself, or
register a `BackdropBlurPerformModule` to have it ride the perform beat.

**Properties**

`public bool IsActive`

:   True once the capture camera and its buffers exist.

`public float Strength`

:   How far out of focus the background is, 0 to 1. Zero tears the whole effect down. Writable so a perform module can pull focus on impact and ease it back. Values outside the range clamp rather than doing something surprising.

---

## BattleStageBackdropAsset

```csharp
public sealed class BattleStageBackdropAsset : ScriptableObject
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropAsset.cs</small>

Authored data of a stage backdrop: ordered sprite layers with parallax, and optional ambient particles.
A `BattleStageBackdropRig` renders it with default unlit sprite and particle materials. When a
theme references one, it replaces the generated gradient and floor of the stage.

**Properties**

`public IReadOnlyList<BattleBackdropAmbient> Ambient`

:   Ambient particle placements in authored order.

`public bool DeclaresFloor`

:   True when the stage declares where its floor is. When false the formation stands just above the dock band.

`public bool DeclaresPerspective`

:   True when the stage declares a horizon and a vanishing point, which the Depth layout needs.

`public float FloorBackEdgeY`

:   Height of the back edge of the open floor, normalized like `GroundLineY`. No foot may stand above it.

`public float GroundLineY`

:   Height of the line the feet of the Line layout stand on, normalized over the plate with the origin at its bottom.

`public float HorizonY`

:   Height of the horizon, normalized over the plate with the origin at its bottom.

`public IReadOnlyList<BattleBackdropLayer> Layers`

:   Sprite layers in authored order.

`public int PlateLayer`

:   Index of the layer whose sprite the contract is measured on.

`public Texture2D PropMask`

:   Optional mask texture over the plate: alpha of at least one half is a prop.

`public IReadOnlyList<BattleStageProp> Props`

:   Regions where no foot may stand, as polygons in plate coordinates.

`public float VanishingPointX`

:   Horizontal position of the vanishing point, normalized over the plate with the origin at its left.

**Methods**

`public void ClearFloor()`

:   Removes the floor contract, so the formation stands just above the dock band again.

`public void Configure(IEnumerable<BattleBackdropLayer> newLayers, IEnumerable<BattleBackdropAmbient> newAmbient)`

:   Replaces the layers and ambient placements, for code-built backdrops. The arrays are copied.

    - `newLayers` &mdash; Sprite layers; null clears them.
    - `newAmbient` &mdash; Ambient placements; null clears them.

`public void ConfigureFloor(int plateLayerIndex, float ground, float backEdge, float? horizon, float? vanishingX, IEnumerable<BattleStageProp> blocked)`

:   Sets the floor contract, for code-built backdrops, tests and the stage gizmo. Values are clamped to the plate.

    - `plateLayerIndex` &mdash; Layer whose sprite is the plate; a negative value uses the first layer.
    - `ground` &mdash; Height of the feet line, from 0 at the bottom of the plate to 1 at its top.
    - `backEdge` &mdash; Height of the back edge of the open floor.
    - `horizon` &mdash; Height of the horizon, or null to declare no perspective.
    - `vanishingX` &mdash; Horizontal position of the vanishing point, or null to declare no perspective.
    - `blocked` &mdash; Polygons where no foot may stand; null clears them.

`public void SetFloorLines(float? ground, float? backEdge, float? horizon, float? vanishingX)`

:   Moves the contract lines while a designer drags them. Each value that is not null is clamped to the plate.

    - `ground` &mdash; New ground line height, or null to keep it.
    - `backEdge` &mdash; New back edge height, or null to keep it.
    - `horizon` &mdash; New horizon height, or null to keep it.
    - `vanishingX` &mdash; New vanishing point position, or null to keep it.

`public void SetPerspectiveDeclared(bool declared)`

:   Turns the perspective declaration on or off without touching the horizon values.

    - `declared` &mdash; True when the plate has a horizon and vanishing point.

`public void SetPropMask(Texture2D mask)`

:   Sets the optional prop mask texture: a pixel with alpha of at least one half is a prop. The texture needs Read/Write enabled.

    - `mask` &mdash; Mask drawn over the plate, or null for none.

---

## BattleStageBackdropGeometry

```csharp
public static class BattleStageBackdropGeometry
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropGeometry.cs</small>

How a `BattleStageBackdropRig` places a backdrop layer on the stage, and the conversions between the plate (the
backdrop image's sprite, normalized with the origin at its bottom left) and the stage. The rig and the floor contract share these
functions, so a line drawn on the plate lands on the same pixel the rig draws it at.

The layer is placed at rest: parallax displaces it only while the camera leaves its resting position, and the contract is
measured at rest.

**Fields**

`public const int MaskGridColumns`

:   The number of columns and rows a prop mask texture is reduced to before it becomes polygons.

**Methods**

`public static Vector2 LayerOffset(BattleBackdropLayer layer, Rect stageWorldRect)`

:   The offset of a layer from the stage centre, in world units.

    - `layer` &mdash; Layer whose authored offset is read.
    - `stageWorldRect` &mdash; Stage rectangle in world units; the offset is a fraction of its size.
    - **Returns** &mdash; Offset in world units.

`public static float LayerScale(BattleBackdropLayer layer, Rect stageWorldRect)`

:   The scale a layer is drawn at against the stage rectangle: its own scale, times the cover fit and overscan for a covering layer.

    - `layer` &mdash; Layer to scale; it needs a sprite for a covering fit.
    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - **Returns** &mdash; Uniform scale applied to the sprite.

`public static Vector2 PlateToStage(Rect plateWorldRect, Rect stageWorldRect, Vector2 plate)`

:   Converts a plate coordinate to a position normalized over the stage rectangle, with the origin at its bottom left.

    - `plateWorldRect` &mdash; The plate's world rectangle.
    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `plate` &mdash; Plate coordinate.
    - **Returns** &mdash; Position over the stage; values outside 0..1 lie off the stage.

`public static Vector2 PlateToWorld(Rect plateWorldRect, Vector2 plate)`

:   Converts a plate coordinate to world space.

    - `plateWorldRect` &mdash; The plate's world rectangle.
    - `plate` &mdash; Plate coordinate: (0,0) bottom left, (1,1) top right.
    - **Returns** &mdash; The world position.

`public static StageFloorPlan ResolveFloorPlan(BattleStageBackdropAsset backdrop, Rect stageWorldRect, float unitsPerPixel)`

:   Resolves a backdrop's floor contract into projected stage pixels for the formation: the ground line, the back edge of the open floor, the horizon, the vanishing point and the prop outlines, all in the pixel space of the stage viewport.

    - `backdrop` &mdash; Backdrop to read; null or one that declares no floor gives `StageFloorPlan.None`.
    - `stageWorldRect` &mdash; Stage rectangle in world units, as the presenter reports it.
    - `unitsPerPixel` &mdash; World units per stage pixel.
    - **Returns** &mdash; The plan the formation solver reads.

`public static Vector2 StageToPlate(Rect plateWorldRect, Rect stageWorldRect, Vector2 stage)`

:   Converts a position normalized over the stage rectangle to a plate coordinate.

    - `plateWorldRect` &mdash; The plate's world rectangle.
    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `stage` &mdash; Position over the stage, origin at its bottom left.
    - **Returns** &mdash; Plate coordinate.

`public static bool TryGetLayerWorldRect(BattleBackdropLayer layer, Rect stageWorldRect, out Rect rect)`

:   The rectangle a layer's sprite covers in world space when the rig draws it at rest.

    - `layer` &mdash; Layer with a sprite.
    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `rect` &mdash; Receives the sprite's world rectangle.
    - **Returns** &mdash; False when the layer has no sprite or the stage rectangle is empty.

`public static bool TryGetPlateWorldRect(BattleStageBackdropAsset backdrop, Rect stageWorldRect, out Rect plateWorldRect)`

:   The world rectangle of the plate a backdrop's floor contract is measured on.

    - `backdrop` &mdash; Backdrop whose plate layer is used.
    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `plateWorldRect` &mdash; Receives the plate's world rectangle.
    - **Returns** &mdash; False when the backdrop has no sprite on its plate layer.

`public static Vector2 WorldToPlate(Rect plateWorldRect, Vector2 world)`

:   Converts a world position to a plate coordinate.

    - `plateWorldRect` &mdash; The plate's world rectangle.
    - `world` &mdash; World position.
    - **Returns** &mdash; Plate coordinate: (0,0) bottom left, (1,1) top right; values outside 0..1 lie off the plate.

---

## BattleStageBackdropRig

```csharp
public sealed class BattleStageBackdropRig : MonoBehaviour
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropRig.cs</small>

Renders a `BattleStageBackdropAsset` behind the stage and swaps between backdrops with a
crossfade. Layers are plain sprite renderers and the ambient prefabs are the project's own particles, so no
shader is created here and the result is the same in Built-in and URP.

The outgoing backdrop stays fully opaque until the incoming one is fully opaque, so the swap never shows the
camera clear color. Time is driven by `Tick` with the presentation clock; nothing runs in Update.
The incoming layers fade in with an ease-out, one curve for the plate, its particles and the ambient emission.
The particles of the outgoing backdrop stop being born in the first frame and fade out with the swap, so no flame
of the old stage burns over the new one and none is cut off at the end, and the particles of the incoming
backdrop are born at the pace the plate arrives. The ambient of the incoming backdrop also follows the opacity of its
plate, frame by frame: the particles already in the air (a flame that was prewarmed when it was built) and the painted
lights and glows of its ambient prefabs are drawn at it, so no flame is brighter than the stage it belongs to, and at
the end of the swap nothing is left dimmed.
Reduce Motion holds the parallax still and shortens a swap to a dissolve of `ReducedCrossfadeSeconds`:
a fade moves nothing, and a stage that changes in a single frame is the flash a player who asked for less motion
does not want either.

**Properties**

`public int BaseSortingOrder`

:   Sorting order the backdrop starts at. Layers add their own order to it.

`public float CrossfadeSeconds`

:   Crossfade length in seconds, clamped from zero to `MaximumCrossfadeSeconds`. Zero swaps instantly.

`public BattleStageBackdropAsset Current`

:   The backdrop that is shown, or that the rig is fading toward. Null when none.

`public Camera FollowCamera`

:   Camera used to drive parallax from `LateUpdate`; null leaves it to `SetParallaxFocus`. Parallax is measured from where the camera stood when a backdrop was shown or the stage rectangle last changed, so a camera that frames the stage off center does not displace any layer at rest.

`public float IncomingOpacity`

:   Opacity of the backdrop fading in, from zero to one; zero when no backdrop is entering.

`public bool IsCrossfading`

:   True while a swap is in progress.

`public float OutgoingOpacity`

:   Opacity of the backdrop that was visible before the swap, from zero to one. It stays at one while a new backdrop fades in.

`public bool ReduceMotion`

:   When true, parallax stays at rest and a swap is a dissolve of at most `ReducedCrossfadeSeconds` instead of a cut. A swap already under way is shortened to that length, not finished at once.

`public int RendererCount`

:   Number of sprite renderers currently alive in both groups.

`public string SortingLayerName`

:   Sorting layer name used by every renderer; empty keeps the default layer.

**Fields**

`public const int DefaultBaseSortingOrder`

:   Sorting order the backdrop starts at, far below any combatant.

`public const float DefaultCrossfadeSeconds`

:   Default crossfade length in seconds.

`public const float MaximumCrossfadeSeconds`

:   Longest crossfade accepted, in seconds.

`public const float Overscan`

:   Extra size given to covering layers so camera movement never reveals an edge.

`public const float ReducedCrossfadeSeconds`

:   Seconds a swap takes while Reduce Motion is on, at most: a short dissolve, not a cut.

**Methods**

`public void Clear()`

:   Removes every renderer and particle immediately.

`public void FinishCrossfade()`

:   Completes any swap in progress at once.

`public void SetParallaxFocus(Vector2 cameraOffset)`

:   Sets how far the camera has moved from its resting position, in world units, to drive parallax.

    - `cameraOffset` &mdash; Camera displacement from its resting position, in world units.

`public void SetWorldRect(Rect rect)`

:   Sets the stage rectangle, in world units, that layers are fitted to.

    - `rect` &mdash; Stage rectangle in world space.

`public void Show(BattleStageBackdropAsset backdrop, bool instant = false)`

:   Shows a backdrop, replacing the current one.

    - `backdrop` &mdash; Backdrop to show; null removes the current backdrop.
    - `instant` &mdash; True to swap without a crossfade. A zero crossfade length also swaps instantly. Reduce Motion does not: it dissolves, as long as there is a backdrop on screen to dissolve from, so a backdrop shown for the first time still appears at once.

`public void Tick(float deltaSeconds)`

:   Advances the crossfade by presentation time.

    - `deltaSeconds` &mdash; Positive visual delta in seconds; other values are ignored.

---

## BattleStageBloom

```csharp
public sealed class BattleStageBloom : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageBloom.cs</small>

Optional stage bloom and vignette. **Off by default and never required.**

The shipped look needs no post-processing: glow is drawn inside the
skinned-surface shader. That is why TurnHerald depends on no
post-processing package at all, and why a buyer's existing volumes,
renderer features, and profiles cannot conflict with it.

This component exists only for buyers who want a softer bloom across the
whole stage and are not already running their own post stack. It is a
self-contained image effect with no package dependency.

Built-in render pipeline only. Under URP or HDRP, `OnRenderImage` is
never called, so rather than silently doing nothing this component detects
the active pipeline, logs one explanatory warning, and disables itself.
Use that pipeline's own Bloom volume override instead.

To enable: add it to the battle camera and tick `Enabled`. Nothing in
the package adds it for you.

**Properties**

`public float Intensity`

:   Bloom strength added over the stage. Zero skips the bloom pass entirely and blits the frame through unchanged. Writable so a perform module can pulse it on impact and ease it back to the authored resting value. Negative values clamp to zero rather than inverting the effect.

`public bool IsSupportedPipeline`

:   True when this effect can run in the active pipeline.

`public float VignetteStrength`

:   Corner darkening strength, 0 to 1. Zero skips the vignette. Writable for the same reason `Intensity` is: a perform module can close the frame in on impact and ease it back to the authored resting value. Independent of the bloom -- a vignette with `Intensity` at zero draws the vignette and no bloom.

**Fields**

`public const string ShaderName`

:   Name of the optional bloom shader.

`public const string ShaderResourcePath`

:   Resources path of the optional bloom shader.

---

## BattleStageFloorSource

```csharp
public sealed class BattleStageFloorSource : IStageFloorSource
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropGeometry.cs</small>

Reads the floor contract of a `BattleStageBackdropAsset` for the formation. It resolves against the stage rectangle it
is asked about, so the contract follows the window as it is resized.

**Constructors**

`public BattleStageFloorSource(BattleStageBackdropAsset backdrop)`

:   Creates a source for a backdrop.

    - `backdrop` &mdash; Backdrop whose contract is read; null declares nothing.

**Properties**

`public BattleStageBackdropAsset Backdrop`

:   The backdrop whose contract this source reads.

**Methods**

`public override bool Equals(object obj)`

:   Two sources are equal when they read the same backdrop, so the stage does not lay out again for a source that changed nothing.

    - `obj` &mdash; Object to compare with.
    - **Returns** &mdash; True when `obj` is a source of the same backdrop.

`public override int GetHashCode()`

:   Hash of the backdrop.

    - **Returns** &mdash; A hash consistent with `Equals(object)`.

`public StageFloorPlan Resolve(Rect stageWorldRect, float unitsPerPixel)`

:   Resolves the contract against the stage rectangle.

    - `stageWorldRect` &mdash; Stage rectangle in world units.
    - `unitsPerPixel` &mdash; World units per projected pixel.
    - **Returns** &mdash; The plan in projected stage pixels.

---

## BattleStageFrame

```csharp
public sealed class BattleStageFrame : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageFrame.cs</small>

Controls where the battle stage sits on screen and how large it is.

Without this, the stage was pinned to a hardcoded 1920x1080 viewport, so on
any other resolution the formation was cropped or floated in dead space,
and a buyer had no supported way to reserve screen area for their own
interface. Every value here is presentation-only: moving or resizing the
stage cannot change a state hash, an event chain, or a result.

Attach next to a `BattlePresenter`; it re-applies the viewport
whenever the screen, safe area, or any field changes.

**Properties**

`public FormationViewport AppliedViewport`

:   The viewport most recently pushed to the presenter.

**Methods**

`public void ApplyNow()`

:   Recomputes and applies the stage viewport. Cheap to call repeatedly: when the result matches the viewport already applied, the presenter is not touched at all. Screen and safe-area changes trigger this automatically, so an explicit call is only needed to force a re-frame.

`public void ApplyNow(int width, int height, Rect safeArea)`

:   Applies framing for an explicit display size, including editor Game view dimensions.

    - `width` &mdash; Display width in pixels. Outside Explicit mode, non-positive values resolve to the frame's 1x1 fallback; Explicit mode ignores display dimensions.
    - `height` &mdash; Display height in pixels. Outside Explicit mode, non-positive values resolve to the frame's 1x1 fallback; Explicit mode ignores display dimensions.
    - `safeArea` &mdash; Safe area in the same bottom-left pixel coordinate space as the display.

`public FormationViewport Resolve(int screenWidth, int screenHeight, Rect safeAreaPixels)`

:   Computes the stage viewport for a screen. Public and parameterised so EditMode tests can verify every mode and margin without a device. Pure: it reads the serialized fields but applies nothing to the presenter.

    - `screenWidth` &mdash; Screen width in pixels. Outside Explicit mode, a non-positive value falls back to a 1x1 viewport rather than throwing.
    - `screenHeight` &mdash; Screen height in pixels, treated as `screenWidth` is.
    - `safeAreaPixels` &mdash; The device safe area in pixels. Ignored unless the safe-area option is on, and ignored when its width or height is not positive, so passing a default Rect is a valid way to ask for the full screen.
    - **Returns** &mdash; The stage rectangle in pixels with a bottom-left origin, never smaller than 1x1. In Explicit mode the screen arguments are ignored entirely.

`public void SetInterfaceLayout(IBattleStageLayout layout)`

:   Binds an optional native/custom view's stage reservation. Null restores legacy or host margins.

    - `layout` &mdash; View supplying normalized stage bounds, or null to restore the configured margin policy. The viewport is refreshed immediately.

`public void SetMode(StageFrameMode value)`

:   Sets the framing mode and re-frames immediately. Exists because a scene that builds its presenter at runtime, as the runtime demo does, has no inspector to set this in. `StageFrameMode.FullScreen` is what gives a wider screen more stage instead of wider empty gutters.

    - `value` &mdash; How the stage rectangle is derived from the screen.

---

## BattleStageInformationBank

```csharp
public sealed class BattleStageInformationBank
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageInformationBanks.cs</small>

A side rail. Entries are never discarded when the pilot capacity is exceeded.

**Properties**

`public bool CapacityExceeded`

:   Whether the retained entries exceed the visible three-row capacity.

`public IReadOnlyList<BattleStageInformationEntry> Entries`

:   All entries retained for the side, including overflow entries.

`public BattleStageInformationBankSide Side`

:   Rail side represented by this bank.

---

## BattleStageInformationBankSide

```csharp
public enum BattleStageInformationBankSide
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageInformationBanks.cs</small>

Which side of the information rail receives a team.

| Value | Meaning |
| --- | --- |
| `Left` | Left information rail. |
| `Right` | Right information rail. |

---

## BattleStageInformationBanks

```csharp
public sealed class BattleStageInformationBanks : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageInformationBanks.cs</small>

Optional, renderer-independent composition information for the two side
rails. It is inert until a presenter calls `Configure`.

**Properties**

`public IReadOnlyList<string> Diagnostics`

:   Layout diagnostics produced while rebuilding the banks.

`public bool IsConfigured`

:   Whether a stage has been configured for the banks.

`public BattleStageInformationBank Left`

:   Current left-side bank, or an empty bank after clearing.

`public BattleStageInformationBank Right`

:   Current right-side bank, or an empty bank after clearing.

**Fields**

`public const int BackingHorizontalExpansionPixels`

:   Horizontal backing expansion reserved around a cell.

`public const int BackingVerticalExpansionPixels`

:   Vertical backing expansion reserved around a cell.

`public const int CellPixels`

:   Authored side-cell size in pixels.

`public const int ContentHeightPixels`

:   Content height remaining inside a side-cell backing.

`public const int ContentWidthPixels`

:   Content width remaining inside a side-cell backing.

`public const int FirstTopPixels`

:   Top offset of the first rail row in full-HUD pixels.

`public const int MinimumHudWidthPixels`

:   Minimum full-HUD width that keeps both side rails readable.

`public const int RailLeftPixels`

:   Left rail inset from the full-HUD left edge in pixels.

`public const int RailRightPixels`

:   Right rail reference position in the default 1920-pixel HUD.

`public const int RailWidthPixels`

:   Authored width of each side rail in pixels.

`public const int RowStepPixels`

:   Vertical step between rail rows in full-HUD pixels.

`public const int RowsPerSide`

:   Maximum number of visible pilot rows per side.

**Methods**

`public void Clear()`

:   Clears the optional seam and all derived entries.

`public void Configure(BattleStage2D source, int fullHudWidthPixels, int fullHudHeightPixels, float pixelUnits, StableId playerTeam)`

:   Builds the pilot rail from a stage. The player identity is compared as data; no team display name or ordering convention is inferred.

    - `source` &mdash; Stage whose current placements populate the banks.
    - `fullHudWidthPixels` &mdash; Full-HUD width in pixels.
    - `fullHudHeightPixels` &mdash; Full-HUD height in pixels.
    - `pixelUnits` &mdash; World units represented by one authored pixel.
    - `playerTeam` &mdash; Team identity used by the default side mapping.

`public void Configure(BattleStage2D source, int fullHudWidthPixels, int fullHudHeightPixels, float pixelUnits, StableId playerTeam, IReadOnlyList<BattleStageInformationSide> sides)`

:   Builds the rail with explicit team-to-side identities.

    - `source` &mdash; Stage whose current placements populate the banks.
    - `fullHudWidthPixels` &mdash; Full-HUD width in pixels.
    - `fullHudHeightPixels` &mdash; Full-HUD height in pixels.
    - `pixelUnits` &mdash; World units represented by one authored pixel.
    - `playerTeam` &mdash; Team identity used when an explicit mapping is absent.
    - `sides` &mdash; Optional explicit team-to-side assignments.

`public static RectInt PilotCell(int fullHudHeightPixels, BattleStageInformationBankSide side, int row)`

:   Returns one pilot cell in full-HUD pixel coordinates.

    - `fullHudHeightPixels` &mdash; Full-HUD height in pixels.
    - `side` &mdash; Rail side for the cell.
    - `row` &mdash; Zero-based visible rail row.
    - **Returns** &mdash; The full-HUD rectangle assigned to the requested cell.

`public static RectInt PilotCell(int fullHudWidthPixels, int fullHudHeightPixels, BattleStageInformationBankSide side, int row)`

:   Returns one pilot cell in full-HUD pixel coordinates.

    - `fullHudWidthPixels` &mdash; Full-HUD width in pixels.
    - `fullHudHeightPixels` &mdash; Full-HUD height in pixels.
    - `side` &mdash; Rail side for the cell.
    - `row` &mdash; Zero-based visible rail row.
    - **Returns** &mdash; The full-HUD rectangle assigned to the requested cell.

`public void SetSelection(StableId actor, IReadOnlyList<StableId> targets)`

:   Marks the actor and selected targets for a legible plate highlight.

    - `actor` &mdash; Current actor identity.
    - `targets` &mdash; Current target identities, or null for no targets.

---

## BattleStageInformationEntry

```csharp
public readonly struct BattleStageInformationEntry
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageInformationBanks.cs</small>

One combatant retained by a side bank, including overflow entries.

**Constructors**

`public BattleStageInformationEntry(StableId combatantId, StableId teamId, ProjectedFormationPoint projected, BattleStageInformationBankSide side, RectInt cell, bool hasCell, Vector2 worldPosition, bool isActor, bool isTarget)`

:   Initializes the retained rail entry with projected formation, cell and selection data.

    - `combatantId` &mdash; Combatant identity represented by the entry.
    - `teamId` &mdash; Team identity associated with the combatant.
    - `projected` &mdash; Projected formation information for the combatant.
    - `side` &mdash; Rail side containing the entry.
    - `cell` &mdash; Full-HUD pixel cell assigned to the entry.
    - `hasCell` &mdash; Whether the entry fits within the visible rail capacity.
    - `worldPosition` &mdash; World-space position corresponding to the assigned cell.
    - `isActor` &mdash; Whether the entry is the current actor.
    - `isTarget` &mdash; Whether the entry is one of the current targets.

**Properties**

`public RectInt Cell`

:   Full-HUD pixel cell assigned to the entry.

`public StableId CombatantId`

:   Combatant identity represented by the entry.

`public bool HasCell`

:   Whether the entry fits within the visible rail capacity.

`public bool IsActor`

:   Whether the entry is the current actor.

`public bool IsTarget`

:   Whether the entry is one of the current targets.

`public ProjectedFormationPoint Projected`

:   Projected formation information for the combatant.

`public BattleStageInformationBankSide Side`

:   Rail side containing the entry.

`public StableId TeamId`

:   Team identity associated with the combatant.

`public Vector2 WorldPosition`

:   World-space position corresponding to the assigned cell.

---

## BattleStageInformationSide

```csharp
public readonly struct BattleStageInformationSide
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageInformationBanks.cs</small>

Maps a caller-owned team identity to a rail side without naming assumptions.

**Constructors**

`public BattleStageInformationSide(StableId teamId, BattleStageInformationBankSide side)`

:   Creates an explicit team-to-rail assignment.

    - `teamId` &mdash; Team identity assigned to the rail.
    - `side` &mdash; Rail side that receives the team.

**Properties**

`public BattleStageInformationBankSide Side`

:   Rail side assigned to the team.

`public StableId TeamId`

:   Team identity assigned to the rail.

---

## BattleStageProp

```csharp
public sealed class BattleStageProp
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationUnity/BattleStageBackdropAsset.cs</small>

A region of the stage plate where no foot or body may stand: a staircase, a well, a wall, a stack of rocks. The outline is a
closed polygon in plate coordinates, normalized over the plate sprite with the origin at its bottom left, so it does not change
when the plate is rescaled or the stage is resized.

**Fields**

`public string Name`

:   Name shown in validation messages and in the stage gizmo.

`public Vector2[] Outline`

:   Polygon corners in plate coordinates: (0,0) is the bottom left of the plate and (1,1) its top right. Fewer than three corners block nothing.

**Methods**

`public static BattleStageProp Rectangle(string name, Vector2 min, Vector2 max)`

:   Creates a rectangular prop.

    - `name` &mdash; Name shown in messages.
    - `min` &mdash; Bottom left corner in plate coordinates.
    - `max` &mdash; Top right corner in plate coordinates.
    - **Returns** &mdash; A prop whose outline is the rectangle.

---

## BattleWorldPlateMode

```csharp
public enum BattleWorldPlateMode
```

`TurnHerald.UI` &middot; <small>Runtime/PresentationCore/BattleWorldPlateMode.cs</small>

Which plates the combatants on the stage draw. The choice belongs to the theme, because it decides where health is read.

| Value | Meaning |
| --- | --- |
| `Standard` | Every combatant draws its whole plate: name, health, shield, status pips. |
| `Compact` | One health representation per combatant. |

---

## BattleWorldStyle

```csharp
public sealed class BattleWorldStyle
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleWorldStyle.cs</small>

How a theme dresses the plates and target marks of the stage, apart from the HUD and the compiled skin: which plates the
combatants draw and the painted marks of a selected target. It never changes formation, scale or framing. A style is
immutable; hosts swap it with `BattlePresenter.SetWorldStyle`.

**Constructors**

`public BattleWorldStyle(BattleWorldPlateMode plateMode = BattleWorldPlateMode.Compact, Sprite reticle = null, Sprite groundRing = null, float reticlePulseSeconds = TargetPreviewView.DefaultPulseSeconds)`

:   Creates a style.

    - `plateMode` &mdash; Which plates the combatants draw. Compact unless a layout that has room for whole plates asks otherwise.
    - `reticle` &mdash; Square sprite of four corner brackets, fitted to the painted body of each picked target without turning; null uses the procedural ring.
    - `groundRing` &mdash; Elliptical ring drawn on the ground under previewed targets; null uses the procedural ring.
    - `reticlePulseSeconds` &mdash; Seconds one subtle pulse of the reticle takes; zero or less keeps it still. Reduced motion always keeps it still.

**Properties**

`public static BattleWorldStyle Default`

:   The package default: the compact plates and no painted marks. One health representation per combatant -- the party's is in the party panel, an opponent draws a bare bar and a selected target the whole plate above its head -- because the line layout stands the combatants too close for the whole plate of every one of them, and both shipped themes use it.

`public Sprite GroundRing`

:   Ground ring sprite, or null.

`public BattleWorldPlateMode PlateMode`

:   Which plates the combatants draw.

`public Sprite Reticle`

:   Four-bracket reticle sprite, or null.

`public float ReticlePulseSeconds`

:   Seconds one pulse of the reticle takes; zero or less keeps it still.

`public static BattleWorldStyle Standard`

:   The package default style, kept under the name it had when the default drew whole plates; it is the same style as `Default` and its plate mode is `BattleWorldPlateMode.Compact`. Use `WholePlates` for the style that draws a whole plate under every combatant.

`public static BattleWorldStyle WholePlates`

:   A whole plate under every combatant and no painted marks: name, health, shield and status pips for each one. It is for the legacy layout and for the stage that keeps its information on the sides, which have room for it; the line layout does not.

**Methods**

`public bool SameAs(BattleWorldStyle other)`

:   Tests whether two styles would draw the same plates and marks.

    - `other` &mdash; Style to compare with; null differs.
    - **Returns** &mdash; True when every value is equal.

---

## BeatDeriver

```csharp
public static class BeatDeriver
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BeatDeriver.cs</small>

Pure event-to-beat derivation. Every gameplay event maps to exactly one
beat: the resolved recipe when one matches, otherwise an instant
no-visual beat. The deriver reads only the event's property set and the
supplied recipe set/catalog, performs no simulation math, and holds no
engine reference.

**Methods**

`public static PresentationBeatContext BuildContext(BattleEvent battleEvent)`

:   Extracts the beat context from an event's property set.

    - `battleEvent` &mdash; The event to read; only its typed properties are inspected.
    - **Returns** &mdash; The extracted context, or the default context when the event is null. Source falls back to the actor id, and amount to the actual delta when present, otherwise the plain amount; both are absent when untyped. The critical, shielded, and killing-blow flags read false unless the event says otherwise.

`public static PresentationBeatContext BuildContext(BattleEvent battleEvent, bool critical)`

:   Extracts the beat context from an event's property set, with a critical hit the host read from elsewhere.

    - `battleEvent` &mdash; The event to read; only its typed properties are inspected.
    - `critical` &mdash; True when the hit was critical although the event carries no flag; the event's own flag still counts.
    - **Returns** &mdash; The extracted context, or the default context when the event is null.

`public static PresentationBeat Derive(BattleEvent battleEvent, PresentationRecipeSet recipes, CompiledAuthoringCatalog catalog)`

:   Derives the single beat for one event (never null).

    - `battleEvent` &mdash; The gameplay event to map; null yields a default context.
    - `recipes` &mdash; The candidate recipe set searched for a match.
    - `catalog` &mdash; Compiled content supplying the skill/status tag tables that tag selectors match against.
    - **Returns** &mdash; A beat pairing the event's context with the winning recipe, or with a null recipe (an instant no-visual beat) when no recipe matches.

`public static PresentationBeat Derive(BattleEvent battleEvent, PresentationRecipeSet recipes, CompiledAuthoringCatalog catalog, bool critical)`

:   Derives the single beat for one event when the host knows the hit was critical although the event does not say so.

    - `battleEvent` &mdash; The gameplay event to map; null yields a default context.
    - `recipes` &mdash; The candidate recipe set searched for a match.
    - `catalog` &mdash; Compiled content supplying the skill/status tag tables that tag selectors match against.
    - `critical` &mdash; True when the hit was critical. The engine does not write the critical flag on its damage events, so a host that read it from the formula evidence says so here; the event's own flag still counts.
    - **Returns** &mdash; A beat pairing the event's context with the winning recipe, or with a null recipe (an instant no-visual beat) when no recipe matches.

---

## CombatantPuppet

```csharp
public sealed class CombatantPuppet
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/CombatantPuppet.cs</small>

A procedural puppet for one static illustration: wind-up, advance, contact squash, return, knock-back, red hit tint, knock-out
dissolve and an idle breath, all computed from a few numbers and a clock. It holds no object of the engine and reads no clock
of its own, so the presenter's clock (a manual one included) is the only time it knows, and it can be stepped in a plain test.
With reduced motion it plays only short fades: no lean, squash, push or breath.

A cast adds a second layer under those motions: a pose that is held for as long as the cast lasts (a crouch, a head slid
sideways over fixed feet, a slow pulse and a glow), kept apart from the motions that start and end, so a blow received while
casting is played over the pose and ends back in the pose, not in a body at rest.

**Properties**

`public int ContactCount`

:   How many times the body has made contact since its wind-up or its advance began, which is how the presenter tells the first contact of a blow that reaches several targets from the lighter ones that follow it.

`public float Direction`

:   The world sign of the way the last target lay, which is the way a return runs back from.

`public float FreezeRemainingSeconds`

:   Seconds of hit stop still to run.

`public bool HasAdvanced`

:   True from the advance toward a target until the walk back begins. A blow that reaches several targets advances once and returns once, and this is how the presenter knows the advance has been made.

`public bool HasCastPose`

:   True while any part of the cast pose is on the body, held or still leaving.

`public bool HasStrikePose`

:   True while the pose of a blow from afar is on the body, on its way in, held or on its way out.

`public bool IsCasting`

:   True from `BeginCast` until the cast is released or cancelled: the body holds the cast pose.

`public bool IsDisplaced`

:   True while the body is away from where it stands: winding up, advancing, in contact or returning.

`public bool IsFrozen`

:   True while the body is held still by a hit stop.

`public bool IsReturning`

:   True while the body is walking back to where it stands.

`public bool IsSquashed`

:   True while a squash is still relaxing.

`public bool KoFinished`

:   True once the knock-out has finished: the body is invisible and its shadow is gone.

`public float KoProgress`

:   How far the knock-out has run, 0 before it starts and 1 once it has finished.

`public bool KoStarted`

:   True from the first frame of a knock-out until it is reset.

`public float OffsetXPixels`

:   Where the body is along the ground, in stage pixels.

`public PuppetMotionProfile Profile`

:   The numbers the motion follows.

`public bool ReduceMotion`

:   True when only short fades play: no lean, squash, push or breath.

`public float StrikeLeanDegrees`

:   Degrees the pose of a blow from afar leans the body now, positive toward world -x like `PuppetPose.LeanDegrees`; zero when there is none.

**Methods**

`public void Advance(float direction, float distancePixels, float seconds)`

:   Advances toward the target, leaning into the blow. The move starts from rest and eases out, so the first frame of it is a small share of the fastest. A body with less room than `PuppetMotionProfile.MinimumStrikeTravelPixels` in front of it does not move along the ground at all: it strikes where it stands.

    - `direction` &mdash; World sign of the way the target lies.
    - `distancePixels` &mdash; How far to move from the resting place, in stage pixels; never negative.
    - `seconds` &mdash; How long the move takes, in seconds.

`public void Anticipate(float direction)`

:   Winds up for an attack: the body steps back and leans away from its target, eased in.

    - `direction` &mdash; World sign (+1 or -1) of the way the target lies.

`public void Anticipate(float direction, float maxRecoilPixels)`

:   Winds up for an attack: the body leans away from its target and steps back, eased in, but never further back than there is room for: a body that stands in front of another does not walk into it to gather itself.

    - `direction` &mdash; World sign (+1 or -1) of the way the target lies.
    - `maxRecoilPixels` &mdash; The most the body may step back, in stage pixels; the profile's own recoil when it is smaller.

`public void BeginCast(float shearDirection, float shearDegrees)`

:   Starts the pose of a cast and holds it until `ReleaseCast` or `CancelCast`: the body lowers a little, slides its head sideways over feet that stay on the ground line, pulses slowly and glows. It lives apart from the motions of a blow, so a hit received meanwhile is played over it and ends back in it. A wind-up that was still on the body is let go. With reduced motion the glow is all there is, and it fades in rather than switching on.

    - `shearDirection` &mdash; World sign (+1 or -1) of the way the head slides.
    - `shearDegrees` &mdash; How far the head slides, in degrees; the caller passes what the room beside the body allows, and the profile's own limit applies on top. Zero keeps the head over the feet.

`public void BeginKo()`

:   Begins the knock-out: the body sinks, greys and dissolves, and its shadow goes with it.

`public void CancelCast()`

:   The cast was broken off: the pose leaves quietly, with none of the flourish of a release. Nothing happens when no cast was held.

`public void Configure(PuppetMotionProfile motion, bool reduceMotion, float breathSeed)`

:   Sets the numbers and the motion policy. Anything in flight is put at rest first.

    - `motion` &mdash; The numbers to follow; null uses the shipped values. They are copied and clamped.
    - `reduceMotion` &mdash; True to play only short fades.
    - `breathSeed` &mdash; A number in [0,1) that gives this unit its own breath length and phase, so a row never breathes in step.

`public void Cue(float seconds)`

:   A short glow that names the author of something, with no motion at all: it comes quickly, holds a moment and goes, by the same share as the glow of a cast (`PuppetMotionProfile.CastGlow`). Reduced motion uses it to say whose blow or heal a number is, now that nothing moves. It is a layer of its own, so a cast that is held keeps its glow underneath, and asking again while it is on restarts it from where it stands. A fallen body takes none.

    - `seconds` &mdash; How long it lasts in all, at least a tenth of a second; `PuppetMotionProfile.ReducedCueSeconds` is the usual value.

`public PuppetPose Evaluate()`

:   The pose of this frame.

    - **Returns** &mdash; The body's shift, lean, shear, scale, tint, glow, opacity and sorting rise.

`public void FinishKo()`

:   Makes the knock-out complete at once: the body is already gone, as for a combatant that was down before the battle was shown.

`public void Freeze(float seconds)`

:   Holds the body still for a moment, as the instant of a hit does.

    - `seconds` &mdash; Seconds to hold; reduced motion never holds.

`public void Hit(float awayDirection, bool critical)`

:   A blow lands: the body turns red, is pushed back, leans away and returns. With reduced motion it only flushes red and fades.

    - `awayDirection` &mdash; World sign of the way the blow pushes the body.
    - `critical` &mdash; True for a critical hit, which pushes harder.

`public void Impact(bool critical)`

:   The moment of contact for the attacker: the body is at its target and squashes, wider and lower, then relaxes.

    - `critical` &mdash; True for a critical hit, which squashes a little harder.

`public void Impact(bool critical, float strength)`

:   The moment of contact for the attacker, at a share of its full strength: the later contacts of a blow that reaches several targets are lighter.

    - `critical` &mdash; True for a critical hit, which squashes a little harder.
    - `strength` &mdash; Share of the squash, from 0 to 1.

`public void Pulse(float amount)`

:   A soft pulse in place: the body stretches a little taller (a heal received) or squashes (a flinch, the start of a status), over `PuppetMotionProfile.PulseRiseSeconds` from the size it has, then relaxes. It comes in over two frames of a capture and not in one, so no head drops between two of them; a pulse asked for while another is on goes on from where that one stands, with no jump.

    - `amount` &mdash; Share of the height to squash by; negative stretches it instead.

`public void Recover(float direction)`

:   Walks back to where the body stands, running slightly past it before it settles. Both legs ease in and out, so the walk starts from rest (a body that has just struck does not jump into motion) and ends at rest.

    - `direction` &mdash; World sign of the way the target lay.

`public void RecoverIfDisplaced()`

:   Walks back the way the last target lay, but only when the body is away from where it stands and is not already on its way.

`public void ReleaseCast()`

:   The cast is done: the pose is let go with a flourish a player can see, a quick stretch and the head sliding back past its place, and then the body comes to rest. Nothing happens when no cast was held. With reduced motion the glow fades.

`public void Reset()`

:   Puts the puppet at rest: no motion, no tint, not knocked out. The breath keeps its phase.

`public void SetReduceMotion(bool reduceMotion)`

:   Changes the motion policy; a change puts the body at rest.

    - `reduceMotion` &mdash; True to play only short fades.

`public void Settle()`

:   Brings every motion to its resting end at once, as a skipped beat does: the body is back where it stands, a knock-out that had begun is complete, and the hit stop and the tint are over. A cast pose that was held is let go; a presenter that knows the cast is still going puts it back with `BeginCast`.

`public void Strike(float direction)`

:   The pose of a blow from afar. The author of a blow that does not touch its target (it stands too far, or a body is in the way) leans into it: it reaches `PuppetMotionProfile.StrikePoseLeanDegrees` toward the target in `PuppetMotionProfile.StrikePoseRiseSeconds`, holds it for `PuppetMotionProfile.StrikePoseHoldSeconds` and comes back in `PuppetMotionProfile.StrikePoseReturnSeconds`, while the link leaves it, so what the player sees go out of the body is seen to be thrown by it. The pose is its own lean, kept apart from the wind-up and the contact, and it moves the body along the ground by nothing but the return of a wind-up it lets go. Asking again while it is on restarts it from where it stands. With reduced motion there is no pose; the glow of `Cue` names the author.

    - `direction` &mdash; World sign (+1 or -1) of the way the target lies.

`public void Tick(float seconds)`

:   Advances the puppet by presentation time.

    - `seconds` &mdash; Elapsed seconds; zero or less changes nothing.

---

## CombatantTokenView

```csharp
public sealed partial class CombatantTokenView
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/CombatantTokenView.Puppet.cs</small>

The puppet half of a token: the procedural motion of a static illustration. The token's own transform never moves for it. The
body is drawn a second time by a child renderer that carries the pose (a shift along the ground, a lean, a shear and a squash
about the feet, a red or grey tint, a glow, a fade), while the token's renderer keeps its place, its bounds and its colour but
is not drawn. So the layout, the plates, the target marks and the floating numbers keep reading the body where it stands, and
the feet of the drawn body stay on the ground line in every pose.

The body is two nested transforms because a shear is not a transform: a parent that rotates and scales over a child that
scales and rotates draws the lean, the squash and the shear together (see `PuppetShear`), with the renderer on
the child.

**Properties**

`public PuppetPose AppliedPuppetPose`

:   The pose the body was last drawn in.

`public ProjectedFormationPoint ApproachProjected`

:   The projected point a step-in should travel toward, in reference pixels. It is recorded but never used here; the token stays at `SlotProjected` unless the host animates it.

`public ArtReach ArtReach`

:   The box around every texel the art paints in the frames it shows now, as shares of the sprite rectangle as the art is drawn (`Presentation.ArtReach`). Target marks are fitted outside it as well as outside the painted body; the layout and the numbers keep the painted body, and so do the sides and the width of a plate, which stands over the brackets of the reticle when they reach higher than the painted head. A host that plays a clip reaching past the idle (an attack that swings forward) declares the reach of that clip when it starts it and the reach of the idle again when it ends. The default declares nothing, and marks are fitted to the painted body.

`public float BodyCenterOffsetFraction`

:   How far the middle of the painted body lies from the middle of the sprite rectangle, as a fraction of its width, in the art as drawn (positive is to the right). The token mirrors it when the sprite is flipped.

`public float BodyWidthFraction`

:   Share of the sprite rectangle's width that the painted body covers. The line layout spaces neighbours from it, so a narrow figure in a wide cell does not leave a gap. It is a property of the art, not of the slot.

`public bool CandidateDimHeld`

:   True while the dim of a combatant that could not be picked is held past the end of the aim, waiting for the action to take over.

`public float CandidateDimLevel`

:   How far this combatant is dimmed as one the skill being aimed cannot reach, from 0 (a legal pick) to 1 (fully dimmed).

`public StableId CombatantId`

:   The combatant this token stands for, as given to `Configure`. It is the default id until the token has been configured, which matters for tokens taken from a pool.

`public bool DeathPending`

:   True when the combatant is down in the snapshot but its knock-out has not begun, which is the time between the snapshot and the beat that plays the fall. The body is drawn standing until then.

`public int DepthRank`

:   How far back this combatant stands, 0 at the front. Ranks come from the formation's own ground lines rather than from anything authored here, so a flat arrangement leaves every token at 0 and nothing scales or fades.

`public float EffectiveArtScale`

:   The size this token is actually drawn at: the stage fit multiplied by its rank's share of `SkinStagePresenceTokens.RankScale`.

`public Vector2 FaceCoreFractions`

:   Left and right edge of the face as fractions of the sprite rectangle's width, as the art is drawn; equal values mean unknown.

`public FormationFacing Facing`

:   The facing recorded from the compiled slot. The sprite is mirrored when this differs from the direction set by `SetSourceArtFacing`, so one sprite serves both sides of the field.

`public float FocusDim`

:   How far the uninvolved are pushed back by the focus pull, 0 for not at all.

`public Vector2? FootTarget`

:   The world point the feet are held at by the layout, or null when the token stands at its authored seat.

`public FormationPresence FormationPresence`

:   How this combatant asks to be drawn against the others: the value its prototype carries. A stage that was told otherwise for this combatant (`BattleStage2D.SetCombatantPresence`) uses that instead, and keeps it when the token goes back to the pool.

`public int Health`

:   Health from the last mirrored snapshot state. A null combatant passed to `ApplyState` leaves the previous value standing.

`public float HealthFraction`

:   Normalized health in [0,1] for a bar; 0 when max is unset.

`public bool IsDead`

:   Whether the mirrored state has stopped counting the combatant as living. This is what desaturates and fades the sprite; the token is never hidden or destroyed on death.

`public bool IsTargetCandidate`

:   Whether this combatant is a legal pick for the skill being aimed. True is the resting state, so a token that is never told about targeting is never dimmed. Set false and the token also stops accepting picks, because a body the player can click but not target is worse than one they cannot click at all.

`public int MaximumHealth`

:   The health ceiling from the last mirrored snapshot state, used by `HealthFraction`.

`public SkinnedTokenPlate Plate`

:   The plate drawing this token's values, or null when unskinned.

`public BattleWorldPlateMode PlateMode`

:   The plate policy this token currently follows.

`public bool PlateSelected`

:   True while this token is a selected target.

`public CombatantPuppet Puppet`

:   The puppet that moves this token's drawn body, or null until a presenter has switched the motion on. It is stepped by the presenter's clock, so a test or a capture that owns that clock owns the motion too.

`public bool PuppetEnabled`

:   True while a presenter drives this token's puppet.

`public float PuppetOffsetWorldX`

:   How far the drawn body is from the token's own place, in world units along the ground. The token itself, its `TryGetVisibleBoundsWorld` and its feet stay where the layout put them.

`public SpriteRenderer PuppetRenderer`

:   The body the pose is drawn on, or null while the body is drawn by the token's own renderer. It is the inner of the two nested transforms of the pose, so its world transform is the whole pose.

`public int ShieldAmount`

:   The shield total the plate draws. A negative amount handed to `ApplyState` is stored as zero, so the bar can never invert.

`public ProjectedFormationPoint SlotProjected`

:   The projected rest position in reference pixels, which `Configure` converts to world units and moves the token to.

`public StableId SortingLayerKey`

:   The sorting layer the caller asked for. It is recorded only: `Configure` never assigns a layer to the renderer, so a host that cares about layers has to apply this itself.

`public int SortingOrder`

:   Draw order within the sorting layer. Unlike `SortingLayerKey`, this is written straight onto the sprite renderer.

`public FormationFacing SourceArtFacing`

:   The direction in which the current source sprite is authored before the token mirrors it for its formation slot.

`public int StatusPipCount`

:   How many status pips to draw, clamped at zero the same way `ShieldAmount` is.

`public float VisibleTopInsetFraction`

:   Share of the sprite rectangle's height that is empty above the painted body. It shapes the visible box that target marks are fitted to and the height the whole plate of a selected target stands at. The Line layout sizes a body by its head line, which this does not move; the Depth layout holds the group to 15% and a boss to 22 to 25% of the screen height on the painted body, which ends where this inset says.

**Fields**

`public const float CandidateHoldSeconds`

:   Seconds the dim of a combatant that could not be picked is held after the aim closes on a confirmed command, if no beat takes over first.

`public const int ContactShadowSortingOrder`

:   Sorting order every contact shadow is drawn at, before the token's own order is added to break ties between them. Well below any body and well above `BattleStage2D.BackdropSortingOrder`. A shadow ordered relative to its own combatant would be correct for that combatant and wrong for the stage: the front rank's shadow would fall across the feet of the rank behind it, which is the one place a contact shadow must never be.

`public const float CueGlowMaximum`

:   The glow of the puppet at which the cue ring is as opaque as it gets.

`public const float CueRingMaximumOpacity`

:   Opacity of the cue ring at `CueGlowMaximum`.

`public const float DefaultBodyWidthFraction`

:   Share of the sprite rectangle's width that the painted body covers when nothing more precise is known.

`public const float MinimumPlateScale`

:   How far the nameplate is allowed to shrink with the stage. The 24px combatant name is the smallest type on the plate, and 16px is the floor for anything a player reads mid-turn, so the plate may lose a third of its size and no more. Below this it stops following the stage, and two combatants standing close enough to collide is the composition's problem to solve rather than the plate's.

`public const float NonCandidateDim`

:   How far a combatant the current skill cannot reach is pushed back. This multiplier is applied after the stage's rank tint. At 0.72 a non-candidate is clearly de-emphasized while retaining enough of its authored colour to remain legible in a deep arrangement.

`public const float PlateGroundOverlapPixels`

:   Signed offset of the plate's top from a combatant's visual ground, in reference pixels. A negative value leaves space for the targeting ring beneath the feet instead of covering it with the identity card.

`public const float PlateOffsetPixels`

:   Plate offset above the token, in reference pixels.

**Methods**

`public void ApplySkin(CompiledBattleSkin battleSkin, float unitsPerPixel)`

:   Attaches the skinned plate that renders this token's values. Optional: a token with no skin still mirrors state onto its properties, which is what the headless tests assert against.

    - `battleSkin` &mdash; The compiled skin to draw with; null leaves the token unskinned and adds no plate.
    - `unitsPerPixel` &mdash; World units per reference pixel, used to size and offset the plate.

`public void ApplyState(CombatantState combatant, int shieldAmount, int statusPipCount)`

:   Mirrors snapshot/event state onto the token and its plate.

    - `combatant` &mdash; Snapshot state to mirror; null leaves health, maximum, and death as they were.
    - `shieldAmount` &mdash; Shield amount to display; negative values clamp to zero.
    - `statusPipCount` &mdash; How many status pips to show; negative values clamp to zero.

`public void ClearFootTarget()`

:   Releases the feet from the layout. The token stays where it is until it is configured again.

`public void Configure(StableId combatantId, FormationFacing facing, StableId sortingLayerKey, int sortingOrder, ProjectedFormationPoint slotProjected, ProjectedFormationPoint approachProjected, float unitsPerPixel)`

:   Places the token from its compiled slot projection.

    - `facing` &mdash; Compiled slot facing; the sprite is mirrored when this differs from its source art direction.
    - `sortingLayerKey` &mdash; Recorded for the caller to apply; only `sortingOrder` reaches the sprite renderer.
    - `slotProjected` &mdash; Projected rest position, in reference pixels, that the token is moved to.
    - `approachProjected` &mdash; Projected approach point, recorded for callers that animate a step-in; Configure does not move the token to it.
    - `unitsPerPixel` &mdash; World units per reference pixel, applied to the projected position.
    - `combatantId` &mdash; Stable combatant identity retained for later stage lookups.
    - `sortingOrder` &mdash; Renderer order within `sortingLayerKey`.

`public void ConfigurePuppet(PuppetMotionProfile motion, bool reduceMotion)`

:   Switches the procedural motion on for this token, or reconfigures it. The token is put at rest. A presenter calls this for every token of its stage; a token nobody configures is drawn exactly as before.

    - `motion` &mdash; The numbers the motion follows; null uses the shipped values.
    - `reduceMotion` &mdash; True to play only short fades.

`public void DisablePuppet()`

:   Switches the procedural motion off and draws the body with the token's own renderer again.

`public void Pulse()`

:   Starts a visual pulse that always returns to rest. Replaces the older behaviour of assigning a scale that was never restored.

`public void RefreshPuppet()`

:   Draws the puppet's pose now, without advancing time. A command given to the puppet shows on the next frame this way.

`public void Reposition(ProjectedFormationPoint slotProjected, ProjectedFormationPoint approachProjected, int sortingOrder, float unitsPerPixel)`

:   Moves the token to another standing point and draw order without resetting anything else: scale, rank, plate policy and art stay as they are. The stage uses it when a layout is solved again. A foot target set earlier is released.

    - `slotProjected` &mdash; New rest position in reference pixels.
    - `approachProjected` &mdash; New approach point in reference pixels, recorded for callers that animate a step-in.
    - `sortingOrder` &mdash; Draw order of the body; the contact shadow, fallback card and plate follow it.
    - `unitsPerPixel` &mdash; World units per reference pixel.

`public void SetArt(Sprite art)`

:   Gives this combatant its painted body. This is the supported way to dress a token, and it does the two things that assigning `SpriteRenderer.sprite` directly does not: it retires the lettered fallback card, which would otherwise sit behind the art as a leftover box, and it moves the nameplate down to the new body's ground line.

    - `art` &mdash; The combatant's illustration, or null to return to the lettered fallback. A renderer is provisioned on the token root when needed.

`public void SetArtReach(ArtReach reach)`

:   Declares the box around every texel the art paints in the frames it shows now. The brackets of the reticle are fitted outside it, and the stage hangs the bare health bar of the combatant under them, so it places the bar again when the reach changes.

    - `reach` &mdash; The box as shares of the sprite rectangle, as the art is drawn; sides are kept inside the rectangle, and a value that declares no box (`Presentation.ArtReach.IsDeclared`) clears it.

`public void SetArtScale(float scale)`

:   Scales this combatant's art to fit the stage it is standing on. Only the body scales. The nameplate is built in reference pixels and keeps its own size, because a plate that shrank with the stage would take the name and the health readout below the size anybody can read - which is the fault this whole pass exists to fix.

    - `scale` &mdash; Multiplier for the art, normally `BattleStage2D.TokenScale`. Zero or less is ignored, so a caller that has not computed one yet leaves the token at its authored size.

`public void SetBarHeightMinimum(float stagePixels)`

:   Sets the least height of the bare health bar in stage pixels, which the stage derives from the screen height so the bar stays readable at every resolution and does not shrink with a small sprite. Zero or less removes the minimum.

    - `stagePixels` &mdash; Least bar height in projected pixels.

`public void SetBarWidthLimit(float stagePixels)`

:   Limits the width of the bare health bar under the feet, in stage pixels, so it stays narrower than its owner and never touches the bar of a neighbour. The stage sets it after every layout; zero or less removes the limit.

    - `stagePixels` &mdash; Widest the bar may be on the stage, in projected pixels.

`public void SetBodyCenterOffsetFraction(float fraction)`

:   Sets how far the middle of the painted body lies from the middle of the sprite rectangle, as a fraction of its width.

    - `fraction` &mdash; Offset in the art as drawn, clamped to -0.5..0.5; positive is to the right.

`public void SetBodyWidthFraction(float fraction)`

:   Sets the share of the sprite rectangle's width that the painted body covers.

    - `fraction` &mdash; Fraction of the sprite width, clamped to 0.3..1.

`public void SetCastProgress(float fraction, bool visible)`

:   Shows cast progress on the plate, or hides the cast bar.

    - `fraction` &mdash; Cast progress in [0,1]; read only when `visible` is true.
    - `visible` &mdash; False hides the cast bar. Does nothing when the token is unskinned.

`public void SetFaceCoreFractions(float left, float right)`

:   Sets where the face lies across the sprite rectangle, so the line layout never lets a neighbour cover it.

    - `left` &mdash; Left edge of the face as a fraction of the width, in the art as drawn.
    - `right` &mdash; Right edge of the face as a fraction of the width, in the art as drawn.

`public void SetFocusDim(float amount)`

:   Pushes this combatant back for the focus pull. It composes with the dim of a combatant that cannot be picked by the stronger of the two, not by their product, so a combatant that goes from one to the other does not brighten or darken in between. The focus module writes it every frame of the fade, so the colour moves with the presentation clock instead of switching.

    - `amount` &mdash; Share of the brightness removed, clamped to 0..1; 0 restores the colour.

`public void SetFootTarget(Vector2 world)`

:   Holds the visual ground of the art at a world point, whatever the art, its ground anchor or its scale: the token moves so its feet land there, and moves again when any of them changes. The stage uses it so a line of combatants shares one ground line even when their illustrations leave different padding below the feet.

    - `world` &mdash; World position of the feet; only x and y are read.

`public void SetFormationPresence(FormationPresence presence)`

:   Sets how this combatant asks to be drawn against the others, and lays the stage out again.

    - `presence` &mdash; Automatic, Boss or Standard.

`public void SetGauge(float fraction, bool visible)`

:   Shows the scheduler gauge on the plate, or hides it.

    - `fraction` &mdash; Gauge fill in [0,1]; a full gauge is drawn with the ready accent.
    - `visible` &mdash; False hides the gauge. Does nothing when the token is unskinned.

`public void SetPlateCeilingWorld(float? worldY)`

:   Keeps the whole plate of a selected target under a given world height, which the stage sets to the top of the band it draws in so the plate never leaves the stage for the turn ribbon above it. Null removes the ceiling.

    - `worldY` &mdash; World height the top of the plate must not pass, or null.

`public void SetPlateFloorWorld(float? worldY)`

:   Sets the lowest world height the plate may reach, or null for none. The stage supplies the bottom of its band.

    - `worldY` &mdash; World-space height of the floor, or null.

`public void SetPlateHeadFloor(float? worldY)`

:   Raises the whole plate of a selected target so it stands above a given world height, which the stage sets to the tallest head among the neighbours the plate is wide enough to reach. Null removes the floor.

    - `worldY` &mdash; World height the plate must stand above, or null.

`public void SetPlateIdentity(string label, Color teamTint)`

:   Updates set plate identity on presentation state only. The call cannot submit a command, advance a tick, or change an authoritative hash.

    - `label` &mdash; The resolved display string; ignored when the token is unskinned.
    - `teamTint` &mdash; Tint that distinguishes ally from enemy, replacing the skin default.

`public void SetPlateIdentity(string label, Color teamTint, Color healthTint)`

:   Names the plate and gives it a team tint and a health fill of its own.

    - `label` &mdash; Display name shown on the plate.
    - `teamTint` &mdash; Name tint and fallback body tint of the token's team.
    - `healthTint` &mdash; Fill color of the health bar while the combatant lives.

`public void SetPlatePolicy(BattleWorldPlateMode mode, bool isAlly)`

:   Chooses which plates this token draws. In the standard mode every token draws its whole plate under its feet. In the compact mode the player's side draws nothing, because its health is in the party panel, every other combatant draws a bare health bar, and a selected target gets the whole plate above its head.

    - `mode` &mdash; Plate policy of the active theme.
    - `isAlly` &mdash; True when the combatant is on the viewing player's team.

`public void SetPlateSelected(bool selected)`

:   Marks this combatant as a selected target, which gives it the full plate above its head in the compact mode.

    - `selected` &mdash; True while a target preview or the player's pick names this combatant.

`public void SetPuppetReduceMotion(bool reduceMotion)`

:   Changes the motion policy of the puppet; a change puts the body at rest.

    - `reduceMotion` &mdash; True to play only short fades.

`public void SetSourceArtFacing(FormationFacing value)`

:   Sets the direction painted into the source sprite, independently of its compiled slot facing.

    - `value` &mdash; The source illustration's unmirrored direction. It persists when the stage reconfigures this token.

`public void SetStagePresence(SkinStagePresenceTokens presence, int rank)`

:   Stages this token for the depth rank it stands at. This is what makes a formation read as a scene instead of a diagram: a body further from the camera is smaller, darker, and lit less by the key light, and the three cues together are what the eye reads as distance. One of them alone reads as a smaller character, a shadowed character, or a differently-painted one.

    - `presence` &mdash; The skin's staging tokens. Sanitized on the way in, so an unclamped authored value cannot reach the transform.
    - `rank` &mdash; Depth rank, 0 at the front. Negative values are treated as the front, which is what a caller that could not resolve a rank should pass.

`public void SetTargetCandidate(bool eligible)`

:   Marks this token eligible, or not, for the pick in progress.

    - `eligible` &mdash; False dims the token to `NonCandidateDim`.

`public void SetVisibleTopInsetFraction(float fraction)`

:   Sets how much of the sprite rectangle's height is empty above the painted body.

    - `fraction` &mdash; Empty share of the cell height above the body, clamped to 0..0.9.

`public void SetVisualGroundAnchor(Transform anchor)`

:   Sets an authored point on this token that represents where its art meets the ground. The anchor may be the token itself or any descendant; a foreign transform is rejected so one combatant cannot ground itself from another object's moving hierarchy. Passing null restores renderer or fallback bounds grounding.

    - `anchor` &mdash; A transform in this token's hierarchy, or null to use visible bounds.

`public void StopPulse()`

:   Cancels the sample pulse without changing health, art, or selection.

`public void Tick(float deltaSeconds)`

:   Advances plate and pulse animation by a visual delta.

    - `deltaSeconds` &mdash; Wall-clock seconds since the last call. Non-positive values are ignored, and this is presentation time only: it never advances the battle.

`public void TickPuppet(float deltaSeconds)`

:   Advances the puppet by presentation time and draws its pose.

    - `deltaSeconds` &mdash; Elapsed presentation seconds; zero or less changes nothing.

`public bool TryGetMarkBoundsWorld(out Rect box)`

:   The box target marks are fitted outside, in world units. It is the painted body (`TryGetVisibleBoundsWorld`) grown to the declared `ArtReach`, raised by the most the breath of the puppet and the slow pulse of a held cast stretch a body, and taken also where the puppet draws the body in its pose now (a lean, the shear of a cast, a squash). So a mark crosses neither the faint edge of the art, nor a frame that reaches past the body, nor a body that leans, and it does not bob with a breath. It holds the place where the body stands too, so a mark does not shrink when a pose ends. A fallback card is its own box.

    - `box` &mdash; Receives the box; x and y are its lower left corner in world units.
    - **Returns** &mdash; False when the token has nothing drawn.

`public bool TryGetPuppetFootWorld(out Vector3 foot)`

:   The world position of the feet of the drawn body, which is the visual ground with the pose's shift added. A lean and a squash turn the body about this point, so its height is the same in every pose.

    - `foot` &mdash; Receives the foot position, or the token position when the token draws nothing.
    - **Returns** &mdash; False when the token has no body to stand on.

`public bool TryGetVisibleBoundsWorld(out Rect box)`

:   The box the painted body occupies, in world units: from the visual ground to the top of the painted body, across the painted width, centred where the body is centred in the art as drawn now. It is built from the authored metrics of the art (`BodyWidthFraction`, `BodyCenterOffsetFraction`, `VisibleTopInsetFraction`), which the shipped sample characters measure from their alpha, so it needs no pixel readback and stays stable while the art idles. A fallback card is its own visible box.

    - `box` &mdash; Receives the box; x and y are its lower left corner in world units.
    - **Returns** &mdash; False when the token has nothing drawn.

`public bool TryGetVisualGroundWorld(out Vector3 groundWorld, out float widthWorld)`

:   Returns the actual visual ground line and width in world space. Renderer bounds keep this correct for a configured child renderer, pivots, flipX and transformed parents. When art is absent, the visible fallback card supplies the same contract.

    - `groundWorld` &mdash; Receives the visual ground centre in world coordinates.
    - `widthWorld` &mdash; Receives the visual width in world units.
    - **Returns** &mdash; True when a visible sprite or fallback body supplies a non-zero width.

`public bool TryGetVisualHeadWorld(out Vector3 headWorld)`

:   Returns the top of the painted body in world space, centred over the visual ground.

    - `headWorld` &mdash; Receives the head line point.
    - **Returns** &mdash; True when the token wears art or a fallback body.

`public bool TryMeasureNaturalArt(float unitsPerPixel, out float heightPixels, out float paintedWidthPixels, out float paintedOffsetPixels, out float faceMinPixels, out float faceMaxPixels)`

:   Measures the painted art at scale one, in the reference pixels combatant art is authored in: the height from the visual ground to the head line, and the width of the painted body.

    - `unitsPerPixel` &mdash; World units per reference pixel.
    - `heightPixels` &mdash; Receives the height from the ground anchor to the head line at scale one.
    - `paintedWidthPixels` &mdash; Receives the painted body width at scale one.
    - `paintedOffsetPixels` &mdash; Receives how far the middle of the painted body lies right of the ground anchor at scale one, as the sprite is drawn now (mirrored when it is flipped).
    - `faceMinPixels` &mdash; Receives the left edge of the face from the middle of the painted body at scale one, as drawn now; equal to `faceMaxPixels` when unknown.
    - `faceMaxPixels` &mdash; Receives the right edge of the face measured the same way.
    - **Returns** &mdash; False when the token wears no sprite, which leaves the fallback card to the stage's own scale.

---

## PresentationBeat

```csharp
public sealed class PresentationBeat
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationBeat.cs</small>

One immutable presentation beat: the event context plus the resolved
recipe. A null recipe is an instant, no-visual beat (an unmapped event).
Beat timing is derived from the recipe only for visuals and never feeds
back into any authoritative hash.

**Constructors**

`public PresentationBeat(PresentationBeatContext context, PresentationRecipeDefinition recipe)`

:   Pairs an event's beat context with the recipe resolved for it.

    - `context` &mdash; The data extracted from the source event.
    - `recipe` &mdash; The resolved recipe, or null to make this an instant no-visual beat.

**Properties**

`public PresentationBeatContext Context`

:   Everything the beat knows about the event it came from: participants, tick, and any amount. It is captured once when the beat is built, so a beat that plays several frames later still draws the situation as it stood at the event rather than as the battle stands now.

`public bool IsNoVisual`

:   True when the source event mapped to no recipe.

`public int PhaseCount`

:   The number of visual phases (0 for a no-visual beat, else 3).

`public PresentationRecipeDefinition Recipe`

:   The resolved recipe, or null for a no-visual beat.

`public float TotalDurationSeconds`

:   Total clamped duration across the three phases, in seconds.

---

## PresentationBeatContext

```csharp
public readonly struct PresentationBeatContext
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationBeat.cs</small>

The non-authoritative, immutable data a beat needs, extracted entirely
from one gameplay event's property set. It carries participants and an
optional amount for floating numbers; it performs no simulation math.

**Constructors**

`public PresentationBeatContext(StableId eventTypeId, long tick, ulong eventSequence, StableId? sourceId, StableId? targetId, StableId? skillId, StableId? statusId, StableId? reactionId, int? amount)`

:   Creates a beat context. Normally produced by `BeatDeriver.BuildContext` from an event's property set; construct one directly only to drive a beat without a live battle.

    - `eventTypeId` &mdash; The source event's type, one of the `BattleIds` event identifiers.
    - `tick` &mdash; The tick the source event was emitted on.
    - `eventSequence` &mdash; The source event's battle-wide sequence, which identifies this beat's origin uniquely.
    - `sourceId` &mdash; The acting combatant, or null when the event names none.
    - `targetId` &mdash; The affected combatant, or null when the event names none.
    - `skillId` &mdash; The skill involved, or null.
    - `statusId` &mdash; The status involved, or null.
    - `reactionId` &mdash; The reaction rule involved, or null.
    - `amount` &mdash; The event's numeric amount, for a floating number. Null when the event carries none, which is the common case for non-numeric events such as a cast starting.

`public PresentationBeatContext(StableId eventTypeId, long tick, ulong eventSequence, StableId? sourceId, StableId? targetId, StableId? skillId, StableId? statusId, StableId? reactionId, int? amount, bool isCritical, bool blockedByShield, bool isKillingBlow)`

:   Creates a beat context that also carries the outcome flags a hit can have. Same as the shorter form in every other respect; the flags default to false there, which is what an event that does not report them reads as.

    - `eventTypeId` &mdash; The source event's type, one of the `BattleIds` event identifiers.
    - `tick` &mdash; The tick the source event was emitted on.
    - `eventSequence` &mdash; The source event's battle-wide sequence, which identifies this beat's origin uniquely.
    - `sourceId` &mdash; The acting combatant, or null when the event names none.
    - `targetId` &mdash; The affected combatant, or null when the event names none.
    - `skillId` &mdash; The skill involved, or null.
    - `statusId` &mdash; The status involved, or null.
    - `reactionId` &mdash; The reaction rule involved, or null.
    - `amount` &mdash; The event's numeric amount, for a floating number. Null when the event carries none.
    - `isCritical` &mdash; Whether the event reported the hit as critical.
    - `blockedByShield` &mdash; Whether a shield absorbed some or all of the amount.
    - `isKillingBlow` &mdash; Whether the amount took its target out of the battle.

`public PresentationBeatContext(StableId eventTypeId, long tick, ulong eventSequence, StableId? sourceId, StableId? targetId, StableId? skillId, StableId? statusId, StableId? reactionId, int? amount, bool isCritical, bool blockedByShield, bool isKillingBlow, StableId? effectEntryId)`

:   Creates a beat context that also names the effect entry that produced the event. A damage or healing event does not carry the skill it belongs to, but it does carry its effect entry, which belongs to exactly one skill of the compiled content.

    - `eventTypeId` &mdash; The source event's type, one of the `BattleIds` event identifiers.
    - `tick` &mdash; The tick the source event was emitted on.
    - `eventSequence` &mdash; The source event's battle-wide sequence, which identifies this beat's origin uniquely.
    - `sourceId` &mdash; The acting combatant, or null when the event names none.
    - `targetId` &mdash; The affected combatant, or null when the event names none.
    - `skillId` &mdash; The skill involved, or null.
    - `statusId` &mdash; The status involved, or null.
    - `reactionId` &mdash; The reaction rule involved, or null.
    - `amount` &mdash; The event's numeric amount, for a floating number. Null when the event carries none.
    - `isCritical` &mdash; Whether the hit was critical.
    - `blockedByShield` &mdash; Whether a shield absorbed some or all of the amount.
    - `isKillingBlow` &mdash; Whether the amount took its target out of the battle.
    - `effectEntryId` &mdash; The effect entry that produced the event, or null when the event names none.

**Properties**

`public int? Amount`

:   The amount to show as a floating number, or null when the source event carries no numeric amount.

`public bool BlockedByShield`

:   Whether a shield absorbed some or all of the amount. Offered so a project can play a block rather than a hit; nothing in the shipped beats reads it yet.

`public StableId? EffectEntryId`

:   The effect entry that produced the event, or null. A damage or healing event names its entry but not its skill; the entry belongs to one skill of the compiled content, which is how the stage learns what kind of blow it is playing.

`public ulong EventSequence`

:   The source event's battle-wide sequence. It identifies this beat's origin uniquely, so it is what to key on when suppressing a beat already played.

`public StableId EventTypeId`

:   Which kind of gameplay event the beat came from. Recipe resolution matches on it before anything else, so a recipe declaring another event type is never considered however specific its selector is.

`public bool IsCritical`

:   Whether the source event reported the hit as critical. False when the event says nothing about it, so a beat built from an emitter that does not report criticals reads exactly as it always did.

`public bool IsKillingBlow`

:   Whether this amount is what took the target out of the battle. The authoritative death is still its own event; this only lets a visual react on the blow instead of one event later.

`public StableId? ReactionId`

:   The reaction rule that produced the event, or null. Only a recipe selecting by reaction ID reads it, which is how a counter-attack can be given its own look without touching the ordinary attack recipe.

`public StableId? SkillId`

:   The skill involved, or null. A recipe that selects by skill ID or skill tag can only match while this is present; without it the candidates are the event-default recipes plus any status or reaction selector the event still satisfies.

`public StableId? SourceId`

:   The acting combatant, or null when the event names none. Animations play on this combatant's token, and a visual effect anchors here when the event carries no target.

`public StableId? StatusId`

:   The status involved, or null. It is what recipes selecting by status ID or status tag match against.

`public StableId? TargetId`

:   The affected combatant, or null when the event names none. Visual effects prefer this anchor over `SourceId`, so a hit lands on the receiver rather than on whoever swung.

`public long Tick`

:   The tick the source event was emitted on. It is battle time, not the moment the beat is drawn - a queue of beats can still be playing out several ticks behind the simulation.

---

## PresentationStagePreset

```csharp
public sealed class PresentationStagePreset : ScriptableObject
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Closed, neutral presentation content for a battle stage. This asset is
visual-only and is never read by simulation or included in its hashes.

**Properties**

`public IReadOnlyList<StageAnimationBinding> AnimationBindings`

:   Authored neutral animation bindings in explicit order.

`public IReadOnlyList<StageAudioBinding> AudioBindings`

:   Authored one-shot sound bindings in explicit order.

`public PerformFeelPreset Feel`

:   Authored feel copied by each playback session.

`public PresentationRecipeSet Recipes`

:   Authored recipe set copied by each playback session.

`public IReadOnlyList<StageSkillMotionBinding> SkillMotions`

:   Authored statements of how the user of a skill moves, which override the presenter's reading of the skill.

`public IReadOnlyList<StageVfxBinding> VfxBindings`

:   Authored prefab/sprite effect bindings in explicit order.

**Methods**

`public IReadOnlyList<string> Validate()`

:   Returns authoring diagnostics without throwing. Duplicate keys are reported even though playback keeps the first binding deterministically.

    - **Returns** &mdash; Ordered diagnostics for missing content, duplicate keys and invalid effect values; empty when valid.

---

## PresenterBinding

**Start here**

```csharp
public sealed class PresenterBinding
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresenterBinding.cs</small>

The explicit dependency bundle a driver hands to a
`BattlePresenter`. It carries compiled content, the
non-authoritative formation layout, the recipe set, the four visual
adapters, the display-string table, and an optional uGUI root. The
binding contains no engine and no authoritative mutator.

**Constructors**

`public PresenterBinding(CompiledAuthoringCatalog catalog, CompiledEncounterFormationLayout layout, PresentationRecipeSet recipes, IAnimationAdapter animation, IVfxAdapter vfx, IAudioAdapter audio, IPoolAdapter pool, DisplayStringTable labels, BattleUiRoot ui = null, PresentationLog log = null, IBattleView surface = null)`

:   Bundles everything a presenter needs into one value. Every argument through `labels` is required and throws `ArgumentNullException` when null, so a binding that constructs is always complete: the presenter never has to null-check its own dependencies.

    - `layout` &mdash; The non-authoritative formation layout, used for placement only.
    - `recipes` &mdash; The recipe set beats are resolved against.
    - `labels` &mdash; The display-string table names are resolved through.
    - `ui` &mdash; Optional legacy uGUI root; null omits that root while an optional native surface can still provide a HUD.
    - `log` &mdash; Optional shared log-once ledger; a fresh one is created when null.
    - `animation` &mdash; Required adapter that plays animation keys named by presentation phases.
    - `audio` &mdash; Required adapter that plays phase sound keys without affecting simulation state.
    - `catalog` &mdash; Compiled content used to interpret event, skill, status, and combatant identities.
    - `pool` &mdash; Required owner of reusable token, floating-number, and effect instances.
    - `vfx` &mdash; Required adapter that spawns phase effect keys at resolved formation anchors.
    - `surface` &mdash; Optional native or custom view retained for presentation and target interaction. Its session and pointer contracts are bound by the presenter when supported.

**Properties**

`public IAnimationAdapter Animation`

:   Plays the animation keys named by a beat's phases.

`public IAudioAdapter Audio`

:   Plays the one-shot sound keys named by a beat's phases.

`public CompiledAuthoringCatalog Catalog`

:   The compiled catalog battle events are interpreted against, used to derive beats and the shape of a pending decision. It is read only, so the presenter can share the same catalog instance as the engine.

`public DisplayStringTable Labels`

:   Display text for the IDs shown to players. Compiled content carries no labels, so an ID this table does not hold falls back to its raw ID text instead of rendering blank.

`public CompiledEncounterFormationLayout Layout`

:   Where each combatant sits on the stage. It is non-authoritative, so swapping it moves the art and nothing else.

`public PresentationLog Log`

:   Shared log-once ledger for missing-key degradation.

`public IPoolAdapter Pool`

:   Lends out the instances behind token views, floating numbers, and pooled effects. The presenter and the stage return what they borrowed on teardown rather than destroying it, so the same pool survives repeated battles.

`public PresentationRecipeSet Recipes`

:   The ordered recipe list every battle event is matched against. Candidate recipes come only from this set and nothing else in the project is scanned, though tag selectors are matched against the catalog's compiled skill and status tables. An event that matches no recipe here still becomes a beat, just one with no visuals.

`public IBattleView Surface`

:   Renderer-independent HUD, supplied instead of the legacy uGUI root.

`public BattleUiRoot Ui`

:   Optional legacy uGUI root. Null omits only this root; the stage and an optional native surface can still be presented.

`public IVfxAdapter Vfx`

:   Plays the one-shot effect keys named by a beat's phases.

---

## PuppetActionKind

```csharp
public enum PuppetActionKind
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattlePresenter.Puppet.cs</small>

How an attacker moves when it uses a skill. The presenter reads it from the skill; a project can state it for any skill.

| Value | Meaning |
| --- | --- |
| `Auto` | The presenter decides from the skill's tags, cast time and target rule. |
| `Melee` | The attacker walks up to its target, strikes at contact and walks back. |
| `Ranged` | The attacker stays where it stands and only steps a little toward its target. |
| `InPlace` | The attacker does not move from its place at all: a heal, a guard, a cast on itself. |

---

## PuppetApproach

```csharp
public static class PuppetApproach
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PuppetApproach.cs</small>

How far an attacker has to travel to reach its target, and how deep it ends up in it. Pure geometry on the visible span of
the two bodies along the ground, so it needs no object of the engine and a test can state its answers in plain numbers.

**Methods**

`public static float ContactDistance(float attackerMin, float attackerMax, float targetMin, float targetMax, float overlapFraction, out float direction)`

:   The distance that brings the attacker's near edge to the target's near edge, plus the allowed interpenetration. The attacker never retreats: a pair that already touches or overlaps by more than the allowance stays where it is.

    - `attackerMin` &mdash; Left edge of the attacker's visible body, in world units.
    - `attackerMax` &mdash; Right edge of the attacker's visible body.
    - `targetMin` &mdash; Left edge of the target's visible body.
    - `targetMax` &mdash; Right edge of the target's visible body.
    - `overlapFraction` &mdash; Share of the narrower visible width the attacker may reach into the target; clamped to [0, 0.1].
    - `direction` &mdash; Receives +1 when the target lies to the right of the attacker and -1 when it lies to the left.
    - **Returns** &mdash; The distance to travel along the ground, in world units, never negative.

`public static float Interpenetration(float attackerMin, float attackerMax, float targetMin, float targetMax)`

:   How deep the attacker reaches into the target, as a share of the narrower visible width.

    - `attackerMin` &mdash; Left edge of the attacker's visible body after it has moved.
    - `attackerMax` &mdash; Right edge of the attacker's visible body after it has moved.
    - `targetMin` &mdash; Left edge of the target's visible body.
    - `targetMax` &mdash; Right edge of the target's visible body.
    - **Returns** &mdash; 0 when the bodies do not overlap; 1 when the narrower one is wholly inside the other.

`public static float NearestContact(float attackerMin, float attackerMax, float direction, float overlapFraction, float bodyMin, float bodyMax, float nearestSoFar)`

:   Folds one body of the other side into the distance an attacker may walk: the smaller of what it was and the distance that brings the attacker to that body, if the body lies ahead of it (on the side of `direction`). Folding every body of the other side leaves the distance to the first one in the way.

    - `attackerMin` &mdash; Left edge of the attacker's visible body.
    - `attackerMax` &mdash; Right edge of the attacker's visible body.
    - `direction` &mdash; World sign of the way the attacker walks.
    - `overlapFraction` &mdash; Share of the narrower visible width the attacker may reach into a body; clamped to [0, 0.1].
    - `bodyMin` &mdash; Left edge of the other body's visible span.
    - `bodyMax` &mdash; Right edge of the other body's visible span.
    - `nearestSoFar` &mdash; The distance so far; start from positive infinity.
    - **Returns** &mdash; The distance after folding this body in.

`public static float NearestRoom(float attackerMin, float attackerMax, float side, float tolerance, float bodyMin, float bodyMax, float roomSoFar)`

:   Folds one body into the room a body has toward `side`: the smaller of what it was and `RoomBeside` for this body.

    - `attackerMin` &mdash; Left edge of the moving body's visible span, in world units.
    - `attackerMax` &mdash; Right edge of the moving body's visible span.
    - `side` &mdash; World sign of the way the body travels.
    - `tolerance` &mdash; Share of the narrower visible width the body may reach in beyond where it stands now.
    - `bodyMin` &mdash; Left edge of the other body's visible span.
    - `bodyMax` &mdash; Right edge of the other body's visible span.
    - `roomSoFar` &mdash; The room so far; start from positive infinity.
    - **Returns** &mdash; The room after folding this body in.

`public static float RoomBeside(float attackerMin, float attackerMax, float side, float tolerance, float bodyMin, float bodyMax)`

:   How far a body may travel toward `side` before it stands deeper into another body than it stands now by more than a tolerance. Bodies of one side overlap a little at rest, so this is not "until they touch": a body that already overlaps its neighbour may go no further than the tolerance, and one that stands clear may go until the edges meet and then reach the tolerance in. The same arithmetic gives the room behind a body for a wind-up and the room beside it for a lean of the head, so every pose a body takes is judged against the bodies around it by one rule.

    - `attackerMin` &mdash; Left edge of the moving body's visible span, in world units.
    - `attackerMax` &mdash; Right edge of the moving body's visible span.
    - `side` &mdash; World sign of the way the body travels.
    - `tolerance` &mdash; Share of the narrower visible width the body may reach in beyond where it stands now; clamped to [0, 0.1].
    - `bodyMin` &mdash; Left edge of the other body's visible span.
    - `bodyMax` &mdash; Right edge of the other body's visible span.
    - **Returns** &mdash; The distance, in world units and never negative; positive infinity when the other body does not lie on that side.

---

## PuppetMotionProfile

```csharp
public sealed class PuppetMotionProfile
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PuppetMotionProfile.cs</small>

The numbers behind the procedural "puppet" motion of a combatant: how far it winds up, how hard it squashes on contact, how
long the hit freezes, how it falls when it is knocked out. Every value is presentation only; none of them reaches a battle,
a hash or a replay. The shipped values are tuned for a static illustration that stands on one ground line, and a project that
wants a heavier or a lighter feel changes them here instead of editing a clip.

**Fields**

`public float AllyOverlapTolerance`

:   How much deeper than it already stands an attacker may reach into a body of its own side that is in front of it, as a share of the narrower of the two visible widths. Bodies of one side overlap a little at rest (a row is drawn that way); an attacker behind another walks no further into the one in front than that, so it never passes through it.

`public float AnticipationLeanDegrees`

:   Degrees the body leans away from its target during the wind-up. The pivot is the feet.

`public float AnticipationRecoilPixels`

:   Stage pixels the body steps back from its target during the wind-up.

`public float AnticipationSeconds`

:   Seconds the wind-up takes before an attack, eased in.

`public float AreaFollowUpTimeScale`

:   Share of its authored length a beat is played at when it belongs to a blow that reaches several targets and the attacker is already in place: each target after the first is struck in this share of the time (and the first one's beat gives up the same share of what is left of it after the contact, so the next contact follows closely), which makes the blow one gesture with a run of contacts and not a series of whole actions. It applies to an attacker that makes an advance (a melee blow, or the step of a ranged one); a body that is not drawn as a puppet, or does not move, plays every beat as authored. One plays every beat as authored for everyone.

`public float AreaWaveStepSeconds`

:   Seconds from one contact to the next when a blow reaches several targets: the targets are struck in a wave a few frames long, so the blow reads as one gesture. The beat of each target after the first is played in this time, and the first one's beat gives up what is left of it after its contact; the last target's beat then plays out at `AreaFollowUpTimeScale`. It never makes a beat longer than that scale would.

`public int AttackerSortBoost`

:   Sorting-order rise of an attacker that is out in front of its row, so it is drawn over its neighbours.

`public float BreathAmplitude`

:   Share of its height an idle body grows by at the top of a breath.

`public float BreathMaximumSeconds`

:   Longest breath, in seconds.

`public float BreathMinimumSeconds`

:   Shortest breath, in seconds. Each unit takes its own length between this and `BreathMaximumSeconds`.

`public float CastCancelSeconds`

:   Seconds the pose takes to leave when a cast is cancelled.

`public float CastCrouch`

:   Share of its height a casting body lowers by while it holds the pose. The pivot is the feet.

`public float CastEnterSeconds`

:   Seconds the pose takes to settle in when a cast begins, eased out.

`public float CastGlow`

:   How much the colour of a casting body brightens, as a share, while it holds the pose.

`public float CastPulseAmplitude`

:   Share of its height the held pose breathes by, up and down about the crouch.

`public float CastPulseSeconds`

:   Seconds one pulse of the held pose takes.

`public float CastReleaseSeconds`

:   Seconds the release of a cast takes in all: a quick stretch and a shear the other way, and the return to rest.

`public float CastReleaseShearDegrees`

:   Degrees the head slides the other way at the release, at most; it is a share of the shear that was held.

`public float CastReleaseStretch`

:   Share of its height the body stretches by at the release of a cast.

`public float CastShearDegrees`

:   Most degrees the head of a casting body slides sideways while it holds the pose. It is a shear about the feet, so both boots stay on the ground line; it is smaller where a neighbour stands close.

`public float ContactLeanDegrees`

:   Degrees the body leans toward its target at the moment of contact.

`public float ContactOverlapFraction`

:   How far the attacker's visible body may reach into the target's, as a share of the narrower of the two visible widths. Contact is the closest an attacker comes; it never stands inside the sprite it hits.

`public float CriticalImpactSquash`

:   The squash of a critical hit.

`public float CriticalKnockbackPixels`

:   Stage pixels a combatant is pushed back by a critical hit.

`public float FollowUpImpactShare`

:   Share of its strength the second and later contacts of a blow that reaches several targets have: the squash and the hit stop of the attacker.

`public float HealStretch`

:   Share of its height a combatant stretches by when it receives a heal.

`public float HitLeanDegrees`

:   Degrees a struck combatant leans away from the blow.

`public float HitTintFadeSeconds`

:   Seconds the red takes to fade once it has held. It is long enough for the fade to be seen at 30 frames per second: at the 0.04 s it had, the whole of the fade was one frame of a capture and the red was cut.

`public float HitTintSeconds`

:   Seconds a struck combatant stays fully red.

`public float HitstopSeconds`

:   Seconds attacker and target stand frozen at the moment of contact.

`public float ImpactSquash`

:   Share of its height the attacker squashes by at contact; the width grows by the same share.

`public float KnockbackHoldSeconds`

:   Seconds the combatant holds at the end of the push.

`public float KnockbackPixels`

:   Stage pixels a struck combatant is pushed back.

`public float KnockbackReturnSeconds`

:   Seconds the combatant takes to come back.

`public float KnockbackSeconds`

:   Seconds the push takes.

`public float KoScaleFraction`

:   Share of its size a knocked-out body shrinks by while it dissolves.

`public float KoSeconds`

:   Seconds a knock-out takes: the body sinks, greys and dissolves, and its shadow goes with it.

`public float KoSinkFraction`

:   Share of its height a knocked-out body sinks by, with the feet staying on the ground.

`public float MaximumAdvanceSeconds`

:   Longest the advance toward a target takes, in seconds.

`public float MinimumAdvanceSeconds`

:   Shortest the advance toward a target takes, in seconds.

`public float MinimumStrikeTravelPixels`

:   The least an attacker walks, in stage pixels, for the walk to be worth showing. An attacker with less room than this in front of it (a body of its own side stands there) strikes where it stands: it leans into the blow and squashes, and does not move along the ground.

`public float PulseRiseSeconds`

:   Seconds a pulse (a flinch, the stretch of a heal, the start of a status) takes to reach its size, eased in and out. A pulse that took its whole size in one frame dropped the head of a body by six pixels at 720p between two frames of a capture, which is a jolt and not a flinch; over this time no frame at 30 per second moves it by more than half.

`public float RangedStepStageFraction`

:   How far a ranged or casting attacker steps toward its target, as a share of the stage width. A ranged attack does not close the distance, so the step stays under four percent.

`public float ReactionFlinch`

:   Share of its height a combatant squashes by when a reaction of its own fires: a small flinch, so the reaction is something the body does.

`public float ReducedCastFadeSeconds`

:   Seconds the glow of a cast takes to come and to go when motion is reduced, where it is the only thing a cast shows.

`public float ReducedCueSeconds`

:   Seconds the glow that names the author of a number lasts when motion is reduced. Nothing moves then, so at the birth of a number the one who dealt it glows for this long (by `CastGlow`) and the one who took it takes the tint of a hit.

`public float ReducedHitTintSeconds`

:   Seconds the fade of a hit lasts with reduced motion.

`public float ReducedHitTintStrength`

:   How strongly the red fades in with reduced motion, where it is only a short fade and never a flash.

`public float ReducedKoSeconds`

:   Seconds a knock-out takes with reduced motion, which is a fade and nothing else.

`public float ReturnOvershootPixels`

:   Stage pixels the return runs past the resting place before it settles.

`public float ReturnSeconds`

:   Seconds the attacker takes to walk back to where it stood. The walk starts from rest and ends at rest, so a body that has just struck does not jump into motion.

`public float SortBoostMinimumOffsetPixels`

:   How far, in stage pixels, an attacker has to be in front of its resting place before it is drawn over its neighbours.

`public float SquashSeconds`

:   Seconds the squash takes to relax.

`public float StrikePoseHoldSeconds`

:   Seconds the author holds the peak of that pose.

`public float StrikePoseLeanDegrees`

:   Degrees the body of the author leans toward its target at the peak of the pose of a blow from afar. The pivot is the feet.

`public float StrikePoseMinimumDistancePixels`

:   How far from its target, in stage pixels, an attacker has to stand before it makes the pose of a blow from afar: the gap between its painted body and the target's. A blow that crosses less than this is shown by the contact itself; one that crosses more reaches its target by a link and a mark alone, and without a pose of its own the author does nothing a player can see.

`public float StrikePoseReturnSeconds`

:   Seconds the author takes to come back from that pose to its own stance, eased in and out.

`public float StrikePoseRiseSeconds`

:   Seconds the author takes to reach the peak of that pose, eased out.

**Methods**

`public static PuppetMotionProfile CreateDefault()`

:   A copy of the shipped values.

    - **Returns** &mdash; A new profile the caller may edit.

`public PuppetMotionProfile Sanitized()`

:   A copy with every value pulled into the range the motion supports, so no authored number can break the pose.

    - **Returns** &mdash; A new, clamped profile.

---

## PuppetPose

```csharp
public struct PuppetPose
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/CombatantPuppet.cs</small>

The pose a combatant's painted body is drawn in this frame. The pivot of every value is the feet: the body leans, squashes and
slides across the ground, but its feet never leave the ground line.

**Properties**

`public static PuppetPose Identity`

:   The body at rest, untinted and fully visible.

`public bool IsIdentity`

:   True when the pose draws the body exactly as it stands, so nothing needs to be moved or tinted.

**Fields**

`public float Alpha`

:   Opacity of the body, from 1 to 0 as it dissolves.

`public float Desaturate`

:   How grey the body has gone, from 0 to 1, while it is knocked out.

`public float Glow`

:   How much the body brightens, as a share from 0 (not at all) up, while it gathers a cast and, with motion reduced, for a moment when a number names it as the author of a blow or a heal (`CombatantPuppet.Cue`). The two add up.

`public float HitTint`

:   How red the body is, from 0 (untouched) to 1 (fully red).

`public float LeanDegrees`

:   Degrees the body is turned about its feet, counter-clockwise, so a positive angle puts the head toward world -x.

`public float OffsetXPixels`

:   Stage pixels the body is shifted along the ground, positive toward world +x.

`public float ScaleX`

:   Horizontal scale about the feet.

`public float ScaleY`

:   Vertical scale about the feet.

`public float ShadowOpacity`

:   Opacity of the contact shadow, from 1 to 0 as the body dissolves.

`public float ShearDegrees`

:   Degrees the head is slid sideways over the feet, which stay where they are: every point of the ground line holds its place and the point at height h moves by h times the tangent of the angle. A positive angle puts the head toward world -x, as `LeanDegrees` does. Unlike a lean, a shear does not lift one boot off the ground and sink the other.

`public int SortBoost`

:   Sorting-order rise that draws an attacker over its neighbours while it is out in front of its row.

---

## PuppetShear

```csharp
public static class PuppetShear
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PuppetShear.cs</small>

How a horizontal shear about the feet is drawn by two nested transforms, because a transform holds a rotation and a scale and
no shear.

A body that leans by turning about its feet swings one boot below the ground line and the other above it, because the two
boots are not at the same point. A shear keeps every point of the ground line where it is and slides the head sideways, so
both boots stay on the ground. The matrix `[[1, k], [0, 1]]` (the point at height y moves sideways by k times y) has the
singular value decomposition `R(outer) * diag(scaleX, scaleY) * R(inner)`, and a parent that rotates and scales by the
first two factors over a child that rotates by the last one draws exactly that matrix, with no further cost.

**Fields**

`public const float NegligibleShear`

:   Shears smaller than this (the tangent) are drawn as no shear at all, so the two transforms are left at identity.

**Methods**

`public static void Decompose(float shearDegrees, out float outerDegrees, out float scaleX, out float scaleY, out float innerDegrees)`

:   Splits the shear `[[1, tan(shearDegrees)], [0, 1]]` into a rotation, a scale and a rotation.

    - `shearDegrees` &mdash; The angle whose tangent is how far the point at height one slides sideways; positive slides toward +x.
    - `outerDegrees` &mdash; Counter-clockwise rotation of the outer factor, which is the last one applied.
    - `scaleX` &mdash; Scale along x between the two rotations.
    - `scaleY` &mdash; Scale along y between the two rotations; the product of the two scales is one, so the area is kept.
    - `innerDegrees` &mdash; Counter-clockwise rotation of the inner factor, which is the first one applied.

`public static void Recompose(float shearDegrees, float x, float y, out float shearedX, out float shearedY)`

:   Applies the decomposition to a vector, as the two transforms apply it to a point measured from the feet.

    - `shearDegrees` &mdash; The shear, as in `Decompose`.
    - `x` &mdash; Horizontal distance from the feet.
    - `y` &mdash; Height over the feet.
    - `shearedX` &mdash; Horizontal distance from the feet after the shear.
    - `shearedY` &mdash; Height after the shear; it is the height it had.

---

## StageAnimationBinding

```csharp
public sealed class StageAnimationBinding
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Authored key to neutral source/target pulse binding.

**Fields**

`public string Key`

:   Ordinal animation key named by a presentation phase.

`public StageAnimationSource Source`

:   Participant whose neutral sample pulse plays.

---

## StageAnimationSource

```csharp
public enum StageAnimationSource
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Where a neutral sample animation is anchored.

| Value | Meaning |
| --- | --- |
| `SourcePulse` | Pulses the source token named by the presentation cue. |
| `TargetPulse` | Pulses the target token named by the presentation cue. |

---

## StageAudioBinding

```csharp
public sealed class StageAudioBinding
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Authored key to a one-shot audio clip.

**Fields**

`public AudioClip Clip`

:   One-shot clip; missing clips warn and play nothing.

`public string Key`

:   Ordinal sound key named by a presentation phase.

---

## StageFrameMode

```csharp
public enum StageFrameMode
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/BattleStageFrame.cs</small>

How the stage rectangle is derived from the screen.

| Value | Meaning |
| --- | --- |
| `FullScreen` | Use the whole screen, inset by the configured margins. |
| `FixedAspect` | Keep a fixed aspect ratio inside the margins, letterboxing as needed. |
| `Explicit` | Use an explicit pixel rectangle, ignoring screen size. |

---

## StagePresentationPlayback

```csharp
public sealed class StagePresentationPlayback : IPerformBeatModule, IDisposable
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/StagePresentationPlayback.cs</small>

Owns a preset's isolated presentation copies and transient stage effects.
All objects are parented below the supplied owner; no camera or scene scan
is used. Missing and malformed bindings degrade with one warning each.

**Constructors**

`public StagePresentationPlayback(PresentationStagePreset preset, BattlePresenter presenter, Transform owner, PresentationLog presentationLog = null)`

:   Copies recipes and feel without modifying their authored assets, then owns timed effects and one-shot audio below an explicit scene parent. Null preset or owner throws; absent effect bindings warn and play nothing.

    - `preset` &mdash; Authored visual content read once and copied for this session.
    - `presenter` &mdash; Optional existing stage for token pulses and relative sprite sorting.
    - `owner` &mdash; Required scene parent; Dispose destroys only descendants created by this playback.
    - `presentationLog` &mdash; Optional shared warning deduplicator; null creates a private one.

**Properties**

`public int ActiveVfxCount`

:   Live effects not yet expired or reset.

`public IAnimationAdapter Animation`

:   Neutral source/target pulse adapter.

`public IAudioAdapter Audio`

:   One-shot sound adapter under the explicit owner.

`public Transform EffectsRoot`

:   Root containing this session's effects, prototypes and audio.

`public PerformFeelPreset Feel`

:   Owned feel copy used by this playback session.

`public Transform Owner`

:   Explicit parent supplied by the host.

`public BattlePresenter Presenter`

:   Optional stage presenter used for token pulses and sprite sorting.

`public PresentationRecipeSet Recipes`

:   Owned recipe set containing owned definition copies.

`public IReadOnlyList<StageSkillMotionBinding> SkillMotions`

:   How the user of each named skill moves, copied from the preset.

`public IVfxAdapter Vfx`

:   Effect adapter with bounded, timed instances owned by this session.

**Methods**

`public void Dispose()`

:   Resets playback and destroys all owned copies and scene objects, once.

`public void OnPhaseBegin(PerformPhaseContext context)`

:   Intentionally does not redispatch phases already handled by the presenter.

    - `context` &mdash; Phase notification; adapters are dispatched separately by BattlePresenter.

`public void Reset()`

:   Releases effects, stops audio and restores owned neutral pulses.

`public void Tick(float presentationDeltaSeconds)`

:   Expires effects on positive finite presentation time.

    - `presentationDeltaSeconds` &mdash; Elapsed visual seconds; zero, negative and non-finite values are ignored.

---

## StageSkillMotionBinding

```csharp
public sealed class StageSkillMotionBinding
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Authored statement of how the user of one skill moves: walks up to its target, steps a little, or stays in place.

**Fields**

`public PuppetActionKind Kind`

:   How the skill's user moves; Auto leaves it to the presenter's own reading of the skill.

`public string SkillId`

:   Stable id of the skill, for example `skill.power-blow`.

---

## StageVfxBinding

```csharp
public sealed class StageVfxBinding
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/PresentationStagePreset.cs</small>

Authored key to a stage VFX prototype.

**Fields**

`public string Key`

:   Ordinal effect key named by a presentation phase.

`public float LifetimeSeconds`

:   Positive finite lifetime in the shared visual clock.

`public GameObject Prototype`

:   Optional prefab cloned with its authored renderer settings.

`public float Scale`

:   Positive finite multiplier of the effect's authored scale.

`public string SortingLayerName`

:   Sorting layer of the sprite alternative.

`public int SortingOrderOffset`

:   Sorting order relative to the target body, or source when no target exists.

`public Sprite Sprite`

:   Sprite alternative when no prefab is assigned.

`public Color Tint`

:   Tint for the sprite alternative; prefab colors are preserved.

---

## StrikeEffectKind

```csharp
public enum StrikeEffectKind
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/StrikeEffectLayer.cs</small>

What one effect of a `StrikeEffectLayer` draws.

| Value | Meaning |
| --- | --- |
| `Link` | A flare on the trunk of the author, and a bright head that travels from it to the target and leaves a tapered streak that fades once the head has arrived. |
| `Impact` | A short burst on the body of the target: a bright X, and for a critical hit a ring that opens around it. |
| `Wave` | An arc that leaves the author and sweeps toward the targets of an area strike, so that several targets read as one gesture. |

---

## StrikeEffectLayer

```csharp
public sealed class StrikeEffectLayer : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/StrikeEffectLayer.cs</small>

Draws what joins the author of a strike to its targets on the 2D stage: a link that is born on the body of the author and
travels to the target, a mark of impact on the body that is hit and a wave that sweeps over the targets of an area strike. A
link is lit where it starts, so that it reads as leaving the body it starts on whatever it crosses on its way: the head of a link
that is bright only where it is passes over the sleeve of whoever stands between, and reads as that one's blow. A blow that does not touch its target
reads as nothing without them: an area strike only makes its targets flash, a strike from the back row "cuts" through empty
floor, and a strike at a target covered by an ally stops on the ally's body.

The layer only draws. When each effect plays is the presenter's decision: it calls `PlayLink`,
`PlayImpact` and `PlayWave` at the frame it chooses, with world points and world units, and the stage
passes the presentation clock to `Tick`. The layer reads no clock of its own (a capture that steps a manual clock
sees the same frames the player does) and nothing here depends on the time scale.

Everything is drawn with sprite renderers of the default sprite material, in shapes the layer generates once (a streak, a disc,
an X, a ring and a crescent: nothing to author, no shader, no texture asset), tinted by the colour of each call. They sit at
`SortingOrder`, over the bodies and the target marks and under the plates and the floating numbers, so an effect
never hides a name or a number. The renderers are pooled: the pool grows on demand the first time effects play and is reused,
so a layer that stands still, and one that plays effects it has played before, allocate nothing in a frame.

Opacity never changes by more than half in one frame at 30 frames per second: every effect comes in over
`FadeInSeconds` and goes out over at least `MinimumFadeSeconds`, whatever the caller asks for.

**Properties**

`public int ActiveCount`

:   Number of effects alive. An effect that has run its course is dropped in the `Tick` that ends it.

`public bool ReduceMotion`

:   When true nothing travels or grows: a link shows whole and fades, an impact shows at its final size and fades, and a wave is not drawn. A fade is not motion, so every effect still comes in and goes out. Turning it on ends the waves that are playing.

`public float UnitsPerPixel`

:   World units one stage pixel is worth. What the layer measures in pixels (the least width of a link, the least impact, how high a link may arch and the height of a wave) follows it, so the effects keep their proportion to the bodies on a stage that is not at 0.01. A value that is not positive and finite restores `BattlePresenter.DefaultUnitsPerPixel`.

**Fields**

`public const float FadeInSeconds`

:   Seconds an effect takes to come in. Three frames at 30 per second, so the opacity climbs by a third a frame and never jumps.

`public const int MaximumEffects`

:   Most effects alive at once. A request past it takes the place of the oldest effect, which ends on the spot.

`public const float MinimumFadeSeconds`

:   Least seconds an effect takes to go out. A shorter fade is lengthened to this, because a fade of two frames or less is a pop, not a fade.

`public const int SortingOrder`

:   Sorting order of every renderer of the layer: over the bodies (small orders) and the target marks (`TargetPreviewView.ReticleSortingOrder`, 900), under the plates (`SkinnedTokenPlate.DefaultSortingOrder`, 1000) and the floating numbers (`FloatingNumberLabel.DefaultSortingOrder`, 2000).

**Methods**

`public void Clear()`

:   Ends every effect at once and hides every renderer. For a skip, a restart and a teardown; the pool is kept for the next effect.

`public Vector3 DestinationAt(int index)`

:   Where the effect ends up: the point a link reaches, the point an impact is centred on, the point a wave stops at.

    - `index` &mdash; Position among the effects alive, oldest first.

`public Vector3 HeadAt(int index)`

:   Where the effect is now: the head of a link, the centre of an impact, the middle of the front of a wave.

    - `index` &mdash; Position among the effects alive, oldest first.

`public bool IsFinishedAt(int index)`

:   True when the effect has run its course. An effect is dropped in the `Tick` that ends it, so an index inside 0 to `ActiveCount` minus one answers false and an index outside it, which names an effect that is gone, true.

    - `index` &mdash; Position among the effects alive, oldest first.

`public StrikeEffectKind KindAt(int index)`

:   The kind of the effect at `index`, counted from the oldest. Every reader that takes an index returns the default of its type for an index outside 0 to `ActiveCount` minus one, except `IsFinishedAt`.

    - `index` &mdash; Position among the effects alive, oldest first.

`public float OpacityAt(int index)`

:   The opacity the effect is drawn at now, from zero to the alpha of its colour. It is zero before the first `Tick`.

    - `index` &mdash; Position among the effects alive, oldest first.

`public Vector3 OriginAt(int index)`

:   Where the effect started: the point a link leaves, the point an impact is centred on, the point a wave leaves.

    - `index` &mdash; Position among the effects alive, oldest first.

`public void PlayImpact(Vector3 atWorld, float sizeWorld, Color color, bool critical, float seconds)`

:   Draws the mark of a blow on the body that takes it: a short burst in the shape of an X with a bright centre, centred on `atWorld`. It is born at 60 percent of its size, reaches all of it with an ease-out over the first half of its life and fades over the rest. A critical hit is drawn 1.35 times bigger and adds a ring that opens around it.

    - `atWorld` &mdash; World point on the body of the target, at the chest or the hip and clear of the face.
    - `sizeWorld` &mdash; Width of the burst at its full size, in world units. At least 24 stage pixels.
    - `color` &mdash; Colour of the burst; its alpha is the opacity it peaks at. The centre is white mixed with it.
    - `critical` &mdash; True for a critical hit: bigger, with a ring.
    - `seconds` &mdash; Life of the mark in seconds. At least 0.2, at most ten.

`public void PlayLink(Vector3 fromWorld, Vector3 toWorld, Color color, float travelSeconds, float lingerSeconds, float widthWorld)`

:   Draws the link between the author of a strike and its target. A flare lights where the link starts and a bright head leaves `fromWorld` and reaches `toWorld` in `travelSeconds` with an ease-out, trailing a streak that is thin at the author and wide at the head and lit all along; once the head has arrived the whole streak fades over `lingerSeconds`, and the flare goes out in the first quarter of a second. The path is a gentle arc that peaks over the straight line by 15 percent of the distance (60 stage pixels at most) so that it does not run flat through the bodies between the two. The layer draws over every body, so the link is seen over the ones in the way, and the flare is what says whose it is. With a travel of zero or less the whole streak appears at once and fades.

    - `fromWorld` &mdash; World point the link starts on, which is the trunk of the author: the flare is drawn there.
    - `toWorld` &mdash; World point the head reaches, on the body of the target and clear of its face.
    - `color` &mdash; Colour of the streak; its alpha is the opacity the link peaks at. The centre of the head is white mixed with it.
    - `travelSeconds` &mdash; Seconds the head takes to arrive; zero or less shows the whole streak at once. At most ten.
    - `lingerSeconds` &mdash; Seconds the streak takes to fade once the head has arrived. At least `MinimumFadeSeconds`, at most ten.
    - `widthWorld` &mdash; Width of the streak where it meets the head, in world units. At least four stage pixels.

`public void PlayWave(Vector3 fromWorld, float reachWorld, float direction, Color color, float seconds)`

:   Draws the wave of an area strike: a crescent that leaves the author, advances toward the targets and fades as it goes, so that three targets read as one gesture. It is drawn as high as a body (300 stage pixels). With `ReduceMotion` on it is not drawn.

    - `fromWorld` &mdash; World point the wave leaves, at the author.
    - `reachWorld` &mdash; Distance in world units the wave advances along x, from the author to past the farthest target.
    - `direction` &mdash; Which way the targets lie: negative for toward -x, anything else for toward +x.
    - `color` &mdash; Colour of the wave; its alpha is the opacity it peaks at.
    - `seconds` &mdash; Life of the wave in seconds, which it takes to reach `reachWorld`. At least 0.25, at most ten.

`public float ProgressAt(int index)`

:   How far through its life the effect is, from zero to one.

    - `index` &mdash; Position among the effects alive, oldest first.

`public float SizeAt(int index)`

:   The size the effect is drawn at now, in world units: the head of a link, the width of an impact (the ring is bigger), the height of a wave.

    - `index` &mdash; Position among the effects alive, oldest first.

`public void Tick(float deltaSeconds)`

:   Advances every effect by presentation time and drops the ones that have run their course. Call it once a frame, after the frame's effects have been started, with the clock the stage passes to its other motions.

    - `deltaSeconds` &mdash; Positive presentation-clock duration; zero, negative and not-a-number steps are ignored.

---

## TargetPreviewView

```csharp
public sealed class TargetPreviewView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/TargetPreviewView.cs</small>

Draws what a skill is about to hit, on the stage, before the player
commits.

The invariant this exists to hold: the affected set is drawn on the stage
rather than described in a tooltip sentence. Nine of the twelve shipped
resolvers take no player pick at all, so for those a sentence was the only
thing the player ever got - and a sentence cannot say which three of six
bodies are in the blast.

Every treatment is procedural: rings, bands, scrims and ticks drawn from
the skin's own palette. Nothing ships for it, and every one is fed by
`TargetCandidateQuery.GetCandidates`, which already agrees with
the engine. Eight looks, one data source, no new simulation code.

**Properties**

`public bool BandVisible`

:   Whether a formation-row band is currently drawn.

`public TargetTreatment? Current`

:   The treatment currently on screen, or null when nothing is previewed.

`public Sprite GroundRingSprite`

:   The ground ring sprite in use, or null.

`public bool ManualClock`

:   When true the pulse is no longer driven by the engine clock in LateUpdate: the host steps it through the presenter. Off by default, which keeps the normal unscaled-time behaviour.

`public IReadOnlyList<StableId> MarkedCombatants`

:   The combatants whose marks carry the reticle: the picked targets of the last `Show`.

`public float ReticlePulse`

:   Where the pulse of the reticle is, from 0 (full opacity) to 1 (faded by `PulseAlphaDepth`); always 0 while motion is reduced.

`public float ReticleScale`

:   Scale the reticle is drawn at now: 1 minus `PulseScaleDepth` at the deepest of the pulse, which is 1, so the brackets keep the box they are fitted to.

`public Sprite ReticleSprite`

:   The reticle sprite in use, or null.

`public bool ScrimVisible`

:   Whether a region fill is currently drawn.

`public bool UsesSpriteMarks`

:   True when the preview draws painted sprites instead of the procedural ring.

`public int VisibleMarkCount`

:   How many marks the last `Show` drew.

**Fields**

`public const float DefaultPulseSeconds`

:   Default period of the reticle pulse, in seconds. Slow enough to read as a lock-on, not as a flash.

`public const int PreviewSortingOrder`

:   Where the preview draws: above the contact shadows, below every body. A scrim over the combatants would be a filter on the picture rather than a mark on the ground, and the player would be judging the pick through it.

`public const float PulseAlphaDepth`

:   How far the pulse fades the brackets, as a share of their opacity.

`public const float PulseScaleDepth`

:   How far the pulse draws the brackets in, as a share of their size: zero. The pulse fades the brackets and keeps their size, because drawing them in by a share of the box took them past the margin and onto a large body (a boss is several hundred pixels tall).

`public const float ReticleMarginPixels`

:   Gap, in stage pixels, between the inner edge of the ink of the brackets and the body they wrap (`CombatantTokenView.TryGetMarkBoundsWorld`: the painted body, the reach of its art and its pose), and between the outer edge of their ink and a neighbour. The brackets stand around the body, not on it: drawn inside, the corners of a body with a bright edge (flames, horns, a raised weapon) were lost in it. The gap is counted from the inner edge of the bars, which are drawn outside the box the brackets frame (`TryGetReticleBox`); counted from the outer edge, a bar of four to six pixels left its inner edge at the body or over it. It is four pixels, a whole pixel more than the three the eye needs, so the edge of the ink that falls between pixels and is smoothed never reads closer than three pixels to the body on the screen. The dark line under the brackets (`ReticleUnderlineAlpha`) reaches a pixel and a half closer.

`public const int ReticleSortingOrder`

:   Sorting order of the reticle brackets: above every body, below every plate.

`public const float ReticleUnderlineAlpha`

:   Opacity of the dark line under the brackets, which keeps them readable over a body or a backdrop of their own colour.

`public const float RingPixels`

:   Diameter of a candidate ring, in reference pixels.

`public const float RowBandPixels`

:   Height of a formation-row band, in reference pixels.

`public const float ScrimOpacity`

:   Opacity of a team or stage scrim.

**Methods**

`public void Build(CompiledBattleSkin battleSkin, float unitsPerPixel)`

:   Prepares the preview to draw with a skin. Call before `Show`.

    - `battleSkin` &mdash; The compiled skin whose palette the marks are drawn from.
    - `unitsPerPixel` &mdash; World units per reference pixel, matching the stage.

`public void FinishFades()`

:   Finishes every fade of the marks at once, as a skipped beat does.

`public void Hide(BattleStage2D stage)`

:   Clears the preview and gives every token its colour back, as a cancelled aim does.

    - `stage` &mdash; The stage to un-dim; null skips that half.

`public void Hide(BattleStage2D stage, bool commandConfirmed)`

:   Clears the preview. When the aim closed because a command was confirmed, the combatants that could not be picked keep their dim until the action's own focus takes over (see `CombatantTokenView.CandidateHoldSeconds`) instead of brightening for the frames between the two; a cancelled aim gives them their colour back at once.

    - `stage` &mdash; The stage to un-dim; null skips that half.
    - `commandConfirmed` &mdash; True when the aim ended in a confirmed command.

`public void SetMarkStyle(Sprite reticle, Sprite groundRing, float pulseSeconds)`

:   Gives the preview painted marks. A themed stage supplies a four-bracket reticle and a ground ring, both white so the accent colour of the skin tints them. Either may be null; with both null the procedural ring is used.

    - `reticle` &mdash; Square sprite of four corner brackets, or null.
    - `groundRing` &mdash; Wide elliptical ring drawn on the ground, or null.
    - `pulseSeconds` &mdash; Seconds one pulse of the reticle takes; zero or less keeps it still. The reticle never turns.

`public void Show(BattleStage2D stage, TargetTreatment treatment, IReadOnlyList<StableId> affected, IReadOnlyList<StableId> candidates, StableId playerTeamId)`

:   Draws `treatment` for the set the resolver returned. The treatment is degraded for the party in front of it first, so a region shape with one candidate collapses to the single-pick look rather than drawing a team scrim around one body.

    - `stage` &mdash; The stage whose placements supply every position.
    - `treatment` &mdash; The classified treatment, before degradation.
    - `affected` &mdash; Combatants the skill would reach.
    - `candidates` &mdash; Legal picks. Anything on the stage and not in here is dimmed.
    - `playerTeamId` &mdash; The player's team, which decides which half of the stage is theirs.

`public void Show(BattleStage2D stage, TargetTreatment treatment, IReadOnlyList<StableId> affected, IReadOnlyList<StableId> candidates, StableId playerTeamId, IReadOnlyList<StableId> picked)`

:   Draws `treatment` and tells which of the affected combatants are picked. With painted sprites in use, every affected combatant gets the ground ring and only a picked one gets the reticle.

    - `stage` &mdash; The stage whose placements supply every position.
    - `treatment` &mdash; The classified treatment, before degradation.
    - `affected` &mdash; Combatants the skill would reach.
    - `candidates` &mdash; Legal picks. Anything on the stage and not in here is dimmed.
    - `playerTeamId` &mdash; The player's team, which decides which half of the stage is theirs.
    - `picked` &mdash; The combatants the player has chosen or the rule has chosen for them; null treats every affected combatant as picked.

`public bool TryGetReticleBox(StableId combatant, out Rect box)`

:   The box the brackets of a marked combatant frame, in the stage pixels of the preview: the box its marks are fitted outside (`CombatantTokenView.TryGetMarkBoundsWorld`: the painted body, grown to the reach of its art, to the top of its breath and to its pose) grown by `ReticleMarginPixels` on every side, and clear of the painted body of every other combatant. The inner edge of the ink of the bars stands on this box; the bars are drawn outside it, so their outer edge is the thickness of a bar farther out (two to six pixels, by the size of the box), and a neighbour is cleared by the margin beyond it.

    - `combatant` &mdash; A combatant carrying a reticle.
    - `box` &mdash; Receives the box; x and y are its lower left corner.
    - **Returns** &mdash; False when the combatant carries no reticle or has nothing drawn.

---

## TargetingReticleView

```csharp
public sealed class TargetingReticleView : MonoBehaviour
```

`TurnHerald.Presentation` &middot; <small>Runtime/Presentation/Stage/TargetingReticleView.cs</small>

The cursor that lives on one candidate: a marker hanging over whoever is
currently pointed at, with that candidate's position in the list beside it.

This is the treatment `TargetingPreset.Reticle` asks for, and it
is the one the genre trained players to expect -- a marker above a head that
steps sideways when you press a direction and commits when you press
confirm. Until now the package expressed every pick the same way whatever the
preset said: a row of name buttons under the stage, which is fine with a
mouse and close to unusable on a pad.

It is drawn from the skin's own shapes, so it ships no texture, needs no font
glyph, and inherits whatever look the project chose. It is presentation only:
it never resolves a target, it only says which one is being pointed at.

**Properties**

`public bool IsShown`

:   True while the marker is asked to be on screen. It stays drawn for the length of a fade after it is hidden; see `Opacity`.

`public float Opacity`

:   How opaque the marker is drawn right now, from 0 to 1.

`public StableId? Pointed`

:   The combatant the marker is over, or null while it is hidden.

**Fields**

`public const float BobHertz`

:   Bobs per second. Slow enough to read as breathing, not as an alarm.

`public const float BobPixels`

:   Half-height of the marker's bob, in reference pixels.

`public const float HoverPixels`

:   How far above the combatant's art the marker floats, in reference pixels.

`public const float MarkerPixels`

:   Marker width and height in reference pixels.

`public const int ReticleSortingOrder`

:   Sorting order the marker draws at, above every combatant plate.

**Methods**

`public void ApplySkin(CompiledBattleSkin battleSkin)`

:   Re-applies the skin's colours without rebuilding the marker.

    - `battleSkin` &mdash; The skin to adopt.

`public void Build(CompiledBattleSkin battleSkin, float pixelScale)`

:   Builds the marker. Explicit so EditMode tests can construct one.

    - `battleSkin` &mdash; Skin the marker is dressed from; null falls back to the package default.
    - `pixelScale` &mdash; World units one reference pixel is worth.

`public void Hide()`

:   Takes the marker off screen.

`public void Show(BattleStage2D stage, StableId combatantId, int index, int count)`

:   Puts the marker over one candidate.

    - `stage` &mdash; Stage that knows where the combatant is standing.
    - `combatantId` &mdash; The candidate to point at.
    - `index` &mdash; Zero-based position in the candidate list.
    - `count` &mdash; How many candidates there are.

`public void Tick(float presentationDeltaSeconds)`

:   Advances the marker's bob around the anchor it was shown at. The offset is applied to a remembered anchor rather than to the current position, because adding a delta to the live transform every frame is how a bob turns into a drift.

    - `presentationDeltaSeconds` &mdash; Visual seconds elapsed.

---
