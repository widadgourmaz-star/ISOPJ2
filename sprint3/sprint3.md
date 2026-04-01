### Administració de Dominis i Seguretat

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/2131e7d9-ca4a-4d85-ad58-6492063f7d78" />


### Configuració LDAP - Servidor
primer en servidor canviem el hostname

<img width="883" height="177" alt="image" src="https://github.com/user-attachments/assets/86d572f8-eab2-4393-b6ae-a1859f25d8ac" />

he instalat el paquet ldap-utils i slapd.

<img width="565" height="53" alt="image" src="https://github.com/user-attachments/assets/bef987f8-750c-4905-93b3-d1f2ed08d380" />


<img width="716" height="276" alt="image" src="https://github.com/user-attachments/assets/4c2463ac-66e3-4426-8e69-535812736232" />

He configurat la IP a estatica en el servidor, perque sempre hem de tenir la IP fixa

<img width="707" height="366" alt="image" src="https://github.com/user-attachments/assets/3a3fdf38-8e33-4750-ac93-5f55bc2038cf" />


<img width="585" height="459" alt="image" src="https://github.com/user-attachments/assets/f6035c64-5b36-4edb-acc9-9187f7fcedf6" />

### Creació i configuració servidors

despres passem a la gestió de la configuració

<img width="708" height="518" alt="image" src="https://github.com/user-attachments/assets/96f53db8-5f42-4c50-9c74-21e168f8676a" />


<img width="551" height="412" alt="image" src="https://github.com/user-attachments/assets/0bef92fa-66a4-4468-b32a-bae8edea0785" />


<img width="597" height="433" alt="image" src="https://github.com/user-attachments/assets/7fb16774-491d-431d-be52-6c4ae6b4da7b" />

li diem que no volem que s'esborri la base de dades

<img width="605" height="110" alt="image" src="https://github.com/user-attachments/assets/dee714e2-100d-45c1-b97b-95fecf97f66a" />

he modificat el ou.ldif

<img width="768" height="688" alt="image" src="https://github.com/user-attachments/assets/73447ee5-ab13-4ff4-b427-972f39ba6cfe" />

### Població i Verificació del Directori LDAP
#### servidor

