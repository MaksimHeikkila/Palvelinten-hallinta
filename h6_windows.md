# Johdanto

Tein tehtävät HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home- käyttöjärjestelmä.


# x) Lue ja tiivistä.

-Lataa sivustolta https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise Windows- virtuaalikoneeseen tarvittava ISO-tiedosto, avaa Virtualbox ja valitse kohta ``New``

-Nimeä virtuaalikoneesi, aseta käyttöjärjestelmäksi Windows 10, keskusmuistiksi 8 GB, luo

-Valitse kovalevyn tyypiksi VDI, koko 50 GB, dynaamisesti allokoitu. Määritä prosessorien määräksi 4 klikkaamalla juuri luotua virtuaalikonetta hiiren oikealla näppäimellä ja siirtymällä system -> processor- kohtaan

-Seuraa asennusohjeita. Määritä sijainniksi oma sijainti. Custom install Windows only. Kun pyytää kirjautumista, valitse "domain login"

-/etc- hakemisto: sisältää asennustiedostoja. "Asennustiedosto" on tiedosto, jolla hallitaan ohjelman toimintaa.

-/home- hakemisto: käyttäjän kotihakemisto. 

-/bin- hakemisto: sisältää komentoja, joita järjestelmänvalvoja ja käyttäjät voivat käyttää. Binissä ei voi olla alahakemistoja.







# a) Asenna Windows virtuaalikoneeseen.


Windowsin asennusta varten tarvitsen ISO-tiedoston. Siirryn tiedoston latausta varten osoitteeseen https://www.microsoft.com/en-us/evalcenter/download-windows-10-enterprise ja lataan sen. Latasin 64-bittisen version.


<img width="463" alt="iso" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2d558bc4-f2f4-484e-a76d-126df01218e7">


Seuraavaksi siirryn Virtualboxiin, päivitän sen ja aloitan asennuksen kohdasta New. Valitsen lataamani ISO-tiedoston, käyttöjärjestelmäksi Windows 10


<img width="798" alt="asennusta" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/92378932-8f0d-4bdc-a696-a93cfd722d2a">


Valitaan 8 GB keskusmuistia ja 4 prossua


<img width="802" alt="prossut" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/80521649-314a-4b5b-a80b-4e14b6e462f9">

Kovalevyn koko 50 GB ja VDI (VirtualBox Disk Image)


<img width="796" alt="muistii" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/aa6bfd90-1a29-4bbd-b0d5-3aa9d83550c3">


Virtuaalikone näkyy luotuna


<img width="360" alt="luotuna" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/dcf5c54b-a428-43f2-a72e-040520bbdf00">



Konfigurointi ohjeiden mukaisesti.


<img width="308" alt="now" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/952d3508-3eb9-455c-8fc4-7f3424cc601c">


<img width="514" alt="konff" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/9d542561-f2b3-4454-91d5-01129764b5fb">


<img width="321" alt="setup" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/62a92f76-3b25-4698-8ac9-2128c7f400cf">



<img width="513" alt="finland" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/8b542c6e-e658-4b5b-87ef-b02d07a69105">



<img width="511" alt="maksim" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2df8e7c8-84e8-40db-9e19-68643865274b">


Windows on nyt asennettu.

<img width="508" alt="asennettu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/74c64947-23ca-40b2-b7ff-c67e2a3820a0">











# b) Asenna Salt Windowsille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.


# c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.


# d) Kokeile Saltin file -toimintoa Windowsilla.


# e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla. (Voit käyttää apuna edellisten vuosien kotitehtäväraporttia tai Karvinen 2018: Control Windows with Salt. Huomaa, että noissa muistiinpanoissani voi jo hieman ikä painaa, ja niissä on myös epärelevantteja kokeiluja.)

# Lähteet




