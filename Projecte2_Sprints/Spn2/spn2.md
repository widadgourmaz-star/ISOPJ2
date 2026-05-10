Sprint 2 – Windows: Discs, Quotes, Scripts, Processos i ACLs (Widad)
Fase 1 – Preparació del sistema
Pas 1 – Afegir un nou disc virtual a la màquina virtual
Per ampliar l'emmagatzematge, he accedit a Configuració → Emmagatzematge de VirtualBox. He creat un nou disc dur virtual anomenat Windows 11 Pro_1.vdi amb una mida virtual de 5,00 GB en format dinàmic.

Pas 2 – Iniciar Windows i obrir Gestió de discs
He iniciat la VM i he executat diskmgmt.msc. El sistema reconeix el nou Disc 1 (5 GB) amb l'estat "No asignat". Això confirma que el maquinari virtual està ben connectat.

Pas 3 – Inicialitzar el disc i crear les particions Dades i Portable
He inicialitzat el disc en GPT i he creat dues particions:

Dades (NTFS): He assignat 3000 MB. He triat NTFS perquè és l'únic que suporta quotes i permisos ACL.

Portable (FAT32): He usat l'espai restant. Aquest format és per a compatibilitat amb altres dispositius.

Pas 4 – Assignar lletres i comprovar amb diskpart
He obert el CMD i he executat diskpart per verificar que tot és correcte:

Unitat E: (Dades - NTFS).

Unitat F: (Portable - FAT32).

Fase 2 – Quotes i usuaris
Pas 5 – Activar quotes de disc a la partició Dades (NTFS)
A les propietats de la unitat E:, he anat a la pestanya Cuota i he clicat a "Mostrar configuració de cuota" per activar l'administració.

Pas 6 – Establir límit de 300 MB per usuari
Dins de la configuració de quotes, he establert:

Límit d'espai: 300 MB.

Nivell d'advertència: 150 KB.

He marcat l'opció de denegar espai a qui superi el límit.

Pas 7 – Crear els usuaris alumne1 i alumne2
He executat lusrmgr.msc i he creat dos usuaris locals per fer les proves de seguretat.

Pas 8 – Afegir-los al grup Limitats
He creat un grup nou anomenat Limitats i hi he afegit els dos alumnes. Això permet aplicar permisos a tots dos a la vegada.

Pas 9 – Provar la còpia de fitxers (Error 112)
He intentat crear un fitxer gran amb la comanda fsutil. Com que superava els 300 MB, Windows ha donat l'error d'espai insuficient, demostrant que la quota funciona.

Fase 3 – Script de còpia i automatització
Pas 10 – Afegir tercer disc virtual (Backups)
He creat un altre disc de 5 GB a VirtualBox per guardar les còpies de seguretat de forma externa.

Pas 11 – Crear carpeta CòpiesUsuaris dins Backups
Dins la nova unitat B:, he creat la carpeta CòpiesUsuaris per centralitzar els backups.

Pas 12 – Crear l'script .bat de còpia
He creat un fitxer de text amb extensió .bat amb el següent codi:

DOS

@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y
Pas 13 – Obrir gpedit.msc per configurar l'inici de sessió
He executat gpedit.msc i he navegat fins a: Configuració d'usuari → Configuració de Windows → Scripts (Inici de sessió).

Pas 14 – Assignar l'script
He seleccionat el fitxer .bat que he creat. Ara, cada cop que un alumne entri, els seus fitxers es copiaran automàticament al disc B:.

Fase 4 – Verificació i Processos
Pas 15 – Comprovació de la còpia
He reiniciat sessió i he comprovat que a B:\CòpiesUsuaris\alumne1 ja apareixen totes les carpetes del seu perfil.

Pas 19 – Llistar processos actius
Amb la comanda tasklist, he generat un fitxer anomenat processos_inici.txt per analitzar què s'està executant.

Pas 20 – Identificar processos prescindibles
He vist que OneDrive.exe consumeix uns 135 MB. En una màquina virtual sense internet real, aquest procés no serveix de res.

Pas 21 i 22 – Eliminar processos i automatitzar
He modificat l'script .bat anterior afegint:

DOS

taskkill /IM OneDrive.exe /F
Això fa que la màquina vagi molt més ràpida en iniciar sessió.

Pas 23 – Documentació de rendiment
He calculat que eliminant processos com OneDrive o Teams, podem alliberar fins a 600 MB de RAM, vital per a VMs de 4 GB.

Fase 5 – Gestió de permisos (ACLs)
Pas 24 – Crear la carpeta Projectes
Dins de la unitat E:, he creat la carpeta Projectes.

Pas 25 – Assignar permisos al grup Limitats
He entrat a Seguretat Avançada, he clicat a Deshabilitar herència i he donat Control total al grup Limitats.

Pas 26 – Comprovar accés amb alumne1
L'alumne 1 ha pogut crear un fitxer anomenat hey.txt, confirmant que té permisos d'escriptura.

Pas 27 – Aplicar excepció per alumne2 (Només lectura)
He usat la comanda icacls per fer una excepció individual:

DOS

icacls "E:\Projectes" /grant:r alumne2:(R)
Pas 28 – Comprovar l'excepció amb alumne2
He intentat crear una carpeta amb l'alumne 2 i ha sortit el missatge de "Denegació d'accés". L'excepció funciona!

Pas 29 – Consultar permisos finals
He executat icacls "E:\Projectes" per veure l'estat final. L'entrada d'usuari (alumne2:R) té prioritat sobre la del grup, per això no pot escriure.
