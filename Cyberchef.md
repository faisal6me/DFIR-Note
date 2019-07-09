
#### In this Tutrail i will show you how to Deofcated A milieous VBS enabded in Doc File 

Start : https://www.hybrid-analysis.com/sample/9a43186e72bde764614b092b55d4dfba00f528c5f0d45e6ccb56dcee8763a845?environmentId=100 

![1](https://user-images.githubusercontent.com/29158503/60865490-d0fdcc80-a22e-11e9-8114-827ce5233897.png)


#### After Downloading the sample let go to Cyberchef to analyze the Malicious cmd.exe command present on Hyperd analysis


![2](https://user-images.githubusercontent.com/29158503/60865489-d0fdcc80-a22e-11e9-8a97-e358694714ee.png)


Now we need to  de-obfuscate the command using cyberchef as follow : 
1. Using replace| find Function to clean the code from (^) 

2. We notice there are SET for a verivble called (9ojB) we select that veribale and see we can find ! 

3. By the end of line we found "For /l  %3  IN  (+1640 ,  -3 ,+2 )", that mean the attcker telling the script to start from index 1640 (Whic is the last characker in the code )  and skkiping  two ckarakter all the way up.

4. To make this readbale lets revrese the code (Despaiye the fact it start from down top up) by using revrese function in Cybershef 

5. Now we need to select first Character and skipping two Characters by using regulare experation "(.).." and also select "List Capture Gruops" 

6. Great, All you need to do now is adding Synatx highliter to make the output more clear screen shot below 

![3](https://user-images.githubusercontent.com/29158503/60870145-f2fc4c80-a238-11e9-9774-79f7cace6eff.PNG)


