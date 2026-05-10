# SPRINT 3: ADMINISTRACIÓ DE DOMINIS I SEGURETAT - Windows

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/6b3c0e59-6503-4b00-b27a-75e6a752c60b" />

---

# Active Directory: Instal·lació del DC i unió d'un client Windows

En aquest apartat documentem el procés complet de configuració d'un **Controlador de Domini (DC)** amb **Active Directory Domain Services (AD DS)** sobre Windows Server 2022, i la posterior unió d'un client **Windows 11** al domini creat `widad.cat`.

---

## Configuració del Servidor Windows (DC)

### Pas 1 – Configuració IP estàtica del servidor
El primer pas és assignar una adreça IP estàtica al servidor perquè el client pugui trobar-lo sempre a la mateixa adreça. He anat a **Panel de control → Redes e Internet → Conexiones de red** i he configurat el **Protocol TCP/IPv4** amb els valors següents:

* **Adreça IP:** `10.0.2.14`

<img width="456" height="629" alt="image" src="https://github.com/user-attachments/assets/6165ee29-afff-469d-a36b-fdaccd286cd9" />



### Pas 2 – Agregar el rol de Active Directory Domain Services
He obert el **Administrador del servidor** i he accedit al menú **Administrar → Agregar roles y características** per iniciar l'assistent d'instal·lació.

![Administrador del servidor - Agregar roles](imatges-windows/2.png)

### Pas 3 – Selecció del servidor de destí
Dins de l'assistent, he seleccionat el servidor local **WIN-WIDAD2026** amb la IP `10.0.2.17` per procedir amb la instal·lació del rol.

![Selecció del servidor de destí](imatges-windows/3.png)

### Pas 4 i 5 – Selecció del rol: Servicios de dominio de Active Directory
A la llista de rols, he marcat **Servicios de dominio de Active Directory**. El sistema ha avisat que calia instal·lar també les eines d'administració (RSAT), les quals he acceptat clicant a **Agregar características**.
<img width="605" height="387" alt="image" src="https://github.com/user-attachments/assets/7192b285-c534-48e4-a79b-3acd30ba9442" />


![Confirmació d'instal·lació de característiques addicionals](imatges-windows/4.png)

### Pas 6 – Confirmació i inici de la instal·lació
He revisat el resum de la instal·lació del rol AD DS i les seves eines. He clicat a **Instalar** per començar el procés.

![Confirmació de la instal·lació](imatges-windows/6.png)

---

## Promoció del servidor a Controlador de Domini

### Pas 8 – Notificació: Promoure aquest servidor a DC
Després de la instal·lació, he clicat sobre la icona de la bandera groga a l'Administrador del Servidor i he seleccionat **Promover este servidor a controlador de dominio**.

![Notificació: Promoure a DC](imatges-windows/8.png)

### Pas 9 – Configuració d'implementació: nou bosc
Com que és el primer domini de la xarxa, he seleccionat l'opció **Agregar un nuevo bosque** i he configurat el nom de domini arrel com a `widad.cat`.

![Configuració d'implementació - Nou bosc widad.cat](imatges-windows/9.png)

### Pas 10 – Opcions del controlador de domini
He establert el nivell funcional a **Windows Server 2016** i he deixat marcades les opcions de **Servidor DNS** i **Catálogo global**. També he definit la contrasenya del mode de restauració (**DSRM**).

![Opcions del controlador de domini](imatges-windows/10.png)

### Pas 11 – Opcions addicionals: nom NetBIOS
L'assistent ha assignat automàticament el nom NetBIOS **WIDAD**. Aquest és el nom curt per identificar el domini a la xarxa.

![Nom de domini NetBIOS: WIDAD](imatges-windows/11.png)

### Pas 12 – Rutes d'accés
He mantingut les rutes per defecte per a la base de dades **NTDS**, els arxius de registre i la carpeta **SYSVOL**.

![Rutes d'accés de la base de dades AD DS](imatges-windows/12.png)

### Pas 13 – Comprovació de requisits previs i instal·lació
El sistema ha verificat que tots els prerequisits es compleixen correctament. He clicat a **Instalar** i el servidor s'ha reiniciat automàticament en finalitzar.

![Comprobació de requisits previs](imatges-windows/13.png)

### Pas 15 – Primer inici de sessió com a WIDAD\Administrador
Un cop reiniciat, la pantalla de login ja m'ha permès entrar com a **WIDAD\Administrador**, confirmant que el controlador de domini ja està operatiu.

![Inici de sessió com a WIDAD\Administrador](imatges-windows/15.png)

---

## Gestió d'usuaris al Active Directory

### Pas 16 – Obrir "Usuarios y equipos de Active Directory"
Per començar a gestionar comptes, he obert la consola **Usuarios y equipos de Active Directory** des del menú d'eines administratives.

### Pas 17 – Crear un nou usuari de domini
Dins del contenidor **Users** del domini `widad.cat`, he fet clic dret i he seleccionat **Nuevo → Usuario**.

### Pas 18 – Dades del nou usuari Widad
He omplert la informació del compte:
* **Nombre de pila:** `widad`
* **Nombre de inicio de sesión:** `widad@widad.cat`

![Dades de l'usuari Widad](imatges-windows/18.png)

### Pas 19 – Contrasenya i opcions de seguretat
He definit una contrasenya segura i he marcat les opcions següents:
* **El usuario no puede cambiar la contraseña.**
* **La contraseña nunca expira.**

![Configuració de contrasenya de l'usuari Widad](imatges-windows/19.png)

### Pas 20 – Verificació: usuari creat correctament
He confirmat que l'usuari **Widad** ja apareix correctament al llistat del contenidor Users dins del bosc `widad.cat`.

---

## Unió del Client Windows 11 al Domini

### Pas 22 – Configuració DNS del client: apuntar al DC
Pas fonamental: he configurat l'adreça **10.0.2.17** (la IP del servidor) com a **Servidor DNS preferit** del client Windows 11 perquè pugui trobar el domini `widad.cat`.

![Configuració DNS del client](imatges-windows/22.png)

### Pas 23 – Unir el client al domini
Dins de Windows 11, he anat a **Configuración → Cuentas → Obtener acceso a trabajo o escuela** i he seleccionat **"Unir este dispositivo a un dominio local de Active Directory"**.

![Configuració unió a domini](imatges-windows/23.png)

### Pas 24 – Introduir el nom del domini
Al diàleg d'unió, he escrit el nom del meu domini: `widad.cat`.

### Pas 25 – Autenticació amb credencials del domini
He introduït les credencials de l'**Administrador** per autoritzar l'entrada de l'equip al domini.

![Credencials de l'administrador](imatges-windows/25.png)

### Pas 27 – Inici de sessió al client amb l'usuari de domini
He reiniciat el client i a la pantalla de login ja he pogut entrar amb el compte **WIDAD\widad**.

![Pantalla d'inici de sessió: widad.cat\widad](imatges-windows/27.png)

### Pas 28 – Benvinguda: sessió iniciada correctament
L'usuari **Widad** ha entrat correctament al sistema, finalitzant amb èxit tota la configuració de l'Active Directory.

![Pantalla de benvinguda](imatges-windows/28.png)
