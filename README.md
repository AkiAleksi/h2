# h2

Tehtävien tekeminen alkaa 31.10.2023 klo 21.51.

# x
Videomateriaali:

Hoikkala "joohoi" 2020: Still Fuzzing Faster (U fool). In HelSec Virtual meetup #1. (about 1 hour)

Tiivistelmä:

-web fuzzer on tietoturvatyökalu

-Fuzzing on menetelmä, jossa syötetään suuri määrä satunnaista dataa 
,jotta voidaan tarkkailla järjestelmän reagointia tälläiseen syötteeseen.

-Web-fuzzerit toimivat usein HTTP-protokollan päällä ja lähettävät HTTP-pyyntöjä sovelluksen eri osiin satunnaisesti muokatuilla tai manipuloiduilla syötteillä.

-Fuff on joohoi:n luoma web fuzzer

-Fuff tarvitsee sanakirjan. Esim. Yleiset verkkopolkuosoitteet.

-fuff korvaa kohde url:sta FUZZ kohdan sanakirjasta tuleville sanoilla.

-ffuf vastauksia voi filtteröidä.

# a.)

Tehtävänanto:

Can you find two URLs: Admin page and Version control related page

Seurasin ohjeita ja latasin harjoitusmaalin dirfutz-1 niiden mukaan.
Laitoin harjoitusmaalin käyntiin. Asensin myös ffuf ja common.txt.

<img width="653" alt="dirfutz" src="https://github.com/AkiAleksi/h2/assets/112399816/e657c1fb-e418-4eee-8429-1324ae888d92">

Ajoin komennon. $ ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ

<img width="338" alt="eka komento" src="https://github.com/AkiAleksi/h2/assets/112399816/53a54c8d-b1d7-4c71-ba56-63e931469c8e">

Tutkin epähaluttujen vastausten yhteisiä piirteitä. Vaikuttaisi, että niiden koko on 154 bittiä.
Filtteröin sillä. 


<img width="388" alt="tulos" src="https://github.com/AkiAleksi/h2/assets/112399816/feeb79a7-e278-4498-881c-147ad088c811">

Annoin komennon $ ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 154.

<img width="428" alt="tulokset" src="https://github.com/AkiAleksi/h2/assets/112399816/4969fcf8-040c-4637-a267-e3355927c0bd">

Sain päätteet wp-admin ja .git. Kokeilin päätteitä.


<img width="796" alt="vastausa1" src="https://github.com/AkiAleksi/h2/assets/112399816/8e4a4c32-a2f8-4f78-8ce9-ef94dd0d6bc5">



<img width="586" alt="vastausa2" src="https://github.com/AkiAleksi/h2/assets/112399816/d83715da-8337-4291-8456-fc3d641f13b3">


Tehtävä ratkaistu

31.10.2023 klo klo 22:30. 1.11.2023 klo 19:00.

# b.)

Ffufme harjoitusmaali asennettu

<img width="132" alt="asennus" src="https://github.com/AkiAleksi/h2/assets/112399816/51204403-f8d9-484d-8de7-be8ccd11f8f7">

# Basic content disvovery

Ajoin komennon ffuf -w ~/words/common.txt -u http://ffuf.me/cd/basic/FUZZ. Pitäis löytyä class ja development.log.


<img width="394" alt="eka" src="https://github.com/AkiAleksi/h2/assets/112399816/90cb62ac-b80f-41bd-9b34-dad05b839800">


class ja development.log tiedostot löytyi.

# Content Discovery With Recursion

Ajoin komennon ffuf -w ~/words/common.txt -recursion -u http://ffuf.me/cd/recursion/FUZZ
Pitäisi löytyä /admin, /admin/users ja /admin/users/96

<img width="373" alt="toka" src="https://github.com/AkiAleksi/h2/assets/112399816/40680b0b-c344-41a3-acc9-a48a3295e459">

Löytyi!

# Content Discovery With File Extensions

Ajoin komennon ffuf -w ~/wordlists/common.txt -e .log -u http://ffuf.me/cd/ext/logs/FUZZ.
Pitäisi löytyä /logs/users.log

<img width="339" alt="kolme" src="https://github.com/AkiAleksi/h2/assets/112399816/fd428172-e33a-4d28-8f96-78d437fa055c">

Löytyi!

# No 404 status

