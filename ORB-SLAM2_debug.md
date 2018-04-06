Debug ORB-SLAM2 in IDE (Qt Creater)

**I had ORB-SLAM2 started in debug mode using the following procedures but the programme crashed midway after loading the vacabularys.... not sure why..**

1. Download Qt from  [Qt-download-linux64-open source](qt-unified-linux-x64-3.0.4-online)  
Note: if your installation file(*.run) can't be excuted. (Mine doesn't work...), you can make it excutatble and excute it using following commands in terminal:
enter `cd /home/user/Downloads`  
enter `chmod +x some-app.run`  
enter `./some-app.run`  
Please refer to [ask ubuntu-How do I install .run files?](https://askubuntu.com/questions/18747/how-do-i-install-run-files)
2. Import project in Qt creator:
	1. In Qt Creator:
	File-> New file or project->Import Project->git clone
	Repository: https://github.com/raulmur/ORB_SLAM2  
	Feel free to set your own path and directry name.  
	2. Once git clone finishes, import g2o and DBoW2 as projects as you need to compile them before compile ORB-SLAM2:  

	File-> Open file or project
	Choose the '*Thirdparty*' folder under your **ORBSLAM2** directory. 
	open the '*CMakeList*' file in '*g2o*' and  '*DBoW2*' respectively to import them as projects
	
3. Build the projects in debug mode:
	1. In Qt Creator:
		Build-> Open Build and Run selector: change selection in '*Build*' to '**Debug**' for all three projects
	2. I built g2o and DBoW2 before ORB-SLAM2 as those are dependencies
	3. Right click on projects -> set as active project and Build-> build project '***'
4. Uncompress the vocabulary file in 'YOUR-ORB-SLAM2-FOLDER*/Vocabulary*'
5.  Run TUM dataset:
	1. I downloaded TUM dataset in the '*Download*' folder, this could influnce the following command line arguments
	2. Select ORB_SLAM2 project, and click on Projects pannel on the left of the screen:
	3. In '*Build and run*'->run, now '*run settings*' shall be shown
	4. change *'run configuration'* to **rgbd_tum**
	5. change '*command line arguments*' to  `./Examples/RGB-D/rgbd_tum Vocabulary/ORBvoc.txt Examples/RGB-D/TUMX.yaml PATH_TO_SEQUENCE_FOLDER ASSOCIATIONS_FILE`
	Mine is `Vocabulary/ORBvoc.txt Examples/Monocular/TUM2.yaml ~/Downloads/rgbd_dataset_freiburg2_xyz Examples/RGB-D/associations/fr2_xyz.txt`
	please refer to **6. RGB-D Example** of [GitHub - raulmur/ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2 )
	6. Change '*Working Direcory*' to the directory of ORBSLAM2.  
The following is the capture of my settings: 
![Run_settings](https://raw.githubusercontent.com/Dkaka/Little_tutorials/master/Run_settings.png)

6. Now the 'RUN' and 'RUN IN DEBUG' bottons on the bottom left of screen should work    
**I followed [debug the code #77](https://github.com/raulmur/ORB_SLAM/issues/77) to do this.**
