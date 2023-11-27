# Johdanto

Tein tehtävät HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home- käyttöjärjestelmä.


# x) Lue ja tiivistä.

-Asenna kaikki manuaalisesti. Asetustiedostot ovat /etc/-hakemistossa.

-Komennolla ``$ sudo find -printf '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort`` näet muokatut tiedostot. Komennot ``cat`` ``ls-l`` ja ``less`` näyttävät lisätietoja tiedostoista.

-Käytettäessä komentoa tilassa, on komennosta tehtävä idempotentti.

-``$ sudo salt '*' state.apply apache`` lisää tilan masterilta.





# a) CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.

Käytin Tero Karvisen ohjetta https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/. Aloitin tehtävän tekemisen ottamalla yhteyden aikaisemmassa tehtävässä luodulle herrakoneelle komennolla ``vagrant ssh tmaster``. Sisällä siirryin /etc/- hakemistoon ja käytin ``find`` komentoa hakemiston sisällä ja lopputuloksena oli pitkä lista tiedostoja.


<img width="249" alt="lista" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/bbc02162-f3ce-4133-b717-b39a8d5178cf">


Kokeilen vielä komennolla ``sudo find -printf '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort``. että mitä näkyy. Tässä komennossa -printf määrittää tulostusmuodon, find etsii tiedostoja nykyisestä hakemistosta ja |sort lajittelee tulokset, jotta viimeisimmäksi muokatut tiedostot näkyvät alimmaisena.

Format string eli '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort on merkkijono, joka määrittelee, että miten ``find``-komento näyttää tulokset käyttäjälle:

-%T+ M %p: Näyttää tiedoston muokkausajan lisättynä kuukaudella, jonka jälkeen näytetään tiedoston polku

-%A+ A %p: Näyttää tiedoston viimeisimmän käyttöajan lisättynä vuodella, jonka jälkeen näytetään tiedoston polku

-%C+ C %p: Näyttää tiedoston metadata-muutoksen ajan lisättynä vuodella, jonka jälkeen näytetään tiedoston polku



<img width="326" alt="etc" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/18f2c03d-b21a-4b5a-a152-0c776fa779ef">


Kotihakemiston viimeksi muokatut tiedostot samoilla parametreillä ja format stringeillä.


<img width="291" alt="home" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/ef1fa345-6d26-4d9d-8c71-6f1db580ede2">



# b) Gui2fs. Muokkaa asetuksia jostain graafisen käyttöliittymän (GUI) ohjelmasta käyttäen ohjelman valikoita ja dialogeja. Etsi tämä asetus tiedostojärjestelmästä.

Tätä tehtävää varten siirryin Virtualboxiin ja avasin Debian- virtuaalikoneen graafisella käyttöliittymällä. 


<img width="360" alt="debian" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/88ac0a80-a6af-4ad4-aac1-d80eeb4b54a8">


Tehtävää varten loin tekstitiedoston graafisella käyttöliittymällä ja tallensin sen virtuaalikoneen työpöydälle.


<img width="639" alt="tallennettu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/453962ff-a578-434e-909a-a31a40c8c539">


Nyt kun tiedosto on tallennettu, avaan komentokehotteen, siirryn samaan hakemistoon, mihin tallensin tekstitiedoston eli Desktop ja käytän komentoa ``sudo find -printf '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort`` nähdäkseni viimeksi muokatut tiedostot ja siellä näkyy tallentamani tiedosto esimerkkitiedosto.odt parametreineen.


<img width="620" alt="desktop" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/4170b787-e306-4ec6-8bdf-f970f851054c">



# c) Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennon.

Käytän tässä tehtävässä aikaisemmin luomiani Vagrantin virtuaalikoneita. Laitetaan ne käyntiin ja otetaan yhteys masteriin komennoilla ``vagrant up`` ja ``vagrant ssh tmaster``-


<img width="337" alt="up" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/608bc606-738f-459b-8fe2-6fd1c007e3de">


<img width="413" alt="tmaster" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/9cd5883f-08d5-49db-b057-1a1c374ccba8">



Siirryn tässä kohtaa tyhjään hakemistoon /usr/local/bin.


<img width="224" alt="bin" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2be6c33c-e956-4a9e-9aba-2069cc7caa7d">


Teen yksinkertaisen Hello World- skriptin. Luodaan uusi skriptitiedosto komennolla ``sudo nano hello.md``- Löysin tämän skriptin sivustolta https://www.hostinger.com/tutorials/bash-script-example#1_Hello_World