Ajoin ensin komennon ffuf -w ~/wordlists/common.txt -u http://ffuf.me/cd/no404/FUZZ.
Sen jälkeen filtteröin 669 bitillä. 

<img width="404" alt="4" src="https://github.com/AkiAleksi/h2/assets/112399816/a57b1dea-7953-47ed-9874-9daf505230af">







<img width="400" alt="5" src="https://github.com/AkiAleksi/h2/assets/112399816/8e0233ed-2989-4c6c-8f7e-54e070553c8f">

Sain halutun vastauksen secret.


# Param Mining

Ajoin komennon ffuf -w ~/words/parameters.txt -u http://ffuf.me/cd/param/data?FUZZ=1

<img width="411" alt="6" src="https://github.com/AkiAleksi/h2/assets/112399816/f5be78dd-ab45-4bfc-a2a4-0c363f853339">

Löysin puuttuvan parametrin debug.

# Rate Limited

Ajoin komennon: ffuf -w ~/wordlists/common.txt -u http://ffuf.test/cd/rate/FUZZ -mc 200,429

Komennon ei ollut tarkoituskaan toimia. Sain erroreita enkä löytänyt oraclea.

Sen jälkeen ajoin komennon: ffuf -w ~/words/common.txt -t 5 -p 0.1 -u http://ffuf.test/cd/rate/FUZZ -mc 200,429


<img width="476" alt="fail1" src="https://github.com/AkiAleksi/h2/assets/112399816/80c292fe-0b87-4552-bfd2-ec26c7fe1424">

Sain saman vastauksen kuin aikaisemminkin. Errorit tulevat yhä edelleen eikä oraclea löydy.
En saanut tätä komentoa toimimaan valitettavasti, vaikka yritin pitkään. Tämä kohta jäi valitettavasti ratkaisematta.

1.11.2023 klo 20:27. 2.11.2023 klo 11:34.

# c.)

Porttiskannasin oman koneeni.
nmap TCP connect scan -sT "Oma ip-osoite"

<img width="498" alt="nmap" src="https://github.com/AkiAleksi/h2/assets/112399816/a3f5c2ee-8f8c-4293-92d1-de0db16c23e0">

sieppaa liikenteen wiresharkilla. Mysql palvelin, joka on päällä portissa 3306 näkyy sieppauksessa.
Portti vastaa. Se on auki.

<img width="1078" alt="scan mysql" src="https://github.com/AkiAleksi/h2/assets/112399816/1b67151f-7e68-4af8-b2b4-0b1e7f68113b">


Sieppauksessa näkyy kiinni olevat portit. Yritetty ottaa yhteys, mutta ei vastausta.


<img width="1030" alt="scan general" src="https://github.com/AkiAleksi/h2/assets/112399816/6d593019-2ec1-4d6b-a4e5-edfac168393d">


tauko 2.11.2023 klo 11:44. 2.11.2023 klo 15:49

# d.)

nmap -Ss "oma IP-osoite". (Stealth Scan)


<img width="510" alt="ss" src="https://github.com/AkiAleksi/h2/assets/112399816/6e03d288-15a4-4a2d-8230-1651552a9eb8">

Lähettää SYN-paketteja portteihin. Kiinni olevat portit eivät vastaa.

<img width="1065" alt="nod" src="https://github.com/AkiAleksi/h2/assets/112399816/ca364b5f-fde7-4159-9ada-46be91725798">



# e.)
nmap -sn <kohde>

<img width="590" alt="onni2" src="https://github.com/AkiAleksi/h2/assets/112399816/0bc906dd-01c3-4ba3-85a1-85c9f16da275">

Komento nmap -sn <kohde> lähettää ping-pyynnöt määritettyyn kohdeosoitteeseen. Nmap sai vastauksen ping-pyynnöistä, se merkitsi koneen eläväksi (1 host up). 

<img width="1102" alt="onni" src="https://github.com/AkiAleksi/h2/assets/112399816/f20702a3-69a6-447a-bb4b-e9118a6ff7ef">




# f.)

Sieppauksessa näkyy nmap -Pn <kohde> tulokset.

<img width="1054" alt="-Pn" src="https://github.com/AkiAleksi/h2/assets/112399816/b27db739-661c-4e86-9742-2465e661e045">


