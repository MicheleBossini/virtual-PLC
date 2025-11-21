PULM DIAGRAM for the first task

For the firt task, MAIN task, the machine need to automatize an entire production of coffe.
There is a start bottom, which the user has to set manually on, and then the machine starts with the production.
The main function are: 
FILLING (only if the water is not enough)
HEATING (to reach the correct temperature)
CHOISE the intensity of the coffee
BREWING (pouring hot water over the coffee grounds)
choise the quantity of sugar
and cleaning part if we have already made 5 coffee


```plantuml
@startuml
title Coffee Maker - Linear Process Flow

== Start Process ==

User -> VAR : Start := TRUE

VAR -> Water : Check Water_Level
Water -> VAR : Water_Level

alt Water_Level < 80%
VAR -> Water : Start Filling
Water -> VAR : FILLING := TRUE
Water -> Timer : timer 5s
Timer -> Water : timer.Q := TRUE
Water -> VAR : Water_Level := 100%
Water -> VAR : FILLING := FALSE
end

VAR -> Heater : Start Heating
Heater -> VAR : HEATING := TRUE
Heater -> Timer : timer 5s
Timer --> Heater : Timer.Q = TRUE
Heater -> VAR : HEATING := FALSE
Heater -> VAR : Water_Temp := 90.0
Heater -> VAR : Water_Ready := TRUE

== Brewing Process ==

VAR -> Brewer : Check Water_Ready
alt Water_Ready = TRUE
Brewer -> VAR : BREWING := TRUE
Brewer -> Timer : Start 3s/6s/9s
Timer --> Brewer : Timer.Q = TRUE
Brewer -> VAR : BREWING := FALSE
Brewer -> VAR : Coffee_Ready := TRUE
end

== End Process ==

alt coffe_ready := TRUE
CoffeeReady -> GVL : Finish :=TRUE
end

@enduml