primer intallem libnss-ldap libpam-ldap nscd -y i verifequem que s`hagi creat correctament


<img width="720" height="471" alt="image" src="https://github.com/user-attachments/assets/66dca740-1659-485b-a520-102d62472a66" />

<img width="669" height="411" alt="image" src="https://github.com/user-attachments/assets/87e4b8c8-a1ad-49e3-81b2-2bdd216a6b13" />

<img width="697" height="531" alt="image" src="https://github.com/user-attachments/assets/13254b0b-3b40-4a25-b3e7-2d94629af84e" />

<img width="698" height="497" alt="image" src="https://github.com/user-attachments/assets/1c7b9f27-3e06-4b55-9c01-e6c4031bf190" />

<img width="687" height="344" alt="image" src="https://github.com/user-attachments/assets/e0d4f4da-96aa-46cc-a0ff-6bc9857e456f" />

<img width="675" height="353" alt="image" src="https://github.com/user-attachments/assets/7c2c12e3-0044-4406-a778-0a9994d260ff" />

<img width="554" height="246" alt="image" src="https://github.com/user-attachments/assets/d580f430-9bf3-4654-a903-92d476a95ef9" />

<img width="668" height="316" alt="image" src="https://github.com/user-attachments/assets/a91fd8b1-ad47-4413-a6e0-5ebe6122347f" />

### Configuració de Clients i Proves d’Autenticació LDAP

Un cop el servidor ja està operatiu i amb les dades carregades, el següent pas és configurar el sistema d’autenticació perquè aquest mateix servidor —o altres equips clients— puguin identificar i validar els usuaris que es troben al directori LDAP.
Per fer aquesta integració amb els mecanismes d’autenticació del sistema (NSS i PAM), cal instal·lar els paquets corresponents: libnss-ldapd, libpam-ldapd i nscd. Aquests paquets permeten que el sistema consulti el servidor LDAP quan necessita informació d’usuaris o processos d’autenticació.

<img width="734" height="219" alt="image" src="https://github.com/user-attachments/assets/1352cb8b-45d6-4e49-b7f5-996c4b977ff4" />

<img width="708" height="386" alt="image" src="https://github.com/user-attachments/assets/8d7004e0-9d9c-418b-bd6a-8849aff65a3a" />

<img width="717" height="330" alt="image" src="https://github.com/user-attachments/assets/9e35484c-a2f6-41c2-a521-952750f4cd8d" />

<img width="707" height="279" alt="image" src="https://github.com/user-attachments/assets/b9a642e0-4859-4602-ac66-d968b70a65bb" />

<img width="704" height="314" alt="image" src="https://github.com/user-attachments/assets/b5297554-93b8-4569-80c0-c2343dad2f26" />

<img width="660" height="234" alt="image" src="https://github.com/user-attachments/assets/2f813cb6-546f-4c5b-8d0e-f5b9bf960d45" />

<img width="574" height="279" alt="image" src="https://github.com/user-attachments/assets/c77aa4fd-71db-4f3c-9995-8c9d32cdbde4" />

<img width="690" height="263" alt="image" src="https://github.com/user-attachments/assets/f0ee6e7c-bf40-4f5d-84bf-34d53625e3e6" />

<img width="704" height="425" alt="image" src="https://github.com/user-attachments/assets/c969db70-0177-4be8-8d65-a4964ed1a5ed" />

<img width="730" height="431" alt="image" src="https://github.com/user-attachments/assets/695c40b7-59b4-47ac-a300-989091fa69df" />

<img width="1000" height="441" alt="image" src="https://github.com/user-attachments/assets/d24b1dca-f7d8-43ac-ac5c-7363e35e40e7" />

<img width="995" height="441" alt="image" src="https://github.com/user-attachments/assets/8ee8089e-5a4e-4963-af20-95b59d76ab24" />

<img width="817" height="175" alt="image" src="https://github.com/user-attachments/assets/18496735-237d-44d8-8495-8f96de08dfdf" />

<img width="635" height="77" alt="image" src="https://github.com/user-attachments/assets/232965da-1f57-45fa-9e17-1c3604e4d837" />

<img width="336" height="63" alt="image" src="https://github.com/user-attachments/assets/faf27ef3-f27d-4a3d-8e93-7075255e2720" />

### Entorn Gràfic
Per a configurar LDAP en un entorn gràfic tenim moltes opcions com ara:

- phpldapadmin
- apache directory stdio
- jxplorer
- ldap account manager (LAM)
  ### Requeriments Prèvis

<img width="910" height="559" alt="image" src="https://github.com/user-attachments/assets/6cd336be-14f1-4bf2-9676-454647cc4938" />

<img width="899" height="146" alt="image" src="https://github.com/user-attachments/assets/77946ccb-6123-4ff8-b094-3fd0237bc794" />

<img width="1406" height="498" alt="image" src="https://github.com/user-attachments/assets/226aff1e-ca05-40d0-ba07-54587595068b" />

<img width="1452" height="899" alt="image" src="https://github.com/user-attachments/assets/b0c59b21-5515-4ba7-9bd0-dc81a6b4cce1" />

<img width="1219" height="644" alt="image" src="https://github.com/user-attachments/assets/d14d1a7e-1468-416f-b5e3-3fdade0558e4" />

<img width="1044" height="308" alt="image" src="https://github.com/user-attachments/assets/fa770edf-8ec7-4636-8ec7-ccad7bef39bb" />

<img width="600" height="372" alt="image" src="https://github.com/user-attachments/assets/61b46382-f638-408f-98eb-d593339ec5c1" />

<img width="1534" height="447" alt="image" src="https://github.com/user-attachments/assets/79ee1934-3d0e-47e7-b0d3-c0f3c77e4649" />

### creacio de una nova OU
Pprimer hem d'anar a "Tools" i "OU Editor".

<img width="1184" height="280" alt="image" src="https://github.com/user-attachments/assets/f37d7242-5139-4d35-90e5-6692836126da" />

<img width="1205" height="410" alt="image" src="https://github.com/user-attachments/assets/2321e264-bb3b-4d64-82e6-02062172f35d" />

ja tenim creada 

<img width="1091" height="293" alt="image" src="https://github.com/user-attachments/assets/470b3ffb-16a1-4a21-9106-98433096cd91" />

### creació d'un nou grup
per a crear un nou grup primer hem d'anar a "Accounts" i "Groups2.

<img width="1075" height="191" alt="image" src="https://github.com/user-attachments/assets/13d8352e-2182-41e6-a984-e565fb6cea00" />

I aqui anirem a "New Group"

<img width="1651" height="334" alt="image" src="https://github.com/user-attachments/assets/2f35de6b-801c-4254-9eaf-adcba9ab9ded" />

Ifinalment cream el grup, amb aquest cas li fiquem un nom i un UID

<img width="1449" height="367" alt="image" src="https://github.com/user-attachments/assets/26ee6815-c080-4111-a54c-646064b41753" />

s'ha creat correctament 

<img width="1030" height="182" alt="image" src="https://github.com/user-attachments/assets/9f7baf75-decb-4e78-9644-6a3106ee3558" />

<img width="1516" height="378" alt="image" src="https://github.com/user-attachments/assets/50fa3120-7c6f-4b7d-81bf-2826779a4283" />

### creació d'un nou usuari 
primer hem d'anar "Accounts" i despres a "Users".

<img width="1266" height="193" alt="image" src="https://github.com/user-attachments/assets/b4426bd9-3a63-43d0-90d3-cce7b909e6a7" />

Un cop a la pestanya d'usuaris, fem clic a "New user" per obrir el formulari de creació. A la pestanya **Personal** omplim el nom i cognoms de l'usuari. En el nostre cas: First name: `Widad`, Last name: `Gourmaz`.

![Formulari Personal - creació usuari](EntornGrafic/2.png)

A la pestanya **Unix** configurem el nom d'usuari (`wgourmaz`), el grup principal (`SPR3WIDAD`), el directori home (`/home/$user`) i la shell (`/bin/bash`).

![Pestanya Unix - configuració usuari](EntornGrafic/3.png)

Fem clic a **Set password** per establir la contrasenya de l'usuari. Introduïm la contrasenya dues vegades i confirmem amb **Ok**.

![Establir contrasenya de l'usuari](EntornGrafic/4.png)

Un cop guardat, apareix el missatge de confirmació: **LDAP operation successful. Account was created successfully.**

![Confirmació de creació de l'usuari](EntornGrafic/5.png)

Tornem a la llista d'usuaris i podem veure que l'usuari `wgourmaz` (Widad Gourmaz) apareix correctament a la llista amb UID 10000 i GID 1234.

![Llista d'usuaris amb el nou usuari creat](EntornGrafic/6.png)

Per verificar que l'usuari s'ha creat correctament al sistema, executem la comanda `id` com a l'usuari `wgourmaz`:

```bash
id
```

![Verificació amb la comanda id](EntornGrafic/7.png)

La sortida mostra: `uid=10000(wgourmaz) gid=1234(SPR3WIDAD) grups=1234(SPR3WIDAD)`, confirmant que l'usuari existeix al domini.

## Gestió del domini mitjançant comandes

En aquest apartat gestionem el domini LDAP directament des de la línia de comandes, sense entorn gràfic.

### Exercicis plantejats

Els exercicis que hem de fer:

![Llista d'exercicis de gestió del domini](Gestió del domini mitjançant comandes/1.png)

### Reconfigure slapd i verificació inicial

Primer reconfigurarem el servei LDAP per deixar la base de dades buida amb només el domini i l'usuari admin. Executem:

```bash
dpkg-reconfigure slapd
slapcat
```

![dpkg-reconfigure slapd i slapcat inicial](Gestió del domini mitjançant comandes/2.png)

La sortida de `slapcat` mostra que el domini `dc=widad,dc=cat` amb l'organització `widad` s'ha configurat correctament i la base de dades queda neta.

### Descàrrega del fitxer de dades

Descarreguem el fitxer `dades_pt10.ldif` des del servidor de l'alumnat (IP 192.168.1.140, port 8000) per tenir les dades de mostra:

```bash
wget http://192.168.1.140:8000/dades_pt10.ldif
```

![Descàrrega del fitxer dades_pt10.ldif](Gestió del domini mitjançant comandes/3.png)

### Càrrega de dades amb ldapadd

Un cop descarregat el fitxer, el carreguem al servidor LDAP amb la comanda `ldapadd`:

```bash
ldapadd -x -D "cn=admin,dc=widad,dc=cat" -W -f dades_pt10.ldif
```

![ldapadd carrega dades_pt10.ldif](Gestió del domini mitjançant comandes/4.png)

S'han afegit les OUs `rrhh` i `departaments`, i els usuaris xavier, enric i sergi a `ou=rrhh`, i els grups informatica i administracio a `ou=departaments`.

### Verificació amb slapcat

Comprovem que les dades s'han carregat correctament amb `slapcat`:

```bash
slapcat
```

![slapcat - verificació de les dades carregades](Gestió del domini mitjançant comandes/5.png)

### Cerques amb ldapsearch

Busquem les Unitats Organitzatives (OUs) i els usuaris del domini:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=organizationalUnit)" dn | grep "^dn:"
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=inetOrgPerson)" dn | grep "^dn:"
```

