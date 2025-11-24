TASK 2: maintenance task

For the second task, the program has to handle the machine’s cleaning maintenance.

Every 5 cycles—that is, every 5 coffees made—the machine must be cleaned.
The cleaning function is automatically called by the maintenance task, and when it runs, the main task needs to wait an additional 8 seconds to ensure the machine is not operating during the cleaning process.

```plantuml
@startuml
title maintenance task - cleaning function

GVL -> Cycle_Counter : coffeeready := TRUE
Cycle_Counter -> Cycle_Counter : +1

alt Cycle_Counter >=5 
VAR -> MaintenanceNeeded : start maintenance
MaintenanceNeeded -> VAR : MaintenanceNeed := TRUE
MaintenanceNeeded -> GVL : CLEANING := TRUE
MaintenanceNeeded -> Timer : timer 5s
Timer --> VAR : timer.Q := TRUE
MaintenanceNeeded -> GVL : CLEANING := FALSE
VAR -> MaintenanceNeeded : stop maintenance
MaintenanceNeeded -> VAR: MaintenanceNeeded := FALSE
MaintenanceNeeded -> VAR : ResetCounter := TRUE
end
alt ResetCounter := TRUE
VAR -> Cycle_Counter : =0
MaintenanceNeeded -> VAR : ResetCounter := FALSE

end

@enduml
```


