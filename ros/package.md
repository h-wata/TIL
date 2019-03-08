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
