# dijon_metropolitain_campus_data

These json files represent a sample of data from **Dijon Metropolitain Campus**, which owns the Ready2Service (R2S) label for its IT infrastructure that provides digital services. The campus covers 10,000 square meters and features a *data-driven smart building* environment with sensors that monitor occupancy, temperature, CO2 levels, and energy consumption. The dataset contains over 12,000 metadata and time series data with up to 1.7 million daily updates. They are stored in two collections within a schema-less MongoDB database in JSON format.

The dataset is provided by Linksper Building Operating System, a platform that connects building data with services like meeting room booking, analytics, and smart campus applications. Linksper is a key product of VayanData [VayanData | Expert De La Transformation Digitale Des Bâtiments](https://vayandata.com/), a French company that specializes in digital transformation and business process management solutions.

Primatice is another industrial partner, a subsidiary of Vinci Facilities group. They are actively developing TwinOps [Accueil - TwinOps](https://www.twinops.com/), a platform designed to manage digital twins of real estate assets to enhance the operation and maintenance of connected buildings.

RealEstateCore (REC) [RealEstateCore/rec: RealEstateCore ontologies. (github.com)](https://github.com/RealEstateCore/rec) is a domain ontolgy that describes concepts and relations in building data. REC adopts the Digital Twin Definition Language (DTDL), [DTDL models - Azure Digital Twins | Microsoft Learn](https://learn.microsoft.com/en-us/azure/digital-twins/concepts-models), based on JSON-LD.

The example dataset contains 

- *metadata.json*: an example of originally metadata provided by Linkpser from Vayandata company. It describes an occupancy sensor located in the campus, at room 00-99-N.
- *timeserie_n.json*: examples of originally timeserie data for a boolean value observatation of an occupancy sensor, provided by Linkpser from Vayandata company
- *rec_room_node.json*: example of room node structured in REC format, transformed from metadata.json
- *rec_occupancy_sensor.json*: example of occupancy sensor node structured in REC format, transformed from metadata.json
- *rec_boolean_value_observation.json*: example of boolean observation node structured in REC format, transformed from timeserie.json
