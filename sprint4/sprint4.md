### Sprint 4: Configuració del Programari de Base i Sistemes d'Emmagatzematge en Ubuntu


<img width="1408" height="768" alt="Gemini_Generated_Image_kfd7mukfd7mukfd7" src="https://github.com/user-attachments/assets/6c917acd-3ce7-4b53-893e-07fb235d6759" />


### Què és un RAID?
Un RAID (acrònim en anglès de Redundant Array of Independent Disks, que en català vol dir "Matriu Redundant de Discos Independents") és una tecnologia d'emmagatzematge que consisteix a agrupar diversos discos durs físics per fer que el sistema operatiu els vegi i els tracti com si fossin una única unitat lògica.

L'objectiu principal de crear un RAID no és només sumar l'espai dels discos, sinó aconseguir dos beneficis clau que un disc individual no pot oferir: millorar el rendiment (velocitat de lectura i escriptura) i augmentar la tolerància a fallades (seguretat de les dades).

### Nivells de RAID
RAID 0 (Fraccionament pur): Centrat 100% en la velocitat. Suma la capacitat dels discos i la seva velocitat. El gran inconvenient és que no té seguretat. Si tens dos discos en RAID 0 i se'n trenca un, perds absoluament tota la informació de tots dos discos (perquè els fitxers estaven partits per la meitat). Ús típic: Edició de vídeo o disseny 3D on es necessita moure fitxers gegants molt ràpidament, però que ja tenen còpia de seguretat en un altre lloc.

RAID 1 (Emmirallament pur): Centrat 100% en la seguretat. Si tens dos discos d'1 TB cadascun, no tindràs 2 TB d'espai, sinó només 1 TB, perquè l'altre disc s'utilitza com a mirall invisible. És molt segur, ja que pot fallar un disc i no passa res. Ús típic: Ordinadors d'oficina importants, servidors petits o emmagatzematge de documents personals vitals.

RAID 5 (Fraccionament + Paritat): És l'equilibri perfecte i el més utilitzat en empreses petites i mitjanes (NAS domèstics o empresarials). Necessita un mínim de 3 discos. Ofereix molta capacitat (només "sacrifica" l'espai equivalent a un disc per guardar la paritat matemàtica), guanya velocitat de lectura i, si es trenca un disc (qualsevol d'ells), les dades continuen intactes.

RAID 10 (1+0): Necessita un mínim de 4 discos. Combina la seguretat del RAID 1 amb la brutal velocitat del RAID 0. És el sistema més car (perds la meitat de la capacitat total dels discos comprats), però és el més ràpid i segur. Ús típic: Bases de dades d'empreses grans o servidors web amb moltíssim trànsit.
