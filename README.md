# Research Project '20-'21
## Chess Assistant
### PXL Digital | AI & Robotics

#### In deze repo vind je enkele praktische benodigdheden, zoals de rosbags die camerabeelden uit de AI Hub bevatten.
#### Deze README wordt, samen met de andere bestanden in de repo, nog aangevuld wanneer daar nood aan is.

## IP Camera
We gebruiken een DLink IP camera (dcs-4602ev) om beelden te maken van het schaakbord. Deze kan je in de AI Hub rechtstreeks aanspreken voor live beelden.
Doordat we veel op afstand moeten werken, hebben we ook _*rosbags*_ voorzien, wat eigenlijk opnames zijn van ROS topics. Deze opnames kunnen dan lokaal afgespeeld worden om in dit geval de camera beelden te simuleren in dezelfde ROS omgeving.

### Remote setup: rosbag
Om remote te kunnen werken met de IP camera, hebben we `rosbags` voorzien. (zie folder *rosbags*) Dit kan je zien als een soort recording van één of meerdere ROS topics en de berichten die er over verstuurd worden. Deze kan je opnieuw afspelen en zo dus 'simuleren'. Op die manier kan je dan in je applicatie naar de opgenomen data luisteren op de bijhorende ROS topics, alsof dat het *live* beeld is. Dit kan je dan reeds in je applicatie proberen te tonen, zodat jullie nadien enkel de koppeling eventueel wat moeten aanpassen.
We geven jullie hieronder de info die jullie normaal nodig hebben, maar een andere tutorial kunnen jullie [hier](http://wiki.ros.org/rosbag/Tutorials/Recording%20and%20playing%20back%20data) vinden.

Stap 1 als je met ROS gaat werken: `roscore` uitvoeren in een terminal venster.

De rosbag kan je daarna afspelen door in een terminal naar de folder te navigeren waar het rosbag bestand is opgeslagen. Daarna kan je met `rosbag play <naam van het rosbag bestand>` de opgenomen topics weer laten afspelen. Je kan de recording eventueel laten loopen, door de `-l` flag toe te voegen. Denk er wel aan dat dat mogelijk rare neveneffecten kan hebben in jullie applicatie. (beeld springt van spel in progress naar startpositie in eerste frame van opname)

`rosbag play (-l) 2021-03-04-12-07-54_fools-mate.bag`

Let op: `roscore` moet ook opstaan voordat je dit doet. 
Na het opstarten van de recording, kan je normaal gezien de opgenomen topic zien. Na `rostopic list` zou je dus het volgende moeten zien:

`sam@sam:~$ rostopic list
/clock
/chesscam/compressed
/rosout
/rosout_agg`

De topic `/chesscam/compressed` is dezelfde die jullie zullen opvragen aan de 'live' camera, dus hiermee kunnen jullie voorlopig aan de slag om dit te integreren in de applicatie en computer vision algoritmen uit te proberen.


### AI Hub setup
De camera kan aangesproken worden via ROS als je volgende stappen onderneemt:
- Clone de [RODIPCa](https://github.com/PXLRoboticsLab/RODIPCa) github repo
- Verbind met het netwerk ```AI Hub Devices``` (wachtwoord te verkrijgen via Sam & Sam)
- Start ```roscore```
- Run het RODIPCa script ```connect.py``` met de gewenste parameters (adres en login camera te verkrijgen via Sam & Sam)

Nadien zou met bv. ```rostopic list``` een nieuwe topic zichtbaar moeten zijn (eventueel met de gespecifieerde naam in de parameters) waarop je kan subscriben om de camerabeelden binnen te halen.

Wanneer we terug on campus mogen werken, wordt dit nog verder gespecifieerd.


## ROSbags

Wanneer bepaalde scenario's ontbreken om te testen, kan aan Sam & Sam gevraagd worden om wat nieuwe op te nemen. Deze kunnen dan als aanvulling toegevoegd worden aan de rosbags folder.