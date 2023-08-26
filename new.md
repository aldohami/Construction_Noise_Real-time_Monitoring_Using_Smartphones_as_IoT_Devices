# Real-time Noise Monitoring at Construction Sites

![Construction noise](https://github.com/alizargham10/DesignDrivenProject-ali-omar/blob/main/media/csm_PR019-standard-construction-safety_843b927ee9.jpg)
*Figure 1*

## Table of Contents
1. [Introduction](#introduction)
2. [Installations](#installations)
   1. [Pre-requisites](#pre-requisites)
   2. [Sensor Node Free App](#sensor-node-free-app)
   3. [Node-Red](#node-red)
3. [Methodology](#methodology)
   1. [Technical Background](#technical-background)
   2. [Plotting Graphs](#plotting-graphs)
   3. [GPS Noise Tracking](#gps-noise-tracking)
   4. [Construction Noise Management](#construction-noise-management)
4. [Functionality](#functionality)
5. [Testing](#testing)
6. [References](#references)

## 1. Introduction
The aim of this project is real-time monitoring of noise levels at a construction site for improved implementation of administrative control methods. The exposure to high noise levels has short- and long-term effects on the physical and mental well-being of both the workers and the residents within the vicinity of construction sites. The microphone of the smartphone has been used as a noise sensor, while its GPS is used to locate the workers exposed to the noise in-situ, and eventually Noise Perimeter Zone (NPZ) can be generated. The data is then streamed live on remotely accessible digital dashboard using the MQTT protocol. This noise data can be analysed to plan work activities in a way which will reduce the worker's frequent exposure to high noise levels. This IoT project shall provide noise real-time data with generated maps and automated notifications (SMS) to the user in such ease and economy yet with relatively adequate precision and reliability.

## 2. Installations
### 2.1 Pre-requisites
1. Node Sensor Free android app.
2. Node-Red Visual programming.

### 2.1.1 Sensor Node Free App
Node sensor free is an android app which allows to convert smartphone into a sensor node for wireless sensor network. Sensor node makes use of smartphone's amazing sensors and streams them to a personal computer in real time through MQTT protocol.

**Requirements**
1. An android phone with android 5.0 or above.
2. Access to location (GPS precise location), storage and microphone.
3. Network connection.

### 2.1.2 Node-Red
Node-Red is free, JavaScript-based server and web GUI for wiring together hardware devices.

**Requirements**
1. Operating system i.e. Windows, macOS or Raspberry pi 3 or 4.
2. Network connection.

**Step 1. Install Node.js**
Download the latest 14.x LTS version of Node.js from the official [Node.js Home page](https://nodejs.org/en/)

Once installed, open a command prompt and run the following command to ensure Node.js and npm are installed correctly.

**Step 2. Install Node-Red**
Installing Node-RED as a global module adds the command node-red to your system path. Execute the following at the command prompt:
npm install -g --unsafe-perm node-red

**Step 3. Run Node-Red**
Once installed, the simple way to run Node-RED is to use the node-red command in a command prompt. If you have installed Node-RED as a global npm package, you can use the node-red command:
C:>node-red
**Step 4. Manage Palette**
After running node-red go to the User Settings and choose Palette to install following nodes required to run this Repo:
1. node-red-dashboard
2. node-red-contrib-chart-image
3. node-red-contrib-web-worldmap
4. node-red-node-sqlite
5. node-red-node-twilio

**Step 5. Node-Red Dashboard**
GUI for real time monitoring can be accessed from the Dashboard

click on the triangle icon then click on the dashboard as shown in the image below

In dashboard window click on the arrow button as highlighted in the image below 

A new tab will open in the browser. Now you can monitor the real-time noise data.
Maps can be accessed from menu 
1. Click on the menu icon at the top left corner of the screen 
2. Click on the GPS Tracker 

## 3. Methodology


### 3.1 Technical Background
The Laborers’ Health and Safety Fund of North America classifies solutions to construction noise into three main control methods. Engineering Control refers to the equipment or the work area to make it quieter. Examples of engineering controls are: substituting existing equipment with quieter equipment; retro-fitting existing equipment with damping materials, mufflers, or enclosures; erecting barriers; and maintenance. Personal Protective Equipment (PPE) is the second noise control solution. Earplugs are the typical PPE given to workers to reduce their exposure to noise. Earplugs are the control of last resort and should only be provided when other means of noise controls are infeasible. As a general rule, workers should be using earplugs whenever they are exposed to noise levels of 85 dB (A) or when they have to shout in order to communicate. Last but not least are the administrative control methods. These are management decisions on work activities, work rotation and work load to reduce workers’ exposure to high noise levels. Typical management decisions that reduce worker exposures to noise are: moving workers away from the noise source; restricting access to areas; rotating workers performing noisy tasks; and shutting down noisy equipment when not needed.
It is obvious that the traditional approach is to attack the source of the noise through redesign or modification of the machinery, equipment or surrounding work area. Engineering controls, when feasible and properly applied, is the approach of choice. However, the cost and implementation process are considerations. Therefore, integrating IoT concepts and automation advancements to the administrative control seems most convenient solution to the construction noise problem.

### 3.2 Plotting Graphs
Sound Level Meters (SLM) measures the sound level in an environment by calculating the frequency weighted pressure of the sound waves which travel through the air from its source. The units of the sound intensity calculated are called decibels. Electronic circuits within the sound meter amplify and filter the sound picked up from the microphone. The voltage ratio of the sound pressure is then calculated and displayed in dB. The data collected from the microphone is then streamed to the Node-Red through MQTT and is imported to the graphing packages which creates graphs like dB vs. Time, Intensity vs. Time, Voltage Ratio vs. Time, etc. These graphs help us analyze the intensity of sound at a construction site and are quite handy in decision-making to control the noise at construction site.

### 3.3 GPS Noise Tracking
On this stage of the project we make use of the latitude and longitude of the smartphone’s location. For the sake of convenience, MQTT is being used as the message protocol to transmit the noise data from the mobile sensor nodes to the broker server. The message broker was established in Node-Red. A topic has been created for each node in the system. This will make it easy to manage messages in the Node-Red. Each node is assigned a unique ID. This ID is stored in the database of the server along with the coordinate (latitude and longitude) of the smartphone location, using SQLite. This data is then visualized on Node-Red Dashboard in real time. We have slightly modified the basic GPS tracking flows in such a way that it allows the GPS data to be loaded into the Node-Red in real-time. An MQTT input node of Node-Red can be used to import the GPS data to Node-Red in real-time. This data is then sent to the Web-WorldMap to visualize the location of the mobile sensor nodes in the map. This real-time importing of the location of the nodes through MQTT saves a lot of time and energy, which is otherwise lost in traditional importing.

### 3.4 Construction Noise Management
For the past many years, a relationship between exposure to noise and noise-induced hearing loss has been understood. It is obvious that the greater the exposure the greater the chance of hearing loss. Several schemes have been developed to express noise exposure as a single number that characterizes the noise exposure. All of these schemes, of course, take into account the intensity of the noise, but they also factor in the duration of exposure, a factor that has been determined to be of great importance. One common scheme is the exchange rate. Exchange rates of 3, 4 and 5 dB are most commonly used. There are others. An example of a dose-exchange rate is 5 dB. It means that for every increase of 5 dB in the intensity of the noise, the duration of exposure is cut in half.

## 4. Functionality
The functionality of the system is more clear when understood in context of the nature of the user, i.e. the administrative manager of the construction site. The dashboard which is shown above is the most important part of the system. The manager of the site can easily see the dashboard of the noise data. The dashboard shows us the real-time data of the noise levels, and if you click on the map of dashboard then you can see the real-time location of the workers on the site. This GPS real-time location is transmitted to the Node-Red in real-time using MQTT. The map of dashboard is shown above. The red dots represent the location of the mobile sensor nodes in real time. This real-time location of the workers can also be seen by clicking on the menu icon on the top-left corner of the screen. After clicking on the icon, click on the "GPS Tracker" as shown in the figure above. 

## 5. Testing
The system was tested several times. Different spots at the construction site were selected for the experiments. The data that we collected from the system was actually real. The initial requirement for this test was at least 5 mobile sensor nodes to cover a single spot at the construction site. The coverage area was about 100 feet. Therefore, if we take each mobile sensor node's coverage area to be 40 feet, the 5 mobile sensor nodes had to be located within a 100 feet area. This distribution gave us overlapping of 40 feet area for each mobile sensor node. Therefore, even if there were a spot where the workers stood 100 feet away from the mobile sensor node, the remaining 4 nodes would still cover that spot. The test results were quite overwhelming. The system was successful to cover a huge area at the construction site and to send real-time location to the server. This real-time location was then visualized on the map of Node-Red.

## 6. References
1. ABC, Inc. (2020). Construction noise and its effects on laborers' health. [Online]. Available: [https://www.abccolumbia.com/2020/08/05/construction-noise-and-its-effects-on-laborers-health/](https://www.abccolumbia.com/2020/08/05/construction-noise-and-its-effects-on-laborers-health/)
2. Alkass, S., Cusack, P., Hume, K., & Summers, V. (2016). Sleep disturbance and hospitalisation among residents near a cement plant. Environmental Research, 147, 276-284.
3. Azar, A., & Zohry, K. (2014). Smart helmet. IJARCET, 3(5), 3722-3725.
4. Babisch, W. (2011). Cardiovascular effects of noise. Noise & health, 13(52), 201-204.
5. Gajalakshmi, V., & Kanimozhi, K. (2013). A study on environmental impact assessment of Madukkarai limestone mine, Coimbatore, Tamil Nadu, India. World journal of science and technology, 3(12), 15-23.
6. Ghamry, I. A. (2013). Investigating smart helmet as an automated safety device for construction workers. Ain Shams Engineering Journal, 4(3), 545-557.
7. Hilal, A., & Mourad, A. H. (2019). IoT based monitoring and controlling system for buildings and smart cities. IJCSNS, 19(5), 32-37.
8. ISO 9612:2009 Acoustics – Determination of occupational noise exposure – Engineering method.
9. Khaing, Z. Z., & Zaw, Z. L. (2019). Smart helmet for construction safety and health monitoring. In 5th International Conference on Mechanical Engineering Research (ICMER 2019) (pp. 1-8).
10. Lam, K. C., Cheung, T. Y., & Tang, S. L. (2013). An evaluation of real-time noise dosimeter to detect construction noise exposure. Automation in Construction, 35, 342-347.
11. Neitzel, R., & Seixas, N. (2005). The effectiveness of hearing protection among construction workers. Journal of Occupational and Environmental Hygiene, 2(4), 227-238.
12. Thind, H. S., Kumar, R., & Brar, G. S. (2014). An in-depth analysis of the noise pollution problem in the Punjab (India) state. Environmental Monitoring and Assessment, 186(9), 5831-5840.
13. Thind, H. S., Kumar, R., & Brar, G. S. (2014). An in-depth analysis of the noise pollution problem in the Punjab (India) state. Environmental Monitoring and Assessment, 186(9), 5831-5840.
14. Tompsett, S. L., & Firth, S. K. (2019). Evaluation of smartphone-based sound level meter applications for occupational noise assessments. Applied Acoustics, 150, 124-132.
