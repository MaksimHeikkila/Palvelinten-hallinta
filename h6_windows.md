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


# b) Asenna Salt Windowsille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.


# c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.


# d) Kokeile Saltin file -toimintoa Windowsilla.


# e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla. (Voit käyttää apuna edellisten vuosien kotitehtäväraporttia tai Karvinen 2018: Control Windows with Salt. Huomaa, että noissa muistiinpanoissani voi jo hieman ikä painaa, ja niissä on myös epärelevantteja kokeiluja.)

# Lähteet





