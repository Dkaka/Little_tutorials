


# Some useful (I hope) comments for starters like me in the robotics field

**Before carry on the tutorial, I assumed that you have got all the dependencies for ORB-SLAM2 installed already, or you have followed  [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 ) for all prerequisites.**  

**The following procedures will create a fresh ORB-SLAM2 Debug project in Qt.**  

## The comments
1. Before isntalling any open-source packages, always check the dependency requirements. 
  Neither packages that are too new (dpptam requires Ubuntu 14.04 and I couldn't get it running in Ubuntu 16.04) or too old (you name the examples) will get your package running. 
2. RAM size is not usually the issue, until you got a virtual machine
	* 	Clone the ORB_SLAM2 in Qt Creator:  
	`File-> New file or project->Import Project->git clone`
	* 	Repository: https://github.com/raulmur/ORB_SLAM2  
	* 	Feel free to set your *own* path and directory name.e.g. : **ORBSLAM2DEBUG**  
	*	Click on *Configure* when prompted 
	
3. Built *g2o* and *DBoW2* before ORB-SLAM2 as those are dependencies  
 	* Modify the *install.sh* file in your **ORBSLAM2DEBUG**  directory, comment out the last paragraph for building ORB-SLAM2. <br>A copy of modified install.sh is provided along with this tutorial.  
 	<br>
	* Use command `chmod +x build.sh` and `./build.sh` to build g2o and DBoW2.  

    >Details please refer to **3. Building ORB-SLAM2 library and examples** of [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 )
4. Build the project in debug mode	
	* 	 In Qt Creator:  
	 		`Build-> Open Build and Run selector`: change selection in '*Build*' to '*Debug*'  
	* 	 Right click on `projects -> build project `

5.  Download and execute TUM dataset
	1. Downloaded TUM [rgbd-fr2-xyz](https://vision.in.tum.de/data/datasets/rgbd-dataset/download) dataset and extract its contents in the home directory. This dataset could influence the following command line arguments
	   * 	Select ORB_SLAM2 project, and click on Projects pannel on the left of the screen
	   * 	In '*Build and run*'->run, now '*run settings*' shall be shown
	   * 	Set *'run configuration'* to **rgbd_tum**
	   * 	Set '*command line arguments*' to  ` Vocabulary/ORBvoc.txt Examples/RGB-D/TUM2.yaml ~/rgbd_dataset_freiburg2_xyz Examples/RGB-D/associations/fr2_xyz.txt`  
        
            > Details please refer to [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 ) in **6. RGB-D Example** part
        
	   * 	Change '*Working Direcory*' to the directory of ORBSLAM2.  
	   * The following is the capture of my settings: 
![Run_settings](https://raw.githubusercontent.com/Dkaka/Little_tutorials/master/Run_settings.png)

    2. Now the 'RUN' and 'RUN IN DEBUG' bottons on the bottom left of screen should work    

    >**You can follow [debug the code #77](https://github.com/raulmur/ORB_SLAM/issues/77) to do this.**

## Other issues
I came across this error when I am using Ubuntu(16.04) under Parallel (13.2) virtual machine on my Mac:
`terminate called after throwing an instance of 'std::runtime_error' what(): Pangolin X11: Unable to retrieve framebuffer options`
Just turn off 3D acceleration to solve this :[Pangolin X11: Unable to retrieve framebuffer options #74](https://github.com/stevenlovegrove/Pangolin/issues/74#issuecomment-178248684)



