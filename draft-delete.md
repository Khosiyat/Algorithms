# Project Architecture Diagram

The architecture diagram for the React TypeScript project is as follows:

```plaintext
Root Directory
├───api
│   ├───dataset
│   ├───event
│   ├───instrument
│   ├───organism
│   ├───project
│   └───record
├───app
│   ├───about
│   ├───detail
│   │   └───[id]
│   └───visualisation
│       └───[id]
├───assets
│   └───images
├───components
│   ├───graphs
│   │   ├───actogram
│   │   ├───line
│   │   └───map
│   └───overview
└───hooks
    └───sensorSelectContext
```



# Directory Breakdown

<details>
  <summary><strong>api</strong></summary>
  Contains various subdirectories that handle different types of data and interactions:

  - **dataset**: Handles dataset-related API interactions.
  - **event**: Manages event-related API calls.
  - **instrument**: Responsible for instrument data API interactions.
  - **organism**: Deals with organism-related API calls.
  - **project**: Manages project-specific API interactions.
  - **record**: Handles record-related API data.
</details>

<details>
  <summary><strong>app</strong></summary>
  Contains the main application structure and pages:

  - **about**: Information about the application.
  - **detail**: Detailed view for specific items, using dynamic `[id]` routing.
    - `[id]`: Placeholder for dynamic route parameters.
  - **visualisation**: Visualization components with dynamic `[id]` routing.
    - `[id]`: Placeholder for dynamic route parameters.
</details>

<details>
  <summary><strong>assets</strong></summary>
  Contains static assets like images:

  - **images**: Directory for storing image files.
</details>

<details>
  <summary><strong>components</strong></summary>
  Holds reusable UI components and visual elements:

  - **graphs**: Contains different types of graph components.
    - **actogram**: Actogram graph component.
    - **line**: Line graph component.
    - **map**: Map visualization component.
  - **overview**: Overview components for various summaries.
</details>

<details>
  <summary><strong>hooks</strong></summary>
  Contains custom React hooks for shared logic:

  - **sensorSelectContext**: Context and hooks related to sensor selection functionality.
</details>
