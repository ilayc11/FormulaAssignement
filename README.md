# FormulaAssignement
At the start, I downloaded the FSDS Asset and cloned the repository. I installed the modules from requirements.txt and tried to run autonomous_example.py, but it wouldn't let me because of problems with backports.ssl_match_hostname, so I had to reinstall it.
Then I ran the file again and got this:


```python
WARNING:tornado.general:Connect error on fd XXX: WSAECONNREFUSED.
```
 So I understood that something was refusing the connection. I opened the simulator itself and tried to run it again. 
 Now I got this:


```python
msgpackrpc.error.RPCError: rpclib: function 'getLidarData' (called with 2 arg(s)) threw an exception. The exception contained this information: No lidar with name Lidar exist on vehicle.
```
I realized that it connected but wasn't recognizing an entity called 'Lidar'. I changed the settings.json in the simulator itself, and now everything seems to work, and the vehicle drives itself.


![image](https://github.com/user-attachments/assets/a198c87c-75ae-43b7-b32a-4dc542351bbf)

Next, I added a new camera without changing its position from the camera_color_png.py, and this is the image I got:

![example](https://github.com/user-attachments/assets/8ca7f901-906f-4b0b-9cf1-5bf5a00eb9b8)

At this point, my settings.json looks like this:


```json
{
  "SettingsVersion": 1.2,
  "Vehicles": {
    "FSCar": {
      "DefaultVehicleState": "",
      "EnableCollisionPassthrogh": false,
      "EnableCollisions": true,
      "AllowAPIAlways": true,
      "RC":{
          "RemoteControlID": -1
      },
      "Sensors": {
        "Gps" : {
          "SensorType": 3,
          "Enabled": true
        },
        "Lidar": {
          "SensorType": 6,
          "Enabled": true,
          "X": 1.3, "Y": 0, "Z": 0.1,
          "Roll": 0, "Pitch": 0, "Yaw" : 0,
          "NumberOfLasers": 1,
          "PointsPerScan": 500,
          "VerticalFOVUpper": 0,
          "VerticalFOVLower": 0,
          "HorizontalFOVStart": -90,
          "HorizontalFOVEnd": 90,
          "RotationsPerSecond": 10,
          "DrawDebugPoints": true
        }
      },
      "Cameras": {
        "examplecam": {
    "CaptureSettings": [
    {
        "ImageType": 0,
        "Width": 785,
        "Height": 785,
        "FOV_Degrees": 90
    }
    ],
    "X": 1.0,
    "Y": 0.06,
    "Z": -1.20,
    "Pitch": 0.0,
    "Roll": 0.0,
    "Yaw": 0
}
      },
      "X": 0, "Y": 0, "Z": 0,
      "Pitch": 0, "Roll": 0, "Yaw": 0
    }
  }
}
```
I changed the "Z" value of the camera for a better position.

After that, I downloaded the OpenCV module for Python, saw how the camera_color_png.py file works, and added the relevant lines from it to the autonomous_example.py. Then I added the relevant commands from the OpenCV module for reading images, and now we get live feedback (by creating and reading a PNG file in a loop).


![Recording2024-11-27121530-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/6ce11d04-e6f3-4088-8ae8-ac3f1478c0c0)


