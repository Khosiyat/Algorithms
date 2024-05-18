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


***About*** Sub-folder includes:
- **Description**: Renders information about SBDI Biologging tools and its role in managing data from animal sensor systems.
- **API Details**: Provides links to the Biologging Open API and its data model.
- **Contact Information**: Offers contact details for inquiries and contributions.

***Details*** Sub-folder includes:
- **Overview**: Displays detailed information about a specific dataset and available dataset versions with download links.

</details>

<details>
  <summary><strong>assets</strong></summary>
  Contains static assets like images:

  - **images**: Directory for storing image files.
</details>

<details>
  <summary><strong>components</strong></summary>

***The overview of each subfolder's components, their functionalities, props, dependencies, and usage.***

## 1. `actogram` Subfolder
**Description**: This subfolder contains components dedicated to visualizing actogram data, representing activity patterns over time. 

### Actogram Component
- **Description**: Fetches actogram data and renders a graph displaying activity patterns.
- **Props**: Accepts an array of event objects (`events`).
- **Dependencies**: Utilizes React, date-fns for date manipulation, and custom API modules for data fetching.
- **Usage**: `<Actogram events={events} />`

### ActogramGraph Component
- **Description**: Renders the actogram graph based on provided data.
- **Props**: Receives data arrays (`data`), a map of month counts (`mCounts`), and the total number of days (`days`).
- **Dependencies**: Utilizes React and react-chartjs-2 for graph rendering.
- **Usage**: `<ActogramGraph data={data} mCounts={mCounts} days={days} />`

## 2. `line` Subfolder
**Description**: Contains components for displaying line graphs.

### LineGraph Component
- **Description**: Fetches data and renders a line graph displaying sensor data over time.
- **Props**: Accepts an array of event objects (`events`) and the name of the sensor (`sensor`).
- **Dependencies**: Requires React, react-chartjs-2, and custom API modules.
- **Usage**: `<LineGraph events={events} sensor={sensor} />`

## 3. `map` Subfolder
**Description**: Houses components for displaying geographical data on maps, facilitating the visualization of spatial information.

### MapGraph Component
- **Description**: Fetches geographical data and renders a map with markers and polylines.
- **Props**: Receives an array of event objects (`events`).
- **Dependencies**: Depends on React, react-leaflet, and custom API modules for data retrieval.
- **Usage**: `<MapGraph events={events} />`

### MapComponent Component
- **Description**: Renders the Leaflet map and coordinates the rendering of markers and polylines.
- **Props**: Accepts an array of coordinate arrays (`data`).
- **Dependencies**: Utilizes React, react-leaflet, and leaflet library.
- **Usage**: `<MapComponent data={data} />`

### Polylines Component
- **Description**: Renders polylines on the map based on provided coordinate data.
- **Props**: Receives an array of coordinate arrays (`coords`).
- **Dependencies**: Requires React, react-leaflet, and leaflet library.
- **Usage**: `<Polylines coords={coords} />`

</details>

<details>
  <summary><strong>hooks</strong></summary>
  Contains custom React hooks for shared logic:

  - **sensorSelectContext**: Context and hooks related to sensor selection functionality.
</details>
