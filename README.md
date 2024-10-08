# AD-home-lab-auth-autorisation-strategies

## first : creation of the environnement 
Two windows server vms called DC1 and DC2 
one client vm called CL1 
--> problems that might occure : 
For the client machine : when creating the client machine if it's stuck at a certain % mostly ( 79% ) then you gotta add some space to the hard disk ( 70GB or 80GB instead of 60GB ) if it didn't work then try to recreate a new vm during the creation process verify that the option **split virtual disk as a single file** is choosen not storing it as a single file by doing this your ptoblem should be fixed  

For the server machines : after installing the server machine you'll want to create active directory ( promote it ) but something have to be done before , you should check your connection between the host machine ( your laptop ) and the vm  to check this first you gonna see the laptop icon down on the bar on your server it shouldn't be red if it is then go here on your host machine  **Panneau de configuration\Réseau et Internet\Connexions réseau** you will probably not find the ethernet cable connected to your virtualmachine (espesially if it is vmware the problems occures quite much there ) so what you're gonne do is go back to your vmware ( it should be a pro xorkstation so as you can edit not the player one  ) click on edit and go to virtual network editor you're gonna click on change settings and create a new network let's nemae ir VMnet2 keep it as host-only save eveything and go back to your host the this path **Panneau de configuration\Réseau et Internet\Connexions réseau** you'll see that a new ethernet connection it will be the vm's one now restart the workstation when powering on the server you'll find the problem fixed 
