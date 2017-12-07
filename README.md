# webserver73


Vi skal create new Droplets ind i: https://cloud.digitalocean.com
Vælge Centos,  billigste park, det nærmeste areal. Sætte hak ved Jolitas Mac 

Vi åbne: terminal og skrive:
ssh root@95.85.22.162  -Enter
kodeord ******  -Enter

1. Nu vi skal   Installer Nano, skriver:  yum install nano  -Enter
Vi skal svar: j   -Enter

2. Nu vi skal installere MySql
skrive: yum install mysql-server   -Enter
svar: j  -Enter

Vi kan starte server:
service mysqld start -Enter

Konfigurer MySQL:
sudo /usr/bin/mysql_secure_installation

Der vil komme spørgsmål om pasword og nogen andre hvilken du skal besvar. 

Nu vi Installer Node.js:

yum install epel-release -Enter
j -Enter
yum install nodejs  -Enter
j -Enter 
yum install npm  -Enter
j -Enter

npm install -g n  -Enter

vi kan opdatere nodejs til en ny version 

n lts  -Enter

Vi kan tjekker hvilken verson vi har nu med at skrive: n -Enter 
jeg har version: ο node/8.9.2

 3. Installer PM2 (PM2 er en process manager til Node.js applikationer.)
 npm install -g pm2  -Enter

 Kør PM2 ved startup:
 pm2 startup

 4.  Installer Git
 yum install git -Enter
 j _Enter

git config --global user.name "jolitadarguzyte"  -Enter
git config --global user.email "jdarguzyte@gmail.com"  -Enter

Tjek konfigurationen:
nano ~/.gitconfig  -Enter   (vi kan komme tilbage med control+X)

5. Opret et nøglesæt til at logge ind på GitHub

    -Opret nøglesæt:
    ssh-keygen -t rsa         -Enter
vil komme følgende spørgmål: 
    Enter file in which to save the key osv hvor vi skal bare taster Enter 
    indtil vi kan skrive vider:
    cat ~/.ssh/id_rsa.pub  -Enter
    (Nu vi vil for lang kode) 
    kopier indholdet af den offentlige nøgle til
    GitHub -> Settings -> SSH and GPG keys -> New SSH key

6. Opret en mappe til din applikation
     mkdir ~/www   -Enter
 Naviger ind i mappen
     cd ~/www  -Enter

 7. Clone dit repository fra GitHub  
         git clone git@github.com:jolitadarguzyte/expressjs  
           (i brugernavn vi skrive det navn vi skal flytte) og -Enter

 Efte du kan prøve åbne en fane og skrive IPadres eksemp:  95.85.22.162:3000 (3000 den port vi fik ved at skrive)  

 Husk clone projekt på Github (og det skal være på din egen navn: dvs når du åbne projekt lige føre du clone du skal Førk først og efte clone - så vi det være på din navn og du kan redigere.) 
 Du kan redigere info og gemt det (husk comment og push i Visio)
 (og når du har en opdatering, skal du lave et pull)

 til sidst du skal skrive:
 git pull git@github.com:jolitadarguzyte/expressjs master






           




















Brians vejledling:
Hvordan man loger på MySql på din Linux server fra din windows maskine via MySgl-workbench.
For man kan logge på vores Mysgl server fra en anden maskine blev vi nyd til at give nogen
tilladelse ind på vores Linux server på vores MySql-server på vores Linux maskine.

Nå vi logge ind på server i Putty så først vi skal logge ind på MySql på vores Linux maskine. Vi
gøre sådan - skrive:

     "mysql -p" tryk Enter, 
     efter vi vil blive bedt om pasword. Vi taste pasword og igen Enter. Så vi er logget ind. 
      
nu vi skal give vores root brug lov til at logge ind fra andre adresser end localhost. 
Og det gøre vi med at skrive: 

     GRANT ON ALL *.* TO "root"@"%";
     og tryke Enter

og det betyde at brugen vil for alle tilladelse og adgang til alle databesen og tabellerner,
han kan logge ind fra alle maskiner.
Det neste vi skal gøre at vi skal sette kodeord til root brugen nå man logge på med root brugen 
fra andre adreese end local host.
vi gøre sådan - skrive:

      SET PASSWORD FOR  "root"@"%" = PASSWORD("1234");
      og tryk Enter.

Her jeg skrivet som eksempel pasword 1234, man kan selv vælge hvilken vi vil gerne har. 
Det kan være det sammen som den først.

Nu faktisk vi er klar. Vores root bruge har lov til at logge ind fra andre steder med 
adgangskode: 1234.
Og nå vi logge ind med root brugen fra andre steder han også for lov at forsætte med alle handliger. 

Nu vi skal ud af vors MySql. Vi skrive:
       quit; 
       og tryk enter. Nu vi er ud af vors MySql og igen er på vores Linux maskin. 


 Nu vi skal brug vores MySql workbench til at ekportere databasen fra vores localhost og 
 inporteres over på vores Linux maskine. Så vi skal starte vores MySQL Workbench up. Nå 
 vi åbne den vi har en Local instance som forbinde til localhost og det her vi skal trykke 
 for vi kan kom ind og henter nogen databesn. 
 Den logge vi på.
 Nu vi kan se vores databesen. Den vi vil gerne inportere på vores maskine vi makere.
 
 Med mussen vi går helt up på vores Server og vælge Data Export, vælge kilden. 
 Ned vi kan se hvor vi kan væjge og eksportere:
 Export to Dump Project Folder (Vi kan også se hvor den vil blive send).
 Vi skal bare trykke på pillen: Start Export. Nå vi kan se at den blev exportered 
 vi kan slukke forbindelsen fra.

 Nu vi har helt mappe med vores databesens indhold. Så vi er klar nu importere til Linux maskine. 
 For vi kan gør det vi skal brug vors MySQl workbench til ar forbinde MySql serveren 
 på mine Linux maskin.
 Vi skal lave ny forbindelse. 
 Vi trykke på plus pillen til venstre (MySQL Connections). I den komende vindue
 vi skal hente og skrive vores IP adressen fra (Linux) serveren og give navn (Connection name).
 Og vi skal skrive også User name: root
 Trykke OK. Nu vi har forbindelse til MySql serveren på vores Linux maskine.
 Vi kan se til venstre box hvor der stå den Connection 
 navn vi har givet, bruge navn og IP adressen. Nå vi trykke på den - vi vil for lov at teste
 kode til at logge ind.
 Nu vi er logget på MySql server på Linux maskine.
 Vi skal oprette en databassens mappe hvilken vi vil gerne inportere. 
 Vi skal går up på en icona - create a new scema. 
 Og trykke på den. Giver navn (det kan være det sammen navn som dem var) og Aplly.
 Nu vi kan se vores mappe i tabbel til venstre. Vi er klar ti importere.
 Vi går up på Server og vælge - Data Import. Så nu vi vælge:
 Import from Dump Project Folder og vi vælge den mappe 
 hvor ligge alle vores databeserens inhold - OK og Start Import.




