


fel reseaux lan lkol i need to have 3 levels!!! :
core level : routers
2nd level : switches
3rd : more specific switches 


routers : connectes different networks to each other


switches : are intelligent hubs: connect hosts to each other 


bridges:: yorbot deux segments moch deux reseaux that would be a router 


those who regroup 
broadcast domains: switches allow broadcast everywhere
the only one who limits el domaine de diffusion is the router 

=> so the router is the only device eli limits diffusion ou collision 


## fonctionnement du commutateur 

#### filling the table

Initially el table de commutation bech tebda fergha , it will be broadcasting info everywhere

so<mark style="background: #ADCCFF2B;"> how can i configure el switch te3i</mark> ?

show mac-address table ==> shows el registered mac @
##### dynamically

know<mark style="background: #FFB8EB47;"> that we'll always save el @mac source</mark> , so bech tkoun el table te3i maabya , all the hosts need to be sources, yaanni all of them need to send trames

to clear the whole table : clear mac-address-table dynamic
##### statically
<mark style="background: #FFB86C40;">to add</mark> : (config) mac address table static <address-mac> vlan <ID_vlan>interface <ID_interface> 
<mark style="background: #BBFABB47;">to remove</mark> : (config) no mac address table static <address-mac> vlan <ID_vlan>interface <ID_interface> 


#  configuring vlans

## <mark style="background: #BBFABB47;">Access</mark> : heya ay rabt entre switch - pc
### switchport mode access

here , ken aana nafs el commutateur partager par different sub networks , we will need vlans for each sub network to limit the broadcast ken lel les membres of the same sub network

**un vlan howa un domaine de diffusion**


## <mark style="background: #ADCCFF2B;">trunk</mark> : ay rabt bin switch and a switch


used to send info to the destination vlan, we add a **tag** in the trame , which will contain el id taa el vlan , because by default maandich el id taa el vlan eli fel switch lekher !
		





