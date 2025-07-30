# MazeSimul


**MazeSimul** is an **autonomous maze navigation project using TurtleBot3 and the [Webots](https://cyberbotics.com/) simulator.**<br>
The main objective is to enable the robot to follow the left wall in a maze environment and navigate without collisions.
Both rule-based and PID controllers were first implemented and tested in the Webots simulator.
Based on the collected data, a machine learning model was trained and then deployed to a real TurtleBot3 using ROS2.

📄 [Visit our notion for more detail!](https://sparkly-onion-be7.notion.site/MazeSimul-2378e2ec5d7a8096aeaae80c80a3efa6?source=copy_link)

### Members
<img src='./assets/members.jpg' width=580><br><br>

### Tech Stack
<img src='./assets/members.jpg' width=580><br><br>

## How to Run

To deploy and run the wall-following controller on the actual TurtleBot3 hardware, follow the steps below :<br><br>
**✅ Step 1: Configure Wi-Fi on Raspberry Pi**
1. Connect your laptop to the Raspberry Pi via Ethernet cable.
2. SSH into the Raspberry Pi using :
   ```
   ssh simulsimul@192.168.0.49
   ```
3. Edit the Wi-Fi credentials in the following files :
   - wpa_supplicant.conf
   - 50-cloud-init.yaml

4. After editing, reboot the Pi :
   ```
   sudo reboot
   ```
5. Once restarted, apply the network settings :
   ```
   sudo netplan apply
   ip a
   ```
6. Check that the wlan interface is connected to Wi-Fi and note the assigned IP address.
   (It may take some time for the connection to be established.)

**✅ Step 2: Connect via Wi-Fi**
1. Disconnect the Ethernet cable.
2. Ensure both the laptop and TurtleBot3 are connected to the same Wi-Fi network.
3. SSH into the Raspberry Pi again using the new IP :
   ```
   ssh simulsimul@<copied IP address>
   ```

**✅ Step 3: Pull the Docker Image**
1. Pull the docker image :
   (In most cases, the system is already configured to automatically pull the latest image on boot.)
   ```
   docker pull ybkim4053/simulsimul:latest
   ```
2. Check if the image is available :
   ```
   docker images
   ```
**✅ Step 4: Launch the Docker Container**
1. Launch the docker container
   ```
   sudo systemctl start turtlebot-auto
   ```
- Check if the container is running :
  ```
   docker ps
   ```
- If it's not running, restart the service :
  ```
   sudo systemctl restart turtlebot-auto
   ```

**✅ Step 5: Monitor Logs and Confirm Execution**
1. Display the runtime logs and allow you to verify that TurtleBot3 is operating correctly.
   ```
   sudo docker logs turtlebot-auto -f
   ```

   
