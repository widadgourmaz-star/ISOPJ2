

# Sprint 1: Instal·lació i Configuració de Windows 11 - Widad

## Fase 1 – Instal·lació del sistema operatiu

<img width="954" height="540" alt="image" src="https://github.com/user-attachments/assets/8acbbee8-753d-4758-b2a3-994747931025" />

### Pas 1 – Creació de la VM
He configurat una nova màquina virtual a VirtualBox anomenada **Windows 11 Widad**. He seleccionat el tipus **Microsoft Windows** i la versió **Windows 11 (64-bit)**.

<img width="849" height="425" alt="image" src="https://github.com/user-attachments/assets/e013b533-cbba-43fb-ac68-59de217b5a70" />


### Pas 2 – Recursos de Maquinari
He assignat els recursos necessaris perquè el sistema funcioni correctament:
* **Memòria RAM:** 4096 MB (4 GB).
* **Processador:** 2 CPUs.
* **EFI:** Activat (obligatori per a Windows 11).


<img width="841" height="448" alt="image" src="https://github.com/user-attachments/assets/171bc872-a8be-4d1d-8ef0-abe551ddf587" />

---<img width="836" height="443" alt="image" src="https://github.com/user-attachments/assets/0c101df5-44ef-49f1-993a-6821377c0dc3" />

<img width="654" height="269" alt="image" src="https://github.com/user-attachments/assets/89929ef3-5730-4b97-ab3c-fd80062b410d" />

<img width="647" height="458" alt="image" src="https://github.com/user-attachments/assets/742d6282-9870-4117-89e5-0bffa81af693" />

Despres de insl.lar , he tret espnya com pais o regio 

<img width="848" height="589" alt="image" src="https://github.com/user-attachments/assets/b03deb44-2f77-4701-829e-48163a752b70" />



## Fase 3 – Llicències de Windows

He consultat l'estat d'activació del sistema a la configuració. Aquí teniu la informació sobre els tipus de llicenciament oficials de Microsoft:

| Tipus de Llicència | Descripció | Preu Aproximat |
| :--- | :--- | :--- |
| **OEM** | Preinstal·lada pel fabricant. No es pot moure a un altre PC. | Inclosa al PC |
| **Retail** | Comprada a la botiga. Es pot transferir a un altre equip. | ~259 € (Pro) |
| **Volume** | Per a empreses i centres educatius. | Variable |

---<img width="675" height="537" alt="image" src="https://github.com/user-attachments/assets/f888094f-00ac-491b-9472-f51215046e13" />

He configurat l'idioma, he seleccionat español.

<img width="691" height="515" alt="image" src="https://github.com/user-attachments/assets/1bcc5bc5-1db0-41f8-8234-2e7cf95e6199" />

Aqui he seleccionat la configuracio de instal.lacio 

<img width="673" height="535" alt="image" src="https://github.com/user-attachments/assets/8bcb16db-7d8f-4306-b905-92194fcc9881" />
Despres la 
<img width="611" height="258" alt="image" src="https://github.com/user-attachments/assets/a200834d-004c-4d7b-a421-dc500078534d" />

## Fase 4 – Gestor d'arrencada (bcdedit)

He executat la comanda `bcdedit` al terminal (CMD) com a administrador per identificar els fitxers d'arrencada:

* **Boot Manager**: Gestiona quin sistema s'inicia.
* **Boot Loader**: El fitxer `winload.efi` s'encarrega de carregar el nucli de Windows.

![Resultat bcdedit](imatges/bcdedit.png)

---

## Fase 5 – Configuració de Xarxa

He verificat la connectivitat del sistema mitjançant la línia de comandes:

1. **Consulta de IP**: He utilitzat `ipconfig` per veure l'adreça IP assignada per DHCP.
2. **Prova de connexió**: He fet un `ping google.com` per confirmar l'accés a Internet.

![Prova de xarxa](imatges/ping.png)

---

## Fase 6 – Comandes i PowerShell

Diferències clau entre els dos terminals de Windows:

| Característica | CMD | PowerShell |
| :--- | :--- | :--- |
| **Dades** | Treballa amb text pla. | Treballa amb **Objectes**. |
| **Potència** | Tasques bàsiques. | Automatització avançada i scripts `.ps1`. |
| **Motor** | Basat en MS-DOS. | Basat en el framework .NET. |

---

## Fase 7 – Gestió d'Aplicacions

He realitzat una prova de cicle de vida d'una aplicació:
1. **Instal·lació**: He descarregat i instal·lat **Visual Studio Code**.
2. **Verificació**: He comprovat que l'aplicació s'obre correctament.
3. **Desinstal·lació**: He eliminat l'aplicació des de "Configuració > Aplicacions" per netejar el sistema.

![Aplicació instal·lada](imatges/vscode.png)

