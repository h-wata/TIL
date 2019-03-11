# package指差呼称

### turtlebot_follower
 - [turtlebot_apps](https://github.com/turtlebot/turtlebot_apps)
 - launchフォルダ内のremapがおかしい
   - launchファイル内ではpointsをSubscribeするようになっているが、srcではdepth_image_rectをSubscribeするように変更されている
   - kinect v1をベースに書かれているのでencodingが32FC1でないと正しく認識しない
   - v2で使う場合は[depth_image_proc/convet_metric](http://wiki.ros.org/depth_image_proc)を使ってencodingを変換してから使う
 - min_ max_ x y zはそれぞれROIの設定
 - depth_imageをそのまま使うとノイズによって、実際より近いところをトラッキングしてしまう
 - sd_edgeでedge除去したものをベースにFollowerを行うとある程度認識率が向上した
 - velocity_smootherの角加速度の最大値を上げると追随性が向上した
 - そもそも、人を追っている最中に壁を見ると壁に吸い寄せられる
   - ROIのうち一番近いものに近づいていくため、目の橋で壁を見るとそちらに行きがち
   - 人認識を行ってFollowするパッケージが無いか検討すべきかも

### rtabmap
 - 画像データからvisual odometryを取って、Odomを作成しているよう
 - rtabmap_ros/launch/rtabmap_rgbd.launchのTopic名とOdom名をいじったら汚い地図は作成可能
 - ただし、OdometryF2M.cpp:469::computeTransform() Registration failed: "Not enough inliers 0/20 (matches=0) between -1 and 550 のようなエラーがひっきりなしに出続ける
 - ROS wiki answerをみながら勉強中
   - https://answers.ros.org/question/216337/visual-odometry-low-numbers-of-inlier-viso2fovis/
   - gazebo環境下では特徴点が少ないからか、Visual odomがいまいち?
   - comparison VSlam https://www.researchgate.net/publication/320623436_Comparison_of_ROS-based_Visual_SLAM_methods_in_homogeneous_indoor_environment
   - Odom/Strategyパラメータが怪しい
     - http://wiki.ros.org/rtabmap_ros/Tutorials/Advanced%20Parameter%20Tuning
     - argsの中に記述するとパラメータが変わる
 - 所感
   - 時間がかかるのとGP/GPUは必須（Find objectとかと同様にマッチングをかけながらOdomを取る）OpenCVが重いのでは？
   - 画像だとどうしても視野が狭く、Lidarと比べるとどうしてもマッピングが遅くなる

### 
