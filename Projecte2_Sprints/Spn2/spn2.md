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
