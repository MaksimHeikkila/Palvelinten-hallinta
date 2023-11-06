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


<img width="394" alt="vagrant ssh" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/55c7c848-6251-40a5-af6e-06a30f18ea2a">

SSH-yhteys muodostettu onnistuneesti.

<img width="497" alt="ping testi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/e972b2f1-85d9-4b62-8a5e-ad38d444abc8">

Kokeilin ping-testillä, että netti toimii.



# c) Oma orjansa. Asenna Salt herra ja orja samalle koneelle.

Asensin Salt Masterin komennoilla 

sudo apt-get update

sudo apt-get install salt-master


<img width="275" alt="saltin käynnistys" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/743d2d96-ac52-43aa-999b-c03733769229">

Salt Masterin käynnistys


Asensin Salt Minionin komennolla

sudo apt-get install salt-minion

<img width="280" alt="salt minion start" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/caa992a1-9b7e-436f-9ff7-1752eda9c989">

Salt minionin käynnistys




# d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli. (Verkko voi olla virtuaalinen verkko paikallisten virtuaalikoneiden välillä, kuten muissakin alakohdissa)



<img width="649" alt="yhteys" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/6fc494fd-beaa-46b2-8e5d-f7c3cb89f68c">






# e) Aja useita idempotentteja (state.single) komentoja verkon yli.


<img width="666" alt="idempotentti" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c09841be-b441-4373-b561-3c3dc3121a22">




sudo salt '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com'



# f) Kerää teknistä tietoa orjista verkon yli (grains.item)


Hain tietoa käyttöjärjestelmästä ja muistin kapasiteetista komennolla 

sudo salt *'* grains.item os os_family mem_total

<img width="201" alt="tietoa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d93f068e-eed4-45ad-97b7-a463c24af86c">




# g) Aja shell-komento orjalla verkon yli.


Ajoin komennon sudo salt 'vagrant.vm' cmd run 'ls -l'


<img width="654" alt="komento" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/26543dad-9adc-4ba2-9540-e91325754c9d">






# h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.


<img width="304" alt="ongelma" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/04ff7225-6fd9-4925-8ec3-b550a0df0997">

Tässä kohtaa minulla tuli ongelmia

# Lähteet

Karvinen, 2023. Salt Vagrant - automatically provision one master and two slaves. Luettavissa: https://terokarvinen.com/2023/salt-vagrant/

Karvinen, 2017. Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds. Luettavissa: https://terokarvinen.com/2017/04/11/vagrant-revisited-install-boot-new-virtual-machine-in-31-seconds/

Slater, 2017. What is the definition of "cattle not pets"? Luettavissa: https://devops.stackexchange.com/questions/653/what-is-the-definition-of-cattle-not-pets#654


















