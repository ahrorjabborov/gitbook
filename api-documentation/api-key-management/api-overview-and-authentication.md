---
icon: square-a-lock
---

# API Overview & Authentication

#### What is an API Key?

An API key is a unique identifier that grants you access to the AiKYNETIX API. It acts as a secure token that you must include in every API request to authenticate and authorize your access.

#### How to Use Your API Key

*   **Include in Request Headers:**\
    For every API call, add your API key to the `Authorization` header in the following format:

    ```
    Authorization: API-KEY <your_api_key>
    ```
*   **Example Using cURL:**

    ```bash
    curl -X GET https://api.aikynetix.com/v1/your-endpoint \
      -H "Authorization: API-KEY YOUR_API_KEY"
    ```
* **Secure Your Key:**\
  Never share your API key publicly. If your key is compromised, regenerate it immediately from your dashboard.

