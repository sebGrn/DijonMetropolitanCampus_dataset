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
   
3. Count of spaces with temperature sensors
   
   `MATCH (room:Space)-[:hasPoint]->(sensor:Temperature_Sensor) RETURN COUNT(room)`
   
5. Count of spaces with water consumption sensors
   
   `MATCH (room:Space)-[:hasPoint]->(sensor:Water_Level_Sensor) RETURN COUNT(room)`
   
7. Count of spaces with CO2 sensors
   
   `MATCH (room:Space)-[:hasPoint]->(sensor:CO2_Sensor) RETURN COUNT(room)`
   
9. List of areas with CO2 rate superior to 700 ppm
    
   `MATCH (room:Space)-[:hasPoint]->(sensor:CO2_Sensor)<-[:sourcePoint]-(e:DoubleObservationValue) WHERE toInteger(e.value) > 700 RETURN n.displayName`