![ldapsearch - cerques de OUs i usuaris](Gestió del domini mitjançant comandes/6.png)

Trobem les OUs `ou=rrhh` i `ou=departaments`, i els usuaris xavier, enric i sergi a la OU rrhh.

### Creació d'una nova OU: asix

Creem l'arxiu LDIF per a la nova unitat organitzativa `asix` i l'afegim:

```bash
cat asix.ldif
```

```ldif
dn: ou=asix,dc=widad,dc=cat
objectClass: organizationalUnit
ou: asix
description: Unitat Organitzativa per al grup ASIX
```

```bash
ldapadd -x -D "cn=admin,dc=widad,dc=cat" -W -f asix.ldif
```

![Creació OU asix](Gestió del domini mitjançant comandes/7.png)

### Eliminació de l'atribut roomNumber

Esborrem l'atribut `roomNumber` de l'usuari xavier:

```bash
cat delete_attrs.ldif
```

```ldif
dn: cn=xavier,ou=rrhh,dc=widad,dc=cat
changetype: modify
delete: roomNumber
```

```bash
ldapmodify -x -D "cn=admin,dc=widad,dc=cat" -W -f delete_attrs.ldif
```

![Eliminació atribut roomNumber de xavier](Gestió del domini mitjançant comandes/8.png)

