# h2

31.10.2023 klo 21.51.

a.)

Fuff. Ratkaise Teron ffuf-haastebinääri. Artikkelista Find Hidden Web Directories - Fuzz URLs with ffuf voi olla apua.

Seurasin ohjeita ja latasi harjoitusmaalin dirfutz-1 niiden mukaan.
Laitoin harjoitusmaalin käyntiin. Asensin ffuf ja common.txt.

<img width="653" alt="dirfutz" src="https://github.com/AkiAleksi/h2/assets/112399816/e657c1fb-e418-4eee-8429-1324ae888d92">

Ajoin komennon. $ ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ

<img width="338" alt="eka komento" src="https://github.com/AkiAleksi/h2/assets/112399816/53a54c8d-b1d7-4c71-ba56-63e931469c8e">

Tutkin epähaluttujen vastausten yhteisiä piirteitä. 

<img width="388" alt="tulos" src="https://github.com/AkiAleksi/h2/assets/112399816/feeb79a7-e278-4498-881c-147ad088c811">

Annoin komennon 

<img width="428" alt="tulokset" src="https://github.com/AkiAleksi/h2/assets/112399816/4969fcf8-040c-4637-a267-e3355927c0bd">

Kokeilin päätteitä


<img width="796" alt="vastausa1" src="https://github.com/AkiAleksi/h2/assets/112399816/8e4a4c32-a2f8-4f78-8ce9-ef94dd0d6bc5">



<img width="586" alt="vastausa2" src="https://github.com/AkiAleksi/h2/assets/112399816/d83715da-8337-4291-8456-fc3d641f13b3">


Tehtävä ratkaistu

31.10.2023 klo klo 22:30. 1.11.2023 klo 19:00.

b.)

Ffufme harjoitusmaali asennettu

<img width="132" alt="asennus" src="https://github.com/AkiAleksi/h2/assets/112399816/51204403-f8d9-484d-8de7-be8ccd11f8f7">

Basic content disvovery

<img width="394" alt="eka" src="https://github.com/AkiAleksi/h2/assets/112399816/90cb62ac-b80f-41bd-9b34-dad05b839800">

Content Discovery With Recursion

<img width="373" alt="toka" src="https://github.com/AkiAleksi/h2/assets/112399816/40680b0b-c344-41a3-acc9-a48a3295e459">

Content Discovery With File Extensions

<img width="339" alt="kolme" src="https://github.com/AkiAleksi/h2/assets/112399816/fd428172-e33a-4d28-8f96-78d437fa055c">

No 404 status


<img width="404" alt="4" src="https://github.com/AkiAleksi/h2/assets/112399816/a57b1dea-7953-47ed-9874-9daf505230af">


<img width="400" alt="5" src="https://github.com/AkiAleksi/h2/assets/112399816/8e0233ed-2989-4c6c-8f7e-54e070553c8f">

Param Mining

<img width="411" alt="6" src="https://github.com/AkiAleksi/h2/assets/112399816/f5be78dd-ab45-4bfc-a2a4-0c363f853339">

Rate Limited

<img width="476" alt="fail1" src="https://github.com/AkiAleksi/h2/assets/112399816/80c292fe-0b87-4552-bfd2-ec26c7fe1424">

1.11.2023 klo 20:27. 2.11.2023 klo 11:34.

c.)
Porttiskannaa paikallinen kone (127.0.0.2 tms), sieppaa liikenne snifferillä, analysoi.
nmap TCP connect scan -sT "Oma ip-osoite"

<img width="498" alt="nmap" src="https://github.com/AkiAleksi/h2/assets/112399816/a3f5c2ee-8f8c-4293-92d1-de0db16c23e0">

Mysql palvelin. 

<img width="1078" alt="scan mysql" src="https://github.com/AkiAleksi/h2/assets/112399816/1b67151f-7e68-4af8-b2b4-0b1e7f68113b">

Yleinen skannaus.

<img width="1030" alt="scan general" src="https://github.com/AkiAleksi/h2/assets/112399816/6d593019-2ec1-4d6b-a4e5-edfac168393d">


