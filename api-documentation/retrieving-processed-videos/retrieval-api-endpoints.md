---
icon: rectangle-list
---

# Retrieval API Endpoints

Our system exposes multiple endpoints that return session details – including the URL to the processed (analyzed) video. Use the endpoint that corresponds to your session’s activity:

#### A. Session-Specific Endpoints

### [**Jumping Sessions**](../developer-resources-and-api-reference/api-reference/jumping.md)

* **Endpoint:** [`GET /jumping/sessions/{session_id}/`](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id)
* **Description:** Retrieves detailed data for a jumping session. The response includes an `analyzed_video_url`(a public URI pointing to the analyzed video) along with the original `video_url` and other session metrics.
* **Example Response Fragment:**

```
{
  "session_id": "abcd1234",
  "analyzed_video_url": "https://storage.googleapis.com/your-bucket/analyzed_video.mp4",
  "video_url": "https://storage.googleapis.com/your-bucket/original_video.mov",
  "created_at": { "date": "05/02/2025", "time": "06:00 PM" },
  ...
}
```

[**GET /jumping/sessions/{session\_id}/export/**\
](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id-export)Export comprehensive data for a jumping session. This endpoint provides landmark keypoints, angle data, and other metrics useful for in-depth analysis.

***

### [**Running Sessions**](../developer-resources-and-api-reference/api-reference/running.md)

* **Endpoint:** [`GET /running/sessions/{session_id}/`](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id)
* **Description:** Returns details for a running session. The response includes an `analyzed_video_url` along with metrics, angles, timestamps, and other relevant data.
* **Example Response Fragment:**

```
{
  "session_id": "abcd1234",
  "analyzed_video_url": "https://storage.googleapis.com/your-bucket/analyzed_video.mp4",
  "video_url": "https://storage.googleapis.com/your-bucket/original_video.mov",
  "created_at": { "date": "05/02/2025", "time": "06:00 PM" },
  ...
}
```

* [**GET /running/sessions/{session\_id}/export/**](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id-export)\
  Export running session data for further analysis. This includes keypoints, angles, timestamps, and additional performance metrics.
* [**GET /sessions/{session\_id}/analyzed-video/**](../developer-resources-and-api-reference/api-reference/analyzed-video.md#session-management-sessions-session_id-analyzed-video)\
  Fetch the URL for the analyzed video. If the video isn’t available yet, this endpoint can trigger its generation.

***

### [**Weightlifting Sessions**](../developer-resources-and-api-reference/api-reference/weightlifting.md)

* **Endpoint:** [`GET /weightlifting/sessions/{session_id}/`](../developer-resources-and-api-reference/api-reference/weightlifting.md)
* **Description:** Retrieves details for a weightlifting session. In addition to exercise-specific metrics and angles, the response returns an `analyzed_video_url` showing the processed lift.
* **Example Response Fragment:**

```
{
  "session_id": "abcd1234",
  "analyzed_video_url": "https://storage.googleapis.com/your-bucket/analyzed_video.mp4",
  "video_url": "https://storage.googleapis.com/your-bucket/original_video.mov",
  "created_at": { "date": "05/02/2025", "time": "06:00 PM" },
  ...
}
```

* [**GET /weightlifting/sessions/{session\_id}/export/**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id-export)Export weightlifting session data, which includes keypoints, angles, timestamps, and numerical metrics.
* [**GET /weightlifting/sessions/{session\_id}/lift-analysis/**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id-lift-analysis)Obtain detailed analysis images and recommendations for the lift. This endpoint returns multilingual analysis results for further review.

***

**Session Management – Analyzed Video**

* **Endpoint:** [`GET /session-management/sessions/{session_id}/analyzed-video/`](../developer-resources-and-api-reference/api-reference/analyzed-video.md)
* **Description:** This endpoint either retrieves the analyzed video URL for a session (if processing is complete) or triggers a lookup/creation routine if not yet available.
* **Example Request:**

```
GET /session-management/sessions/abcd1234/analyzed-video/ HTTP/1.1
Host: api.example.com
Authorization: API-KEY <token>
```

#### B. Security and Usage

* **Authentication:**\
  Every retrieval call requires a valid API-KEY token in the `Authorization` header.
* **Access Control:**\
  Only authenticated users (with proper privileges) may retrieve session details. Unauthorized requests yield HTTP 401 responses with a clear error message.