### Cerca de grups d'un usuari (memberUid)

Cerquem en quins grups es troba l'usuari xavier com a `uniqueMember`:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(&(objectClass=posixGroup)(memberUid=xavier))" cn
```

![Cerca dels grups de xavier](Gestió del domini mitjançant comandes/9.png)

L'usuari xavier pertany al grup `informatica` dins la OU departaments.

### Moviment d'usuaris de People a asix

Movem els usuaris xavier, enric i sergi de la OU People a la nova OU asix:

```bash
cat move_to_asix.ldif
```

```ldif
dn: cn=xavier,ou=People,dc=widad,dc=cat
changetype: moddn
newrdn: cn=xavier
deleteoldrdn: 1
newsuperior: ou=asix,dc=widad,dc=cat

dn: cn=enric,ou=People,dc=widad,dc=cat
changetype: moddn
newrdn: cn=enric
deleteoldrdn: 1
newsuperior: ou=asix,dc=widad,dc=cat

dn: cn=sergi,ou=People,dc=widad,dc=cat
changetype: moddn
newrdn: cn=sergi
deleteoldrdn: 1
newsuperior: ou=asix,dc=widad,dc=cat
```

```bash
ldapmodify -x -D "cn=admin,dc=widad,dc=cat" -W -f move_to_asix.ldif
```

![Moviment d'usuaris a la OU asix](Gestió del domini mitjançant comandes/10.png)

### Cerques avançades de verificació

Verifiquem les cerques per OUs i usuaris una vegada fets els canvis anteriors amb:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=organizationalUnit)" dn
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=inetOrgPerson)" dn
```