tauko 2.11.2023 klo 11:44. 2.11.2023 klo 15:49

d.)

<img width="510" alt="ss" src="https://github.com/AkiAleksi/h2/assets/112399816/6e03d288-15a4-4a2d-8230-1651552a9eb8">

<img width="1065" alt="nod" src="https://github.com/AkiAleksi/h2/assets/112399816/ca364b5f-fde7-4159-9ada-46be91725798">

<img width="1075" alt="d1" src="https://github.com/AkiAleksi/h2/assets/112399816/64e8d3ff-7dd2-4792-bd85-846bea30aed9">

e.)

<img width="491" alt="-sn" src="https://github.com/AkiAleksi/h2/assets/112399816/f44f9e37-4415-4a4a-ac36-8ad88c19e3eb">

<img width="918" alt="-sn noresult" src="https://github.com/AkiAleksi/h2/assets/112399816/734a7b35-0aa2-4859-902f-e8b4d05d5ebd">

f.)

<img width="1054" alt="-Pn" src="https://github.com/AkiAleksi/h2/assets/112399816/b27db739-661c-4e86-9742-2465e661e045">


<img width="1130" alt="-Pn common" src="https://github.com/AkiAleksi/h2/assets/112399816/87f62ea1-349b-45b5-90d1-382d701b264e">

g.)

<img width="1059" alt="-sV" src="https://github.com/AkiAleksi/h2/assets/112399816/c5cc8da7-5985-44e9-bee4-e7e86c38ed65">

h.)
tulokset.nmap
 Nopea tarkistus skannauksen tuloksista ja yleinen ymmärrys avoimista porteista ja palveluista.
 
<img width="601" alt="h" src="https://github.com/AkiAleksi/h2/assets/112399816/1cfeaee0-ce08-42a2-8087-af709e98d8fd">

tulokset.gnamp
 Automaattinen tietojen käsittely ja analyysi skripteissä tai ohjelmissa.
 
<img width="619" alt="Screenshot 2023-11-02 at 17 03 35" src="https://github.com/AkiAleksi/h2/assets/112399816/7f09efbc-b3d1-4e9b-b541-64d4f17354fe">

tulokset.xml
Tarkempi analyysi ja tietojen käsittely ohjelmissa, joissa XML-tiedot voidaan jäsentää ja käsitellä automaattisesti.

<img width="1680" alt="Screenshot 2023-11-02 at 17 05 22" src="https://github.com/AkiAleksi/h2/assets/112399816/5bb87784-dd99-4961-85bb-fb27146a9ffb">


skanna

i.)

<img width="676" alt="Screenshot 2023-11-02 at 17 45 52" src="https://github.com/AkiAleksi/h2/assets/112399816/0f1df28d-2736-4d1b-b9fd-42e2c4a1369a">

Tämä komento käyttää -vv-näppäintä, joten näet paljon yksityiskohtia skannauksesta. -sS-näppäin määrittelee SYN-skannauksen, joka on yksi Nmapin perusskannausmenetelmistä. -Pn-näppäin ohittaa ping-skannauksen ja mahdollistaa skannauksen vaikka kohde ei vastaisi ping-pyyntöihin.

j.)

<img width="1042" alt="Screenshot 2023-11-02 at 18 04 26" src="https://github.com/AkiAleksi/h2/assets/112399816/d2f1fd75-1881-47dc-8074-4930dda68356">


k.)

<img width="600" alt="Screenshot 2023-11-02 at 17 56 33" src="https://github.com/AkiAleksi/h2/assets/112399816/122ae0da-c6e4-482d-93bc-92a9aa7c8e80">

<img width="1069" alt="Screenshot 2023-11-02 at 17 58 05" src="https://github.com/AkiAleksi/h2/assets/112399816/38fbb8b8-2f3c-47ab-a71b-411a5e7c0313">

l.)

UDP-skannaus on hankalaa ja epäluotettavaa useista syistä. Ei-yhteysorientoitunut protokolla,
puuttuvat vahvistukset, palomuurisuodatus, monet suljetut palvelut ja vasteaika.

2.11.2023 klo 18:10.
