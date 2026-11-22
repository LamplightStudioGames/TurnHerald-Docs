# Declare the floor of a stage

A painted stage plate has a floor, a back wall and props standing on it, and the layout has no
way to see any of that. The **stage floor contract** is how you tell it: where the feet stand, where
the open floor ends, where the horizon is, and which parts of the plate no foot may touch. With it,
the formation follows the picture instead of standing just above the dock band.

You need a theme with a stage backdrop and a formation layout. The layouts themselves are explained
in [Place combatants with the Formation Editor](place-formations.md#how-seats-become-standing-points).

---

## What the contract holds

A **Stage Backdrop** is created with **Assets > Create > TurnHerald > Stage Backdrop** and is assigned
to the theme as its `StageBackdrop`. Its **Stage contract** fields are all optional, and all of them
are **normalized over the plate sprite with the origin at its bottom left**: `(0, 0)` is the bottom
left corner of the plate and `(1, 1)` its top right. Nothing is in pixels, so the contract does not
change when the plate is rescaled or the stage is resized.

| Field | Meaning |
| --- | --- |
| **Declares Floor** | Turn on to use the values below. Off leaves the feet just above the dock band, and the values below are ignored. |
| **Plate Layer** | The index of the backdrop layer whose sprite the values are measured on. |
| **Ground Line Y** | Height of the line the feet of the Line layout stand on, from the bottom of the plate (0) to its top (1). |
| **Floor Back Edge Y** | Height of the back edge of the open floor. No foot may stand above it: that is the wall, the steps or the set behind the floor. |
| **Declares Perspective** | Turn on when the plate has a real horizon and vanishing point. Off makes Depth fall back to Line. |
| **Horizon Y** | Height of the horizon on the plate. Depth scales sprites in proportion to their distance below it. |
| **Vanishing Point X** | Horizontal position of the vanishing point, from the left (0) to the right (1). Depth pulls receding rows toward it. |
| **Props** | Polygons, in plate coordinates, where no foot may stand: stairs, wells, walls, rocks. A polygon with fewer than three corners blocks nothing. |
| **Prop Mask** | An optional texture drawn over the plate: a pixel with alpha of at least one half is a prop. It needs **Read/Write** enabled, and it adds to the polygons. |

A new backdrop starts with a ground line of 0.34, a back edge of 0.57, a horizon of 0.58 and a
vanishing point of 0.5. The stage reads the contract again every time it lays out, so it follows the
window as it is resized.

!!! note "How a prop mask is read"
    The mask is reduced to a grid of 64 columns by 36 rows. A cell is a prop when the pixel at its
    middle is at least half opaque, and neighbouring cells are merged into rectangles named `mask`.
    A fine detail narrower than a cell is therefore lost.

## Mark the lines on the preview

In Combat Studio, open the **Appearance** tab, then its **Stage** sub-tab. Under **Formation and
stage floor**, pick the **Formation layout**, then turn on **Edit floor lines on the preview**. The
preview shows the ground line in green, the back edge of the open floor in red, the horizon and the
vanishing point in blue and the props in orange. Drag a line to move it, or type its value into
**Ground line**, **Floor back edge**, **Horizon** or **Vanishing point**.
**Declares horizon and vanishing point** is the switch for the perspective pair.

Props are drawn on the preview but are edited on the backdrop asset, in **Props** and **Prop Mask**.
A theme with no backdrop shows a note instead of the fields: with nothing to measure, there is no
floor to edit.

## What each layout reads

| Layout | Uses from the contract |
| --- | --- |
| **Line** | The ground line for the feet. The back edge and the props are checked after the layout is solved, and the props that cross the ground line also decide how far each side may spread. The horizon and the vanishing point are ignored. |
| **Depth** | The ground line for the front row, the horizon and the vanishing point for the sizes and the lean of the rows. It needs all three, with the horizon above the ground line. The back edge and the props are checked after the layout is solved. |
| **Legacy** | Nothing. The authored seats are projected as written. |

Depth also needs art no taller than 15% of the screen height. When either condition fails, the stage
uses Line and `BattleStage2D.LayoutResult.Fallback` says why.

## When it does not fit

The Line layout fits each side between the edge of the plate (a margin of 1.5% of its width is kept
free) and the first prop that stands on the ground line, a quarter of a body plus 6 pixels short of
it. When a side does not fit, it gives way in this order, and stops at the first step that fits:

1. **Lean.** When one side runs out of room and the other has some, the whole formation leans toward
   the free side, by up to 3% of the width.
2. **Shrink.** The combatants shrink toward the smallest height of the window for their population,
   which keeps the overlap inside its range.
3. **Pack.** The neighbours overlap more, up to 25% of the narrower silhouette.
4. **Squeeze.** Only then is the side pulled toward the centre, however much the silhouettes overlap.

The layout never moves a foot up or down to dodge the contract, and Depth does none of the four
steps. Anything left over is **reported, not hidden**.

## Read the problems

Each solved layout lists what it could not avoid.
[`BattleStage2D.LayoutResult`](../reference/stage-and-tokens.md#battlestage2d) holds a
[`FormationLayoutResult`](../reference/formations.md#formationlayoutresult) whose `Issues` is a list
of [`FormationLayoutIssue`](../reference/formations.md#formationlayoutissue), one per defect:

| Issue kind | Meaning |
| --- | --- |
| `FootAboveFloorBackEdge` | A foot stands above the back edge of the open floor, on the wall or the set behind it. |
| `FootInsideProp` | A foot stands inside a prop. `PropName` names it. |

A foot counts as inside a prop when the point at its middle, or a quarter of the painted body to
either side, lies in the prop. `LayoutResult` is `null` while the Legacy layout is in use or no
combatant is on the stage.

The **Content Validator** reports the same defects before you build. Open **Tools > TurnHerald >
Content Validator**, assign the backdrop and a layout in the toolbar's second row and press
**Validate Stage Floor**. The Combat Studio **Stage** sub-tab shows the same text under its fields.
The check places 1, 3, 5 and 6 combatants a side at 1280x720, 1366x768, 1920x1080 and 1920x1200, so
a plate that only works at 16:9 is reported. Its findings are:

| Finding | Severity |
| --- | --- |
| The theme asks for Depth but the stage declares no floor and perspective | Error |
| The plate layer has no sprite to measure on | Error |
| The ground line is above the back edge | Error |
| The horizon is not above the ground line | Error |
| A foot stands above the back edge | Error |
| A foot stands inside a prop | Error |
| The prop mask texture has Read/Write disabled, so it is ignored | Warning |

The foot checks always solve the **Line** layout, which is what a Depth stage falls back to. When the
theme asks for Depth and the stage declares what Depth needs, they solve the Depth layout too, so the
back row is checked for feet; those findings say "in the Depth layout".

## Implement your own floor source

A stage whose floor is not a painted plate, such as a 3D set seen through a camera, can supply the
contract itself. The stage asks an
[`IStageFloorSource`](../reference/formations.md#istagefloorsource) every time it lays out, handing
it the stage rectangle in world units and the size of a pixel, and expects a
[`StageFloorPlan`](../reference/formations.md#stagefloorplan) in **projected stage pixels**: absolute
pixel positions in the stage viewport, with Y increasing upward. The plate-based source the package
uses is [`BattleStageFloorSource`](../reference/stage-and-tokens.md#battlestagefloorsource).

```csharp
using TurnHerald.Authoring;      // IStageFloorSource, StageFloorPlan, StageFloorProp, FormationLayoutMode
using TurnHerald.Presentation;   // BattlePresenter
using UnityEngine;              // Rect, Mathf, Debug

// A floor measured as fractions of the stage rectangle.
public sealed class PlazaFloor : IStageFloorSource
{
    public StageFloorPlan Resolve(Rect stageWorldRect, float unitsPerPixel)
    {
        int X(float f) => Mathf.RoundToInt((stageWorldRect.xMin + f * stageWorldRect.width) / unitsPerPixel);
        int Y(float f) => Mathf.RoundToInt((stageWorldRect.yMin + f * stageWorldRect.height) / unitsPerPixel);

        var well = new StageFloorProp("Well", new[]
        {
            new ProjectedFormationPoint(X(0.46f), Y(0.20f)),
            new ProjectedFormationPoint(X(0.54f), Y(0.20f)),
            new ProjectedFormationPoint(X(0.54f), Y(0.55f)),
            new ProjectedFormationPoint(X(0.46f), Y(0.55f)),
        });

        // ground line, back edge, horizon, vanishing point, props
        return new StageFloorPlan(Y(0.30f), Y(0.62f), Y(0.66f), X(0.5f), new[] { well });
    }
}

public static class PlazaSetup
{
    public static void Apply(BattlePresenter presenter)
    {
        presenter.SetStageLayout(FormationLayoutMode.Depth, new PlazaFloor());

        var stage = presenter.Stage;
        if (stage == null || stage.LayoutResult == null) return;
        foreach (var issue in stage.LayoutResult.Issues)
            Debug.LogWarning(issue.Kind + " " + issue.CombatantId + " " + issue.PropName);
    }
}
```

A floor that never changes can skip the class. [`StaticStageFloorSource`](../reference/formations.md#staticstagefloorsource)
answers with one fixed plan, and `null` for any value means the stage declares nothing for it:

```csharp
var plan = new StageFloorPlan(
    groundLineY: 360, floorBackEdgeY: 520, horizonY: null, vanishingPointX: null, floorProps: null);
presenter.SetStageLayout(FormationLayoutMode.Line, new StaticStageFloorSource(plan));
```

Three things to know:

- A plan declares a perspective only when it gives **both** `horizonY` and `vanishingPointX`.
- The stage asks the source only while it lays out. When what your source would answer changes
  without the viewport changing, call `BattleStage2D.RelayoutTokens()`.
- `BattleRuntimeController` calls `SetStageLayout` with the theme's layout and its backdrop's floor
  whenever it applies a theme, which replaces a source you set earlier. Set yours after the theme is
  applied, and again after a theme change, or drive the `BattlePresenter` yourself.

## Next

- **[Place combatants with the Formation Editor](place-formations.md)** - the layouts, and how the
  authored seats become standing points.
- **[Fit the battle to your screen](interface-layout.md)** - the stage rectangle the floor is measured in.
- **[Formations reference](../reference/formations.md)** and
  **[Stage and tokens reference](../reference/stage-and-tokens.md)** - every type on this page in full.
