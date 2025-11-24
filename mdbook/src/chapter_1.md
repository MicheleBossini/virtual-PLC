Process and safety individual part

authors = Michele Bossini

student number : 586306

routine chosen: automatic coffee machine and maintenance requirements

symple sequence diagram:

``` plantuml
@startuml
actor "User" as User

User -> CoffeeMachine : "I want a coffee"
CoffeeMachine -> CoffeeMachine : start making coffee
CoffeeMachine -> User : "What intensity"
User -> CoffeeMachine : intensity selection
CoffeeMachine -> User : "sugar quantity"
User -> CoffeeMachine : sugar selection
CoffeeMachine -> Counter : coffee ready
CoffeeMachine -> User : "your coffee is ready"
alt coffee ready 
CoffeeMachine -> Counter : coffee made +1
end
alt Counter >= 5
Counter -> Maintenance : start cleaning
Maintenance -> CoffeeMachine : CLEANING
end 
CoffeeMachine -> User :"Ready for another coffee"
@enduml
```