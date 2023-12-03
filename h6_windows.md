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


Siirryin sivustolle https://docs.saltproject.io/salt/install-guide/en/latest/topics/downloads.html ja latasin Saltin.

<img width="553" alt="saltti" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/bdfe2835-bddc-469a-bf4b-56fed6f1eda3">

Asennusta.


<img width="314" alt="salttiii" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/4c50496a-79f5-4a89-8568-e41c950b8bcb">


Asennettu.


<img width="310" alt="asennettud" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d6694e6c-29b5-4593-a85a-0a71df1108c8">

Tarkistetaan vielä komennolla ``salt-call --version``, että Salt on varmasti asennettu.


<img width="186" alt="sulfur" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d209cff8-7bc2-4cda-949f-c7043e9e1cfa">






# c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.


Avasin Powershellin järjestelmänvalvojana ja syötin komennon ``salt-call --local grains.items``.



<img width="251" alt="powershell" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c08081db-cc56-4a2a-97e4-fc3e13cb6437">


RAM-muistin määrä.


<img width="72" alt="memory" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/48eb3a15-52a2-433d-92e4-02c34444d190">


Käytössä oleva prosessori.


<img width="213" alt="prossu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/74d77296-e0ca-4f43-8b26-22bc1b00a452">


IPV4-osoite.


<img width="93" alt="ipv4" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/1b50e020-5f3b-4a1b-8990-916c6e4944f8">





# d) Kokeile Saltin file -toimintoa Windowsilla.

Tehtävää varten loin tekstitiedoston työpöydälle ja käytin komentoa ``salt-call --local state.single file.managed C:\users\Maksim\desktop\testi.txt``. Komento toimi onnistuneesti. 



<img width="531" alt="filemanaged" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/43edd8b3-4689-49a5-a512-950f2b51c912">






# e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla. (Voit käyttää apuna edellisten vuosien kotitehtäväraporttia tai Karvinen 2018: Control Windows with Salt. Huomaa, että noissa muistiinpanoissani voi jo hieman ikä painaa, ja niissä on myös epärelevantteja kokeiluja.)

Kokeilin toimintoa, jolla luodaan uusi polku Windowsilla. Käytin komentoa ``salt-call --local state.single win_path.exists C:\users\Maksim\uutta``. Komento näyttäisi onnistuneen.





<img width="438" alt="uutta polkua" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/3ba9cb83-c0bc-4130-8c0a-e8c0b2d6f5dc">










# Lähteet


Salt project, 2023. State modules. Luettavissa: https://docs.saltproject.io/en/latest/ref/states/all/. Luettu: 3.12.2023.

Karvinen, Tero. 2023. Configuration management 2023 autumn. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/. Luettu: 3.12.2023.

Karvinen, Tero. 2018. Control Windows with salt. Luettavissa: https://terokarvinen.com/2018/control-windows-with-salt/. Luettu: 3.12.2023.


