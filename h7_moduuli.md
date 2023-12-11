# Johdanto

Tein moduulin HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home- käyttöjärjestelmä.

# Alkutoimet

Tehtävän suorittamista varten tarvitaan herra-orja arkkitehtuuri. Käytin tässä apuna Teron ohjetta https://terokarvinen.com/2023/salt-vagrant/. Ensiksi loin uuden kansion nimeltä "projekti" komennolla ``mkdir projekti``  isäntäkoneeni C:/käyttäjät/käyttäjänimi/ -hakemistoon. Siirryin kansioon komennolla ``cd projekti`` Tarkistin vielä samalla Vagrantin version ja olemassaolon komennolla ``vagrant -v``. Vagrant olikin jo valmiiksi ladattu isäntäkäyttöjärjestelmääni aikaisemmassa tehtävässä h2 karjaa. 


<img width="175" alt="vagrantti" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/48b19c27-92dc-4702-a93b-184d67e99e11">

Avasin Vagrantfilen komennolla ``notepad Vagrantfile`` ja kopioin sinne Teron valmiin Vagrantfile-tiedoston sisällön ohjeista. Tallensin tiedoston.


<img width="209" alt="vagrantfile" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/5258fe81-5547-4160-af5a-1f6d8d83e435">

Sitten on aika käynnistää nämä virtuaalikoneet komennolla ``vagrant up``. Komennon ajamiseen kuluu useita minuutteja. Onnistunut lopputulos:


<img width="538" alt="onnistu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/272ca320-cf96-4dfa-988e-db0c5fe677ba">

Virtuaalikoneet näkyvät Virtualboxissa:


<img width="360" alt="projekt" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/a736bbc7-6165-4014-b358-a09aedda235e">


Tämän jälkeen siirryn Saltin herrakoneelle komennolla ``vagrant ssh tmaster``. Hyväksyn orjien avaimet komennolla ``sudo salt-key -A``.


<img width="266" alt="avaimet" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/432ad284-8222-406f-b55c-275c2313b2ce">

Testasin vielä herran ja orjien yhteyttä komennolla ``sudo salt '*' test.ping``. Asia näyttäisi olevan kunnossa.


<img width="239" alt="kunnossa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/f898efb8-a9eb-4336-9a57-11d6c4b1e4af">

# Apache

Seuraavaksi Apachen asennuksen kimppuun. Asennetaan Apache herrakoneella komennolla ``sudo apt install apache2``. Asennuksen jälkeen luon uuden hakemisto komennolla ``sudo mkdir /srv/salt``. Loin sinne kansion nimeltä apache2.


<img width="287" alt="apachey" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2e562d6b-1078-4202-8a45-166413ac1d6e">


Loin sinne apache2 index.html-tiedoston komennolla ``sudo nano projekti.html``. Lisäsin tekstiä ja tallensin sen.


<img width="611" alt="html" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/0845556b-ca6a-41a9-b4e6-621264d223b6">

Seuraavaksi tarvitaan init.sls-tiedosto. Luon sen samaan hakemistoon ja lisään sisällön. Vaihdoin tiedoston nimen omaksi eli projekti.html. Pkg. installed tarkistaa, että apache2 on asennettu. file.managed viittaa index.html:n lähteen olevan luomani projekti.html. Service.running varmistaa, että apache pyörii.

``apache2:
 pkg.installed
/var/www/html/index.html:
 file.managed:
   - source: salt://apache2/projekti.html
/etc/apache2/mods-enabled/userdir.conf:
 file.symlink:
   - target: ../mods-available/userdir.conf
/etc/apache2/mods-enabled/userdir.load:
 file.symlink:
   - target: ../mods-available/userdir.load
apache2service:
 service.running:
   - name: apache2
   - watch:
     - file: /etc/apache2/mods-enabled/userdir.conf
     - file: /etc/apache2/mods-enabled/userdir.load``

Seuraavaksi salt-tilan ajo. Ajan sen t001 orjakoneellani. Hyvältä näyttää.


<img width="191" alt="ajo" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/eb64cb95-b91c-4996-afa2-3cb62f461fe8">





# Lähteet

https://terokarvinen.com/2023/salt-vagrant/

https://github.com/ThomasHelminen/Palvelinten-hallinta--kurssi/blob/main/h2-karjaa.md

https://github.com/hautadata/palvelintenhallinta-jh/blob/main/H2-karjaa.md











