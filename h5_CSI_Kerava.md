# x) Lue ja tiivistä.

-Asenna kaikki manuaalisesti. Asetustiedostot ovat /etc/-hakemistossa.

-Komennolla ``$ sudo find -printf '%T+ M %p\n%A+ A %p\n%C+ C %p\n'|sort`` näet muokatut tiedostot. Komennot ``cat`` ``ls-l`` ja ``less`` näyttävät lisätietoja tiedostoista.

-Käytettäessä komentoa tilassa, on komennosta tehtävä idempotentti.

-``$ sudo salt '*' state.apply apache`` lisää tilan masterilta





# a) CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.

# b) Gui2fs. Muokkaa asetuksia jostain graafisen käyttöliittymän (GUI) ohjelmasta käyttäen ohjelman valikoita ja dialogeja. Etsi tämä asetus tiedostojärjestelmästä.

# c) Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennon.

# d) Apassi. Tee Salt-tila, joka asentaa Apachen näyttämään kotihakemistoja.

# e) Ämpärillinen. Tee Salt-tila, joka asentaa järjestelmään kansiollisen komentoja.
