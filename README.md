# simulation-ssg
TRAFFIC MANAGEMENT SYSTEM
graph TD
    A[Start: manage_traffic function] --> B{Get Current Time, Queues, Emergency Vehicle};
    B -- Emergency Vehicle Detected? --> C[clear_path_for_emergency_vehicle function];
    C --> D[Return];
    B -- No Emergency --> E{is_peak_period?};
    E -- Yes --> F{minor_queue > minor_threshold?};
    F -- Yes --> G[shorten_major_green];
    G --> H[extend_minor_green];
    F -- No --> I{major_queue > major_threshold?};
    I -- Yes --> J[lengthen_major_green];
    I -- No --> K[prioritize_major_road];
    H --> L[update_traffic_lights];
    J --> L;
    K --> L;
    E -- No --> M{minor_queue > 0?};
    M -- Yes --> N[extend_minor_green];
    M -- No --> O{major_queue > low_major_threshold?};
    O -- Yes --> P[extend_major_green];
    O -- No --> Q[base_green_time_major];
    N --> L;
    P --> L;
    Q --> L;
    L --> R[wait for cycle time];
    R --> B;
    D --> R;
