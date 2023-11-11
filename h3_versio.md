# a) Online. Tee uusi varasto GitHubiin (tai Gitlabiin tai mihin vain vastaavaan palveluun). Varaston nimessä ja lyhyessä kuvauksessa tulee olla sana "winter". Aiemmin tehty varasto ei kelpaa. (Muista tehdä varastoon tiedostoja luomisvaiheessa, esim README.md ja GNU General Public License 3)

Luodaan uusi varasto Githubiin. Nimessä ja kuvauksessa on mainittu sana "winter".


<img width="537" alt="uusi varasto" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/28894319-f32f-43ac-a5b1-8b27cc2a9aac">


Myös readme.md on luotu.



<img width="689" alt="readme" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/b1aeb552-cc35-410c-8660-7c87f91a3460">





# b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi, tee muutoksia, puske ne palvelimelle, ja näytä, että ne ilmestyvät weppiliittymään.



Tarvitsemme jatkaaksemme Git bashin. Mennään osoitteeseen https://git-scm.com/download/win ja ladataan se Windowsille.


<img width="495" alt="git bash" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/7a51bfb2-e94e-4e77-858e-52484722d812">



Suoritetaan asennus vaihe vaiheelta.


<img width="372" alt="asennus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/615efdc4-d2e7-489d-baa6-807176e0b60f">


Asennus on valmis. Tarkistetaan vielä, että Git on asennettu komennolla git version


<img width="310" alt="tarkistus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/757cdd05-ad11-4139-a1b3-9123eb24d7b3">


Avataan se


<img width="376" alt="valmis" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/ea3880fc-d497-42a1-8ddf-13cd50f8ea7e">


Työskentelen päähakemistossani.


<img width="324" alt="päähakemisto" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/7368d4be-5dbd-4680-b684-f754e325a974">


Aion käyttää SSH-osoitetta kloonaukseen. Githubin artikkeli auttoi minua tässä tehtävässä. Ajoin Windowsin Powershellillä komennon ssh-keygen -o -t rsa -C "key to winter  repo"


<img width="419" alt="luotu on" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/a8ad2ae7-0cde-4fd2-9831-8eb794ae1ad2">




Vaihdetaan hakemisto ssh-hakemistoon ja käydään vielä tarkistamassa, että avain on luotu. Kyllähän se näköjään on.


<img width="314" alt="noin" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/4885ab05-f748-41b4-ab61-85bad0626f36">




Tämän jälkeen lisätään uusi avain SSH-agenttiin. Avasin Powershellin järjestelmänvalvojan oikeuksilla ja käynnistin agentin komennoilla Get-Service -Name ssh-agent | Set-Service -StartupType Manual, sen jälkeen Start-Service ssh-agent ja sitten ssh-add yksityisen avaimen polku.



Navigoin sijaintiin, johon SSH-avain on tallennettu ja avasin avaimen muistiolla. Kopioin sisällön.


<img width="600" alt="navigoi" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/025c33b7-6b39-4d76-b103-0dc1ecddf54b">



Liitin avaimen Github- asetuksissani kohtaan "SSH keys"


<img width="695" alt="key" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/10cbc713-ccf5-401b-a2ba-f13aefafb594">


Seuraavaksi otetaan SSH-yhteys Githubiin Git bashilla. Avasin Git bashin ja syötin komennon ssh -T git@github.com. Yhteys muodostettiin, mutta sain ilmoituksen " the authenticity of host cannot be established, are you sure you want to connect?" kirjoitin yes ja autentikointi onnistui.


<img width="459" alt="gitti" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/34d95b3f-3fb1-4241-9f25-2355db7da76d">


Sen jälkeen käytin komentoja git config --global user.email "maukka.heikkila98@gmail.com" ja git config --global user.name "MaksimHeikkila" puskeakseni tiedot Githubiin.


<img width="452" alt="sen jälkeen" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/64f56739-ac70-439b-9a6d-2414f1dd4d4f">

Sitten aletaan kloonaamaan itse varastoa. Mennään kopioimaan repositoryn SSH-osoite tuolta noin



<img width="692" alt="tuolta noin" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/3cf244ce-01bc-4df8-89b7-b7169d8cd2f7">


