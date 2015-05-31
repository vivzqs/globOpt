RAPter
=======

RAPter provides a set of tools to generate, segment, approximate, and visualize 2D and 3D point clouds with ground truth. It also comes with a set of quantitative and qualitative tests to evaluate the approximation results regarding the ground truth.
The different modules are:
* inputGen: to generate 2D point clouds and ground truth abstraction from svg files. It provides different samplers to convert svg primitives to point clouds and stackable noise kernels (bias, random noise with uniform and normal distribution).
* visualization: based on PCL viewer, support both 2D and 3D point clouds and inter-primitive relations.
* RAPter: the core of the project, a new approach to approximate scenes with primitives supported by global relations.

##Dependencies
* 3rd Party:
** CoinBonmin (optimisation)
** libfbi (fast box intersection)
All dependencies are assumed to be available in a workspace folder and a `3rdparty` subdirectory.

RAPter also requires OpenCV and PointCloudLibrary, and we recommend to use respectively the last stable release and the development branch for these packages (tested with Ubuntu 14.04 and Debian Testing).

Ubuntu packages: python-pygraphviz

###CoinBonmin
First, download Bonmin in `${WORKSPACE}/3rdparty`:
```
svn co https://projects.coin-or.org/svn/Bonmin/stable/1.5 CoinBonmin-stable
```
Then:
* install the following packages (Debian/Ubuntu): `liblapack-dev libblas-dev fortran-compiler`.
* install 3rd party solver using the script `path/to/Bonmin/ThirdParty/Mumps/get.Mumps`.
* Compile and install:
```
mkdir build
cd build
../configure -C
make
make -install
```

###libfbi
Download in `${WORKSPACE}/3rdparty` from [Github](https://github.com/mkirchner/libfbi.git).
No installation required.

##Compilation
###RAPter
Once all the dependencies are satisfied, you can build RAPter. By default, dependencies are expected to be in `/home:${USER}/workspace/` (you may need to edit CMakelist.txt to change that behaviour). 
```
mkdir build
cd build
cmake ..
make
```

###InputGen
Just compile using cmake like usual.