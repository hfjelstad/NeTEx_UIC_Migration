## Structure Overview

```text
ServiceJourneyInterchange
 ├─ @id (1..1)
 ├─ @version (1..1)
 ├─ FromJourneyRef/@ref (1..1)
 ├─ ToJourneyRef/@ref (1..1)
 ├─ Guaranteed (0..1)
 ├─ MinimumTransferTime (0..1)
 ├─ MaximumWaitTime (0..1)
 └─ StaySeated (0..1)
```

## Table

| Element | Type | Description | Path |
|---------|------|-------------|------|
| @id | ID | Unique identifier for the interchange | ServiceJourneyInterchange/@id |
| @version | String | Version label | ServiceJourneyInterchange/@version |
| [ServiceJourney](../ServiceJourney/Table_ServiceJourney.md)@ref | Reference | Reference to the originating (feeder) journey | ServiceJourneyInterchange/FromJourneyRef/@ref |
| [ServiceJourney](../ServiceJourney/Table_ServiceJourney.md)@ref | Reference | Reference to the destination (distributor) journey | ServiceJourneyInterchange/ToJourneyRef/@ref |
| Guaranteed | Boolean | Whether the connection is guaranteed | ServiceJourneyInterchange/Guaranteed |
| MinimumTransferTime | Duration | Minimum time required for transfer (ISO 8601) | ServiceJourneyInterchange/MinimumTransferTime |
| MaximumWaitTime | Duration | Maximum wait time for the distributor (ISO 8601) | ServiceJourneyInterchange/MaximumWaitTime |
| StaySeated | Boolean | Whether passengers can remain seated | ServiceJourneyInterchange/StaySeated |
