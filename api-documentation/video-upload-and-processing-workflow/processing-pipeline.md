---
description: This page includes an overall picture of how your data is processed.
icon: arrow-progress
---

# Processing Pipeline

{% @mermaid/diagram content="flowchart TD
    A[Upload Video via API] --> B[Receive Video]
    B --> C[Validate and Store Video]
    C --> D[Queue Video for Processing]
    D --> E[Extract Frames]
    E --> F[Preprocess Frames]
    F --> G[Apply Processing Algorithms]
    G --> H[Generate Processed Video and Metrics]
    H --> I[Store Processed Video and Data]
    I --> J[Return Job ID]" %}

1. **Upload Video via API:** The client uploads a video file via our API.
2. **Receive Video:** The server receives the video.
3. **Validate & Store Video:** The system validates the video file and stores it in our storage.
4. **Queue Video for Processing:** The video is added to a processing queue.
5. **Extract Frames:** The video is broken down into individual frames.
6. **Preprocess Frames:** Frames are preprocessed (e.g., resizing, normalization) to prepare for analysis.
7. **Apply Processing Algorithms:** Our algorithms process the frames (e.g., for feature extraction or analysis).
8. **Generate Processed Video & Metrics:** A new video is generated along with performance metrics.
9. **Store Processed Video & Data:** The processed video and metrics are stored.
10. **Notify User (Return Job ID):** The user is notified that processing has started and receives a Job ID for tracking.
