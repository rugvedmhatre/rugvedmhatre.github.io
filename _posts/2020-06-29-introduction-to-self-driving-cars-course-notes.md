---
title: "Course Notes: Introduction to Self Driving Cars"
date: 2020-06-29T18:30:00+05:30
toc: true
toc_label: "Notes"
---

# Taxonomy of Driving

Driving Task of an autonomous driving vehicle includes:

- Perceiving the Environment
- Planning how to reach from point A to point B
- Controlling the vehicle

**Operational Design Domain (ODD)**: The ODD constitutes the operating conditions under which a given system is designed to function. It includes environmental, time of day, roadway and other characteristics under which the car will perform reliably. Clearly defining the operating conditions for which a self-driving car is designed, is crucial to ensuring the safety of the system. So the ODD needs to be planned out carefully in advance.

## **How to classify driving system automation?**

- Driver Attention Requirements: Driver attention is one of the crucial questions to consider when defining the level of autonomy.
- Driver Action Requirements
- What exactly makes up a driving task?
    - Lateral Control: refers to the task of steering and navigating laterally on the road. Turning left, right, going straight or tracking a curve and so on.
    - Longitudinal Control: This is the task where we control the position or velocity of the car along the roadway, through actions like breaking or acceleration.
    - Object and Event Detection and Response (OEDR): OEDR is essentially the ability to detect objects and events that immediately affect the driving task and to react to them appropriately. OEDR really encompasses a large portion of autonomous driving. So, is used in conjunction with the specific Operational Design Domain to categorise current self-driving systems.
    - Planning: Planning is another important aspect of driving. As immediate response is already part of OEDR, planning is primarily concerned with the long and short term plans needed to travel to a destination or execute manoeuvres such as lean changes and intersection crossings.
    - Miscellaneous: These include actions like signalling with indicators, hand-waving, interacting with other drivers and so on.

Autonomous Capabilities are decided on the factors:

- Does the vehicle have Autonomous Lateral Control?
- Does the vehicle have Autonomous Longitudinal Control?
- OEDR
    - Does the vehicle have Automatic Emergency Response?
    - Does the vehicle need Driver Supervision?
- Does the vehicle have a complete or a restricted ODD?

## Levels of Self Driving Car Automation

*(defined by the SAE Standard J3 016)*

- Level 0 - No automation
- Level 1 - Vehicle has either longitudinal control or latitudinal control but not both. E.g. Adaptive Cruise Control, Lane Keeping Assistance.
- Level 2 - Partial Automation, it has both longitudinal and latitudinal control.
- Level 3 - Conditional Driving Automation, In addition to Level 2 features, it also has automated object and event detection and response for some conditions.
- Level 4 - High Driving Automation, It can handle emergencies autonomously and the driver can entirely focus on other tasks but has a limited ODD.
- Level 5 - High Driving Automation, it is fully autonomous and has an unlimited ODD.

*Note: The levels of autonomy or actually a coarse measure of automation. In fact, it is possible for two car models to claim level four autonomy but have very different capabilities in ODDs.*

