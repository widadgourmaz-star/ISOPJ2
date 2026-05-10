
# Sprint 2 – Windows: Discs, Quotes, Scripts, Processos i ACLs (Widad)

---

## Fase 1 – Preparació del sistema

### Pas 1 – Afegir un nou disc virtual a la màquina virtual
Per ampliar l'emmagatzematge de la màquina virtual cal afegir un nou disc des de la configuració de VirtualBox. Accedim a **Configuració → Emmagatzematge** de la màquina virtual. Creem el fitxer `Windows 11 Pro_1.vdi` amb una mida de **5,00 GB**.

![Pas 1](imatges-windows/1.png)

### Pas 2 – Iniciar Windows i obrir Gestió de discs
Un cop afegit el disc, iniciem Windows i executem `diskmgmt.msc`. El sistema reconeix el nou **Disc 1** (4,98 GB) amb tot l'espai **No asignat**.

![Pas 2](imatges-windows/2.png)

### Pas 3 – Inicialitzar el disc i crear dues particions: Dades (NTFS) i Portable (FAT32)
He creat dues particions al Disc 1:
* **Dades (NTFS)**: 3000 MB (3 GB). Aquest format és necessari per suportar quotes i permisos ACL.
* **Portable (FAT32)**: Espai restant (aprox. 2 GB) per a compatibilitat universal.

| Característica | NTFS | FAT32 |
| :--- | :--- | :--- |
| Mida màx. fitxer | Il·limitada | 4 GB |
| Permisos ACL | ✅ Sí | ❌ No |
| Quotes de disc | ✅ Sí | ❌ No |

![Pas 3](imatges-windows/12.png)

### Pas 4 – Assignar lletres i comprovar amb diskpart la configuració
He verificat la configuració mitjançant `diskpart` al terminal per confirmar que les unitats **E:** (NTFS) i **F:** (FAT32) estan correctament configurades.

![Pas 4](imatges-windows/13.png)

---

## Fase 2 – Quotes i usuaris

### Pas 5 – Activar quotes de disc a la partició Dades (NTFS)
He entrat a les propietats de la unitat **E:** i he accedit a la pestanya **Cuota** per habilitar l'administració d'espai del sistema de fitxers.

![Pas 5](imatges-windows/15.png)

### Pas 6 – Establir límit de 300 MB per usuari
He configurat els següents límits:
* **Limitar espai a:** 300 MB.
* **Nivell d'advertència:** 150 KB.
* He activat l'opció de **denegar espai** als usuaris que superin el límit.

![Pas 6](imatges-windows/16.png)

### Pas 7 – Crear dos usuaris locals: alumne1 i alumne2
He utilitzat l'eina `lusrmgr.msc` per crear els dos comptes d'usuari locals per a les proves de laboratori.

![Pas 7](imatges-windows/20.png)

### Pas 8 – Afegir-los a un grup nou anomenat Limitats
He creat el grup **Limitats** i he afegit `alumne1` i `alumne2` com a membres per gestionar els permisos de forma centralitzada.

![Pas 8](imatges-windows/22.png)

### Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes
He intentat crear un fitxer gran amb `fsutil`. El sistema ha bloquejat l'operació amb l'**Error 112**, confirmant que la quota de 300 MB és efectiva.

![Pas 9](imatges-windows/24.png)

---

## Fase 3 – Script de còpia i automatització

### Pas 10 – Afegir tercer disc virtual (Backups)
He afegit un tercer disc de 5 GB a VirtualBox per destinar-lo a les còpies de seguretat (Unitat **B:**).

### Pas 11 – Crear carpeta CòpiesUsuaris dins Backups
He creat la carpeta `B:\CòpiesUsuaris` per organitzar els backups de cada perfil.

### Pas 12 – Crear un script .bat de còpia
He creat el fitxer `script.bat` amb la següent comanda:
```dos
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y

```

### Pas 13 – Obrir gpedit.msc per configurar l'inici de sessió

He accedit a la directiva de grup: **Configuració d'usuari → Configuració de Windows → Scripts (Inici de sessió)**.

### Pas 14 – Assignar l'script de l'inici de sessió

He agregat la ruta del fitxer `.bat` perquè s'executi automàticament en cada inici de sessió d'usuari.

---

## Fase 4 – Verificació i Processos

### Pas 15 – Comprovació de la còpia

He verificat que a la unitat **B:** s'ha creat la subcarpeta de l'usuari amb tots els seus fitxers després d'iniciar la sessió.

### Pas 19 – Llistar processos actius

Amb la comanda `tasklist`, he llistat els processos i he guardat el resultat al fitxer `processos_inici.txt`.

### Pas 20 – Identificar processos prescindibles

He identificat que **OneDrive.exe** consumeix uns 135 MB de RAM innecessàriament a la màquina virtual.

### Pas 21 i 22 – Eliminar processos i automatitzar el tancament

He afegit la comanda `taskkill /IM OneDrive.exe /F` a l'script d'inici per alliberar memòria RAM automàticament.

### Pas 23 – Documentació de rendiment

He analitzat que en tancar processos prescindibles alliberem entre **300 i 600 MB de RAM**, millorant el rendiment de la VM.

---

## Fase 5 – Gestió de permisos (ACLs)

### Pas 24 – Crear la carpeta Projectes

He creat el directori `E:\Projectes` per gestionar els permisos compartits.

### Pas 25 – Assignar permisos al grup Limitats

He accedit a la seguretat avançada, he **deshabilitat l'herència** i he assignat **Control total** al grup **Limitats**.

### Pas 26 – Comprovar accés amb alumne1

He comprovat que l'usuari `alumne1` pot crear i modificar fitxers sense restriccions a la carpeta.

### Pas 27 – Aplicar excepció per alumne2 (Només lectura)

He utilitzat la comanda `icacls` per restringir l'accés a `alumne2` malgrat ser del grup:

```dos
icacls "E:\Projectes" /grant:r alumne2:(R)

```

### Pas 28 – Comprovar l'excepció amb alumne2

He verificat que `alumne2` rep un error de **"Denegació d'accés"** en intentar escriure, confirmant que només pot llegir.

### Pas 29 – Consultar permisos finals

He executat `icacls "E:\Projectes"` per confirmar que l'entrada individual d'usuari té prioritat sobre la del grup.
