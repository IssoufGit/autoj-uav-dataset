## Dataset
This folder contains datatset collected in narrow forest road environment, and rural environment. It includes IMU data (250 Hz), camera data (5Hz), LIDAR data (10 Hz), RTK GNSS data, and other data from the flight controller unit (FCU) of the drone. You can download the dataset [here](to be updated).
- 2024_06_27_rtk_test_forest : contains data to check the RTK accuracy in the forest environment. The vehicle was kept in one place an the position data was recorded for around 15 minutes. Use the provided notebook to see the accuracy. From our analysis, the standard deviation of the x, y, and z positions are all less than $2 cm$.
- rosbag2_2024_06_27-12_43_51 : contains data of long forest road trajectory data.
- rosbag2_2024_06_27-12_59_48 : contains data of our SLAM framework run in real-time in the forest road environment. The estimated state topic is "/estimatedState". The Reference RKT data topic are "/fmu/out/vehicle_global_position" and "/fmu/out/vehicle_odometry". Note that the last topic is the RTK fused with the IMU.
- rosbag2_2024_06_27-13_27_45 : contains data of a long forest road trajectory data.
- rosbag2_2024_06_27-14_29_00 : contains data of a paved road in rural area.
- rosbag2_2024_06_27-14_44_55 : contains data of our SLAM framework run in real-time in a small test track area.
- slam_map: contains the resulting map from the rosbag2_2024_06_27-14_44_55 data. The map is obtained directly after running our real-time slam and calling the service we have implemented to save the map.


##Extrinsic:
lidar2VehicleFrame: [0.05, 0.07, -0.05, 0.0, 0.0, 0.0] #[x, y, z, roll(x), pitch(y), yaw(z)] # This is the LIDAR to IMU Frame extrinsic (IMU FRAME = Vehicle Frame)
imu2VehicleFrame: [0.0, 0.0, 0.0, 0.0, 0.0, 0.0] # IMU initial orientation with respect to navigation frame



##Play bag: 
(Use "ros2 bag info folder_name" to check all the topics available inside a particular bag file) 
The data from the FCU have message types defined in the px4_msgs package. You need to clone and build the package in your workspace in order to read the corresponding data.
```bash
ros2 bag play --read-ahead-queue-size 100 --start-offset 1 rosbag2_2024_06_27-12_43_51 --topics /epson/imu/data /velodyne_points /fmu/out/vehicle_odometry /fmu/out/vehicle_local_position 
```

## Credit:
If you are using these data, please cite our work:

