# En saanut valmiiksi ajan puitteissa. Tarvitsen lisäaikaa.

Tein tehtävät HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home.


# x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves

- Komennoilla $ sudo mkdir -p /srv/salt/hello ja $ sudoedit /srv/salt/hello/init.sls saadaan luotua uusi hakemisto ja muokataan SLS-tiedostoa.
  
- Nämä komennot kirjoitetaan SLS:ään: $ cat /srv/salt/hello/init.sls
/tmp/infra-as-code:
  file.managed
  $ sudo salt '*' state.apply hello
  
- $ sudo salt '*' state.apply hello^C, $ sudoedit /srv/salt/top.sls ,$ cat /srv/salt/top.sls
base:
  '*':
    - hello : näillä komennoilla lisätään "hello"-tila kaikille minioneille.
 
Salt contributors: Salt overview

-Rules of YAML: data on jaettu avain-arvo-pareiksi. Avainten arvot voivat olla monenlaisia rakenteita. Kaikki avaimet/ominaisuudet ovat kirjainkoosta riippuvaisia. Välilehtiä EI sallita, käytä vain välilyöntejä. Kommentit alkavat hashilla (“#”).

-YAML koostuu kolmesta peruselementtityypistä: Skalaarit - avain: arvo -mappauksia, joissa arvo voi olla numero, merkkijono tai totuusarvo. Listat - avain, jonka perässä on arvolista, jossa jokainen arvo on omalla rivillään ja aloitetaan kahdella välilyönnillä ja viivalla. Sanakirjat - kokoelma avain: arvo -mappauksia ja listoja.

-Lists and dictionaries - YAML block structures: YAML on jaettu lohkorakenteisiin. Sisennys määrittää kontekstin. Kaksi välilyöntiä on standardi. 

Salt contributors: Salt states

-Top.sls-tiedosto luo yleisiä abstraktioita, eli karttaa, mitkä solmut tulisi vetää mistä ympäristöstä ja määrittelee, mitkä tilat tulisi ajaa näistä ympäristöistä.
-Tilat kannattaa järjestää niin, että toinen kehittäjä voi nopeasti ymmärtää tilan tarkoituksen ja nähdä koko tilapuun työnkulun.
-Tilan määritelmä tilatiedostossa koostuu: tunnisteesta, tilasta, funktiosta, nimestä ja argumentista.





# a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Käytin tässä tehtävässä lähteenä Joonas Hautaviidan GitHub-artikkelia "H4 Demonit". Käytin h2-tehtävässä käytettyjä virtuaalikoneita, jotta ei tarvitse luoda uusia. Otin yhteyden vagrantiin komennolla vagrant ssh.


<img width="379" alt="shhhhhh" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/0d8e4096-ee10-4060-be0d-4e4028b0944f">

Sen jälkeen siirryin aiemmin luotuun hakemistoon, jossa sijaitseekin aiemmin luotu .sls- tiedosto.


<img width="300" alt="innit" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/35c654f3-2d5e-4ebe-8c42-010a9cc578c7">


Avasin Nano- tekstieditorilla .sls-tiedoston, jossa oli jo aiemmin muokkaamaani tekstiä.


<img width="173" alt="aiempaa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/695aa157-1dbf-4f7b-8bd8-5db8e95c6fc6">

Laitoin tilalle koodin, joka printtaa "hei maailma!" ja tallensin sen ctrl+x- painikkeilla


<img width="344" alt="hei maailma" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/af15ff54-69c4-4572-a0a9-4e9e4a657479">


Lähin testaamaan sitä ajamalla komennon sudo salt '*' state.apply hello ja lopputulos ohessa: stdout printtasi "hei maailma"


<img width="572" alt="testi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d85a894d-5ae8-403e-a2e8-e9223ee214bf">






# b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".

Ensiksi varmistetaan, että salt on asennettu kaikille tietokoneille komennolla sudo salt '*' test.ping. Näyttäisi olevan.


<img width="340" alt="true true" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/ce473514-d903-4811-bd0d-b37534e66543">

Sitten luodaan saltin tila, joka määrittelee, että mitkä tilat suoritetaan missä koneessa. Se tehdään komennolla sudo nano /srv/salt/top.sls ja lisätään tiedostoon:
base:
  '*':
    - hello


<img width="181" alt="hello" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/db99f60d-737e-4894-96c5-4f011e8082ae">

Tallensin muutokset ctrl+x- näppäinyhdistelmällä ja sen jälkeen kokeilin ajaa tilan kaikille koneille komennolla sudo salt '*' state.apply



<img width="505" alt="ajettu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/794b2632-cd46-4f20-80e9-4a0aa6dc042e">


    



# c) Apache. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.

Käytetään tässä tehtävässä aikaisemmin, tehtävässä h2 luotuja virtuaalikoneita. Otetaan yhteys t001 minioniin komennolla vagrant ssh t001.



<img width="411" alt="t001" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/1556f598-26af-4f1e-ba37-30c3c9ef27e2">

Sitten tarkistetaan, että onko apache jo olemassa komennolla sudo systemctl status apache2. Ei ollut, joten asennetaan se komennolla sudo apt-get install apache2. Tarkistetaan, että asennus onnistui käyttämällä taas komentoa sudo systemctl status apache2. Onnistui


<img width="541" alt="status" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/ab10c108-9bef-4d52-9808-63710851a48c">

Asennuksen jälkeen siirrytään cd /var/www/html hakemistoon, jossa on index.html, joka tullaan korvaamaan. Poistin index.html-tiedoston sudo rm index-html- komennolla. Tarkistin sen jälkeen ls-komennolla, että tuliko tiedosto poistettua ja tulihan se.


<img width="261" alt="rm" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/063ee21b-8bf7-4539-87c7-503bca2f68ac">

Luon tilalle uuden .txt-tiedoston komennolla sudo nano uusi.txt. Lisäsin sinne tekstiä ja tallensin sen ctrl+x- näppäimillä. 


<img width="336" alt="uusii" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/7f0fa81d-9cb2-453f-9541-70dc8a06b7a7">


Tarkistetaan, että demoni on aktiivinen komennolla sudo systemctl status apache2 | grep "Active".


<img width="419" alt="active" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/98adf48f-f630-4e72-a0a3-32a6059d7e1e">


Sitten vuorossa automatisointi. Poistetaan apache2 orjalta komennolla sudo apt-get remove apache2 ja siirrytään herrakoneelle tmaster. Muokataan hello.sls- tiedostoon 4 funktiota ja tallennetaan. 



<img width="327" alt="activ" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/6246a395-dc45-4e08-b2c8-a7659250d545">








# d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.


Tätä tehtävää lähdin tekemään Virtualboxilla Teron ohjeiden mukaisesti. Käytin tähän Ubuntun desktop-versiota. Asensin ensiksi päivitykset komennoilla sudo apt update ja sudo apt upgrade -y. Sitten konfiguroidaan SSHd. 










# Lähteet




