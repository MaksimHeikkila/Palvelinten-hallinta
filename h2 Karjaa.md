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







# d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli. (Verkko voi olla virtuaalinen verkko paikallisten virtuaalikoneiden välillä, kuten muissakin alakohdissa)






# e) Aja useita idempotentteja (state.single) komentoja verkon yli.








# f) Kerää teknistä tietoa orjista verkon yli (grains.item)






# g) Aja shell-komento orjalla verkon yli.






# h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.

















