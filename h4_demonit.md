# Johdanto

Tein tehtävät HP Pavilion- kannettavallani. Tarkemmat speksit ovat: 8 GT RAM, Intel(R) Core(TM) i5-8265U CPU ja Windows 10 Home.


# x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves

- Komennoilla $ sudo mkdir -p /srv/salt/hello ja $ sudoedit /srv/salt/hello/init.sls saadaan luotua uusi hakemisto ja muokataan SLS-tiedostoa.
  
- Nämä komennot kirjoitetaan SLS:ään: $ cat /srv/salt/hello/init.sls
/tmp/infra-as-code:
  file.managed
  $ sudo salt '*' state.apply hello
  
- $ sudo salt '*' state.apply hello^C, $ sudoedit /srv/salt/top.sls ,$ cat /srv/salt/top.sls
base:
  '*':
    - hello : näillä komennoilla lisätään "hello"-tila kaikille minioneille.





# a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.







# b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".








# c) Apache. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.








# d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.













# Lähteet