<img width="316" alt="hello" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c57a7cf0-d64f-4292-a3bd-470631af6489">


Seuraavaksi yritän ajaa skriptiä, mutta näyttää siltä, että minulla ei ole tarvittavia oikeuksia. Muokataan oikeuksia ``sudo chmod 755 hello.sh``-komennolla. Nyt näyttää toimivan.



<img width="412" alt="sudo" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/82e1abd5-13c4-407b-ba5f-469c3eb3fa70">


Luon vielä /srv/salt- hakemistoon uuden hakemiston ja samanlaisen skriptitiedoston. Muutan hakemiston ja skriptitiedoston nimeksi "world.md", koska hakemistossa on jo hello-niminen hakemisto ja init-tiedosto.


<img width="296" alt="world" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/9d7e6871-9e7e-49ac-8853-c6652b588095">


Sitten tehdään init-tiedosto, joka kertoo orjalle skriptin sijainnin. 



<img width="200" alt="innit" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/84f7755c-872a-41d5-a619-7af91f9ff0ee">


Testivaihe. Komennolla ``sudo salt 't001' state.apply world`` loin t001- orjalle /usr/local/bin- hakemistoon tämän skriptitiedoston. Olin tässä vaiheessa pitkään jumissa, koska init.sls-tiedostostani puuttui .sh worldin perästä. Nyt kuitenkin onnistui kun lisäsin sen. Sen jälkeen ajetaan komento ``sudo salt 't001' cmd.run 'world'`` ja se toimii.


<img width="560" alt="sh" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/818fcdc3-0b05-4724-9ca8-c1510b0c8240">



<img width="369" alt="toimii" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/6a9ec330-c173-4252-b9ad-7e712e2c1848">




# d) Apassi. Tee Salt-tila, joka asentaa Apachen näyttämään kotihakemistoja.

Käytin tässä tehtävässä apuna Tero Karvisen artikkelia https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/. Ensiksi siirryin hakemistoon komennolla ``cd /srv/salt/`` ja loin sinne uuden hakemiston "apache1", koska siellä on jo aiemmassa tehtävässä luotu apache2-hakemisto.



<img width="263" alt="apache 1" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c4b3bfb5-ff31-438c-8064-d46db69fac47">


Luon uuden apache1.html- tiedoston, kopioin internetistä löytämäni mallipohjan ja lisään sinne vähän tekstiä.


<img width="196" alt="tekst" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/0150b39e-07f7-481e-940f-1f114dcb87de">


Nyt luon .sls-tiedoston käyttämällä Teron ohjetta. Kopioin seuraavan pätkän, johon vaihdan nimet omikseni:

``apache2:
 pkg.installed
/var/www/html/index.html:
 file.managed:
   - source: salt://apache1/apache1.html
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




<img width="299" alt="apachee" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/f8fdd7f8-48c1-4570-8a77-b865a001c02e">


Testataan. Ajoin komennon ``sudo salt 't001' state.apply apache1`` ja 3 kohtaa onnistui, 2 ei.

<img width="665" alt="virhe1" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d05403e5-83d3-41e6-a063-976911d8333e">


<img width="544" alt="virhe2" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/003ff6af-da26-4c08-80e3-ddb6170f13d2">


Kokeilin selvittää tätä ongelmaa asentamalla päivitykset ``sudo apt-get update``- komennolla. Päivitys kuitenkin epäonnistuu.



<img width="661" alt="invalid" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/b83c63fd-d969-43ae-b60c-c58e6a145816">


Yritän päästä tässä vielä eteenpäin.







# e) Ämpärillinen. Tee Salt-tila, joka asentaa järjestelmään kansiollisen komentoja.

Tätä tehtävää varten siirryn taas /srv/salt- hakemistoon ja luon uuden kansion, johon luon 5 tekstitiedostoa. Luon kansion komennolla ``sudo mkdir kansiollinen``. Lisään kaikkiin tiedostoihin jonkin simppelin komennon, jotka löydän internetistä.


<img width="331" alt="konennot" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d93c7436-ec42-42d5-8c76-e59a94f41d80">

SLS-tiedoston luonti.


<img width="354" alt="sls" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/e0b0ddf5-c89d-44cf-9609-3f4b62e712bc">







# Lähteet

Tero Karvinen, 2018. Apache User Homepages Automatically – Salt Package-File-Service Example. Luettavissa: https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/. Luettu: 26.11.2023.

https://www.hostinger.com/tutorials/bash-script-example#1_Hello_World