*Reference: [J3016B: Taxonomy and Definitions for Terms Related to Driving Automation Systems for On-Road Motor Vehicles](https://www.sae.org/standards/content/j3016_201806/).*

# Requirements of Perception

## **What is perception?**

- We want to make sense of the environment and ourselves
- We need to:
    - Identify things in the environment
    - Understand their motion
- Why do we need perception systems?
    - To inform our driving decisions

## **Goals for perception**

- Static Objects: Road and Lane Markings (on-road), Curbs (off-road), Traffic Lights (off-road), Road Signs (off-road), Construction Signs, Obstructions and more (on-road)
- Dynamic Objects: Other vehicles, Pedestrians
- Ego Localisation: Position, Velocity, Acceleration, Orientation and Angular Motion

## **Challenges to Perception**

- Robust detection and segmentation
- Sensor Uncertainty
- Occlusion, Reflection
- Illumination, lens flare
- Weather, precipitation

*For Perception Data Sets: [The KITTI Vision Benchmark Suite](http://www.cvlibs.net/datasets/kitti/index.php).*

# Driving Decisions - Planning

- Long term - How to navigate from New York to Los Angeles?
- Short term - Can I change my lane to the lane right of me? Can I pass this intersection and join the left road?
- Immediate - Can I stay on track on this curved road? Accelerate or brake, by how much?

Reactive Planning (Rule Based Planning): In reactive rule based planning, we have rules that take into account the current state of ego and other objects and give decisions. Examples:

- If there is a pedestrian on the road, stop.
- If the speed limit changes, adjust speed to match it.

Predictive Planning: Make predictions about other vehicles and how they are moving. Then use these predictions to inform our decisions. Example:

- That car has been stopped for the last 10 seconds. It is going to be stopped for the next few seconds.
- That pedestrian is jaywalking. She will enter our lane by the time we reach her.

*For further reading, [A Survey of Motion Planning and Control Techniques for Self-Driving Urban Vehicles - IEEE Journals & Magazine](https://ieeexplore.ieee.org/abstract/document/7490340), [Autonomous driving in urban environments: Boss and the Urban Challenge](https://onlinelibrary.wiley.com/doi/abs/10.1002/rob.20255)*

# Glossary of Terms Used

- **ACC: Adaptive Cruise Control**
    
    A cruise control system for vehicles which controls longitudinal speed. ACC can maintain a desired reference speed or adjust its speed accordingly to maintain safe driving distances to other vehicles.
    
- **Ego**
    
    A term to express the notion of self, which is used to refer to the vehicle being controlled autonomously, as opposed to other vehicles or objects in the scene.  It is most often used in the form ego-vehicle, meaning the self-vehicle.
    
- **FMEA: Failure Mode and Effects Analysis**
    
    A bottom up approach of failure analysis which examines individual causes and determines their effects on the higher level system.
    
- **GNSS: Global Navigation Satellite System**
    
    A generic term for all satellite systems which provide position estimation. The Global Positioning System (GPS) made by the United States is a type of GNSS. Another example is the Russian made GLONASS (Globalnaya Navigazionnaya Sputnikovaya Sistema).
    
- **HAZOP: Hazard and Operability Study**
    
    A variation of FMEA (Failure Mode and Effects Analysis) which uses guide words to brainstorm over sets of possible failures that can arise.
    
- **IMU: Inertial Measurement Unit**
    
    A sensor device consisting of an accelerometer and a gyroscope. The IMU is used to measure vehicle acceleration and angular velocity, and its data can be fused with other sensors for state estimation.
    
- **LIDAR: Light Detection and Ranging**
    
    A type of sensor which detects range by transmitting light and measuring return time and shifts of the reflected signal.
    
- **LTI: Linear Time Invariant**
    
    A linear system whose dynamics do not change with time. For example, a car using the unicycle model is a LTI system. If the model includes the tires degrading over time (and changing the vehicle dynamics), then the system would no longer be LTI.
    
- **LQR: Linear Quadratic Regulation**
    
    A method of control utilizing full state feedback. The method seeks to optimize a quadratic cost function dependent on the state and control input.
    
- **MPC: Model Predictive Control**
    
    A method of control whose control input optimizes a user defined cost function over a finite time horizon. A common form of MPC is finite horizon LQR (linear quadratic regulation).
    
- **NHTSA: National Highway Traffic Safety Administration**
    
    An agency of the Executive Branch of the U.S. government who has developed a 12-part framework to structure safety assessment for autonomous driving.  The framework can be found here. https://www.nhtsa.gov/sites/nhtsa.dot.gov/files/documents/13069a-ads2.0_090617_v9a_tag.pdf
    
- **ODD: Operational Design Domain**
    
    The set of conditions under which a given system is designed to function. For example, a self driving car can have a control system designed for driving in urban environments, and another for driving on the highway.
    
- **OEDR: Object and Event Detection and Response**
    
    The ability to detect objects and events that immediately affect the driving task, and to react to them appropriately.
    
- **PID: Proportional Integral Derivative Control**
    
    A common method of control defined by 3 gains.
    
    1. A proportional gain which scales the control output based on the amount of the error
    2. An integral gain which scales the control output based on the amount of accumulated error
    3. A derivative gain which scales the control output based on the error rate of change
- **RADAR: Radio Detection And Ranging**
    
    A type of sensor which detects range and movement by transmitting radio waves and measuring return time and shifts of the reflected signal.
    
- **SONAR: Sound Navigation And Ranging**

    A type of sensor which detects range and movement by transmitting sound waves and measuring return time and shifts of the reflected signal.

# **Sensors**

Sensors are devices that measure or detect a property of the environment, or changes to a property. They are categorised as:

- Exteroceptive: They record the property of the surroundings (extero = surroundings)
- Proprioceptive: They record the properties of the car (proprio = internal)

## Exteroceptive Sensors

- Camera:
    - Cameras are a passive, light-collecting sensor that are great at capturing rich, detailed information about a scene.
    - They are essential for correctly perceiving the environment.
    - They are selected on the basis of these factors (Comparison Metrics):
        - Resolution: The resolution is the number of pixels that create the image. So it's a way of specifying the quality of the image.
        - Field of View: The field of view is defined by the horizontal and vertical angular extent that is visible to the camera, and can be varied through lens selection and zoom.
        - Dynamic Range: The dynamic range of the camera is the difference between the darkest and the lightest tones in an image. High dynamic range is critical for self-driving vehicles due to the highly variable lighting conditions encountered while driving especially at night.
    - There is an important trade off cameras and lens selection, that lies between the choice of field of view and resolution. Wider field of view permits a larger viewing region in the environment. But fewer pixels that absorb light from one particular object. As the field of view increases, we need to increase resolution to still be able to perceive with the same quality, the various kinds of information we may encounter.
    - Other properties of cameras that affect perception exist as well, such as focal length, depth of field and frame rate.
    - The combination of two cameras with overlapping fields of view and aligned image planes is called the stereo camera. Stereo cameras allow depth estimation from synchronized image pairs. Pixel values from one image can be matched to the other image, producing a disparity map of the scene. This disparity can then be used to estimate depth at each pixel.
- LIDAR Sensor:
    - LIDAR stands for light detection and ranging.
    - LIDAR sensing involves shooting light beams into the environment and measuring the reflected return. By measuring the amount of returned light and time of flight of the beam. Both in intensity in range to the reflecting object can be estimated.
    - LIDAR usually includes a spinning element with multiple stacked light sources. And output a three dimensional point cloud map, which is great for assessing scene geometry.
    - Because it is an active sensor with its own light sources, LIDAR is not affected by the environment's lighting. So LIDAR does not face the same challenges as cameras when operating in poor or variable lighting conditions.
    - Comparison Metrics:
        - Number of Beams: The number of sources it contains with 8, 16, 32, and 64 being common sizes.
        - Points per Second: The faster the point collection, the more detailed the 3D point cloud can be.
        - Rotation Rate: The higher this rate, the faster the 3D point clouds are updated.
        - Detection Range: is also important, and is dictated by the power output of the light source.
        - Field of View: it is the angular extent visible to the LIDAR sensor.
    - High-resolution, solid-state LIDAR is a new LIDAR type that is currently emerging. Without a rotational component of the typical LIDARs, these sensors stand to become extremely low-cost and reliable. Thanks to being implemented entirely in silicon. They are still a work in progress, but definitely something exciting for the future of affordable self-driving.
- RADAR Sensor:
    - It stands for radio detection and ranging.
    - They can robustly detect large objects in the environment, and are also useful in relative speed detection.
    - They are particularly useful in adverse weather as they are mostly unaffected by precipitation.
    - Comparison Metrics:
        - Detection Range
        - Field of View
        - Position and Speed measurement accuracy
    - RADAR Configurations:
        - Wide FOV, Short Range
        - Narrow FOV, Long Range
- Ultrasonic Sensor (Sonars):
    - It stands for sound navigation and ranging, which measure range using sound waves.
    - Sonar are sensors that are short range in inexpensive ranging devices. This makes them good for parking scenarios, where the ego-vehicle needs to make movements very close to other cars.
    - Another great thing about sonar is that they are low-cost.
    - Moreover, just like RADAR and LIDAR, they are unaffected by lighting and precipitation conditions.
    - Comparison Metrics:
        - Detection Range
        - Field of View
        - Cost

## Proprioceptive Sensors

- GNSS:
    - It stands for Global Navigation Satellite Systems. It is also known as GPS or Galileo.
    - GNSS receivers are used to measure ego vehicle position, velocity, and sometimes heading.
    - The accuracy depends a lot on the actual positioning methods and the corrections used.
- IMUs:
    - It stands for inertial measurement units.
    - The IMU measures the angular rotation rate and the acceleration of the ego vehicle

The combined measurements from GNSS and IMUs can be used to estimate the 3D orientation of the vehicle. (heading is the most important for vehicle control)

- Vehicle Odometry Sensors:
    - This sensor tracks the wheel rates of rotation, and uses these to estimate the speed and heading rate of change of the ego car.
    - It also tracks the mileage of the vehicle.

    <!-- Add image here... -->
    <img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image1.png" alt="sensor-placement">


# **Computing Hardware**

- The most crucial part is the computing brain, the main decision making unit of the car.
- It takes in all sensor data and outputs the commands needed to drive the vehicle.
- Most companies prefer to design their own computing systems that match the specific requirements of their sensors and algorithms. Some hardware options exist, however, that can handle self-driving computing loads out of the box. The most common examples would be Nvidia's Drive PX and Intel & Mobileye's EyeQ.
- Any computing brain for self-driving needs both serial and parallel compute modules. Particularly for image and LIDAR processing to do segmentation, object detection, and mapping. For these we employ GPUs, FPGAs and custom ASICs, which are specialized hardware to do a specific type of computation. For example; the drive PX units include multiple GPUs. And the EyeQs have FPGAs both to accelerate parallelizable compute tasks, such as image processing or neural network inference.
- Synchronisation Hardware:
    - It helps to make driving decisions based on a coherent picture of the road scene.
    - It is essential to correctly synchronize the different modules in the system, and serve a common clock.
    - Fortunately, GPS relies on extremely accurate timing to function, and as such can act as an appropriate reference clock when available.
    - Regardless, sensor measurements must be time stamped with consistent times for sensor fusion to function correctly.

*For further reading, [http://wavelab.uwaterloo.ca/sharedata/ME597/ME597_Lecture_Slides/ME597-4-Measurement.pdf](http://wavelab.uwaterloo.ca/sharedata/ME597/ME597_Lecture_Slides/ME597-4-Measurement.pdf)*

## **Hardware Configuration Design**

*Assumptions:*

- *Aggressive Deceleration: It is the deceleration rate when the brakes are pressed suddenly in an emergency situation. It is assumed at 5 m/s2.*
- *Comfortable Deceleration: It is the deceleration rate when the brakes are pressed normally. It is assumed at 2 m/s2, unless otherwise stated.*

*Given the deceleration rate the braking distance (or stopping distance) can be calculated as follows, d = v2/2a. We can also factor in reaction time of the system and road surface friction limits.*

**Where to place the sensors?**

- We want our sensors to capture the ODD we have in mind or the ODD our system can produce decisions for. We should be able to provide all of the decisions with sufficient input.
- There can be so many possible scenarios in driving but we'll look at just two common scenarios to see how the requirements drive our sensor selection. Will look at highway and urban driving.
    - Highway Driving: For a divided highway, we have fast moving traffic, usually high volume, and quite a few lanes to monitor, but all vehicles are moving in the same direction. The other highlight of driving on a highway setting is that there are fewer and gradual curves and we have exits and merges to consider as well.
    - Urban Driving: On the other hand, in the urban situation we'll consider, we have moderate volume and moderate speed traffic with fewer lanes but with traffic moving in all directions especially through intersections.

    <img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image2.jpeg" alt="sensor-placement-in-environments">

**Highway Analysis**

- We can break down the highway setting into three basic maneuver needs:
    - We may need to hit the brakes hard if there's an emergency situation
    - We need to maintain a steady speed matching the flow of traffic around us
    - We might need to change lanes
- In the case of an emergency stop, if there is a blockage on our road we want to stop in time. So, applying our stopping distance equation longitudinally, we need to be able to sense about 110 meters in front of us assuming a highway speed of a 120 kilometers and aggressive deceleration. Most self-driving systems aim for sensing ranges of 150 to 200 meters in front of the vehicle as a result.
- To avoid lateral collision or to change lanes to avoid hitting an obstacle in our lane, we need to be able to sense at least our adjacent lanes, which are 3.7 meters wide in North America.
- To maintain speed during vehicle following, we need to sense the vehicle in our own lane. Both their relative position and the speed are important to maintain a safe following distance. This is usually defined in units of time for human drivers and set to two seconds in nominal conditions. It can also be assessed using aggressive deceleration of the lead vehicle and the reaction time from our ego vehicle. So, at 120 kilometers per hour, relative position and speed measurements to a range of 165 meters are needed and typical systems use 100 meters for this requirement.
- Laterally, we need to know what's happening anywhere in our adjacent lanes in case another vehicle seeks to merge into our lane or we need to merge with other traffic. A wide 160 to 180 degree field of view is required to track adjacent lanes and a range of 40 to 60 meters is needed to find space between vehicles.
- Finally, let's discuss the lane change maneuver and consider the following scenario. Suppose we want to move to the adjacent lane, longitudinally we need to look forward, so we are a safe distance from the leading vehicle and we also need to look behind just to see what the rear vehicles are doing and laterally it's a bit more complicated. We may need to look beyond just the adjacent lanes. For example, what if a vehicle attempts to maneuver into the adjacent lane at the same time as we do? We'll need to coordinate our lane change room maneuvers so we don't crash. The sensor requirements for lane changes are roughly equivalent to those in the maintain-speed scenario. As both need to manage vehicles in front of and behind the ego vehicle as well as to each side.
- Overall, this gives us the picture for coverage requirements for the highway driving scenario. We need longitudinal sensors and lateral sensors and both wide field of view and narrow field of view sensors to do these three maneuvers, the emergency stop, maintaining speed and changing lanes. Already from this small set of ODD requirements we see a large variety of sensor requirements that arise.

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image3.png" alt="highway-analysis">

**Urban Analysis**

- The urban scenario as we discussed before is a moderate volume, moderate traffic scenario with fewer lanes on the highway case but with the added complexity of pedestrians. There are six types of basic maneuvers here,
    - Emergency Stop
    - Maintain Speed
    - Lane Change
    - Overtaking
    - Turning, crossing at intersections
    - Passing Roundabouts
- For the first three basic maneuvers, the coverage analysis is pretty much the same as the highway analysis but since we are not moving as quickly, we don't need the same extent for our long-range sensing.
- Overtake maneuver: Consider a case where you have to overtake a parked car. Longitudinally, we definitely need to sense the parked car as well as look for oncoming traffic. So, we need both sensors, wide short-range sensors to detect the parked car and narrow long-range sensors to identify if oncoming traffic is approaching. And laterally, we'll need to observe beyond the adjacent lanes for merging vehicles as we did in the highway case.
- For intersections, we need to have near omni-directional sensing for all kinds of movements that can occur. Approaching vehicles, nearby pedestrians, doing turns and much more.
- For roundabouts we need a wide-range, short distance sensor laterally since the traffic is slow but we also need a wide-range short distance sensor longitudinally because of how movement around the roundabout occurs. We need to sense all of the incoming traffic flowing through the roundabout to make proper decisions.
- The main difference with respect to highway coverage is because of the sensing we require for movement at intersections and at roundabouts and for the overtaking maneuver. In fact, the highway case is almost entirely covered by the urban requirements.

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image4.png" alt="urban-analysis">

Thus an overall placement of sensors, taking into account both scenarios, is given as:

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image5.png" alt="overall-coverage-of-sensors">

*For further reading, [Sensing requirements for an automated vehicle for highway and rural environments](https://repository.tudelft.nl/islandora/object/uuid:2ae44ea2-e5e9-455c-8481-8284f8494e4e)*.

# **Software Architecture**

The architecture will use the information provided by the hardware components and allow us to achieve our goal of autonomous driving.

*Note: This is not the only software architecture used in autonomous driving, but is a good representation of the necessary functions for full vehicle autonomy.*

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image6.png" alt="software-architecture-high-level">

- Environment Perception: These modules have key responsibilities of - identifying the current location of the autonomous vehicle in space, and classifying and locating important elements of the environment for the driving task. Examples of these elements include other cars, bikes, pedestrians, the road, the road markings, and road signs, anything that directly affects the act of driving.
- Environment Mapping: This module creates a set of maps which locate objects in the environment around the autonomous vehicle for a range of different uses, from collision avoidance, to ego motion tracking and motion planning.
- Motion Planning: This module makes all the decisions about what actions to take and where to drive based on all of the information provided by the perception and mapping module. This module's main output is a safe, efficient and comfortable planned path that moves the vehicle towards its goal.
- Controller: The controller module takes the planned path and decides on the best steering angle, throttle position, brake position, and gear settings to precisely follow the planned path.
- System Supervisor: It monitors all parts of the software stack as well as the hardware output to make sure that all systems are working as intended. It is also responsible for informing the safety driver of any problems found in the system.

## Environment Perception

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image7.png" alt="software-architecture-environment-perception">

- There are two important parts of the perception stack, localising the ego-vehicle in space, as well as classifying and locating the important elements of the environment.
- The localization module takes in multiple streams of information, such as the current GPS location, IMU measurements and wheel odometry. It then combines them to output an accurate vehicle location. For greater accuracy, some localization modules also incorporate LIDAR and camera data.
- Typically, the problem of classification and localization of the environmental elements is divided into two segments, first, detecting dynamic objects in the environment, and second, detecting the static objects in the environment.
- The dynamic object detection module uses a set of camera inputs as well as LIDAR point clouds to create 3D bounding boxes around dynamic objects in the scene. The 3D bounding boxes encode the class or type of object as well as the exact position, orientation and size of the object. Once detected, the dynamic objects are tracked over time by a tracking module. The tracker module provides not only the current position of the dynamic objects but also the history of its path through the environment. The history of the path is used along with the roadmaps In order to predict the future path of all dynamic objects. This is usually handled by a prediction module, which combines all information regarding the dynamic object and the current environment to predict the path of all dynamic objects.
- The static object detection module also relies on a combination of camera input and LIDAR data to identify significant static objects in the scene. Such important data include the current lane in which the self-driving vehicle is found, and the location of regulatory elements such as signs and traffic lights.

## Environment Mapping

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image8.png" alt="software-architecture-environment-mapping">

- Environment maps create several different types of representation of the current environment around the autonomous car. There are three types of maps that we discuss briefly, the occupancy grid map, the localization map and the detailed road map.
- The occupancy grid is a map of all static objects in the environment surrounding the vehicle. LIDAR is predominantly used to construct the occupancy grid map. A set of filters are first applied to the LIDAR data to make it usable by the occupancy grid. For example, the drivable surface points and dynamic object points are removed. The occupancy grid map represents the environment as a set of grid cells and associates a probability that each cell is occupied. This allows us to handle uncertainty in the measurement data and improve the map over time.
- The localization map, which is constructed from LIDAR, or camera data, is used by the localization module in order to improve eco state estimation. Sensor data is compared to this map while driving to determine the motion of the car relative to the localization map. This motion is then combined with other proprioceptor sensor information to accurately localise the eco vehicle.
- The detailed road map provides a map of road segments which represent the driving environment that the autonomous vehicle is currently driving through. It captures signs and lane markings in a manner that can be used for motion planning. This map is traditionally a combination of prerecorded data as well as incoming information from the current static environment gathered by the perception stack. The environment mapping and perception modules interact significantly to improve the performance of both modules. For example, the perception module provides the static environment information needed to update the detailed road map, which is then used by the prediction module to create more accurate dynamic object predictions.

## Motion Planning

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image9.png" alt="software-architecture-motion-planning">

- The output from both the environment maps and the perception modules are combined and used by the motion planning module to create a path through the environment.
- Motion planning for self-driving cars is a challenging task, and it's hard to solve in a single integrated process. Instead, most self-driving cars today use a decomposition that divides the problem into several layers of abstraction as follows.
- At the top level, the mission planner handles long term planning and defines the mission over the entire horizon of the driving task, from the current location, through the road network to its final destination. To find the complete mission, the mission planner determines the optimal sequence of road segments that connect your origin and destination, and then passes this to the next layer.
- The behaviour planner is the next level of abstraction, solving short term planning problems. The behaviour planner is responsible for establishing a set of safe actions or manoeuvres to be executed while travelling along the mission path. An example of the behaviour planner decisions would be whether the vehicle should merge into an adjacent lane given the desired speed and the predicted behaviours of nearby vehicles. Along with the manoeuvre of decisions, the behaviour planner also provides a set of constraints to execute with each action, such as how long to remain in the current lane before switching.
- The local planner performs immediate or reactive planning, and is responsible for defining a specific path and velocity profile to drive. The local plan must be smooth, safe, and efficient given all the current constraints imposed by the environment and manoeuvre. In order to create such a plan, the local planner combines information provided by the behaviour planner, occupancy grid, the vehicle operating limits, and other dynamic objects in the environment. The output of the local planner is a planned trajectory which is a combined desired path and velocity profile for a short period of time into the future.

## Vehicle Controller

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image10.png" alt="software-architecture-vehicle-controller">

- A typical controller separates the control problem into a longitudinal control and a lateral control.
- The lateral controller outputs the steering angle required to maintain the planned trajectory.
- Whereas the longitudinal controller regulates the throttle, gears and braking system to achieve the correct velocity.
- Both controllers calculate current errors and tracking performance of the local plan, and adjust the current actuation commands to minimise the errors going forward.

## System Supervisor

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog-images/introduction-to-self-driving-cars/image11.png" alt="software-architecture-system-supervisor">

- The system supervisor is the module that continuously monitors all aspects of the autonomous car and gives the appropriate warning in the event of a subsystem failure. There are two parts, the hardware supervisor, and the software supervisor.
- The hardware supervisor continuously monitors all hardware components to check for any faults, such as a broken sensor, a missing measurement, or degraded information. Another responsibility of the hardware supervisor is to continuously analyse the hardware outputs for any outputs which do not match the domain which the self-driving car was programmed to perform under. For example, if one of the camera sensors is blocked by a paper bag or if snow is falling and corrupting the LIDAR point cloud data.
- The software supervisor has the responsibility of validating this software stack to make sure that all elements are running as intended at the right frequencies and providing complete outputs. The software supervisor also is responsible for analysing inconsistencies between the outputs of all modules.

*For further reading, [DARPA Urban Challenge Technical Paper](https://pdfs.semanticscholar.org/c10a/cd8c64790f7d040ea6f01d7b26b1d9a442db.pdf).*

# **Environment Representation**

Environmental Map Types:

- Localisation Map - This map is created using a continuous set of lidar points or camera image features as the car moves through the environment. This map is then used in combination with GPS, IMU and wheel odometry by the localization module To accurately estimate the precise location of the vehicle at all times.
- Occupancy Grid Map - The occupancy grid also uses a continuous set of LIDAR points to build a map of the environment which indicates the location of all static, or stationary, obstacles. This map is used to plan safe, collision-free paths for the autonomous vehicle.
- Detailed Road Map - It contains detailed positions for all regulatory elements, regulatory attributes and lane markings. This map is used to plan a path from the current position to the final destination.

## Localisation Map

- The localization map uses recorded LIDAR points or images, which are combined to make a point cloud representation of the environment.
- As new LIDAR camera data is received it is compared to the localization map and a measurement of the ego vehicles position is created by aligning the new data with the existing map. This measurement is then combined with other sensors to estimate ego motion and ultimately used to control the vehicle.
- The localization map can be quite large, and many methods exist to compress it's contents and keep only those features that are needed for localization.

## Occupancy Grid Map

- The occupancy grid is a 2D or 3D discretized map of the static objects in the environments surrounding the ego vehicle.
- This map is created to identify all static objects around the autonomous car, once again, using point clouds as our input.
- The objects which are classified as static include trees, buildings, curbs, and all other non drivable surfaces.
- As the occupancy grid only represents the static objects from the environment, all dynamic objects must first be removed. This is done by removing all LIDAR points that are found within the bounding boxes of detected dynamic objects identified by the perception stack.
- Next, static objects which will not interfere with the vehicle are also removed. Such as drivable surfaces or any over hanging tree branches. As a result of these steps only the relevant LIDAR points from static objects from the environment remain.
- The filtering process is not perfect and so it is not possible to blindly trust the remaining points are in fact obstacles.
- The occupancy grid, therefore, represents the environment probabilistically, by tracking the likelihood that a grid cell occupies over time.
- This map is then relied on to create paths for the vehicle which are collusion-free.

## Detailed Road Map

- The detailed roadmap is a map of the full road network which can be driven by the self-driving car.
- This map contains information regarding the lanes of a road, as well as any traffic regulation elements which may affect them.
- The detailed road map is used to plan a safe and efficient path to be taken by the self-driving car.
- The detailed road map can be created in one of three ways:
    - Fully online
    - Fully offline
    - Created Offline and Updated Online
- Fully Online Map:
    - A map which is created fully online relies heavily on the static object proportion of the perception stack to accurately label and correctly localize all relevant static objects to create the map.
    - This includes all lane boundaries in the current driving environment, any regulation elements, such as traffic lights or traffic signs, any regulation attributes of the lanes, such as right turn markings or crosswalks.
    - This method of map creation is rarely used due to the complexity of creating such a map in real time.
- Fully Offline Map:
    - A map which is created entirely offline is usually done by collecting data of a given road several times.
    - Specialized vehicles with high accuracy sensors are driven along roadways regularly to construct offline maps.
    - Once the collection is complete, the information is then labelled with the use of a mixture of automatic labelling from static object perception and human annotation and correction.
    - This method of map creation, while producing very detailed and accurate maps, is unable to react or adapt to a changing environment.
- Created Offline and Updated Online:
    - The third method of creating detailed road maps is to create them offline and then update them online with new, relevant information.
    - This method of map creation takes advantage of both methods, creating a highly accurate roadmap which can be updated while driving.
- A method for storing all of the information present in a detailed roadmap is called the Lanelet model.

*For further reading, [Lanelets: Efficient map representation for autonomous driving - IEEE Conference Publication](https://ieeexplore.ieee.org/abstract/document/6856487)*

> To be continued...