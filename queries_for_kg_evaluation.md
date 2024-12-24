# List of SPARQL queries to assess the Dijon Metropolitan Campus


## Spaces

1. How many laboratories are present on the campus?
   
   `MATCH (n:Laboratory) RETURN COUNT(n) AS numberOfLaboratories`
   
3. How many elevators are present on the campus?
   
   `MATCH (n:ElevatorShaft) RETURN COUNT(n) AS numberOfLift`

5. How many spaces are present on the campus?
   
   `MATCH (n:Space) RETURN COUNT(n) AS numberOfSpace`
   
7. How many toilets are present on the campus?
   
   `MATCH (n:PersonalHygiene) RETURN COUNT(n) AS numberOfToilets`
   
9. How many classrooms are present on the campus?
    
   `MATCH (n:classRoom) RETURN COUNT(n) AS numberOfClassRooms`

## Sensors

1. How many energy sensors are present on the campus
   
   `MATCH (n) WHERE 'Energy_Sensor' IN labels(n) OR 'Energy_Usage_Sensor' IN labels(n) RETURN COUNT(n) AS SensorCount`
   
3. How many occupancy sensors are present on the campus?
   
   `MATCH (n:Occupancy_Sensor) RETURN COUNT(n) AS numberOfOccupancySensor`
   
5. How many sensors are present on the campus?
   
   `MATCH (n:Sensor) RETURN COUNT(n) AS numberOfSensor`
   
7. How many CO2 sensors are present on the campus?
   
   `MATCH (n:CO2_Level_Sensor) RETURN COUNT(n) AS numberOfSensor`
   
9. How many temperature sensors are present on the campus?
    
   `MATCH (n) WHERE 'Average_Zone_Air_Temperature_Sensor' IN labels(n) OR 'Zone_Air_Temperature_Sensor' IN labels(n) RETURN COUNT(n) AS numberOfSensor`

## Sensors to spaces relationships

1. How many occupancy sensors are in room "00-39-N"?
   
   `MATCH (sensor:Occupancy_Sensor)<-[:hasPoint]-(room) WHERE (room.displayName="00-39-N") RETURN COUNT(sensor)`
   
3. List of occupied conference rooms
   
   `MATCH (room:ConferenceRoom)-[:hasPoint]->(sensor:Occupancy_Sensor)<-[:sourcePoint]-(event:BooleanValueObservation) WHERE event.value="True" RETURN room.displayName`
   
5. List of office room temperatures between 20 and 28 degrees
   
   `MATCH (room:OfficeRoom)-[:hasPoint]->(sensor:Temperature_Sensor)<-[:sourcePoint]-(event:TemperatureObservation) WHERE toInteger(event.value) > 19 AND toInteger(event.value) < 28 RETURN DISTINCT room.displayName`
   
7. List of areas with an electrical panel
   
   `MATCH (room:Space)-[:hasPoint]->(sensor:Energy_Sensor) RETURN DISTINCT room.displayName`
   
9. List of areas with CO2 rate superior to 700 ppm
    
   `MATCH (room:Space)-[:hasPoint]->(sensor:CO2_Sensor)<-[:sourcePoint]-(e:DoubleObservationValue) WHERE toInteger(e.value) > 700 RETURN n.displayName`
