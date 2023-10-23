
![alternative text](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/plantuml/plantuml-server/master/src/main/webapp/resource/test2diagrams.txt)


![PlantUML model](http://www.plantuml.com/plantuml/png/RP11JiGm34NtEOKrUox00ir0O8r0EO2dyGoM4YUANN5zN4h5ejqb__rlsV-iXiFcMW9ErWOafG6ea49tdIVkA0QdosnV9Fv7uoOmjTgRk71Ql9UNaD7mYaeGjuVhCOG43q_EuH5UnMWTBrXf1zvHzRkDl0DlSobm67dcKbZkm79he_uk5XoxARhdqwyXwAFTkD1ElnvaupP_BM4v2NHnvxzuSlH1TrOR_pKKCWfdakmT_W00)

```Mermaid
sequenceDiagram
    actor User as U
    participant "Authentication component" as AC
    database Database as D

    U ->> AC : Enter Username
    U ->> AC : Enter Password
    U ->> AC : Enter Full name
    U ->> AC : Enter Billing information
    AC ->> D : Store profile
    AC ->> D : Store billing information
    D ->> AC : Provide profile id
    AC ->> U : Registration complete
```

```plantuml
@startuml
actor User as U
participant "Authentication component" as AC
database Database as D

U -> AC : Enter Username
U -> AC : Enter Password
U -> AC : Enter Full name
U -> AC : Enter Billing information

AC -> D : Store profile
AC -> D : Store billing information
D -> AC : User data stored
AC -> U : Registration complete
@enduml
```
