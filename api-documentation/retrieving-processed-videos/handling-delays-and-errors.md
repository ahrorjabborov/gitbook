---
icon: circle-exclamation
---

# Handling Delays & Errors

Retrieving processed videos is a critical function. In cases where processing is delayed or errors occur, our system ensures that both clients and operators are properly informed.

#### Automatic Retries

* **Transient Issues:**\
  For temporary issues such as network interruptions or brief resource shortages, our system automatically retries the affected processing steps up to a set limit.
* **Resilient Pipeline:**\
  By incorporating retry logic at key stages, we minimize the impact of short-lived errors and help ensure successful processing without manual intervention.

***

#### Timeout & Alert Mechanisms

* **Timeout Detection:**\
  If a processing job exceeds its expected duration, a timeout is triggered. This helps identify jobs that are stalled or delayed.
* **Real-Time Alerts:**\
  Once a timeout or error is detected, notifications are sent to both administrators and users. This ensures that any issues are promptly addressed and that you’re kept informed of the job status.

***

#### Comprehensive Error Logging

* **Detailed Logs:**\
  Every error and delay is recorded with detailed metadata. This information supports real-time troubleshooting and long-term system improvements.
* **Error Reporting:**\
  Users and administrators receive clear error messages via the API, enabling them to understand the issue and take corrective action if necessary.

***

#### Fallback Mechanisms

* **Graceful Degradation:**\
  In the event of critical failures, fallback procedures are activated to maintain data integrity. Processed data is preserved, and the system provides guidance on next steps.
* **User Notifications:**\
  When significant errors or delays occur, users are notified via status updates. You can track the job’s progress through our job status API, ensuring full transparency.

***

> Please report issues or suggestions to [info@aikynetix.com](https://app.gitbook.com/u/0CO1pdfZVDVltXGVSKad9rhZyEu2).