---

### Fase 2 – Punts de restauració (Detallada)

Aquesta fase és crucial per garantir la seguretat del sistema davant de possibles fallades o configuracions errònies.

* **Pas 5 – Activar la protecció del sistema**: He accedit al Tauler de Control > Sistema > Protecció del sistema. Per defecte estava desactivada, així que he entrat a "Configurar" i he activat la protecció per a la unitat C:.
* **Pas 6 – Crear punt de restauració manual**: He creat un punt amb el nom **"Widad - Punt Inicial"**. Aquest serà el meu "salvavides" si el Windows deixa de funcionar.
* **Pas 7 – Prova de restauració**: 
    1. He creat un fitxer anomenat `PROVA.txt` a l'escriptori.
    2. He executat la restauració del sistema al punt creat anteriorment.
    3. He comprovat que, després del reinici, el fitxer ha desaparegut. Això confirma que la restauració és funcional.

---

### Fase 6 – Comandes generals del sistema (Ampliada)

He utilitzat el terminal per extreure informació detallada que no sempre és visible des de la interfície gràfica:

* **Informació d'identitat**:
    * `hostname`: Mostra el nom oficial de la màquina virtual a la xarxa.
    * `whoami`: Confirma que l'usuari actiu és **Widad**.
* **Gestió del sistema**:
    * `systeminfo`: Genera un informe amb la versió exacta del Windows, el tipus de processador virtual i la memòria RAM lliure.
    * `tasklist`: Llista tots els processos i serveis que s'estan executant en segon pla. És útil per monitoritzar el rendiment.
    * `taskkill /F /IM [nom]`: Comanda utilitzada per forçar el tancament de processos que no responen.

---

### Fase 7 – Instal·lació d'aplicacions (Detalls finals)

* **Pas 37 – Ús de la Microsoft Store**: He realitzat una prova d'instal·lació des de la botiga oficial (per exemple, Python o una eina de sistema) per verificar que el compte d'usuari té els permisos necessaris per gestionar programari.
* **Pas 39 – Desinstal·lació i neteja**: He utilitzat el menú "Aplicacions i característiques" per eliminar **Visual Studio Code**. He comprovat que no queden restes a la carpeta de `Program Files`, assegurant que la desinstal·lació és neta.
* **Pas 40 – Verificació final**: He utilitzat el cercador de Windows per confirmar que l'aplicació ja no existeix al sistema.

* ---

### Fase 2 – Punts de restauració (Detallada)

Aquesta fase és crucial per garantir la seguretat del sistema davant de possibles fallades o configuracions errònies.

* **Pas 5 – Activar la protecció del sistema**: He accedit al Tauler de Control > Sistema > Protecció del sistema. Per defecte estava desactivada, així que he entrat a "Configurar" i he activat la protecció per a la unitat C:.
* **Pas 6 – Crear punt de restauració manual**: He creat un punt amb el nom **"Widad - Punt Inicial"**. Aquest serà el meu "salvavides" si el Windows deixa de funcionar.
* **Pas 7 – Prova de restauració**: 
    1. He creat un fitxer anomenat `PROVA.txt` a l'escriptori.
    2. He executat la restauració del sistema al punt creat anteriorment.
    3. He comprovat que, després del reinici, el fitxer ha desaparegut. Això confirma que la restauració és funcional.

---

### Fase 6 – Comandes generals del sistema (Ampliada)

He utilitzat el terminal per extreure informació detallada que no sempre és visible des de la interfície gràfica:

* **Informació d'identitat**:
    * `hostname`: Mostra el nom oficial de la màquina virtual a la xarxa.
    * `whoami`: Confirma que l'usuari actiu és **Widad**.
* **Gestió del sistema**:
    * `systeminfo`: Genera un informe amb la versió exacta del Windows, el tipus de processador virtual i la memòria RAM lliure.
    * `tasklist`: Llista tots els processos i serveis que s'estan executant en segon pla. És útil per monitoritzar el rendiment.
    * `taskkill /F /IM [nom]`: Comanda utilitzada per forçar el tancament de processos que no responen.

---

### Fase 7 – Instal·lació d'aplicacions (Detalls finals)

* **Pas 37 – Ús de la Microsoft Store**: He realitzat una prova d'instal·lació des de la botiga oficial (per exemple, Python o una eina de sistema) per verificar que el compte d'usuari té els permisos necessaris per gestionar programari.
* **Pas 39 – Desinstal·lació i neteja**: He utilitzat el menú "Aplicacions i característiques" per eliminar **Visual Studio Code**. He comprovat que no queden restes a la carpeta de `Program Files`, assegurant que la desinstal·lació és neta.
* **Pas 40 – Verificació final**: He utilitzat el cercador de Windows per confirmar que l'aplicació ja no existeix al sistema.

