
# API Documentation: Nudge Creation

## Overview

This API allows users to create, update, retrieve, and delete nudges. A nudge is a notification or event reminder tagged with an article or event that includes a title, cover image, description, scheduling time, icon, and an invitation message. This API will enable users to manage their nudges effectively.

## Base URL

api/v3/app/nudges

## Object Data Model: Nudge

| Widget | Request Type | Base URL | API Endpoint | Payload |
| --- | --- | --- | --- | --- |
| Nudge | GET | /nudges | /nudges | \-  |
| Nudge | GET | /nudges | /nudges/{id} | \-  |
| Nudge | POST | /nudges | /nudges | tagged\_event, title, image\_url, scheduled\_date, start\_time, end\_time, description, icon, invitation |
| Nudge | PUT | /nudges | /nudges/{id} | Same as POST payload |
| Nudge | DELETE | /nudges | /nudges/{id} | \-  |

## API Endpoints

### 1\. Create a Nudge

**Endpoint:** `/nudges`

**Method:** `POST`

**Description:** Creates a new nudge.

#### Request Payload:
```json
{
  "tagged_event": "event_12345",
  "title": "New Workshop Event",
  "image_url": "https://example.com/images/workshop.png",
  "scheduled_date": "24/09/2024",
  "start_time": "10:00",
  "end_time": "11:30",
  "description": "Join us for an insightful workshop on technology trends.",
  "icon": "https://example.com/icons/workshop_icon.png",
  "invitation": "Swipe right to join our workshop!"
}
```

#### Response:

**200 OK:** Nudge created successfully

**400 Bad Request:** Invalid input data

#### Response Body:
```json
{
  "id": "nudge_67837",
  "tagged_event": "event_12345",
  "title": "New Workshop Event",
  "image_url": "https://example.com/images/workshop.png",
  "scheduled_date": "24/09/2024",
  "start_time": "10:00",
  "end_time": "11:30",
  "description": "Join us for an insightful workshop on technology trends.",
  "icon": "https://example.com/icons/workshop_icon.png",
  "invitation": "Swipe right to join our workshop!"
}

```

### 2\. Retrieve All Nudges

**Endpoint:** `/nudges`

**Method:** `GET`

**Description:** Fetches all created nudges.

#### Response:

**200 OK:** List of nudges retrieved successfully

#### Response Body:
```json
[
  {
    "id": "nudge_67890",
    "tagged_event": "event_12345",
    "title": "New Workshop Event",
    "image_url": "https://example.com/images/workshop.png",
    "scheduled_date": "24/09/2024",
    "start_time": "10:00",
    "end_time": "11:30",
    "description": "Join us for an insightful workshop on technology trends.",
    "icon": "https://example.com/icons/workshop_icon.png",
    "invitation": "Swipe right to join our workshop!"
  },
  {
    "id": "nudge_54321",
    "tagged_event": "article_98765",
    "title": "Latest Tech Updates",
    "image_url": "https://example.com/images/tech.png",
    "scheduled_date": "25/09/2024",
    "start_time": "12:00",
    "end_time": "13:00",
    "description": "Catch up with the latest in the world of technology.",
    "icon": "https://example.com/icons/tech_icon.png",
    "invitation": "Swipe right to explore!"
  }
]
```

### 3\. Retrieve a Specific Nudge

**Endpoint:** `/nudges/{id}`

**Method:** `GET`

**Description:** Retrieves details for a specific nudge by its ID.

#### Response:

**200 OK:** Nudge retrieved successfully

**404 Not Found:** Nudge not found

#### Response Body:
```json
{
  "id": "nudge_67890",
  "tagged_event": "event_12345",
  "title": "New Workshop Event",
  "image_url": "https://example.com/images/workshop.png",
  "scheduled_date": "24/09/2024",
  "start_time": "10:00",
  "end_time": "11:30",
  "description": "Join us for an insightful workshop on technology trends.",
  "icon": "https://example.com/icons/workshop_icon.png",
  "invitation": "Swipe right to join our workshop!"
}
```

### 4\. Update a Nudge

**Endpoint:** `/nudges/{id}`

**Method:** `PUT`

**Description:** Updates an existing nudge with new details.

#### Request Payload:
```json
{
  "tagged_event": "event_54321",
  "title": "Updated Workshop Event",
  "image_url": "https://example.com/images/new_workshop.png",
  "scheduled_date": "26/09/2024",
  "start_time": "14:00",
  "end_time": "15:30",
  "description": "Join us for an updated workshop on new technology trends.",
  "icon": "https://example.com/icons/new_icon.png",
  "invitation": "Swipe right to join the updated event!"
}

```

#### Response:

**200 OK:** Nudge updated successfully

**404 Not Found:** Nudge not found

**400 Bad Request:** Invalid data

#### Response Body:
```json
{
  "id": "nudge_67890",
  "tagged_event": "event_54321",
  "title": "Updated Workshop Event",
  "image_url": "https://example.com/images/new_workshop.png",
  "scheduled_date": "26/09/2024",
  "start_time": "14:00",
  "end_time": "15:30",
  "description": "Join us for an updated workshop on new technology trends.",
  "icon": "https://example.com/icons/new_icon.png",
  "invitation": "Swipe right to join the updated event!",
  "updated_at": "24/09/2024T14:00:00Z"
}

```

### 5\. Delete a Nudge

**Endpoint:** `/nudges/{id}`

**Method:** `DELETE`

**Description:** Deletes a specific nudge by its ID.

#### Response:

**204 No Content:** Nudge deleted successfully

**404 Not Found:** Nudge not found

## Error Codes

*   **400:** Bad Request – Invalid input data
*   **404:** Not Found – Nudge with the specified ID not found
*   **500:** Internal Server Error – Server encountered an error while processing the request

## Notes

*   The `tagged_event` field refers to the event or article ID associated with the nudge.
*   The API requires image URLs and icons to be uploaded to a separate image hosting service.
*   The scheduled time format is `hh:mm` and date is in `dd/mm/yy`.
*   CRUD functionalities are fully supported for managing nudges.
