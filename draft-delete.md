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

### ***The overview of each subfolder's components, their functionalities, props, dependencies, and usage.***

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
### **Description**: Contains components for displaying line graphs.

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


# Overview

## 1. `table.tsx` file:

### Description:
This file contains the implementation of a table component (`OverviewTable`) for displaying dataset information. It utilizes the AG Grid component for efficient rendering and management of large datasets.

### Dependencies:
- React: For building the user interface.
- ag-Grid: A feature-rich datagrid library for displaying large datasets in tabular format.
- axios: A promise-based HTTP client for making API requests.
- date-fns: A library for manipulating dates in JavaScript.

### Components:
- `OverviewTable`: Renders a table displaying dataset information with features like sorting, filtering, and row selection.

### Features:
- Error handling: Detects and displays error messages if data loading fails.
- Row selection: Allows users to select a row and trigger a callback function (`onSelect`) with the selected dataset item.
- Cell rendering: Custom rendering of certain cells, such as temporal coverage, for improved readability.
- Grid configuration: Configures default grid options and column definitions for consistent behavior and appearance.

## 2. `Snippet.tsx` file:

### Description:
This file contains the implementation of a snippet component (`OverviewSnippet`) for displaying summarized dataset information. It provides links for accessing detailed information, visualization, and dataset download.

### Dependencies:
- React: For building the user interface.
- Font Awesome: For adding icons to enhance visual representation.

### Components:
- `OverviewSnippet`: Renders a summarized view of dataset information with links for detailed information, visualization, and download.

### Features:
- Dataset overview: Displays basic information about the dataset such as title, description, instruments, and sensors.
- Links: Provides links for accessing more detailed information, visualization, and dataset download.
- Download functionality: Allows users to download the dataset in JSON format.
- Error handling: Handles cases where dataset information is unavailable or incomplete.


</details>

<details>
  <summary><strong>hooks</strong></summary>
  

## Description:
The `hooks` folder contains custom hooks and context providers used for managing sensor selection in visualizations.

## Files:

#### Description:
This file exports a custom hook `useSensorSelection` and a context provider `SensorSelectionProvider` for managing sensor selection.

#### Dependencies:
- React: For building the user interface.

#### Components/Interfaces:
- `SensorSelectionContext`: Context for managing sensor selection state.
- `useSensorSelection`: Custom hook for accessing sensor selection context.
- `SensorSelectionProvider`: Context provider component for managing sensor selection state.

#### Features:
- Context management: Provides a context and custom hook for managing sensor selection state across components.
- Sensor selection update: Allows components to update the selected sensors and trigger re-renders when sensor selection changes.


</details>


<details>
  <summary><strong>Summary of Tech Stack and Libraries Used</strong></summary>

## Tech Stack:

- **Frontend Framework:** React.js with TypeScript
- **Styling:** CSS (potentially with CSS-in-JS libraries like styled-components or Emotion)
- **Data Visualization:** react-chartjs-2 for rendering charts/graphs, react-leaflet for mapping, potentially supplemented by Leaflet library
- **State Management:** React Context API (for managing sensor selection)
- **HTTP Requests:** Axios for making API requests
- **Date Manipulation:** date-fns for handling dates
- **Grid Component:** ag-Grid for displaying large datasets efficiently in tabular format

## Libraries and Dependencies:

- **React:** Chosen for its component-based architecture, reusability, and performance optimizations.
- **TypeScript:** Added type safety and enhanced development experience by catching errors during compile time.
- **react-chartjs-2:** Provided a simple and customizable way to render charts/graphs in React applications.
- **react-leaflet and Leaflet:** Utilized for displaying geographical data on interactive maps, offering flexibility and customization options.
- **Axios:** Used for making HTTP requests to fetch data from APIs, offering a promise-based interface and robust error handling.
- **ag-Grid:** Employed for displaying large datasets efficiently in tabular format, providing features like sorting, filtering, and row selection.
- **date-fns:** Facilitated date manipulation tasks, ensuring consistent handling of temporal data across the application.
- **CSS-in-JS Libraries (potentially):** Styled-components or Emotion could be used for styling components, providing scoped styles and enhancing maintainability.

## Reasons for Usage:

- **React.js with TypeScript:** Chosen for its popularity, strong community support, and the ability to build complex UIs with ease while ensuring type safety.
- **react-chartjs-2:** Provided a React-friendly wrapper for Chart.js, enabling the creation of interactive and visually appealing charts/graphs.
- **react-leaflet and Leaflet:** Offered powerful mapping capabilities with extensive customization options, ideal for visualizing geographical data.
- **Axios:** Preferred for its simplicity, flexibility, and built-in support for interceptors, allowing for centralized request and response handling.
- **ag-Grid:** Selected for its performance optimizations, extensive feature set, and compatibility with React, making it suitable for handling large datasets efficiently.
- **date-fns:** Chosen for its lightweight nature, comprehensive date manipulation utilities, and TypeScript support, ensuring reliable handling of temporal data.
- **CSS-in-JS Libraries (potentially):** Offered a convenient way to style components with scoped styles, enhancing encapsulation and reusability.


</details>
