# Manuale CISCO Packet Tracer

## 1 Nozioni di base

### 1.1 Palette dei dispositivi

In basso a sinistra si trova la palette dei dispositivi, suddivisa in sei sezioni in base al tipo di componenti che si desidera inserire nel progetto.
![palette dei dispositivi](img/Cisco-packet.png)
In ordine da sinistra, le sezioni della palette dei dispositivi sono:

1. **Network Devices (Dispositivi di rete)**  
   Contiene tutti i dispositivi fondamentali per creare una rete, come **router, switch, hub e firewall**. Questi apparati permettono di instradare e gestire il traffico dati.

2. **End Devices (Dispositivi finali)**  
   Include i dispositivi degli utenti o terminali della rete, come **PC, laptop, server, telefoni IP e tablet**. Questi dispositivi inviano e ricevono dati attraverso la rete.

3. **Components (Componenti)**  
   Comprende **moduli aggiuntivi** da inserire nei dispositivi di rete, come schede di rete, schede wireless o interfacce supplementari per router e switch.

4. **Connections (Connessioni)**  
   Contiene i **cavi e le connessioni** per collegare i dispositivi, come cavi Ethernet, cavi seriali o connessioni wireless.

5. **Miscellaneous (Varie)**  
   Qui si trovano **strumenti aggiuntivi**, come sensori, luci di segnalazione o altre funzionalità speciali non incluse nelle altre categorie.

6. **Multiuser Connection (Connessione multiutente)**  
   Permette di creare **connessioni tra più utenti o istanze di Packet Tracer**, utile per esercitazioni collaborative o simulazioni avanzate.

# 1.2 Simulazione
Per quanto riguarda la simulazione, è possibile verificare la corretta comunicazione tra due host o dispositivi di rete utilizzando il comando **Add Simple PDU** e cliccando sui due host da testare.

![icona 'add simple PDU'](img/PDU.png)

Successivamente, per visualizzare il risultato della comunicazione, bisogna andare su **Simulation**, cliccare su *Play* e controllare nella tabella in basso la colonna **Last Status**.  
- Se compare la scritta **Successful**, significa che i due host comunicano correttamente.
![succesful](img/connection_succesful.png)  
- In caso contrario, c'è un problema, che può essere di natura fisica (cavi non collegati correttamente) o legato alla configurazione di rete dei singoli host.
![failed](img/connection_failed.png)

# 1.3 Configurazione di rete di un host
Per configurare un host all'interno di una rete, sia cablata (**wired**) che wireless, è necessario assegnargli un **IP univoco** e una **maschera di rete**.

- **Dispositivi cablati (wired):**  
  1. Cliccare sull'host.  
  2. Andare nella sezione **Config**.  
  3. Selezionare la scheda **FastEthernet**.  
  4. Nella parte relativa all'indirizzo **IPv4**, inserire l'**IP** e la **maschera di rete**.

![wired](img/pc_wired_conf.png)

- **Dispositivi wireless:**  
  1. Cliccare sull'host.  
  2. Andare nella sezione **Config**.  
  3. Selezionare la scheda **Wireless**.  
  4. Inserire l'**IP** e la **maschera di rete**, e impostare l'**SSID** corrispondente all'Access Point a cui ci si vuole collegare.

![wireless AP](img/access_point_conf.png)
![wireless PC](img/pc_wireless_conf.png)

## 2 Singola rete LAN: 1 switch con più host

### 2.1 Descrizione
In questo esempio si realizza una **rete LAN semplice** composta da un singolo **switch** collegato a più **host** (PC o dispositivi finali).  
Tutti gli host appartengono alla stessa rete e possono comunicare tra loro tramite lo switch.  
Questa configurazione è utile per simulare ambienti di rete domestici o piccoli uffici, dove tutti i dispositivi condividono lo stesso segmento di rete.

### 2.2 Morfologia
![Morfologia Rete 1](img/Morfologia_Rete1.jpg)

### 2.3 Realizzazione fisica della rete
Per iniziare, inserire nel progetto un PC, un computer e un server. Questi dispositivi si trovano nella palette dei dispositivi, nella sezione **End Devices** → **End Devices**.  

Successivamente, aggiungere uno switch dalla sezione **Network Devices** → **Switches**.  

Infine, collegare tutti gli host allo switch utilizzando i cavi. È possibile utilizzare la scelta automatica del cavo per semplificare il collegamento.

![rete_fisica 1](img/rete_fisica1.png)

### 2.4 Configurazione degli IP e delle maschere

Come si può notare dall'immagine sopra, i collegamenti allo switch sono segnati in arancione. Questo indica che la comunicazione non funzionerebbe correttamente se provassimo a simularla in questo momento, perché non sono stati ancora assegnati IP e maschere agli host.  

Procederemo creando una rete di tipo **C**, con **24 bit per la rete** e **8 bit per gli host**, utilizzando la maschera **255.255.255.0**. L'indirizzo di rete scelto sarà **192.168.1.0**, e agli host assegneremo gli IP seguenti: **192.168.1.1** al PC, **192.168.1.11** al computer e **192.168.1.101** al server.

## 3 Due reti LAN: 1 router interfacciato a 2 switch

### 3.1 Descrizione
In questo esempio si realizza una **topologia con due reti LAN separate**, ciascuna collegata a uno **switch**, e con un **router** che permette la comunicazione tra le due reti.  
Ogni LAN è composta da più host che comunicano tra loro tramite lo switch locale, mentre il router gestisce l'instradamento dei dati tra le due reti.  
Questa configurazione è utile per simulare ambienti di rete più complessi, come uffici con più reparti o segmenti di rete separati, che necessitano di collegamento tramite un dispositivo di routing.

### 3.2 Morfologia
![Morfologia Rete 2](img/Morfologia_Rete2.jpg)

### 3.3 Realizzazione fisica della rete

Per cominciare, inserire nel progetto due PC, due computer e due server. Questi dispositivi si trovano nella palette dei dispositivi, nella sezione **End Devices** → **End Devices**.  

Aggiungere poi due switch dalla sezione **Network Devices** → **Switches** e un router dalla sezione **Network Devices** → **Routers**.  

Infine, effettuare i collegamenti fisici tra gli host e gli switch, e collegare gli switch al router centrale. È possibile utilizzare la funzione di selezione automatica del cavo per semplificare l’operazione, ma è importante collegare il router utilizzando le porte **GigabitEthernet**.


![rete_fisica](img/rete_fisica2.png)

### 3.4 Configurazione degli IP e delle maschere

Per rendere operativa la rete, è necessario configurare gli host. Entrambe le reti saranno di tipo **C** con maschera **255.255.255.0**. Alla **rete 1** viene assegnato l'indirizzo di rete **192.168.1.0**, mentre alla **rete 2** l'indirizzo **192.168.2.0**.  

Per quanto riguarda gli host, in entrambe le reti i PC avranno l'IP **1**, i computer **11** e i server **101**.

Successivamente, si passa alla configurazione del router, che avrà due indirizzi IP: uno per ciascuna rete a cui è collegato. Nella **rete 1** assegneremo al router l'IP **192.168.1.254**, mentre nella **rete 2** l'IP sarà **192.168.2.254**.  

È inoltre necessario abilitare le porte del router utilizzate per il collegamento agli switch. Per farlo, accedere alle impostazioni del router, andare nella sezione **Config** → **Interface**, selezionare la porta desiderata e attivare la casella **Port Status** impostandola su **On**.  

Infine, in ogni host, accedere alla sezione **Config** e impostare come **Default Gateway** l'IP del router corrispondente alla rete a cui l'host appartiene.