# ♿ Accessibility & Indoor Navigation

## 1. 🎯 Introduction

Accessible public transport isn't just about wheelchair ramps — it's about the entire journey: Can a passenger find their way from the station entrance to the right platform? Is there a step-free route? Does the vehicle have low-floor boarding? NeTEx models accessibility at every level — from high-level assessments on stops to detailed navigation paths through stations.

In this guide you will learn:
- ♿ How AccessibilityAssessment declares accessibility at stops and quays
- 🏗️ How equipment objects model lifts, escalators, ramps, and shelters
- 🗺️ How NavigationPath and PathLink model indoor wayfinding routes
- 🚌 How vehicle accessibility connects to stop infrastructure
- 📝 Practical examples from simple to complex

---

## 2. ♿ AccessibilityAssessment — The Starting Point

**AccessibilityAssessment** is the core object for declaring whether a stop, quay, or vehicle is accessible. It uses a simple structure with boolean-like values (`true`, `false`, `unknown`):

```text
StopPlace / Quay
 └── AccessibilityAssessment
      ├── MobilityImpairedAccess: true/false/unknown
      └── limitations
           └── AccessibilityLimitation
                ├── WheelchairAccess: true/false/unknown
                ├── StepFreeAccess: true/false/unknown
                ├── EscalatorFreeAccess: true/false/unknown
                ├── LiftFreeAccess: true/false/unknown
                ├── AudibleSignalsAvailable: true/false/unknown
                └── VisualSignsAvailable: true/false/unknown
```

### Where to Put It

AccessibilityAssessment can appear at **different levels of granularity**:

| Level | What It Describes | Example |
|-------|------------------|---------|
| **StopPlace** | General accessibility of the whole station | "Oslo S is wheelchair accessible" |
| **Quay** | Accessibility of a specific platform | "Platform 3 has step-free access" |
| **Vehicle** | Accessibility of the fleet unit | "Bus EL-12345 has low floor" |

> ⚠️ **Important:** Quay-level assessment overrides StopPlace-level. If the StopPlace says `WheelchairAccess=true` but a specific Quay says `WheelchairAccess=false`, the Quay value takes precedence for that platform.

### Example: Accessible Rail Station

```xml
<StopPlace id="ERP:StopPlace:OsloS" version="1">
  <Name>Oslo S</Name>
  <AccessibilityAssessment id="ERP:AccessibilityAssessment:OsloS" version="1">
    <MobilityImpairedAccess>true</MobilityImpairedAccess>
    <limitations>
      <AccessibilityLimitation>
        <WheelchairAccess>true</WheelchairAccess>
        <StepFreeAccess>true</StepFreeAccess>
        <EscalatorFreeAccess>false</EscalatorFreeAccess>
        <LiftFreeAccess>false</LiftFreeAccess>
        <AudibleSignalsAvailable>true</AudibleSignalsAvailable>
        <VisualSignsAvailable>true</VisualSignsAvailable>
      </AccessibilityLimitation>
    </limitations>
  </AccessibilityAssessment>
  <TransportMode>rail</TransportMode>
  <StopPlaceType>railStation</StopPlaceType>
  <quays>
    <!-- Platform 1: fully accessible -->
    <Quay id="ERP:Quay:OsloS_Spor1" version="1">
      <Name>Spor 1</Name>
      <AccessibilityAssessment id="ERP:AccessibilityAssessment:Spor1" version="1">
        <MobilityImpairedAccess>true</MobilityImpairedAccess>
        <limitations>
          <AccessibilityLimitation>
            <WheelchairAccess>true</WheelchairAccess>
            <StepFreeAccess>true</StepFreeAccess>
          </AccessibilityLimitation>
        </limitations>
      </AccessibilityAssessment>
    </Quay>
    <!-- Platform 9: NOT step-free (stairs only) -->
    <Quay id="ERP:Quay:OsloS_Spor9" version="1">
      <Name>Spor 9</Name>
      <AccessibilityAssessment id="ERP:AccessibilityAssessment:Spor9" version="1">
        <MobilityImpairedAccess>false</MobilityImpairedAccess>
        <limitations>
          <AccessibilityLimitation>
            <WheelchairAccess>false</WheelchairAccess>
            <StepFreeAccess>false</StepFreeAccess>
          </AccessibilityLimitation>
        </limitations>
      </AccessibilityAssessment>
    </Quay>
  </quays>
</StopPlace>
```

