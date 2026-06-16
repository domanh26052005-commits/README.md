### 1.2.2 Use Cases
A use case (UC) describes a sequence of interactions between a system and an external actor that results in the actor being able to achieve some outcome of value. The names of use cases are always written in the form of a verb followed by an object. 

In this section, the UC diagram below illustrates the actor-UCs and UC-UC relationships for the VIVAS Internal Training Management System workflow[cite: 1].

```mermaid
leftToRightDirection
graph TD
    %% Actors
    Admin["Application Administrator"]
    TStaff["Training Staff"]
    Head["Head of Training"]
    Manager["Department Manager"]
    Emp["Employee"]
    Comms["Internal Communications Staff"]

    %% Use Cases
    UC1((Login to System))
    UC2((Manage User Permissions))
    UC3((Configure System Categories))
    UC4((Create a Course))
    UC5((Approve a Course))
    UC6((Assign a Course))
    UC7((Study a Lecture))
    UC8((Take a Test))
    UC9((Review Taken Test))
    UC10((Post Training News))
    UC11((View Department Status))
    UC12((View Global Statistics))

    %% Connections
    Emp --> UC1
    Emp --> UC7
    Emp --> UC8
    Emp --> UC9

    Admin --> UC2
    Admin --> UC3

    TStaff --> UC4
    TStaff --> UC6

    Head --> UC5
    Head --> UC12
    
    Manager --> UC11
    Comms --> UC10

    %% Relationships
    UC7 .-> |"<<include>>"| UC1
    UC8 .-> |"<<include>>"| UC1
    UC4 .-> |"<<include>>"| UC5
