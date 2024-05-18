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

# Summary of API Directory

## General Structure
### `api.ts`
This file defines the API functions for interacting with the specific type of data-related endpoints:

- **getItems**: Fetches all items (datasets, events, instruments, organisms, projects, or records).
- **getItem**: Fetches a specific item by ID.
- **filterItems**: Filters items based on provided criteria.

### `interface.ts`
This file contains TypeScript interfaces that define the structure of the specific type of data:

- **Item**: Represents the main item structure with relevant fields.
- **Contact**: Represents contact information with fields for `firstName`, `lastName`, `email`, `userid`, and `webpage`.
- **Taxon**: Represents taxonomic coverage including fields for `taxonScientificName`, `taxonCommonName`, and `dyntaxaId`.
- **GeographicWENS**: Represents geographical coverage with coordinates and a description.
- **RangeDateTime**: Represents temporal coverage with `startDatetime` and `endDateTime`.
- **Reference**: Represents bibliographic citation with `DOI` and `title`.

## Specific Subdirectories
Each subdirectory under `api` handles interactions for different types of data and includes the following two key files:
- **dataset**: Handles dataset-related API interactions.
- **event**: Manages event-related API calls.
- **instrument**: Responsible for instrument data API interactions.
- **organism**: Deals with organism-related API calls.
- **project**: Manages project-specific API interactions.
- **record**: Handles record-related API data.

Each subdirectory follows the same structure but is tailored to handle its specific type of data interactions and definitions.


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