---

## 3. 🏗️ Equipment — What's Physically There

Beyond assessments, NeTEx models the **physical equipment** that makes accessibility possible. Equipment lives inside `placeEquipments` on a StopPlace or Quay:

```text
StopPlace / Quay
 └── placeEquipments
      ├── ShelterEquipment        -- Weather protection
      ├── WaitingRoomEquipment    -- Indoor waiting areas
      ├── SanitaryEquipment       -- Toilets
      ├── TicketingEquipment      -- Ticket machines
      ├── LiftEquipment           -- Elevators
      ├── EscalatorEquipment      -- Escalators
      ├── StaircaseEquipment      -- Stairs (with handrail info)
      └── RampEquipment           -- Wheelchair ramps
```

### Documented Equipment in This Profile

| Equipment | Key Properties | Where |
|-----------|---------------|-------|
| [ShelterEquipment](../../Objects/ShelterEquipment/Table_ShelterEquipment.md) | Enclosed, StepFree, Seats | StopPlace or Quay |
| [WaitingRoomEquipment](../../Objects/WaitingRoomEquipment/Table_WaitingRoomEquipment.md) | Heated, WheelchairAccess, Seats | StopPlace |
| [SanitaryEquipment](../../Objects/SanitaryEquipment/Table_SanitaryEquipment.md) | WheelchairAccess, Gender | StopPlace |
| [TicketingEquipment](../../Objects/TicketingEquipment/Table_TicketingEquipment.md) | PaymentMethods, TicketTypes | StopPlace or Quay |

### Example: Accessible Bus Stop with Shelter

```xml
<Quay id="ERP:Quay:BusA" version="1">
  <Name>Platform A</Name>
  <AccessibilityAssessment id="ERP:AccessibilityAssessment:BusA" version="1">
    <MobilityImpairedAccess>true</MobilityImpairedAccess>
    <limitations>
      <AccessibilityLimitation>
        <WheelchairAccess>true</WheelchairAccess>
        <StepFreeAccess>true</StepFreeAccess>
      </AccessibilityLimitation>
    </limitations>
  </AccessibilityAssessment>
  <placeEquipments>
    <ShelterEquipment id="ERP:ShelterEquipment:BusA_Shelter" version="1">
      <Enclosed>false</Enclosed>
      <StepFree>true</StepFree>
      <Seats>4</Seats>
    </ShelterEquipment>
  </placeEquipments>
</Quay>
```

---

## 4. 🗺️ Indoor Navigation — Wayfinding Through Stations

For large stations and transport hubs, knowing *that* a platform is accessible isn't enough — passengers need to know *how to get there*. NeTEx models indoor navigation using three objects:

```text
SiteFrame
 └── StopPlace
      ├── pathLinks
      │    └── PathLink          -- A corridor, stairway, ramp, or passage
      ├── pathJunctions
      │    └── PathJunction      -- Where paths meet (lobby, intersection)
      └── navigationPaths
           └── NavigationPath    -- A named route from A to B (e.g., "Entrance to Platform 3")
                └── pathLinksInSequence
                     ├── PathLinkRef (order=1)
                     ├── PathLinkRef (order=2)
                     └── PathLinkRef (order=3)
```

### PathLink — The Building Block

A **PathLink** represents a single segment of a path through a station — a corridor, a staircase, a ramp, an elevator ride:

