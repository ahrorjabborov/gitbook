---
description: >-
  Uploading videos is the critical first step in the AiKYNETIX Video Upload &
  Processing Workflow. This guide outlines how to upload your video files via
  our REST API.
icon: circle-video
---

# Uploading Videos via API

## Overview

The AiKYNETIX API allows both regular users and administrators to initiate video processing sessions. Whether you’re uploading for personal analysis or acting on behalf of another user, the API provides dedicated endpoints for each activity type (Running, Jumping, and Weightlifting). Once a video is uploaded, the system creates a session resource that triggers the processing pipeline.

### Prerequisites

Before uploading a video, ensure that you have:

* **Valid API Credentials:**\
  All requests must include a valid API-KEY token in the `Authorization` header. For example:

```
Authorization: API-KEY <YOUR_API_TOKEN>
```

* **Appropriate Permissions:**
  * **Regular Users:** Can upload videos directly to create their own session.
  * **Administrators/Sub-Admins:** May upload on behalf of another user. In these cases, the request must include an additional `user_id` parameter.
* **Multipart/Form-Data Format:**\
  Video uploads are performed using a `multipart/form-data` POST request. Your request should include the raw video file along with any additional parameters required by the endpoint.

***

### Upload Endpoints Overview

Depending on the activity type and user role, use one of the following endpoints:

<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/running.md">Running Sessions</a></summary>

* [**Regular User Upload**](../developer-resources-and-api-reference/api-reference/running.md#running-sessions)**:**\
  **Endpoint:** `POST /running/sessions/`\
  **Parameters:**
  * **video (file, required):** The video file to be processed.
  * **session\_name (string, optional):** A custom title for the session.
  * **incline\_degree (string/number, optional):** Specifies the treadmill incline (if applicable).
* [**Admin Upload (On Behalf of Another User)**](../developer-resources-and-api-reference/api-reference/running.md#running-management-sessions)**:**\
  **Endpoint:** `POST /running/management/sessions/`\
  **Parameters:**
  * **user\_id (string, required):** The ID of the user for whom this session is created.
  * **video (file, required)**
  * **session\_name (string, optional)**
  * **incline\_degree (string/number, optional)**

</details>

<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/jumping.md">Jumping Sessions</a></summary>

* [**Regular User Upload:**](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions)\
  **Endpoint:** `POST /jumping/sessions/`\
  **Parameters:**
  * **video (file, required)**
  * **session\_name (string, optional)**
  * **incline\_degree (string/number, optional)**
* [**Admin Upload (On Behalf of Another User)**](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-management-sessions)**:**\
  **Endpoint:** `POST /jumping/management/sessions/`\
  **Parameters:**
  * **user\_id (string, required)**
  * **video (file, required)**
  * **session\_name (string, optional)**
  * **incline\_degree (string/number, optional)**

</details>

<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/weightlifting.md">Weightlifting Sessions</a></summary>

* [**Regular User Upload**](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions)**:**\
  **Endpoint:** `POST /weightlifting/sessions/`\
  **Parameters:**
  * **video (file, required)**
  * **exercise\_name (string, required):** Must be one of `snatch`, `clean`, or `clean_and_jerk`.
  * **session\_name (string, optional)**
  * **barbell\_mass (string, optional):** Mass of the barbell. If omitted, a default value of 100 kg (or 220 lb) is assigned.
* [**Admin Upload (On Behalf of Another User)**](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-management-sessions)**:**\
  **Endpoint:** `POST /weightlifting/management/sessions/`\
  **Parameters:**
  * **user\_id (string, required)**
  * **video (file, required)**
  * **exercise\_name (string, required)**
  * **session\_name (string, optional)**
  * **barbell\_mass (string, optional**

</details>

***

### Request Payload & Multipart/Form-Data Requirements

When constructing your upload request, ensure that you:

* Set the **Content-Type** header to `multipart/form-data`.
* Include the **video file** as a binary field.
* Pass additional parameters as form fields:
  * For admin-initiated uploads, include the `user_id` field.
  * For weightlifting sessions, include `exercise_name` (and optionally `barbell_mass`).
  * Optionally, include a descriptive `session_name` to help identify your session.

#### Example cURL Command (Admin Upload for a Jumping Session)

```
curl -X POST \
     -H 'Content-Type: multipart/form-data' \
     -H 'Authorization: API-KEY <YOUR_ADMIN_TOKEN>' \
     -F 'user_id=someUserId123' \
     -F 'video=@/path/to/video.mp4' \
     -F 'session_name=Custom Jump Session' \
     -F 'incline_degree=5' \
     https://aikpy-nsz2.onrender.com/jumping/management/sessions/
```

***

### Workflow Sequence

1. **Authentication:**\
   The client sends the request with a valid API-KEY token. For admin uploads, the additional `user_id` is also provided.
2. **File Upload & Session Creation:**\
   The video file, along with any extra form data, is transmitted to the server. The API then creates a new processing session for the video.
3. **Server Response:**\
   On success, the API responds with a JSON object containing:
   * **session\_id:** A unique identifier for the new session.
   * **title:** The session title (either user-specified or a fallback).
4. **Next Steps:**\
   The returned `session_id` can be used to:
   * Poll for processing status.
   * Retrieve the analyzed video.
   * Access detailed session metrics and analysis reports via subsequent API calls.

***

### Handling the Response

A successful upload response will resemble the following JSON:

```
{
  "session_id": "abcd1234efgh5678",
  "title": "Custom Session"
}
```

{% hint style="info" %}
If the upload fails due to missing fields, invalid token, or insufficient permissions, the response will contain an `error` field with an appropriate message
{% endhint %}

> **Note:** For details on parameters, request/response formats, and error handling, please see the respective sections in our [API Reference](broken-reference).
