# FormulaAssignement
At the start i downloaded FSDS Asset and cloned the repo.
i installed the modules from requirements.txt and tried to run autonomous_example.py, it woudlnt let me because of problems with backports ssl_match_hostname so i had to reinstall it.
then i run the file again and got this error WARNING:tornado.general:Connect error on fd XXX: WSAECONNREFUSED. so i understand that somthing was refusing connection. i opend the simulator itself and tried to run it again.
now i got this error msgpackrpc.error.RPCError: rpclib: function 'getLidarData' (called with 2 arg(s)) threw an exception. The exception contained this information: No lidar with name Lidar exist on vehicle. so i understand that it connected and isnt recognizing entity called 'Lidar'. i changed the settings.json in the simulator itself and now everytinh seems to work and the vehicles drives itself.
![image](https://github.com/user-attachments/assets/a198c87c-75ae-43b7-b32a-4dc542351bbf)

now i added a new camera without changing it position from the camera_color_png.py and this is the image i got
![example](https://github.com/user-attachments/assets/8ca7f901-906f-4b0b-9cf1-5bf5a00eb9b8)
at this point in time my settings.json looks like this:
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
