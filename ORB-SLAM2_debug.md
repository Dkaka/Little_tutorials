


# Debug ORB-SLAM2 in IDE (Qt Creater)
**I assume that you have got all the dependecies for ORB-SLAM2 installed already,or you have followed  [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 ) for all prerequisites**.  
**The follwing procedures will. create a fresh ORB-SLAM2 Debug project in Qt**  
##Procedures
1. Download Qt from  [Qt-download-linux64-open source](qt-unified-linux-x64-3.0.4-online)  
Note: if your installation file(*.run) can't be excuted. (Mine doesn't work...), you can make it excutatble and excute it using following commands in terminal:
enter `cd /home/user/Downloads`  
enter `chmod +x some-app.run`  
enter `./some-app.run`  
Please refer to [ask ubuntu-How do I install .run files?](https://askubuntu.com/questions/18747/how-do-i-install-run-files)
2. Import project in Qt creator:  
	* 	In Qt Creator:  
	File-> New file or project->Import Project->git clone
	* 	Repository: https://github.com/raulmur/ORB_SLAM2  
	* 	Feel free to set your own path and directry name.e.g. : **ORBSLAM2DEBUG**  
	
2. Built g2o and DBoW2 before ORB-SLAM2 as those are dependencies:  
 	* Modify the *install.sh* file in your **ORBSLAM2DEBUG**  directry, comment out the last paragraph for building ORB-SLAM2. A copy of modified install.sh is provided along with this tutorial.  
	*  	Use `chmod +x build.sh` and `./build.sh` to build g2o and DBoW2.  
 	please refer to **3. Building ORB-SLAM2 library and examples** of [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 )
3. Build the projects in debug mode: 	
	* 	 In Qt Creator:  
	 		Build-> Open Build and Run selector: change selection in '*Build*' to '**Debug**'  
	* 	 Right click on projects -> build project 

5.  Run TUM dataset:
	* 	 I downloaded TUM **rgbd-fr2-xyz** dataset in the '*Download*' folder, this could influnce the following command line arguments
	* 	 Select ORB_SLAM2 project, and click on Projects pannel on the left of the screen:
	* 	In '*Build and run*'->run, now '*run settings*' shall be shown
	* 	change *'run configuration'* to **rgbd_tum**
	* 	change '*command line arguments*' to  `./Examples/RGB-D/rgbd_tum Vocabulary/ORBvoc.txt Examples/RGB-D/TUMX.yaml PATH_TO_SEQUENCE_FOLDER ASSOCIATIONS_FILE`  
	* 	Mine is `Vocabulary/ORBvoc.txt Examples/RGB-D/TUM2.yaml ~/Downloads/rgbd_dataset_freiburg2_xyz Examples/RGB-D/associations/fr2_xyz.txt`  
	please refer to **6. RGB-D Example** of [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 )
	* 	Change '*Working Direcory*' to the directory of ORBSLAM2.  
	* The following is the capture of my settings: 
![Run_settings](\Run_settings.png)

6. Now the 'RUN' and 'RUN IN DEBUG' bottons on the bottom left of screen should work    
**I followed [debug the code #77](https://github.com/raulmur/ORB_SLAM/issues/77) to do this.**
## Virtual machine issues
I came across this error when I am using Ubuntu(16.04) under Parallel (13.2) virtual machine on my Mac:
`terminate called after throwing an instance of 'std::runtime_error' what(): Pangolin X11: Unable to retrieve framebuffer options`
Just turn off 3D acceleration to solve this :[Pangolin X11: Unable to retrieve framebuffer options #74](https://github.com/stevenlovegrove/Pangolin/issues/74#issuecomment-178248684)
