# FormulaAssignement
At the start i downloaded FSDS Asset and cloned the repo.
i installed the modules from requirements.txt and tried to run autonomous_example.py, it woudlnt let me because of problems with backports ssl_match_hostname so i had to reinstall it.
then i run the file again and got this error WARNING:tornado.general:Connect error on fd XXX: WSAECONNREFUSED. so i understand that somthing was refusing connection. i opend the simulator itself and tried to run it again.
now i got this error msgpackrpc.error.RPCError: rpclib: function 'getLidarData' (called with 2 arg(s)) threw an exception. The exception contained this information: No lidar with name Lidar exist on vehicle. so i understand that it connected and isnt recognizing entity called 'Lidar'. i changed the settings.json in the simulator itself and now everytinh seems to work and the vehicles drives itself.
![image](https://github.com/user-attachments/assets/a198c87c-75ae-43b7-b32a-4dc542351bbf)
