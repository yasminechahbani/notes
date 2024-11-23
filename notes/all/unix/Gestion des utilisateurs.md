



A User in unix is an entity associated to 3 main elements:

	 LOGIN : id used to connect to a system 
	 UID: user ID , unique to each user 
	 GID : the ID of the group of which he belongs to 

Users are <mark style="background: #FFB8EBA6;">three types</mark>:
		 Root (admin)
		 Simple users
		 Applicatiif = gerer un systeme bien determiné


to change the mode to admin : sudo su 

Passwords: 

password have concepts : 
	<mark style="background: #FFB86CA6;">pass_warn_age</mark>: prior to your password expiring , the system lets you know 
	 <mark style="background: #BBFABBA6;">pass_max_days</mark>: maximum days where the password is valid
	 <mark style="background: #ABF7F7A6;">pass_min_days</mark>: minimum days before you're allowed to change the password again 


if a user belongs to more than one group , and we want to be able to do work as a member of another group :

		newgrp : allows you to change between groups. not to create new ones  

### files that are important for user management

 
 <mark style="background: #D2B3FFA6;"> /etc passwd</mark>  list of users :
 in this file , every line contains 7 fields :




![[BSY+Security+Class+Diagrams+-+_etc_passwd+(L)-3747128276.jpg]]
   
       IF THE X IS ! : hethika maaneha rani maandich password!!
       IF THE X IS * : the admin blocked this account 
    najmou nbadlou el user information field bel commande : 
    
					    sudo chfn username
					    
    (chfn : change finger)
		
<mark style="background: #ADCCFFA6;">/etc shadow </mark> : where we store passwords

![[BSY+Security+Class+Diagrams+-+_etc_shadow+(L).jpg]]

					sudo passwd : to add a password to a user 


<mark style="background: #BBFABBA6;">/etc/group</mark>: list of groups ![[Capture d'écran 2024-07-21 232944.png]]

1. group name
2. pointer on the group password
3. gid
4. members of the group 

<mark style="background: #FFF3A3A6;">/etc/gshadow</mark>: les mot de passes des groupes

![[Capture d'écran 2024-07-22 193845.png]]

1. group name
2. encrypted password
3. owner of the group
4. members of the group

-------------------------------------------------------------------------
###  adding users

<mark style="background: #FFB8EBA6;">userAdd</mark> options : 
sudo userAdd  -u 2400 -g students -G teachers , group1ew -s /bin/bash -m -d /var/islem -p islem

![[Capture d'écran 2024-07-26 184208.png]]


	bech nmodifi les parametres par defaut : -D (Default) [options]

![[Pasted image 20241116114644.png]]
	![[Capture d'écran 2024-07-23 100944(1).png]]

Example : sudo useradd -D -g 120 -b /home

### modifying users


usermod : modify user 


pour appertenir a  plusieurs groupe secondaires:
-G : affectik  ken lgroupe secondaire wehed 
-aG : bech izidou le groupe secondaire ekher


![[usermod_options.jpg]]
