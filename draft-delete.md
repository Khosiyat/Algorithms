```mermaid
graph TD
    A["biologging-sensor-client"] 
    B["biologging-sensor-data"]
    C["src"]
    D["components"]
    E["<span style='color:blue'>graphs</span>"]

    subgraph biologging-sensor-client
        B --> C
    end
    subgraph biologging-sensor-data
        C --> D
    end
    subgraph src
        D --> E
    end

    style E fill:#0f0,stroke:#333,stroke-width:2px;

```
