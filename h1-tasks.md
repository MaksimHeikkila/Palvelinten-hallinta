## x) Lue ja tiivistä

# Create a web page using Github (Karvinen 2023)

-Luo käyttäjätunnus Githubiin ja luo uusi arkisto

-Luo uusi tiedosto ja kirjoita sisältö siihen

-Tallenna se .md-muodossa, jotta tiedosto muunnetaan automaattisesti verkkosivuksi

# Run salt command locally (Karvinen 2023)

-Asenna Salt slave komennoilla sudo apt-get update ja sudo apt-get -y install salt-minion

-Linuxissa kaikki asetukset ovat vain tekstitiedostoja

-Viisi tärkeintä Saltin tilafunktiota ovat pkg, file, service, user ja cmd



## a) Asenna Salt (salt-minion) koneellesi.

<img width="412" alt="Salt on nyt asennettu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/650645c2-19d5-459d-aedf-2acdbd8bd1bb">

Saltin asennus kävi melko helposti käyttäen Teron Salt-ohjetta (Karvinen 2023). Itselläni on käytössä Debianin versio 12, joten asennuksessa mentiin sen version ohjeiden mukaan. 

## b) Viisi tärkeintä. Näytä esimerkit viidestä tärkeimmästä Saltin tilafunktiosta: pkg, file, service, user, cmd. Analysoi ja selitä tulokset.

# pkg.installed

Komennolla varmistetaan tässä tapauksessa, että "tree" on asennettu järjestelmään.

<img width="631" alt="pkg" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/eae028e0-a29e-4d18-8c42-8f37c255d9f6">


# file.managed

Hallinnoi tiedostoa. Esimerkiksi tässä tiedostoa /tmp/hellotero

<img width="369" alt="file" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/f8fe38f5-83fd-4eee-92d9-343499f833f0">

# service.running

Varmistaa, että palvelu on käynnissä. Tässä tapauksessani apache2 ei ole käynnissä, eikä se käynnisty automaattisesti.

<img width="628" alt="service" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/a56e0946-d9e4-43b4-808c-b1470eb12af5">

# user

Varmistaa, että käyttäjä on olemassa järjestelmässä. Tässä tapauksessa käyttäjä terote08


<img width="629" alt="user" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/c16165df-24a8-4220-940d-e1017f653457">


<img width="461" alt="user 2" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/1b768a03-7ed3-47a6-93c7-255893f675d4">

# cmd

Suorittaa komennon


<img width="460" alt="cmd" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/64878ddb-a7ec-4c2f-ab75-4a60411d1c4a">



##c) Idempotentti. Anna esimerkki idempotenssista. Aja 'salt-call --local' komentoja, analysoi tulokset, selitä miten idempotenssi ilmenee.

Idempotentti tarkoittaa operaatiota, joka ei vaikuta sovellukseen, johon se kutsutaan, jos sitä kutsutaan useammin kuin kerran samoilla tuloparametreillä (Techopedia 2023). Esimerkkinä voi olla vaikkapa jonkin paketin asentaminen, esimerkiksi nginx. Jos paketti on jo asennettu, sen tila pysyy muuttumattomana, koska se on jo asennettu.


<img width="628" alt="idempotenssi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/8dbd8f9c-865a-4d39-afb1-1f618d4ea221">

Käytännön esimerkki idempotenssista: komento sudo salt-call --local state.single pkg.installed name=nginx kahteen kertaan. " all specified packages are already installed".


##d) Tietoa koneesta. Kerää tietoja koneesta Saltin grains.items -tekniikalla. Poimi kolme kiinnostavaa kohtaa, näytä tulokset ('grains.item osfinger virtual') ja analysoi ne.

<img width="153" alt="osfinger" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/41bbad58-386d-4489-93dc-af232571f38b">


<img width="166" alt="virtual" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/41becd8e-cb87-4cad-b69b-a45a391b6fb8">

Osfinger kertoo, että mikä käyttöjärjestelmä on käytössä ja mikä versio. Minulla on Debian 12. Virtual kertoo, että onko järjestelmä fyysinen vai virtuaalinen.

Muutama kiinnostava kohta:


<img width="160" alt="manufacturer" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/d5b6cab0-082c-46f1-9cdc-e761fa1e2f51">

Yritys, joka loi VirtualBoxin

<img width="176" alt="ipv4" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/bfdb7403-286f-4941-ad5b-ffbbe931c2ab">

ip-osoitteeni


<img width="170" alt="biosreleasedate" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/e8bdcebf-1cc3-4131-981f-029d90e801e1">


BIOSin julkaisupäivämäärä


##Lähteet

Techopedia, 2023. Idempotenssi. Luettavissa: https://fi.theastrologypage.com/idempotence
Tero Karvinen, 2023. Run salt command locally. Luettavissa: https://terokarvinen.com/2021/salt-run-command-locally/
Tero Karvinen, 2023. Create a web page using Github. Luettavissa: https://terokarvinen.com/2023/create-a-web-page-using-github/