![Verificació cerques avançades](Gestió del domini mitjançant comandes/11.png)

### Creació d'un nou usuari

Creem un nou usuari amb atributs opcionals de la classe `posixAccount`:

```bash
cat new_user.ldif
```

```ldif
dn: cn=malak,ou=asix,dc=widad,dc=cat
objectClass: inetOrgPerson
objectClass: posixAccount
...
```

```bash
ldapadd -x -D "cn=admin,dc=widad,dc=cat" -W -f new_user.ldif
```

![Creació nou usuari](Gestió del domini mitjançant comandes/12.png)

### Cerques per OUs i per grups

Cerques diverses per verificar l'estat del domini:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=organizationalUnit)" dn
ldapsearch -x -LLL -b "ou=Groups,dc=widad,dc=cat" "(objectClass=posixGroup)" cn
```

![Cerques per OUs i grups](Gestió del domini mitjançant comandes/13.png)

### Cerca de tots els usuaris

Cerquem tots els usuaris del domini:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(objectClass=inetOrgPerson)" dn
```

![Cerca de tots els usuaris del domini](Gestió del domini mitjançant comandes/14.png)

### Creació del fitxer asix.ldif

Creem el fitxer `asix.ldif` per afegir una nova OU:

```bash
cat asix.ldif
ldapadd -x -D "cn=admin,dc=widad,dc=cat" -W -f asix.ldif
```

![Creació fitxer asix.ldif](Gestió del domini mitjançant comandes/15.png)

### Eliminació d'atributs

Eliminem l'atribut `roomNumber` amb el fitxer LDIF corresponent:

```bash
cat delete_attrs.ldif
ldapmodify -x -D "cn=admin,dc=widad,dc=cat" -W -f delete_attrs.ldif
```

