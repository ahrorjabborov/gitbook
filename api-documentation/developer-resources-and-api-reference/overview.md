---
description: This pages provides the overall structure of our API.
icon: rectangle-code
---

# Overview

### Global Information

* **Title:** AiKYNETIX API
* **Version:** v1.0
* **Terms of Service:** [https://aikynetix.app/terms](https://aikynetix.app/terms)
* **Contact:** info@aikynetix.com
* **Server URL:** https://aikpy-nsz2.onrender.com
* **Security:** Bearer token via Authorization header

***

### Endpoints by Feature Group

### [1. User Management Endpoints](api-reference/user-management.md)

* **/user-management/organization-status/**
  * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Organization Status
* **/user-management/users/**
  * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve a Paginated List of Users
  * <mark style="background-color:orange;">**PUT**</mark>**:** Update User Information
  * <mark style="background-color:green;">**POST**</mark>**:** Create a New User
  * <mark style="background-color:red;">**DELETE**</mark>**:** Delete a User
* **/user-management/users/filter/**
  * <mark style="background-color:blue;">**GET**</mark>**:** Filter and Paginate Users
* **/user-management/users/{user\_uid}**
  * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Details for a Specific User

***

### [2. Sessions](api-reference/managing-all-sessions.md)

* [**Managing All Sessions**](api-reference/managing-all-sessions.md)
  * **/session-management/sessions/**
    * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve All Sessions
  * **/session-management/sessions/filter/**
    * <mark style="background-color:blue;">**GET**</mark>**:** Fetch Filtered Sessions
  *   **/session-management/sessions/{session\_id}/**

      * <mark style="background-color:orange;">**PUT**</mark>**:** Update a Session Data
      * <mark style="background-color:red;">**DELETE**</mark>**:** Delete a Session


* [**Analyzed Video**](api-reference/analyzed-video.md)
  *   **/session-management/sessions/{session\_id}/analyzed-video/**

      * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Analyzed Video URL
      * <mark style="background-color:green;">**POST**</mark>**:** Upload/Generate Analyzed Video


*   [**Running**](api-reference/running.md)

    * **/running/management/sessions/**
      * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session (Admin on Behalf of Another User)
    * **/running/sessions/**
      * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session
    * **/running/sessions/metrics/total/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Total Metrics
    * **/running/sessions/{session\_id}/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve a Running Session Details
    * **/running/sessions/{session\_id}/export/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Export a Running Session Data
    * **/running/sessions/{session\_id}/form-analysis/**
      * <mark style="background-color:green;">**POST**</mark>**:** Generate Form Analysis Images (Deprecated)
    * **/running/sessions/{session\_id}/gait-analysis/**
      * <mark style="background-color:green;">**POST**</mark>**:** Gait Analysis Report
    * **/running/sessions/{session\_id}/metrics/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Report Metrics (Deprecated)
    * **/running/sessions/{session\_id}/recommendation/**
      * <mark style="background-color:green;">**POST**</mark>**:** Generate Recommendations for a Session (Deprecated)
    * **/running/sessions/{session\_id}/report-comments/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Session Comments
      * <mark style="background-color:orange;">**PUT**</mark>**:** Update Session Comments
      * <mark style="background-color:red;">**DELETE**</mark>**:** Delete Report Comments
    * **/running/sessions/{session\_id}/report/**
      * <mark style="background-color:green;">**POST**</mark>**:** Retrieve Report Analysis Images (Deprecated)
    * **/running/sessions/{session\_id}/summary/**
      * <mark style="background-color:green;">**POST**</mark>**:** Generate Summary for a Session (Deprecated)


*   [**Jumping (Vertical Jump)**](api-reference/jumping.md)

    * **/jumping/management/sessions/**
      * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session (Admin on Behalf of Another User)
    * **/jumping/sessions/**
      * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session
    * **/jumping/sessions/{session\_id}/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Get Jumping Session Data
    * **/jumping/sessions/{session\_id}/export/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Export Jumping Session Data
    * **/jumping/sessions/{session\_id}/jump-analysis/**
      * <mark style="background-color:green;">**POST**</mark>**:** Get Vertical Jump Analysis Report
    * **/jumping/sessions/{session\_id}/recommendation/**
      * <mark style="background-color:green;">**POST**</mark>**:** Create Recommendations Threads
    * **/jumping/sessions/{session\_id}/summary/**
      * <mark style="background-color:blue;">**GET**</mark>**:** Get Summary of a Session
      * <mark style="background-color:green;">**POST**</mark>**:** Generate Summary Threads for a Session


* [**Weightlifting**](api-reference/weightlifting.md)
  * **/weightlifting/management/sessions/**
    * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session (Admin on Behalf of Another User)
  * **/weightlifting/sessions/**
    * <mark style="background-color:green;">**POST**</mark>**:** Create a New Video Processing Session
  * **/weightlifting/sessions/{session\_id}/**
    * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve Weightlifting Session Details
  * **/weightlifting/sessions/{session\_id}/export/**
    * <mark style="background-color:blue;">**GET**</mark>**:** Export Weightlifting Session Data
  * **/weightlifting/sessions/{session\_id}/lift-analysis/**
    * <mark style="background-color:green;">**POST**</mark>**:** Analyze Weightlifting Lift
  * **/weightlifting/sessions/{session\_id}/recommendation/**
    * <mark style="background-color:green;">**POST**</mark>**:** Generate Weightlifting Recommendations

***

### [3. HTML Files](api-reference/html-files.md)

* **/helper/html-files/**
  * <mark style="background-color:blue;">**GET**</mark>**:** Retrieve HTML File
  * <mark style="background-color:green;">**POST**</mark>**:** Upload HTML File

***

### Components

* **Security Schemes:** Bearer token (passed in the Authorization header)
