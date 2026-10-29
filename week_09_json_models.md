Referenced design:
{
  "users": [
    {
      "user_id": 103,
      "display_name": "Requester 103"
    },
    {
      "user_id": 201,
      "display_name": "Agent 201"
    }
  ],
  "tickets": [
    {
      "ticket_id": 1003,
      "subject": "Low water pressure",
      "status": "resolved",
      "requester_id": 103,
      "assignee_id": 201
    }
  ],
  "events": [
    {
      "event_id": 5005,
      "event_type": "created",
      "event_at": "2026-02-03T12:05:00Z"
    },
    {
      "event_id": 5006,
      "event_type": "status_changed",
      "event_at": "2026-02-03T14:25:00Z"
    },
    {
      "event_id": 5007,
      "event_type": "status_changed",
      "event_at": "2026-02-03T19:40:00Z"
    }
  ]
Embedded or hybrid design:
{
  "ticket_id": 1003,
  "subject": "Low water pressure",
  "status": "resolved",
  "requester_id": 103,
  "requester_name": "Requester 103",
  "assignee_id": 201,
  "assignee_name": "Agent 201",
  "events": [
    {
      "event_id": 5005,
      "event_type": "created",
      "event_at": "2026-02-03T12:05:00Z"
    },
    {
      "event_id": 5006,
      "event_type": "status_changed",
      "event_at": "2026-02-03T14:25:00Z"
    },
    {
      "event_id": 5007,
      "event_type": "status_changed",
      "event_at": "2026-02-03T19:40:00Z"
    }
  ]
}
}

Read: It finds facts about ticket 1003 by using requester_id and assignee_id to look up the information in the users array. It also finds
the ticket event in the events array by using the ticket_id.
Change: When changing the requester display_name in the referenced version, you have to update the user table first. In the other version,
the display_name has to be updated in every ticket it's stored in. Since tickets accumulate years of events, the array can grow very large.
This makes the tickets slower and harder to function. 


