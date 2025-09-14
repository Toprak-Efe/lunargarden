#seminar #robotics #localization #gps #autonomy #SLAM
# T-28 First Flight Test
An erroneous procedure was detected in the test flight of the T-28 plane bought to use by Grace Gao. The UAV was lost by the students. After a search the UAV was discovered within a nearby cornfield. The cause for this loss was a lack of sensor instrumentation, the UAV was lacking camera as well as GPS data.
# Ground Localization
## Global Positioning System (GPS)
#trilateration
GPS is a navigational tracking system consisting of $31$ satellites in middle Earth orbit, the transmit power is $26 \ \text{Watts}$ for the common L1 frequency band. The received power is roughly $10^{-16} \ \text{Watts}$.

The concept of GPS is **Trilateration**. 
Contact with at least three satellites when made, allows you to pinpoint your location by considering your distance away from them. The crossing set of different three spheres is at most a single point, this allows you to pinpoint exactly where you are positioned relative to these satellites.
### Applications of GPS-based Localization
For localization we can use GPS for ground applications like self-driving cars.
For aerial applications such as aerial taxi, drone delivery systems, as well as space applications.
#### Urban Environments
#nerf #satelliteshadow
Within cities one of the most prominent GPS faces is when the signal has been blocked by the nearby buildings of tall stature. However, this doesn't mean locating yourself is impossible. You can pinpoint areas where the signal is evidently blocked, and decide on where you are depending on where the closest area of unservice is relative to your last known GPS location. The blocked areas relative to the satellite are called **satellite shadows**.

How can we know where the buildings that can cast satellite shadows are? Recently, we started to get 3D models of our cities, in even more recent times the concept of **Neural City Maps** have begun emerging with the use of **NeRF**.
### Multi-Path Errors
Traditional methods of ignoring multi-path messages is to mitigate or reduce them. However, these multi-path signals can also allow us to deduce or approximate location, by extrapolating from the 3D structure of the environment we can unwrap the reflected rays into a single uni-directional ray, which would pinpoint to an imaginary, virtual satellite when followed.

In order to understand the location of these reflection surfaces, instead of using LiDAR, we can use sensor fusion of a GPS receiver and a fisheye camera. Within this framework we can borrow some concepts SLAM and keep track of past satellite positions, and use graph optimization to map ourselves better into the environment. 
### GPS-Vision Fusion With Efficient Computation While Ensuring Integrity
Too many sensors onboard a robot will overload it's computational capacity and eventually distort the localization results, the latter actually depends on sensor quality. An ingenious way to utilize the fruits of sensor fusion is to implement an **attention mechanism**. Much like the human brain the robot should only consider sensory throughputs of noise which are above the acceptability threshold in terms of cleanliness.  We can adaptively choose a combination of virtual and physical satellite constellations to read from, such that the geometry they create is most apt for precise geolocation.
![[Pasted image 20231223203119.png]]
## Extreme Dynamics for Cars
Prof. Chris Gerdes is a renowned researcher in Stanford University, whose research is in autonomous driving that tackle high acceleration and unorthodoxical movement patterns, such as drifting.

He has successfully created an autonomous drifting system, the next step in his research, having multiple autonomous agents drift in tandem, was supported by Prof. Grace Gao, however, a just as unorthodoxical problem was encountered.

The regular sensors when used within the project would result in high noise. The visual sensors, the cameras, were blocked by a high quantity of smoke which made the agents practically blind. High velocities mean more sensory equipment, which means a large computational requirement.

The solution they have found was to fly an UAV above the two cars, which allowed for precise localization. The first thought out solution was putting AprilTags ontop of the vehicles, which was  not very effective. SegmentEverything model was used to track the cars from the aerial birds-eye footage.
# Aerial Localization
Besides ground vehicles, GPS positioning for aeroplanes within deep valleys or obstructed locations are also a problem. Other than the GPS, the pilot will also experience some difficulties when in high pitch, roll angles due to the view from the side panels missing the horizon, which is a very good way to learn, by eye-sight, just how much tilted you are at any moment.
## Robust GPS Positioning for Highly Dynamical Flights
A plane retrofitted with four GPS receivers on four different locations that were more than five meters apart, had direct position estimation used to calculate the exact location of; this required high computational capacity.

The flight test was scheduled months in advance and a technical difficulty was experienced with the onboard equipment when the time came. A seesaw clock within the plane meant to synchronize all clocks with, carrying a hard-drive, had it's SMA cable dislodge during all the vibrations it experienced in the pre-flight testing.  This meant that sensory-instruments could not be synchronized which meant that position data was skewed randomly as timings were not aligned for data retrieval.

The problem was diagnosed and resolved two days before the actual flight test, the students were relieved and ready to take on further challenges if any were to arise.
# Space Localization
#LunaNet 
The Artemis Mission, is a mission planned by the US space agency that means to send two astronauts onto The Moon. In actuality, there are over 100 official missions planned for Moon as of this document. GPS localization in Moon is an interesting prospect that needs to be explored.
## Future Lunar Positioning, Navigation & Timing
#timers #occultation #LuGRE
The question is, can we set up a GPS-like system for the Moon at a much lower cost? The rationality behind this is because the Terran GPS has extremely expensive, high-end timers with three atomic clocks per satellite for redundancy. With $30$ satellites, this makes for $90$ atomic clocks. Not to say the ground monitoring stations to give error corrections, even atomic clocks drift.

We want to make the Lunar navigation system smaller, cheaper to build and maintain. We don't want any ground monitoring stations as well. The key idea is to use the infrastructure present on Earth for time correction, which outsources the most arduous computational process off-Lunar. There are a lot of technical challenges due to **occultation** when the satellites are behind the Earth relative to the Moon.

Bad geometry means higher signal processing and filtering requirements, but it ends up being cheaper than building new infrastructure on Luna. A future prospect is also the directional nature of the current GNSS antennas, which would at first sight make one think that the receivers on Moon would face difficulties receiving the signals of. However, no antenna is truly one-directional, and the side lobes of the radiation pattern can be reached from the Lunar surface still. This is an active research subject and the **LuGRE** mission by NASA in 2024 aims to address it.
## Case Studies for Lunar Constellations
#constellation #moon
For navigation, you need trilateration. In the case of multiple satellites, all should be used. However, for communication, even one is enough. A subset of the navigation satellites could be designated for communications, exactly how many need to be for effective and efficient communication & navigation combination is currently being studied case by case.
## Robot Swarm on The Moon
#CADRE #robotics #swarm
One of the research being done is a robot swarm exploration on the moon. CADRE, which stands for Cooperative Autonomous Distributed Robotic Explorers is a mission design that intends to implement this concept. Communication loss is one of the problems that are practically tackled in this research.
## Long-Range Autonomous Driving on The Moon: Endurance Mission
#endurancemission #pathfindersatellite 
Most rovers don't go long distances during autonomous driving, Endurance Mission tackles this concept by creating a system capable of autonomously traversing over $2000 \ \text{km}$'s.

This is intended to be done in the South Pole, the reason is the scientific value inherently located in the region, which might give insights into the  geological development of the geo-satellite in great quantities. Especially, it might be to analyze the water content present.

The mission concept begins with a Lunar pathfinder satellite for communication, the research is currently done on whether or a navigational payload from the satellite can help the rover navigate by itself. Within a $24$ hour window an outage graph was created.