```xml
<PathLink id="ERP:PathLink:Entrance_to_Hall" version="1">
  <From>
    <EntranceRef ref="ERP:Entrance:Main"/>
  </From>
  <To>
    <PathJunctionRef ref="ERP:PathJunction:MainHall"/>
  </To>
  <Distance>45</Distance>
  <TransferDuration>
    <DefaultDuration>PT1M</DefaultDuration>
  </TransferDuration>
  <AccessibilityAssessment id="ERP:AccessibilityAssessment:PL1" version="1">
    <MobilityImpairedAccess>true</MobilityImpairedAccess>
    <limitations>
      <AccessibilityLimitation>
        <WheelchairAccess>true</WheelchairAccess>
        <StepFreeAccess>true</StepFreeAccess>
      </AccessibilityLimitation>
    </limitations>
  </AccessibilityAssessment>
</PathLink>
```

Key properties:
- **From / To** — connects Entrances, PathJunctions, Quays, or AccessSpaces
- **Distance** — length in metres
- **TransferDuration** — how long to walk this segment
- **AccessibilityAssessment** — is *this specific segment* step-free, wheelchair-accessible?
- **Covered / Lit** — environmental conditions

### PathJunction — Where Paths Meet

A **PathJunction** is a decision point — a lobby, corridor intersection, or named area:

```xml
<PathJunction id="ERP:PathJunction:MainHall" version="1">
  <Name>Main Hall</Name>
</PathJunction>
```

### NavigationPath — The Complete Route

A **NavigationPath** chains PathLinks into a named, ordered route:

```xml
<NavigationPath id="ERP:NavigationPath:Entrance_to_Spor1" version="1">
  <Name>Main entrance to Platform 1</Name>
  <AccessibilityAssessment id="ERP:AccessibilityAssessment:NP1" version="1">
    <MobilityImpairedAccess>true</MobilityImpairedAccess>
    <limitations>
      <AccessibilityLimitation>
        <WheelchairAccess>true</WheelchairAccess>
        <StepFreeAccess>true</StepFreeAccess>
      </AccessibilityLimitation>
    </limitations>
  </AccessibilityAssessment>
  <TransferDuration>
    <DefaultDuration>PT4M</DefaultDuration>
  </TransferDuration>
  <pathLinksInSequence>
    <PathLinkInSequence id="ERP:PathLinkInSequence:1" version="1" order="1">
      <PathLinkRef ref="ERP:PathLink:Entrance_to_Hall"/>
    </PathLinkInSequence>
    <PathLinkInSequence id="ERP:PathLinkInSequence:2" version="1" order="2">
      <PathLinkRef ref="ERP:PathLink:Hall_to_Lift"/>
    </PathLinkInSequence>
    <PathLinkInSequence id="ERP:PathLinkInSequence:3" version="1" order="3">
      <PathLinkRef ref="ERP:PathLink:Lift_to_Spor1"/>
    </PathLinkInSequence>
  </pathLinksInSequence>
</NavigationPath>
```

### The Full Station Map

```text
                         NavigationPath: "Entrance to Platform 1" (step-free)

  [Main Entrance] ---PathLink 1---> [Main Hall] ---PathLink 2---> [Lift] ---PathLink 3---> [Platform 1]
       45m, 1min          (junction)      30m, 1min                  0m, 1min        Quay

                         NavigationPath: "Entrance to Platform 1" (stairs)

  [Main Entrance] ---PathLink 1---> [Main Hall] ---PathLink 4---> [Staircase] ---PathLink 5---> [Platform 1]
       45m, 1min          (junction)      20m, 30s                    0m, 30s        Quay
```

> 💡 **Tip:** Create **multiple NavigationPaths** between the same origin and destination — one step-free route (via lift) and one regular route (via stairs). Journey planners can then filter by accessibility needs.

---

## 5. 🚌 Vehicle Accessibility

Accessibility on the vehicle side is modelled via **VehicleType** properties:

```xml
<VehicleType id="ERP:VehicleType:LowFloorBus" version="1">
  <Name>Low Floor City Bus</Name>
  <LowFloor>true</LowFloor>
  <HasLiftOrRamp>true</HasLiftOrRamp>
  <PassengerCapacity>
    <WheelchairCapacity>2</WheelchairCapacity>
  </PassengerCapacity>
</VehicleType>
```

This connects back to the stop infrastructure: a wheelchair user needs **both** a step-free path to the Quay **and** a vehicle with low-floor boarding.

---

