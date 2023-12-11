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

Seuraavaksi Apachen asennuksen kimppuun. Asennetaan Apache herrakoneella komennolla ``sudo apt install apache2``. Asennuksen jälkeen siirrytään hakemistoon komennolla ``cd /var/www/html`` ja poistin index.html- tiedoston. 





# Lähteet

https://terokarvinen.com/2023/salt-vagrant/

https://github.com/ThomasHelminen/Palvelinten-hallinta--kurssi/blob/main/h2-karjaa.md

https://github.com/hautadata/palvelintenhallinta-jh/blob/main/H2-karjaa.md











