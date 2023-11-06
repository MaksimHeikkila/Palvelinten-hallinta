# x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

# What is the definition of "cattle not pets"

- Lemmikit: Palvelimia tai palvelinpareja, jotka ovat välttämättömiä tai uniikkeja järjestelmiä, jotka eivät saa koskaan olla alhaalla.
- Karja: Joukko palvelimia, jotka ovat korvattavissa. Vian ilmetessä ei yleensä tarvita ihmisen väliintuloa, vaan kaikki on automatisoitu.
- Siispä sen sijaan, että kiintyisimme palvelimiin, voimme vain korvata tai tuhota ongelmallisen palvelimen

# Vagrant revisited: Install & boot new virtual machines in 31 seconds

- Vagrant asentaa uuden virtuaalikoneen automaattisesti ja hallitset sitä puolessa minuutissa ssh:lla
- $ sudo apt-get update ja $ sudo apt-get -y install vagrant virtualbox asentaa Vagrantin ja Virtualboxin
- $ vagrant init bento/ubuntu-16.04, $ vagrant up ja $ vagrant ssh luovat uuden virtuaalikoneen

# Salt Vagrant - automatically provision one master and two slaves

- Määritysten hallinnan avulla voit hallita satoja tietokoneita

# a) Asenna Vagrant. (Toiminee parhaiten isäntäkäyttöjärjestelmässä, siis siinä, joka pyörii raudalla)

Asensin Vagrantin lataamalla sen osoitteesta https://developer.hashicorp.com/vagrant/downloads Windowsilleni. Järjestelmä käynnistettiin uudelleen asennuksen viimeistelemiseksi.

<img width="438" alt="vagrant windows" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/baac3c42-860f-48cf-b5e7-0524cd4e0c5b">

<img width="386" alt="vagrant asennus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d4e0f35a-dffe-447b-9f25-1a4d15a9fd9e">

# b) Yksi maankiertäjä. Asenna yksi kone Vagrantilla, ota siihen SSH-yhteys, osoita että netti toimii.

Asensin yhden koneen Vagrantilla komennoilla 

$ vagrant init bento/ubuntu-16.04

$ vagrant up

$ vagrant ssh

<img width="365" alt="vagrant ubuntu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/819ecbff-aede-4d5d-9b62-f85143217e7a">


<img width="359" alt="uusi virtuaali" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/f4be1c03-2773-4f2f-b7e1-a89978b3f382">

Uusi virtuaalikone on nyt asennettu.


<img width="394" alt="vagrant ssh" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/55c7c848-6251-40a5-af6e-06a30f18ea2a">

SSH-yhteys muodostettu onnistuneesti.

<img width="497" alt="ping testi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/e972b2f1-85d9-4b62-8a5e-ad38d444abc8">

Kokeilin ping-testillä, että netti toimii.


<img width="430" alt="destroy" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/15e94314-94d0-438f-8a54-717a15e77d68">

Lopuksi vielä poistuin virtuaalikoneesta ja tuhosin sen.



# c) Oma orjansa. Asenna Salt herra ja orja samalle koneelle.

Seuraavaksi loin uuden virtuaalikoneen ja otin siihen yhteyden aikaisempien ohjeiden mukaisesti komennoilla 

$ vagrant init bento/ubuntu-16.04

$ vagrant up

$ vagrant ssh


<img width="412" alt="uusi vagrant" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/aea57aa6-f4df-4dff-ac86-f1049181447e">

Uusi virtuaalikone on valmis. Seuraavaksi Salt Master & Minion asennus Salt Quickstart- ohjeilla (Karvinen 2018)


Asensin Salt Masterin komennoilla 

sudo apt-get update

sudo apt-get -y install salt-master

hostname -I

<img width="195" alt="master luotu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/b227c789-94a1-493c-a857-db0217088764">


<img width="539" alt="master toiminnassa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d9785a66-7069-4c5e-968b-8a95c026814e">


Master luotu ja toiminnassa. Seuraavaksi minion


<img width="529" alt="minion toiminnassa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/0ddf79fd-3f93-408c-9aaf-78ce7451f101">

Minion toiminnassa.


Asensin Salt Minionin komennoilla

sudo apt-get update

sudo apt-get -y install salt-minion


