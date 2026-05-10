# Sprint 2 – Windows: Discs, Quotes, Scripts, Processos i ACLs (Widad)

---

## Fase 1 – Preparació del sistema

### Pas 1 – Afegir un nou disc virtual a la màquina virtual
Per ampliar l'emmagatzematge, he accedit a **Configuració → Emmagatzematge** de VirtualBox i he creat el fitxer `Windows 11 Pro_1.vdi` amb una mida de **5,00 GB**.

![Configuració VirtualBox](imatges-windows/1.png)

### Pas 2 – Iniciar Windows i obrir Gestió de discs
He iniciat la sessió i executat `diskmgmt.msc`. El sistema ha detectat el **Disc 1** (4,98 GB) com a espai no assignat.

![Gestió de discs](imatges-windows/2.png)

### Pas 3 – Inicialitzar el disc i crear dues particions: Dades (NTFS) i Portable (FAT32)
He dividit el nou disc en dues unitats:
* **Partició Dades (E:)**: 3000 MB (3 GB) en format **NTFS** per permetre quotes i ACLs.
* **Partició Portable (F:)**: Espai restant en format **FAT32** per a compatibilitat universal.

| Característica | NTFS | FAT32 |
| :--- | :--- | :--- |
| Mida màx. fitxer | Il·limitada | 4 GB |
| Permisos ACL | ✅ Sí | ❌ No |
| Quotes de disc | ✅ Sí | ❌ No |

![Particions creades](imatges-windows/12.png)

### Pas 4 – Assignar lletres i comprovar amb diskpart la configuració
He verificat la configuració mitjançant la consola amb la comanda `diskpart`:
```cmd
## Fase 2 – Quotes i usuaris

### Pas 5 – Activar quotes de disc a la partició Dades (NTFS)
He entrat a les propietats de la unitat **E:** i he accedit a la pestanya **Cuota** per habilitar l'administració d'espai del sistema de fitxers.

### Pas 6 – Establir límit de 300 MB per usuari
He configurat els següents límits per controlar l'ús del disc:
* **Limitar espai a:** 300 MB.
* **Nivell d'advertència:** 150 KB.
* He activat l'opció de **denegar espai** als usuaris que superin el límit establert.

### Pas 7 – Crear dos usuaris locals: alumne1 i alumne2
He utilitzat l'eina `lusrmgr.msc` per crear els dos comptes d'usuari de prova per a l'entorn de laboratori.

### Pas 8 – Afegir-los a un grup nou anomenat Limitats
He creat el grup **Limitats** i he afegit `alumne1` i `alumne2` com a membres per gestionar els seus permisos i restriccions de forma centralitzada.

### Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes
He intentat crear un fitxer de grans dimensions amb la comanda `fsutil`. El sistema ha bloquejat l'operació amb l'**Error 112**, confirmant que la quota de 300 MB s'aplica correctament.

---

## Fase 3 – Script de còpia i automatització

### Pas 10 – Afegir tercer disc virtual (Backups)
He afegit un tercer disc dur virtual de **5 GB** a la configuració de VirtualBox per destinar-lo exclusivament a les còpies de seguretat.

### Pas 11 – Crear carpeta CòpiesUsuaris dins Backups
He creat el directori `B:\CòpiesUsuaris` per organitzar i emmagatzemar els backups de cada perfil d'usuari de manera independent.

### Pas 12 – Crear un script .bat de còpia
He creat el fitxer `script.bat` utilitzant la comanda `xcopy` per automatitzar el procés de còpia del perfil:

```dos
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y
Pas 13 – Obrir gpedit.msc per configurar l'inici de sessió
He accedit a l'Editor de directives de grup local mitjançant la comanda gpedit.msc i he navegat fins a:
Configuració d'usuari → Configuració de Windows → Scripts.

Pas 14 – Assignar l'script de l'inici de sessió
Dins de la secció d'inici de sessió, he agregat la ruta del fitxer .bat creat anteriorment perquè s'executi automàticament cada vegada que un usuari validi la seva sessió.

Fase 4 – Verificació i Processos
Pas 15 – Comprovació de la còpia
He verificat que, en iniciar sessió, s'ha creat correctament la subcarpeta corresponent a l'usuari a la unitat B: amb tots els seus fitxers.

Pas 19 – Llistar processos actius
Mitjançant la comanda tasklist, he generat una llista dels processos actius i he bolcat el resultat en un fitxer de text anomenat processos_inici.txt.

Pas 20 – Identificar processos prescindibles
He analitzat la llista i he identificat processos com OneDrive.exe, que consumeixen aproximadament 135 MB de RAM de manera innecessària en aquest entorn.

Pas 21 i 22 – Eliminar processos i automatitzar el tancament
He afegit la següent comanda a l'script d'inici per alliberar memòria RAM de forma automàtica:

DOS

taskkill /IM OneDrive.exe /F
Pas 23 – Documentació de rendiment
He constatat que en tancar aquests processos prescindibles s'alliberen entre 300 i 600 MB de RAM, cosa que millora significativament la fluïdesa de la màquina virtual.

Fase 5 – Gestió de permisos (ACLs)
Pas 24 – Crear la carpeta Projectes
He creat el directori E:\Projectes per utilitzar-lo com a espai de treball compartit per al grup.

Pas 25 – Assignar permisos al grup Limitats
He accedit a la configuració de seguretat avançada de la carpeta, he deshabilitat l'herència i he assignat permisos de Control total al grup Limitats.

Pas 26 – Comprovar accés amb alumne1
He validat que l'usuari alumne1 té permisos suficients per crear, modificar i eliminar fitxers dins de la carpeta sense restriccions.

Pas 27 – Aplicar excepció per alumne2 (Només lectura)
He utilitzat la comanda icacls per aplicar una restricció específica a l'usuari alumne2:

DOS

icacls "E:\Projectes" /grant:r alumne2:(R)
Pas 28 – Comprovar l'excepció amb alumne2
He verificat que l'usuari alumne2 rep un missatge de "Denegació d'accés" en intentar realitzar qualsevol modificació o creació de carpetes, confirmant que només pot llegir el contingut.

Pas 29 – Consultar permisos finals
He executat icacls "E:\Projectes" per visualitzar la llista de control d'accés (ACL) i confirmar que l'entrada individual de l'usuari té prioritat sobre la del grup.
