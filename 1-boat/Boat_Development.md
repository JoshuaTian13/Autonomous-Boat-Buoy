# Autonomous Boat Development

This document summarizes the engineering process for converting a Traxxas high-speed RC Boat into an autonomous surface vehicle. It highlights key technical challenges, design iterations, and solutions.


---

## Flight Controller and Software Setup

- Installed **ArduPilot firmware** on Lux HD H7 flight controllers using STM32Cube. Encountered driver/port issues that required reflashing and configuring DFU drivers.  
- Used **Mission Planner**, an open-source ground control system, to configure autonomous navigation. Since ArduPilot is primarily designed for drones and land vehicles, we adapted it for use as an "ArduBoat."  
- After extensive tuning, we transitioned from Lux HD H7 boards to **Pixhawk 2.4.8**, which proved more robust and easier to configure.  



---

## Electronics and Wiring

- Studied pinout diagrams to ensure proper connections to servos, ESC, GPS, and radios.  
- Added headers and connectors via soldering to improve reliability over temporary taped connections.  
- Implemented **Sik radio modules** for ground-to-boat communication.  
- Integrated GPS after troubleshooting wiring errors.  



---

## Power Systems

- Built and soldered **3-cell LiPo battery packs** as an alternative to stock Traxxas batteries.  
- Incorporated battery monitors to provide low-voltage alarms and prevent controller overload.  



---

## RC and Manual Override

- Configured a **TGY-i6S RC controller** for manual control and autonomous override.  
- Verified PWM signals for servo and throttle through Mission Planner.  

---

## Mechanical Design and 3D Printing

- Designed and printed **water-resistant enclosures** for flight controllers, radios, and receivers.  
- Iterated through **3D-printed propeller designs** to improve thrust.  
- Designed custom **rudders and servo linkages** to improve maneuverability.  


---

## Testing and Iterations

### Pool Tests
- Verified propulsion and turning.  
- Identified rudder surface area and servo linkage as limiting factors, then refined designs.  



### Autonomous Trials
- Configured Pixhawk outputs to correct miswired throttle and servo channels.  
- Simulated autonomous navigation using Mission Planner paths.  



### Lake Test
- Conducted field test with a 27-waypoint grid path.  
- Successful autonomous runs without buoy; instability appeared when pulling buoy.  


---

## Lessons Learned

- Robust **power regulation** is essential for protecting sensitive controllers.  
- Iterative **mechanical design** (rudders, enclosures, propellers) was critical.  
- **Autonomous navigation** worked reliably unloaded, but load and radio interference need further refinement.  
