# Johdanto

Tein tehtävät HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home- käyttöjärjestelmä.


# x) Lue ja tiivistä.

-Asenna kaikki manuaalisesti. Asetustiedostot ovat /etc/-hakemistossa.

-Komennolla ``$ sudo find -printf '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort`` näet muokatut tiedostot. Komennot ``cat`` ``ls-l`` ja ``less`` näyttävät lisätietoja tiedostoista.

-Käytettäessä komentoa tilassa, on komennosta tehtävä idempotentti.

-``$ sudo salt '*' state.apply apache`` lisää tilan masterilta.





# a) CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.

Käytin Tero Karvisen |ohjetta|(https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/). Aloitin tehtävän tekemisen ottamalla yhteyden aikaisemmassa tehtävässä luodulle herrakoneelle komennolla ``vagrant ssh tmaster``. Sisällä siirryin /etc/- hakemistoon ja käytin ``find`` komentoa hakemiston sisällä ja lopputuloksena oli pitkä lista tiedostoja.


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








# d) Apassi. Tee Salt-tila, joka asentaa Apachen näyttämään kotihakemistoja.

# e) Ämpärillinen. Tee Salt-tila, joka asentaa järjestelmään kansiollisen komentoja.

# Lähteet

Tero Karvinen, 2018. Apache User Homepages Automatically – Salt Package-File-Service Example. Luettavissa: https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/. Luettu: 26.11.2023.