<img width="1130" alt="-Pn common" src="https://github.com/AkiAleksi/h2/assets/112399816/87f62ea1-349b-45b5-90d1-382d701b264e">



# g.)

Käytin suodatinta. Suodatin itselleni HTTP-palvelimen. 
Kaikki palvelimet eivät välttämättä käytä versionumeroa 'Server', turvallisuussyistä.
En löytänyt 'Server' kohtaa pyyntöjen tai vastausten otsakkeista.
En saanut palvelimen tarkkaa versiota.

<img width="1190" alt="xd" src="https://github.com/AkiAleksi/h2/assets/112399816/ffed14f1-e963-468d-aeeb-90f070ba9c65">




# h.)

Ajoin komennon nmap output files -oA foo. 
Sillä sain kolme tiedosto tyyppiä tulokset.nmap, tulokset.gnamp ja tulokset.xml.

tulokset.nmap
 Nopea tarkistus skannauksen tuloksista ja yleinen ymmärrys avoimista porteista ja palveluista.
 
<img width="601" alt="h" src="https://github.com/AkiAleksi/h2/assets/112399816/1cfeaee0-ce08-42a2-8087-af709e98d8fd">

tulokset.gnamp
 Automaattinen tietojen käsittely ja analyysi skripteissä tai ohjelmissa.
 
<img width="619" alt="Screenshot 2023-11-02 at 17 03 35" src="https://github.com/AkiAleksi/h2/assets/112399816/7f09efbc-b3d1-4e9b-b541-64d4f17354fe">

tulokset.xml
Tarkempi analyysi ja tietojen käsittely ohjelmissa, joissa XML-tiedot voidaan jäsentää ja käsitellä automaattisesti.

<img width="1680" alt="Screenshot 2023-11-02 at 17 05 22" src="https://github.com/AkiAleksi/h2/assets/112399816/5bb87784-dd99-4961-85bb-fb27146a9ffb">




# i.)

<img width="676" alt="Screenshot 2023-11-02 at 17 45 52" src="https://github.com/AkiAleksi/h2/assets/112399816/0f1df28d-2736-4d1b-b9fd-42e2c4a1369a">

Käytin ajonaikaisia toimintoja
Tässä komennossa on -vv-näppäin. Se kertoo paljon yksityiskohtia skannauksesta. -sS-näppäin määrittelee SYN-skannauksen, joka on yksi Nmapin perusskannausmenetelmistä. -Pn-näppäin ohittaa ping-skannauksen ja mahdollistaa skannauksen vaikka kohde ei vastaisi ping-pyyntöihin. Lähde chatGPT: https://chat.openai.com/auth/login

# j.)

nmap skannauksessa yritetään selvittää,
mitkä portit ovat auki palvelimella.
Sieppauksessa näkyy useita peräkkäisiä porttipyyntöjä samasta lähteestä.
Se on merkki skannauksesta.

<img width="1183" alt="piilo" src="https://github.com/AkiAleksi/h2/assets/112399816/5036a13d-3b32-4f39-909a-78db2207182c">

nmap skannauksen piilottaminen on haasteellista.

# k.)
Ajoin nmap -sU <Oma IP osoite>


<img width="600" alt="Screenshot 2023-11-02 at 17 56 33" src="https://github.com/AkiAleksi/h2/assets/112399816/122ae0da-c6e4-482d-93bc-92a9aa7c8e80">

vastauksessa näkyy UDP-paketteja, jotka on lähetetty tiettyihin portteihin.
Pyritään selvittämään, ovatko ne avoinna vai suljettuja.

<img width="1204" alt="kokk" src="https://github.com/AkiAleksi/h2/assets/112399816/f4933ff8-ec9f-4e35-8c67-23df7211dc5a">



<img width="1069" alt="Screenshot 2023-11-02 at 17 58 05" src="https://github.com/AkiAleksi/h2/assets/112399816/38fbb8b8-2f3c-47ab-a71b-411a5e7c0313">

# l.)
Lähde https://windowsbulletin.com/fi/suorita-verkkoporttiskannaus-porttiskannerilla/

UDP ei vaadi yhteyden muodostamista ja on epäluotettava. 
Tiedot lähetetään määräpaikasta riippumatta. Siksi ei ole takeita siitä, että tiedot pääsevät sinne.


2.11.2023 klo 18:10.
