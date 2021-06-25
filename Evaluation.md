### Evaluation

After estimating the camera trajectory of the Kinect and saving it to a file, we need to evaluate the error in the estimated trajectory by comparing it with the ground-truth. There are different error metrics. Two prominent methods is the **absolute trajectory error (ATE)** and the **relative pose error (RPE)**. The ATE is well-suited for measuring the performance of visual SLAM systems. In contrast, the RPE is well-suited for measuring the drift of a visual odometry system, for example the drift per second.

Both trajectories have to be stored in a **text file** (format: 'timestamp tx ty tz qx qy qz qw', [more information](https://vision.in.tum.de/data/datasets/rgbd-dataset/file_formats)). For comparison, we offer a set of [trajectories](https://vision.in.tum.de/lib/exe/fetch.php?tok=78909d&media=https%3A%2F%2Fsvncvpr.in.tum.de%2Fcvpr-ros-pkg%2Ftrunk%2Frgbd_benchmark%2Frgbd_benchmark_tools%2Fdata%2Frgbdslam) from [RGBD-SLAM](http://www.ros.org/wiki/rgbdslam_electric/evaluation).

- **tx ty tz** (3 floats) give the position of the optical center of the color camera with respect to the world origin as defined by the motion capture system.
- **qx qy qz qw** (4 floats) give the orientation of the optical center of the color camera in form of a unit quaternion with respect to the world origin as defined by the motion capture system.

### ABSOLUTE TRAJECTORY ERROR (ATE)

The absolute trajectory error directly measures the **difference** between **points of the true and the estimated trajectory.** As a pre-processing step, we associate the estimated poses with ground truth poses using the timestamps. Based on this association, we align the true and the estimated trajectory using singular value decomposition. Finally, we compute the difference between each pair of poses, and output the mean/median/standard deviation of these differences. Optionally, the script can plot both trajectories to a png or pdf file.

> [Detail in website](https://vision.in.tum.de/data/datasets/rgbd-dataset/tools#evaluation)

# [Dataset Download](https://vision.in.tum.de/data/datasets/rgbd-dataset/download)

We recommend that you use the **'xyz'** series for your first experiments. The motion is relatively small, and only a small volume on an office desk is covered. Once this works, you might want to try the **'desk'** dataset, which covers four tables and contains several loop closures.

