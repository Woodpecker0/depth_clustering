# Depth Clustering #

[![Build Status][travis-img]][travis-link]
[![Codacy Badge][codacy-img]][codacy-link]
[![Coverage Status][coveralls-img]][coveralls-link]

This is a fast and robust algorithm to segment point clouds taken with
Velodyne sensor into objects. It works with all available Velodyne sensors,
i.e. 16, 32 and 64 beam ones.

## How to build? ##
### Prerequisites ###
- Catkin.
- OpenCV: `sudo apt-get install libopencv-dev`
- QGLViewer and Qt4:
    + `sudo apt-get install libqglviewer-dev`
    + `sudo apt-get install libqt4-dev`
- (optional) PCL - needed for saving clouds node
- (optional) ROS - needed for subscribing to topics

### Build script  ###
This is a catkin package. So we assume that the code is in a catkin workspace
and CMake knows about the existence of Catkin. Then you can build it from the
project folder:

- `mkdir build`
- `cd build`
- `cmake ..`
- `make -j4`
- (optional) `ctest -VV`

It can also be built with `catkin_tools` if the code is inside catkin
workspace:
- `catkin build depth_clustering`

P.S. in case you don't use `catking build` you [should][catkin_tools_docs].
Install it by `sudo pip install catkin_tools`.

## How to run? ##
See [examples](examples/). There are ROS nodes as well as standalone
binaries. Examples include showing axis oriented bounding boxes around found
objects (these start with `show_objects_` prefix) as well as a node to save all
segments to disk. The examples should be easy to tweak for your needs.

## Run on real world data ##
Go to folder with binaries:
```
cd <path_to_project>/build/devel/lib/depth_clustering
```

#### Frank Moosman Velodyne SLAM - Dataset ####
Get the data:
```
mkdir data/; wget http://www.mrt.kit.edu/z/publ/download/velodyneslam/data/scenario1.zip -O data/moosman.zip; unzip data/moosman.zip -d data/; rm data/moosman.zip
```

Run a binary to show detected objects:
```
./show_objects_moosman --path data/scenario1/
```

#### Other data ####
There are also examples on how to run the processing on KITTI data and on ROS
input. Follow the `--help` output of each of the examples for more details.

## Documentation ##
You should be able to get Doxygen documentation by running:
```
cd doc/
doxygen Doxyfile.conf
```

## Related publications ##
Please cite related paper if you use this code:

```
@InProceedings{bogoslavskyi16iros,
Title     = {Fast Range Image-Based Segmentation of Sparse 3D Laser Scans for Online Operation},
Author    = {I. Bogoslavskyi and C. Stachniss},
Booktitle = {Proc. of The International Conference on Intelligent Robots and Systems (IROS)},
Year      = {2016},
Url       = {http://www.ipb.uni-bonn.de/pdfs/bogoslavskyi16iros.pdf}
}
```


[travis-img]: https://travis-ci.org/niosus/depth_clustering.svg?branch=github_travis
[travis-link]: https://travis-ci.org/niosus/depth_clustering

[coveralls-img]: https://coveralls.io/repos/github/niosus/depth_clustering/badge.svg?branch=master
[coveralls-link]: https://coveralls.io/github/niosus/depth_clustering?branch=master

[codacy-img]: https://img.shields.io/codacy/grade/6ba7d6f0068944588ecaa5b6cd400c9a.svg
[codacy-link]: https://www.codacy.com/app/zabugr/depth_clustering?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=niosus/depth_clustering&amp;utm_campaign=Badge_Grade

[build-status-img]: https://gitlab.ipb.uni-bonn.de/igor/depth_clustering/badges/master/build.svg
[coverage-img]: https://gitlab.ipb.uni-bonn.de/igor/depth_clustering/badges/master/coverage.svg
[commits-link]: https://gitlab.ipb.uni-bonn.de/igor/depth_clustering/commits/master

[catkin_tools_docs]: https://catkin-tools.readthedocs.io/en/latest/installing.html