# d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli. (Verkko voi olla virtuaalinen verkko paikallisten virtuaalikoneiden välillä, kuten muissakin alakohdissa)

<img width="174" alt="hostname i" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/cebc5c9d-7a4a-422d-b20a-9a011b8c14d9">



Orjan täytyy tietää, että missä master on. Sitä varten avataan tekstieditori ja muokataan asetuksia komennolla

sudoedit /etc/salt/minion


<img width="101" alt="master id" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/790e2e9b-ade5-4b36-8aba-7b914ea9d5a9">

Muokataan Master


<img width="450" alt="uudelleen" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/9a601c2c-9277-4912-90c2-1e192ff4571a">

Sen jälkeen minionin uudelleenkäynnistys, jonka jälkeen avaimen hyväksyntä komennolla

master$ sudo salt-key -A


<img width="256" alt="avain" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/cc872d59-257b-4829-8d3f-4aef12828109">




<img width="649" alt="testi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/7d76d980-d2fa-4576-98da-6fad5e4bcb86">

Testasin, että yhteys toimii. Tässä kohtaa tuli kuitenkin varoitus Key 'file_ignore_glob' with value None has an invalid type of NoneType, a list is required for this value, jonka korjasin Teron ohjeella Quick fix for useless Salt warning.

Menin komennolla sudoedit /etc/salt/master ja lisäsin rivin file_ignore_glob: [], jonka jälkeen varoitusta ei enää tullut.


<img width="256" alt="varoitus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/b8e4bcc4-0be2-472a-a9d5-d3b38185affc">







# e) Aja useita idempotentteja (state.single) komentoja verkon yli.

Kokeillaan seuraavaa komentoa eli Apache2 asennus

sudo salt '*' state.single pkg.installed apache2

Ajoin komennon kaksi kertaa, jolloin tulos näytti tältä:

<img width="399" alt="idem" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2e6efa97-e8c5-4a88-954f-67d18713866f">'

Muutoksia ei tule, joten idempotentti saavutettu.

Seuraavaksi sama, mutta apache2 käynnistäminen:


<img width="428" alt="apache" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/5a2ce28d-1e24-4565-8541-950336f5c30b">

Apachen sammuttaminen:

<img width="421" alt="sammuta" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2b9fc100-ed51-4934-8ada-d86fd08e3833">



<img width="410" alt="sammuta 2" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/fc672073-735c-4aa8-b9d4-0a440b4ca7ed">

Idempotentti saavutettu.




# f) Kerää teknistä tietoa orjista verkon yli (grains.item)


Hain tietoa käyttöjärjestelmästä komennolla 

sudo salt-call --local grains.item osfinger

<img width="353" alt="tietoa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/7617591d-5940-4a20-a250-2dcf226d0d47">








# g) Aja shell-komento orjalla verkon yli.

Tein simppelin komennon:

<img width="462" alt="yksinkertainen" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/abb2eaee-272e-462e-848f-715ab575a21f">






# h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.

Seurasin Teron Salt Vagrant-ohjeita sivulla https://terokarvinen.com/2023/salt-vagrant/


Loin kansion ja tekstitiedoston:

<img width="275" alt="init1" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/ae9d558a-a517-4a25-9e10-c01a3df2b582">


<img width="319" alt="loin" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/e917421c-6ca7-4dce-a338-68461a3e10f0">

Tekstitiedostoon lisäsin tekstin /tmp/infra-as-code:
  file.managed

  
<img width="420" alt="liss" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c16b8844-4a7c-4ede-ada1-c9f8709e379c">

Kohtasin kuitenkin virheen ajaessani tiedostoa



<img width="328" alt="virhe" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/95a82453-6e10-461c-92cf-578606c40197">







# Lähteet

Karvinen, 2023. Salt Vagrant - automatically provision one master and two slaves. Luettavissa: https://terokarvinen.com/2023/salt-vagrant/

Karvinen, 2017. Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds. Luettavissa: https://terokarvinen.com/2017/04/11/vagrant-revisited-install-boot-new-virtual-machine-in-31-seconds/

Slater, 2017. What is the definition of "cattle not pets"? Luettavissa: https://devops.stackexchange.com/questions/653/what-is-the-definition-of-cattle-not-pets#654


