SSH-osoitteen kopioituani siirryn Git Bashiin ja ajan komennon git clone git@github.com:MaksimHeikkila/Winter.git, jonka jälkeen tarkistan, että onnistuiko komennolla cd winter. Hakemisto löytyy.


<img width="444" alt="winterrrrrrr" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/b88b48f9-0c6a-4ac7-9ab0-204a128733d8">


Seuraavaksi luodaan varastoon uusi tiedosto. Siirrytään hakemistoon winter ja testataan komentoa nano push.md, eli luodaan tekstitiedosto varastoon. Lisäsin tiedostoon tekstiä.


<img width="451" alt="tstataa" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/25af76f2-b9c9-4c97-98e4-abfab26e8061">


Tarkistin vielä ls-komennolla, että tekstitiedosto on tallentunut:



<img width="266" alt="tarkistus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/25b6f437-fe08-4e27-8fed-2589c1d8d430">


Pusketaan tiedostot git add --all komennolla. Komento puskee kaikki tiedostot.


<img width="443" alt="jepejp" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/253e7652-eb75-40c4-8a58-f201ce155627">



Seuraavaksi commit komennolla git commit -m "Pusketaan uusi tiedosto GitHubiin". Yksi tiedosto lisätty insertioniin.



<img width="283" alt="insertion" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/3fdf264c-34d7-4ad1-9bda-c855072366de">



Sitten pusketaan itse tiedosto Githubiin komennolla git push. Lopputulos:



<img width="345" alt="lopputulos" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/f793ce1c-d4b4-4967-865d-f96dd0ca1205">



Katsotaan löytyykö tiedosto Githubista ja löytyyhän se.


<img width="680" alt="pushed" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/61388b1a-a9ac-4a76-8060-5acf603e6732">







# c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

Tein tyhmän muutoksen push.md tiedostoon. Komento: nano push.md


<img width="453" alt="tyhmä" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/3bbb122d-fad4-4457-a74c-cb92c978e9b1">


Komennolla cat push.md varmistetaan, että muutos tuli tehtyä


<img width="459" alt="tarkastus" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/2dff06e6-beb7-494b-a4e1-2862c3dfc404">



git reset --hard komennolla tuhoan äskeiset tyhmät muutokset. cat push.md tarkistetaan, että tulivatko muutokset voimaan ja kyllähän ne tulivat.


<img width="327" alt="peruttu" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/cd04946d-3ce0-4515-aea9-1d1680873151">






# d) Tukki. Tarkastele ja selitä varastosi lokia. Tarkista, että nimesi ja sähköpostiosoitteesi näkyy haluamallasi tavalla ja korjaa tarvittaessa.


Tarkastellaan vähän varaston lokia. Komento git log antaa seuraavan näkymän. Lokitiedoissa näkyy tekijän nimi ja päivämäärä. Lokimuutokset näkyvät oikein. Siellä näkyy esim. alkuperäinen commit ja viesti.


<img width="431" alt="lokia" src="https://github.com/MaksimHeikkila/Palvelinten-hallinta/assets/148875816/39edc236-a8ba-4f38-8a47-f23749df76c7">
















# Lähteet

Karvinen, 2023. Infra as code 2023. Luettavissa: https://terokarvinen.com/2023/configuration-management-2023-autumn/#h3-versio. Luettu 11.11.2023

Github inc. Cloning a repository. Luettavissa: https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository. Luettu 11.11.2023

Bitbucket support. Add, edit and commit to source files. Luettavissa: https://support.atlassian.com/bitbucket-cloud/docs/add-edit-and-commit-to-source-files/. Luettu 11.11.2023

Atlassian. What is Git? Luettavissa: https://www.atlassian.com/git/tutorials/what-is-git. Luettu 11.11.2023

Github inc. Connecting to github with ssh. Luettavissa: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection. Luettu 11.11.2023

Cameron McKenzie, 2023. How to git push an existing project to Github. Luettavissa: https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-push-an-existing-project-to-GitHub. Luettu 11.11.2023

Cameron McKenzie, 2023. How to SSH into Github on Windows example. Luettavissa: https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/GitHub-SSH-Windows-Example. Luettu 11.11.2023





