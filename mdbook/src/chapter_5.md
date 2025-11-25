Function Call Sequence

The function is called by both tasks.
For the main task, the function informs the user about the machine’s preparation status — for example, when the machine is starting, when the water is filled, when the water is heated,..., and finally when the coffee ready and is available.

For the second task, the function displays a message indicating the number of coffees produced. When this number reaches five, the message “Maintenance required” is shown, and once the maintenance is completed, the message “Maintenance done” is displayed.

```plantuml
@startuml
title Maintenance Task - Function Call Sequence

MAIN -> FunctionLogMessage : coffee machine's preparation status
MaintenanceTask -> FunctionLogMessage: How many caffee are already made
MaintenanceTask -> FunctionLogMessage: Cleaning information

FunctionLogMessage -> GVL: GVL.MessageMaintenance := 'Coffee made:...'
alt CoffeeMade >=5
FunctionLogMessage -> GVL: GVL.MessageMaintenance := 'Maintenance required!'
FunctionLogMessage -> GVL: CLEANING:=TRUE
end
alt Maintenence done 
FunctionLogMessage -> GVL: GVL.MessageMaintenance := 'Maintenance done!'
FunctionLogMessage -> GVL: CLEANING:=FALSE
end
FunctionLogMessage -> GVL: GVL.MessageToUser := 'preparation state: ...'


@enduml
```