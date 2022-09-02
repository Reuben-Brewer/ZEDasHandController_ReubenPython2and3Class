#########################################################

ZEDasHandController_ReubenPython2and3Class

Wrapper (including ability to hook to Tkinter GUI) to read 6-DOF pose data from StereoLabs ZED stereo camera (with integrated IMU).
This code is intended to allow the ZED camera to be used as a hand-controller where the user grips the ZED (without occluding the cameras).
Under the hood, we're calling the ZED API's "Positional Tracking" module, which uses visuoinertial tracking (SLAM + IMU).

Verified working with ZED-mini (https://www.stereolabs.com/zed-2/) and ZED2 (https://www.stereolabs.com/zed-mini/).

Reuben Brewer, Ph.D.

reuben.brewer@gmail.com

www.reubotics.com

Apache 2 License

Software Revision D, 08/29/2022

Verified working on: 
Python 3.8 on Windows 10 64-bit.
*In Python 2.7, we fail on from scipy.spatial.transform import Rotation .from_matrix*

Functional definition: long/baseline-axis is the line that starts at the left camera and extends to the right camera.
With the user's right hand grasping the ZED2 camera along its long/baseline axis and the tripod mounting hole pointing to the user's right
(also the long/baseline-axis pointing up):
X axis: Right (to the user's right)
Y axis: Foward (along camera axes)
Z: Up (along long/baseline-axis)

It's the same coordinate system for the ZED-mini (held vertically in hand with the USB-C cable pointing downward).

############################
The ZED-mini's USB-C cable is very finicky.
1. The USB-C plug on the camera *only works when the arrows on the cable point towards the camera's blue status-indicator LED*.
2. It may not work plugging the camera's cable into a USB hub (there is both USB2.0 and 3.0 data, and that complexity is lost on most hubs).
For instance, this hub did not work: Anker AK-A7505112 7-Port USB 3.0 Data Hub.
3. The shorter stock cable that came with the ZED-mini worked when plugged directly into the USB-3.0 port of a laptop, but the longer stock cable did NOT.
4. The shorter stock cable worked WITH a 6ft USB3.0 extension cable (brand unknown), plugged directly into a laptop's USB 3.0 port.
5. The ZED-mini will show up as "ZED-M" under "Cameras" within Window's Device Manager.
############################

############################
1.The ZED-2 WILL work when plugged into a USB3.0 hub.
############################

############################
In one instance, the ZED-mini suddenly started giving strange data.
Upon examination in "ZED Sensor Viewer", it was obvious that the orientation was flipping 180deg constantly.
The following line was issued in a command terminal to recalibrate the IMU and fix the issue:

"C:\Program Files (x86)\ZED SDK\tools\ZED Calibration.exe" --cimu

############################

#########################################################

######################################################### Python module installation instructions, all OS's

ZEDminiAsHandController_ReubenPython2and3Class, ListOfModuleDependencies: ['future.builtins', 'LowPassFilter_ReubenPython2and3Class', 'numpy', 'pyzed.sl', 'scipy.spatial.transform']
ZEDminiAsHandController_ReubenPython2and3Class, ListOfModuleDependencies_TestProgram: ['MyPlotterPureTkinterStandAloneProcess_ReubenPython2and3Class', 'MyPrint_ReubenPython2and3Class']
ZEDminiAsHandController_ReubenPython2and3Class, ListOfModuleDependencies_NestedLayers: ['future.builtins', 'numpy', 'pexpect', 'psutil']
ZEDminiAsHandController_ReubenPython2and3Class, ListOfModuleDependencies_All: ['future.builtins', 'LowPassFilter_ReubenPython2and3Class', 'MyPlotterPureTkinterStandAloneProcess_ReubenPython2and3Class', 'MyPrint_ReubenPython2and3Class', 'numpy', 'pexpect', 'psutil', 'pyzed.sl', 'scipy.spatial.transform']

#########################################################

######################################################### Library/driver installation instructions, Windows and Ubuntu (ZED doesn't run on Raspberry Pi or Mac)

https://www.stereolabs.com/docs/installation/windows/

https://www.stereolabs.com/docs/installation/linux/

#########################################################
