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

### `apiService.ts`
This file provides the core functions for making HTTP requests using Axios:
- **get**: 
  - **Purpose**: Performs a GET request to the specified endpoint.
  - **Implementation**: 
    - Constructs the full URL using the base URL (`BASE_URL`) and the given endpoint.
    - Uses Axios to send a GET request to this URL.
    - Returns the response data if the request is successful.
    - Catches any errors during the request and returns the error as an `AxiosError` type.
- **post**: 
  - **Purpose**: Performs a POST request to the specified endpoint with an optional request body and parameters.
  - **Implementation**: 
    - Constructs the full URL using the base URL (`BASE_URL`) and the given endpoint.
    - Uses Axios to send a POST request to this URL with the provided body and optional parameters.
    - Sets the `Content-Type` header to `application/json`.
    - Includes optional parameters, defaulting to `{ take: 100 }`.
    - Returns the response data if the request is successful.
    - Catches any errors during the request and returns the error as an `AxiosError` type.

  
</details>

<details>
  <summary><strong>app</strong></summary>
  Contains the main application structure and pages:


***About*** Sub-folder of app:
- **Description**: Renders information about SBDI Biologging tools and its role in managing data from animal sensor systems.
- **API Details**: Provides links to the Biologging Open API and its data model.
- **Contact Information**: Offers contact details for inquiries and contributions.

***Details*** Sub-folder of app:
- **Overview**: Displays detailed information about a specific dataset and available dataset versions with download links.

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
