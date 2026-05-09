### Instal·lació, Configuració Inicial i Programari de Base

<img width="954" height="540" alt="image" src="https://github.com/user-attachments/assets/8acbbee8-753d-4758-b2a3-994747931025" />



<img width="773" height="373" alt="image" src="https://github.com/user-attachments/assets/cb90293e-58e5-46e5-8f8e-c53a0d8831b7" />

# Sprint 1: Instal·lació i Configuració de Windows 11 - Widad

## Fase 1 – Instal·lació del sistema operatiu

### Pas 1 – Creació de la VM
He configurat una nova màquina virtual a VirtualBox anomenada **Windows 11 Widad**. He seleccionat el tipus **Microsoft Windows** i la versió **Windows 11 (64-bit)**.

![Configuració inicial de la VM](imatges/1.png)

### Pas 2 – Recursos de Maquinari
He assignat els recursos necessaris perquè el sistema funcioni correctament:
* **Memòria RAM:** 4096 MB (4 GB).
* **Processador:** 2 CPUs.
* **EFI:** Activat (obligatori per a Windows 11).

![Hardware assignat](imatges/2.png)

---

## Fase 3 – Llicències de Windows

He consultat l'estat d'activació del sistema a la configuració. Aquí teniu la informació sobre els tipus de llicenciament oficials de Microsoft:

| Tipus de Llicència | Descripció | Preu Aproximat |
| :--- | :--- | :--- |
| **OEM** | Preinstal·lada pel fabricant. No es pot moure a un altre PC. | Inclosa al PC |
| **Retail** | Comprada a la botiga. Es pot transferir a un altre equip. | ~259 € (Pro) |
| **Volume** | Per a empreses i centres educatius. | Variable |

---

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

<img width="405" height="108" alt="image" src="https://github.com/user-attachments/assets/86fcae6b-8035-4d4b-ab8b-878188da7a26" />