## 6. 📐 Putting It All Together

The accessibility story spans three frames:

```text
ResourceFrame                SiteFrame                          ServiceFrame
 └── VehicleType              └── StopPlace                      └── (ScheduledStopPoint)
      LowFloor: true               ├── AccessibilityAssessment
      WheelchairCapacity: 2        ├── placeEquipments
                                   │    ├── ShelterEquipment
                                   │    └── LiftEquipment
                                   ├── pathLinks
                                   │    └── PathLink (with AccessibilityAssessment)
                                   ├── pathJunctions
                                   │    └── PathJunction
                                   ├── navigationPaths
                                   │    └── NavigationPath (step-free route)
                                   └── quays
                                        └── Quay
                                             └── AccessibilityAssessment
```

> 📄 **Full example:** [Example_Accessibility.xml](Example_Accessibility.xml) — A station with AccessibilityAssessment at StopPlace and Quay level, equipment, PathLinks, PathJunctions, and a NavigationPath modelling a step-free route.

---

## 7. ✅ Best Practices

1. **Always set AccessibilityAssessment on Quays.** StopPlace-level is a useful summary, but Quay-level is what journey planners actually use for routing.

2. **Use `unknown` honestly.** If accessibility hasn't been surveyed, set `unknown` rather than guessing `true` or `false`. Incorrect data is worse than missing data.

3. **Model both step-free and regular routes.** Create separate NavigationPaths so journey planners can offer alternatives.

4. **Put navigation objects on StopPlace, not Quay.** PathLinks, PathJunctions, and NavigationPaths are station-level constructs that connect quays — they belong under the StopPlace.

5. **Include TransferDuration on PathLinks.** Walking time is critical for accessibility routing — a lift route may be longer but necessary.

6. **Keep equipment on the right level.** Shelters go on Quays (platform-specific). Waiting rooms and sanitary facilities go on StopPlaces (station-wide).

7. **Connect vehicle and stop accessibility.** A step-free journey requires both `StepFreeAccess=true` on the path *and* a low-floor vehicle on the service.

---

## 8. ❌ Common Mistakes

| Mistake | Why It Fails | Fix |
|---------|-------------|-----|
| AccessibilityAssessment only at StopPlace level | Platforms vary — some may lack step-free access | Add assessment at Quay level too |
| PathLinks under Quay instead of StopPlace | Navigation is a station-level concept | Move pathLinks to the parent StopPlace |
| Missing `unknown` — defaulting to `false` | Misleads passengers into thinking access was surveyed | Use `unknown` when not verified |
| NavigationPath without AccessibilityAssessment | Journey planner can't filter for accessible routes | Always declare accessibility on navigation paths |
| Ignoring TransferDuration | Passengers can't estimate time for connections | Include realistic walking times on every PathLink |

---

## 9. 🔗 Related Resources

### Guides
- [Stop Infrastructure](../StopInfrastructure/StopInfrastructure_Guide.md) -- LogicalStop-to-physical platform chain
- [Interchange](../InterchangeOnly/Interchange_Guide.md) -- Transfer timing depends on navigation path durations

### Frames & Objects
- [SiteFrame](../../Frames/SiteFrame/Table_SiteFrame.md) -- Contains StopPlaces and navigation objects
- [StopPlace](../../Objects/StopPlace/Table_StopPlace.md) -- Station with AccessibilityAssessment
- [Quay](../../Objects/Quay/Table_Quay.md) -- Platform with AccessibilityAssessment
- [ShelterEquipment](../../Objects/ShelterEquipment/Table_ShelterEquipment.md) -- Weather protection
- [WaitingRoomEquipment](../../Objects/WaitingRoomEquipment/Table_WaitingRoomEquipment.md) -- Indoor waiting
- [SanitaryEquipment](../../Objects/SanitaryEquipment/Table_SanitaryEquipment.md) -- Accessible toilets
- [VehicleType](../../Objects/VehicleType/Table_VehicleType.md) -- Low-floor and wheelchair capacity

### External
- [NeTEx CEN Standard](https://www.netex-cen.eu/) -- Official specification
