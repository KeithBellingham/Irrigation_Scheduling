# Irrigation Scheduling Using Soil Moisture Sensors<br />
Rain Garden Plant Species Water Management Assessment
**Introduction**<br />
Stormwater runoff from urban roads and streets is a potential source of surface water pollution. Rain Gardens have been a proven way to filter and adsorb stormwater for not only streets but parking lots and industrial site. The soils and plant species in the rain gardens must be engineered to survive dry summer periods while being able to transpire large amounts of water during the rainier seasons. The soils need to drain freely while holding enough water to keep the plants alive when it is not raining.   These test sites are rain gardens in Portland Oregon that compare several soil mixes with a variety for plant species. Each rain garden contains four soil moisture sensors at a depth of 8 inches and the total depth of the soil is about 50 inches. The data was logged every 15 minutes year-round. The rain gardens are managed by the City of Portland and are occasionally irrigated in the summer months from a water truck and a hand line.   

**Theory**<br />
The relationship between soil moisture and crop health is not straightforward and usually not well understood.  Techniques and tools commonly used in the field of data science are used to understand the flow and retention of water in the soil.  

Water movement in soil is driven by two physical forces, gravity and capillarity. If the soil is completely saturated or very wet (After an irrigation event), the primary force acting on the water will be gravity and can be best discribed be Darcy’s Law; 


$$\frac{\partial \theta}{\partial t} = flow  = -K_s(dh/dz)$$

Where $\theta$  is volumetric soil moisture, $K_s$ is the saturated hydraulic conductivity, *h* is hydraulic head and *z* is depth.  

After gravity gets finish pulling the water out of the soil, the predominant force acting on the water is capillary forces which is the force of the surface tension between water and air. Water movement from capillary forces is commonly called “wicking” and is described by the Richard’s Equation;


$$\frac{\partial \theta}{\partial t} = flow  =   \frac{\partial (K_h   \frac{\partial h}{\partial z}         }{\partial z} )  + \frac{\partial K_h} {\partial z }   -S(h) $$    



In the Richard’s equation $K_h$ is now the head dependent hydraulic conductivity, and $-S(h)$ is basically evaporation. 

In plant/water dynamics, the optimal soil water content for most crops and most plants is call the available water capacity (AWC) and is largely a function of the soil. The upper limit of the AWC is the soil’s “field capacity”. The field capacity is an important hydrological threshold in agriculture and agronomy. Field capacity is defined as the soil moisture after the water drains out. It is where the gravitational force acting on the water in soil is equal to the capillary forces acting on the water and thus $K_h$ from the Richard’s equation is equal to $K_s$ in Darcy’s Law.  The lower limit of the AWC can be assumed to be 80% of the Field capacity. Basically, the optimal soil moisture for most crops is between field capacity and 80% of field capacity. 

Field capacity may be expensive and difficult to measure in the lab. Also, field capacity is highly variable because soil is highly variable. Factors such as compaction, organic matter, texture, particle size distribution, and the roots of the plant all affect the soil moisture values where field capacity would occur.  Because of this variability, each individual soil sensor experiences a local field capacity, and the mathematical and algorithmic determination of field capacity needs to be carried out for each sensor separately.

 Since the local soil field capacity is not likely to change during a grow season, a select time range of the soil moisture time series data can be chosen as training data. This would eliminate errors in the calculation of field capacity if the crop is under or over irrigated.    

The goal is to determine the AWC and determine when crops would become stressed form the time series soil moisture data. 


![curb-ext-45th-and-clay-in-rain](https://user-images.githubusercontent.com/62969383/205175134-f6a9f0bc-b61f-428a-b48d-0da125f206ca.jpeg)


