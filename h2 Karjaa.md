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

Asensin Vagrantin lataamalla sen osoitteesta https://developer.hashicorp.com/vagrant/downloads Windowsilleni

<img width="438" alt="vagrant windows" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/baac3c42-860f-48cf-b5e7-0524cd4e0c5b">

<img width="386" alt="vagrant asennus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d4e0f35a-dffe-447b-9f25-1a4d15a9fd9e">

















