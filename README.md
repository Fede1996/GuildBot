# Entity (PostgreSQL)
```mermaid
classDiagram
      class Events{
        int Id
        int IdCreator
        string Photo
        string Message
        int MaxMembers
        timestamp Timestamp
      }
      class Members{
        int Id
        bool IsAdmin
      }
      class Members_Events{
        int IdMember
        int IdEvent
        int NumberMembers
      }
      Events -- Members_Events
      Members -- Members_Events
```

# Endpoints (Python)

## Admin

### Add Specific Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Add Event
    Bot->>User: Please Select Date
    User->>Bot: Set Date
    Bot->>User: Please Set Message
    User->>Bot: Set Message
    Bot->>User: Please Set Image
    User->>Bot: Set Image
    Bot->>User: Please Set MaxMembers
    User->>Bot: Set MaxMembers
    Bot->>User: Ok
```
### Delete Specific Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Get Event
    Bot->>User: Please Select Date
    User->>Bot: Set Date
    Bot->>User: List of Event in this Date
    User->>Bot: Select Event
    Bot->>User: Info of the Event
    User->>Bot: Delete Event
    Bot->>User: Ok
```
### Update Specific Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Get Event
    Bot->>User: Please Select Date
    User->>Bot: Set Date
    Bot->>User: List of Event in this Date
    User->>Bot: Select Event
    Bot->>User: Info of the Event
    User->>Bot: Update Event
    Bot->>User: List of updatable fields (Photo/Message/MaxMembers)
    loop Update Info
        User->>Bot: Select Field
        Bot->>User: Please Set the Value
        User->>Bot: New Value
        Bot->>User: Ok
    end
    User->>Bot: Done
    Bot->>User: Ok
```
## User (Flowchart)

### Add Reservation at Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Get Event
    Bot->>User: Please Select Date
    User->>Bot: Set Date
    Bot->>User: List of Event in this Date
    User->>Bot: Select Event
    Bot->>User: Info of the Event
    User->>Bot: Reserve table
    Bot->>User: Please Set Number of Reservations
    User->>Bot: Set Number of Reservations
    Bot->>User: Ok
```
### Update Reservation at Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Get Event Rsrvations
    Bot->>User: List of Event with Reservations
    User->>Bot: Select Event
    Bot->>User: Info of the Event
    User->>Bot: Update Reservations
    Bot->>User: Please Set Number of Reservations
    User->>Bot: Set Number of Reservations
    Bot->>User: Ok
```
### Delete Reservation at Event
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    User->>Bot: Get Event Rsrvations
    Bot->>User: List of Event with Reservations
    User->>Bot: Select Event
    Bot->>User: Info of the Event
    User->>Bot: Delete Reservations
    Bot->>User: Ok
```
# Architecture

Databases:
* Postgres for persistence data
* Mongodb for user status

Bot (Python):
* Bot User
* Bot Admin
