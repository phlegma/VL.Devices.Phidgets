# VL.Devices.Phidgets
VL Integration for Phidgets
Try with the visual live-programming environment for .NET Download: http://visualprogramming.net 

## Installing 

To use the latest stable version:
1. Go to Gamma's Quad menu > Manage Nugets > Commandline and type:  
`nuget install VL.Devices.Phidgets -pre`
2. Press Enter and wait the ending of the installation process
3. Open the Help Menu (F1). Open the tap "Learn". Search for the pack "Devices.Phidgets"

## Contributing
Feel free to clone the repro an add missing Phidget devices. Also you can make a pull request or send me the patch over any digital communication cannel. 

### How to add missing Phidgets Nodes
There are a huge List of Phidget devices and classes. So there was no time to add all devices to the package or to do it via factory pattern etc. ([Phidget API](https://www.phidgets.com/?view=api))  
The important operation are bundles via processes, so it is easy to add new nodes to the package. 
1. Clone the repository and open the VL.Devices.Phidgets.vl document
2. Open the definition patch (Shift+Alt+A)
3. Add a process node with the name of the Phidget class you want to add like "Accelerometer"  

![vvvv gamma definition patch](./assets/DefintionPatch.png)  

4. Open the process "Accelerometer" and add the "Create" operation of the Accelerometer class

![Create Accelerometer class](./assets/AssignCreate.png)  

5. Assign the node to the "Create" operation via context menu

![Assign to Create Operation](./assets/AssignCreate.png)

6. Store the instance of the class in a pad with the name of the class.  

![Accelerometer Pad](./assets/AccelerometerPad.png)

8. Every class extends the Phidget class to handle basic operation like open and close. To add these basic phidget operation to the accelerometer, we add the predefined Phidget process and extend the Inputs and Outputs.  

![Phidget Base Process](./assets/phidgetProcesss.png)

9. If necessary you can add the operation for "Hub" or "Sensor" process with their predefined operation.  

![Hub and Sensor](./assets/HubSensor.png)

10. Every Sensor comes with its own Event and EventArgs to send data from device to the computer. This has to implemented by its own, but always follows the same structure. 

![Accelerometer](./assets/AccelerometerEvent.png)  

11. There are class related set operations for the devices. Add the set operations to the patch. The operation should only be applied it if the phidget is attached and the pin is changed.

![Set operations](./assets/setOperations.png)

12. Create a help patch into the [help/Phidgets](./help/Phidgets) folder with the scheme "HowTo [ClassName]" and add your node and test and set the default pin settings so that everything works like expected.  

## Licencing
Licensed under the Apache License, Version 2.0 (the "License"). You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0  
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License. 