![Eliminació d'atributs](Gestió del domini mitjançant comandes/16.png)

### Cerca filtrada per grup

Cerquem usuaris filtrats pel grup on pertanyen com a `memberUid`:

```bash
ldapsearch -x -LLL -b "dc=widad,dc=cat" "(&(objectClass=posixGroup)(memberUid=xavier))" cn
```

![Cerca filtrada per grup](Gestió del domini mitjançant comandes/17.png)

### Moviment d'usuaris al fitxer asix.ldif

Creem el fitxer per moure els usuaris i l'executem:

```bash
cat move_to_asix.ldif
ldapmodify -x -D "cn=admin,dc=widad,dc=cat" -W -f move_to_asix.ldif
```

![Moviment d'usuaris al fitxer asix.ldif](Gestió del domini mitjançant comandes/18.png)

### Reconfigure final

Executem `dpkg-reconfigure slapd` per reconfigura el servei:

```bash
dpkg-reconfigure slapd
```

![Reconfigure final](Gestió del domini mitjançant comandes/19.png)

### Descàrrega final del fitxer de dades

Tornem a descarregar el fitxer `dades_pt10.ldif`:

```bash
wget http://192.168.1.140:8000/dades_pt10.ldif
```

![Descàrrega final dades_pt10.ldif](Gestió del domini mitjançant comandes/20.png)

### Càrrega final de dades

Tornem a carregar les dades al servidor LDAP:

```bash
ldapadd -x -D "cn=admin,dc=widad,dc=cat" -W -f dades_pt10.ldif
```

![Càrrega final de dades](Gestió del domini mitjançant comandes/21.png)

### Verificació final

Comprovem l'estat final del domini amb `slapcat` i `ldapsearch`:

```bash
slapcat
```

![Verificació final del domini](Gestió del domini mitjançant comandes/22.png)

### Configuració Samba
#### Què és Samba?

Samba és un programari lliure que permet compartir fitxers i recursos en una xarxa. Facilita la comunicació entre sistemes Linux i Windows, permetent que un servidor Linux actuï com un servidor de fitxers compatible amb Windows.

Samba permet gestionar usuaris, contrasenyes i permisos, i és molt utilitzat en entorns educatius i empresarials amb sistemes operatius mixtos.
primer instalem samba 

<img width="796" height="501" alt="image" src="https://github.com/user-attachments/assets/b66856cd-f7b0-4d38-a718-81645f888a24" />


Comprovem la instal·lació , i despres editem el fitxer de configuració /etc/samba/smb.conf per definir el grup de treball i els recursos compartits.

<img width="589" height="132" alt="image" src="https://github.com/user-attachments/assets/1c82f5e6-de91-4507-938f-5d52d9171305" />


<img width="596" height="355" alt="image" src="https://github.com/user-attachments/assets/e21b003d-d7ac-42cb-9761-7c5837d496c2" />

Definim la configuració global i els recursos compartits, assegurant els permisos adequats.

<img width="595" height="329" alt="image" src="https://github.com/user-attachments/assets/dce8e1fd-5720-4402-a84a-65ae4c74512d" />


<img width="596" height="326" alt="image" src="https://github.com/user-attachments/assets/2b24effd-8370-4685-958d-31b1b43e2ae7" />


<img width="600" height="409" alt="image" src="https://github.com/user-attachments/assets/619f52cf-2e51-46ee-84fe-411776ed4fb9" />


<img width="838" height="513" alt="image" src="https://github.com/user-attachments/assets/a480d13c-759a-4011-a223-455cddc17560" />


<img width="643" height="512" alt="image" src="https://github.com/user-attachments/assets/304098e7-c25a-4379-9c78-18583a9ed15f" />

<img width="851" height="469" alt="image" src="https://github.com/user-attachments/assets/6f1218f8-cd44-41de-b033-4d627e2d006d" />


### NFS
El NFS (Network File System) és un protocol que permet compartir fitxers a través d'una xarxa.

Bàsicament, fa que una carpeta que està en un servidor remot sembli que està instal·lada directament al teu ordinador.
Primer installem l'equip amb la comanda nfs-kernel-server

<img width="728" height="397" alt="image" src="https://github.com/user-attachments/assets/15421de3-2640-48ea-b712-7fcb9359df0e" />

<img width="742" height="419" alt="image" src="https://github.com/user-attachments/assets/cd36d944-f055-47db-9c09-cb1d257136f9" />

<img width="712" height="450" alt="image" src="https://github.com/user-attachments/assets/6ff23d64-d4bc-4627-b458-86abf79926a3" />

<img width="735" height="251" alt="image" src="https://github.com/user-attachments/assets/510dae87-3a42-43ff-8365-fa22c31e1961" />

<img width="727" height="285" alt="image" src="https://github.com/user-attachments/assets/735a131b-a0e8-41e6-b58d-296b0efd4959" />

<img width="1019" height="427" alt="image" src="https://github.com/user-attachments/assets/fb745e2e-855c-4be4-ab47-db9e47e49835" />

<img width="739" height="414" alt="image" src="https://github.com/user-attachments/assets/2aa2530b-6a2f-4038-a970-70e296e2a5e2" />

<img width="570" height="226" alt="image" src="https://github.com/user-attachments/assets/36e52f34-5062-4f9a-b7c7-304be87bf5a5" />

<img width="730" height="425" alt="image" src="https://github.com/user-attachments/assets/d001a32c-f38a-4016-a0d4-cca416b2b9e3" />

<img width="565" height="405" alt="image" src="https://github.com/user-attachments/assets/97242abd-3217-4b0e-9e9e-6b24e760b193" />

<img width="575" height="138" alt="image" src="https://github.com/user-attachments/assets/b7c6583f-6483-465b-ad60-c631874c113f" />










