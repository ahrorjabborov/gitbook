---
description: >-
  This page aggregates all endpoints related to retrieving reports, metrics,
  summaries, and recommendations for processed video sessions.
icon: file-chart-pie
---

# Analytics

### Overview

Each activity—**Jumping**, **Running**, and **Weightlifting**—has dedicated endpoints to:

* **Export Processed Data:** Retrieve structured session data (e.g., keypoints, angles, timestamps, and metrics).
* **Generate Analysis Reports:** Obtain comprehensive analysis (e.g., jump analysis, gait analysis, lift analysis).
* **Retrieve Summaries:** Generate textual summaries of a session’s performance.
* **Create Recommendations:** Generate personalized recommendations based on the analysis.

All endpoints require a valid Api-Key token in the Authorization header. For more details on request formats and error handling, please refer to our API Reference documentation.



<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/running.md">Running</a></summary>

* [**Retrieve Total Metrics**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-metrics-total)`GET /running/sessions/metrics/total/`\
  &#xNAN;_&#x47;et average metrics across all running sessions and detailed metrics for the most recent session._
* [**Retrieve Running Session Details**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id)`GET /running/sessions/{session_id}/`\
  &#xNAN;_&#x41;ccess detailed information for a specific running session, including processed video URLs, metrics, and computed statistics._
* [**Export Running Session Data**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id-export)`GET /running/sessions/{session_id}/export/`\
  &#xNAN;_&#x45;xport running session data such as keypoints, angles, timestamps, and contact information._
* [**Gait Analysis Report**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id-gait-analysis)`POST /running/sessions/{session_id}/gait-analysis/`\
  &#xNAN;_&#x4F;btain a detailed gait analysis report including phase information and joint angle measurements._
* [**Report Comments Management**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id-report-comments)`GET/POST/DELETE /running/sessions/{session_id}/report-comments/`\
  &#xNAN;_&#x52;etrieve, update, or delete user comments associated with the running session report._
* [**Generate Session Summary**\
  ](../developer-resources-and-api-reference/api-reference/running.md#running-sessions-session_id-summary)`POST /running/sessions/{session_id}/summary/`\
  &#xNAN;_&#x47;enerate a textual summary of a running session’s performance and metrics._

</details>

<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/jumping.md">Jumping</a></summary>

* [**Export Session Data**\
  ](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id-export)`GET /jumping/sessions/{session_id}/export/`\
  &#xNAN;_&#x52;etrieve detailed jumping session data, including keypoints, angles, timestamps, and performance metrics._
* [**Vertical Jump Analysis Report**\
  ](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id-jump-analysis)`POST /jumping/sessions/{session_id}/jump-analysis/`\
  &#xNAN;_&#x47;enerate a comprehensive vertical jump analysis report that includes graphical data, phase details, and user performance insights._
* [**Generate Recommendation Threads**\
  ](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id-recommendation)`POST /jumping/sessions/{session_id}/recommendation/`\
  &#xNAN;_&#x43;reate personalized recommendation threads based on the jump analysis report._
* [**Generate or Retrieve Session Summary**\
  ](../developer-resources-and-api-reference/api-reference/jumping.md#jumping-sessions-session_id-summary)`GET/POST /jumping/sessions/{session_id}/summary/`\
  &#xNAN;_&#x52;etrieve a summary of the session or generate summary threads (note: some summary endpoints may be deprecated)._

</details>

<details>

<summary><a href="../developer-resources-and-api-reference/api-reference/weightlifting.md">Weightlifting</a></summary>

* [**Retrieve Weightlifting Session Details**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id)`GET /weightlifting/sessions/{session_id}/`\
  &#xNAN;_&#x46;etch detailed information about a weightlifting session, including original and analyzed video URLs, timestamps, and exercise data._
* [**Export Weightlifting Session Data**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id-export)`GET /weightlifting/sessions/{session_id}/export/`\
  &#xNAN;_&#x45;xport structured data from a weightlifting session, including keypoints, angles, and various performance metrics._
* [**Analyze Weightlifting Lift**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id-lift-analysis)`POST /weightlifting/sessions/{session_id}/lift-analysis/`\
  &#xNAN;_&#x52;un a detailed analysis of the weightlifting lift, generating images that illustrate key performance indicators such as bar speed and joint angles._
* [**Generate Weightlifting Recommendations**\
  ](../developer-resources-and-api-reference/api-reference/weightlifting.md#weightlifting-sessions-session_id-recommendation)`POST /weightlifting/sessions/{session_id}/recommendation/`\
  &#xNAN;_&#x43;reate tailored recommendations for weightlifting performance based on the session’s analysis._

</details>

