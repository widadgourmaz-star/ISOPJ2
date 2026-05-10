# Sprint 4: Infraestructura d'Emmagatzematge i Seguretat de Dades

---

# Implementació i Gestió de Volums RAID 5 (Widad)

## 1. Fonaments Teòrics: L'Arquitectura RAID

En entorns de servidors professionals, la disponibilitat de les dades és crítica. El sistema **RAID** (*Redundant Array of Independent Disks*) és una solució que combina diversos discos físics per formar una única unitat lògica.

### 1.1 Què és el RAID 5 i com funciona?
El **RAID 5** és un sistema de **Paritat Distribuïda**. És el nivell més utilitzat en empreses perquè ofereix un equilibri perfecte entre cost, velocitat i seguretat.

* **La Paritat (Càlcul XOR):** És un càlcul matemàtic. Si un disc es trenca, el sistema utilitza aquesta informació per reconstruir el que falta.
* **Capacitat Real:** En un RAID 5 de 3 discos, la capacitat útil segueix la fórmula **(N-1)**. Si tenim 3 discos de 10GB, tindrem 20GB de dades i 10GB per a la paritat.
* **Avantatges:** Millora la velocitat de lectura perquè demana dades a tots els discos simultàniament.

| Caracteristica | RAID 0 | RAID 1 | RAID 5 |
| :--- | :--- | :--- | :--- |
| **Tolerància a fallades** | ❌ Cap | ✅ 1 o més discos | ✅ **1 disc** |
| **Ús d'espai** | 100% | 50% | **N-1** |

---

## 2. Fase de Configuració Tècnica Pas a Pas

### Pas 1 – Preparació del Maquinari a VirtualBox
He configurat **3 unitats VDI de 10 GB** cadascuna a VirtualBox per simular els discos físics reals que formaran el RAID.

![Configuració de discos](imatges-windows/1.png)

### Pas 2 i 3 – Inicialització i Estil GPT
He obert el Gestor de Discs. Windows Server ha detectat els nous dispositius i els he inicialitzat fent servir l'estil **GPT**, que és més modern i segur.

![Inicialització GPT](imatges-windows/3.png)

### Pas 4, 5 i 6 – Conversió a Discos Dinàmics
He convertit els 3 discos a **Dinàmics**. Aquest pas és obligatori a Windows per poder crear volums RAID per programari.

![Conversió a Dinàmics](imatges-windows/6.png)

### Pas 7, 8 i 9 – Creació del Volum RAID 5
He seleccionat "Nuevo volumen RAID-5" i he afegit els 3 discos. El sistema m'ha confirmat que l'espai total disponible és de **20 GB**.

![Creació del volum](imatges-windows/9.png)

### Pas 10, 11 i 12 – Sistema de Fitxers i Format
He assignat la lletra **R:** i he formatat la unitat en **NTFS** amb l'etiqueta `RAID5-Widad`. El sistema realitza una sincronització inicial.

![Formatant la unitat](imatges-windows/11.png)

---

## 3. Simulació de Fallades i Resiliència

### Pas 17, 18 i 19 – Primera Fallada (Estat Degradat)
He posat el **Disc 1 fora de línia**. L'estat canvia a **"Error de redundancia"**. Els fitxers segueixen accessibles gràcies a la paritat.

![Estat degradat](imatges-windows/19.png)

### Pas 20 i 21 – Segona Fallada (Col·lapse)
He desactivat un segon disc. En aquest moment, el RAID 5 deixa de funcionar. Això confirma que només suporta la pèrdua d'un disc.

![RAID col·lapsat](imatges-windows/22.png)

### Pas 22 al 27 – Recuperació i Resincronització
He tornat a posar els discos en línia i he seleccionat **Reactivar disco**. Windows ha iniciat la resincronització per tornar a l'estat **Correcto**.

![Resincronització](imatges-windows/26.png)

---

## 4. Conclusions
El RAID 5 és una solució excel·lent per a servidors de dades, ja que optimitza l'espai i garanteix la continuïtat del treball davant d'una avaria física.
