
 ** Protocoles IoT (Internet of Things) **
---

## 🔗 1. **MQTT (Message Queuing Telemetry Transport)**

### 📌 Définition

Protocole de messagerie **pub/sub** léger basé sur **TCP/IP**, conçu pour les réseaux à faible bande passante et les connexions instables.

### 🏗️ Architecture & Fonctionnement

* Basé sur le modèle **Publisher → Broker → Subscriber**.
* Le **broker** (ex : Mosquitto, HiveMQ) centralise tous les messages.
* Utilise des **topics** hiérarchiques.
* Fonctionne au-dessus de **TCP** avec option SSL/TLS.

### ✅ Avantages

* Très léger : parfait pour les capteurs avec peu de ressources.
* Supporte la **qualité de service (QoS)** (0, 1, 2).
* Fonctionne très bien derrière les NAT/firewalls.

### ❌ Inconvénients

* Dépendance au broker.
* Pas adapté pour les transferts de fichiers lourds.

### 📍 Utilisation

* Domotique (Home Assistant, OpenHAB).
* Surveillance industrielle.
* Agriculture connectée.



## 🔗 2. **CoAP (Constrained Application Protocol)**

### 📌 Définition

Protocole RESTful, similaire à HTTP, mais optimisé pour les appareils contraints. Fonctionne sur **UDP**.

### 🏗️ Architecture & Fonctionnement

* Basé sur un modèle **client/serveur**.
* Communication par **messages UDP** avec support de **confirmable (ACK)** et **non-confirmable**.
* Utilise le format **CBOR** ou **JSON**.
* Supporte l'observation des ressources (observer pattern).

### ✅ Avantages

* Très faible overhead.
* Peut fonctionner sans connexion permanente.
* Compatible avec le modèle REST (GET, POST, PUT, DELETE).

### ❌ Inconvénients

* Moins fiable qu’un protocole TCP (perte de paquets possible).
* Pas de standardisation complète pour la sécurité (bien que DTLS soit souvent utilisé).

### 📍 Utilisation

* Capteurs environnementaux.
* Surveillance de réseau LoRaWAN ou 6LoWPAN.
* Réseaux urbains intelligents.

---

## 🔗 3. **HTTP/HTTPS**

### 📌 Définition

Protocole client/serveur universel du Web, parfois utilisé pour des solutions IoT simples ou compatibles Web.

### 🏗️ Architecture & Fonctionnement

* Modèle **requête/réponse**.
* Fonctionne au-dessus de **TCP/IP**.
* Supporte le **RESTful API**.
* HTTPS ajoute **SSL/TLS** pour la sécurité.

### ✅ Avantages

* Très répandu, bien connu, facilement intégrable.
* Facile à debugger et utiliser via navigateur ou outils comme Postman.
* Interopérabilité élevée.

### ❌ Inconvénients

* Overhead élevé.
* Pas optimisé pour les communications fréquentes ou en temps réel.

### 📍 Utilisation

* Appareils connectés à des services Web (cloud).
* Solutions de prototypage rapide.
* API de passerelles ou dashboards IoT.

---

## 🔗 4. **AMQP (Advanced Message Queuing Protocol)**

### 📌 Définition

Protocole de messagerie orienté file d’attente, très robuste, utilisé dans les environnements professionnels et critiques.

### 🏗️ Architecture & Fonctionnement

* Fonctionne au-dessus de **TCP**.
* Modèle **publish/subscribe ou point-à-point**.
* Utilise des **exchanges** et des **queues**.
* Prise en charge des **transactions**, **accusés de réception**, **sécurité forte**.

### ✅ Avantages

* Très fiable et sécurisé.
* Transactions complexes possibles.
* Grande scalabilité.

### ❌ Inconvénients

* Lourd pour les appareils à ressources limitées.
* Complexité de déploiement.

### 📍 Utilisation

* IoT industriel (IIoT).
* Intégration dans les systèmes backend (ex : RabbitMQ).
* Transports et logistique.

---

## 🔗 5. **DDS (Data Distribution Service)**

### 📌 Définition

Protocole orienté données pour systèmes temps réel distribués. Utilise un modèle **data-centric pub/sub** sans broker.

### 🏗️ Architecture & Fonctionnement

* Communication **peer-to-peer**.
* Pas de serveur central : les nœuds découvrent dynamiquement les données disponibles.
* Supporte **QoS avancé**, **multicast**, **sécurité intégrée**.

### ✅ Avantages

* Temps réel avec faible latence.
* Très robuste, sans point de défaillance unique.
* Supporte les systèmes critiques.

### ❌ Inconvénients

* Complexité de configuration.
* Peu utilisé dans des systèmes très contraints (poids du middleware).

### 📍 Utilisation

* Aéronautique (avionique).
* Robotique avancée (ROS 2).
* Systèmes militaires et embarqués critiques.

---

## 🔗 6. **XMPP (Extensible Messaging and Presence Protocol)**

### 📌 Définition

Protocole XML initialement conçu pour la messagerie instantanée, adapté à certains scénarios IoT.

### 🏗️ Architecture & Fonctionnement

* Basé sur **client/serveur**, messages **XML** sur **TCP**.
* Supporte l’**extensibilité via XEPs** (protocoles additionnels).
* Capable de **présence**, **adresse logique**, **sécurité (SASL, TLS)**.

### ✅ Avantages

* Décentralisé et extensible.
* Peut être utilisé pour contrôler et monitorer les appareils.
* Sécurité native.

### ❌ Inconvénients

* XML trop verbeux pour les appareils contraints.
* Complexité des extensions (XEPs).

### 📍 Utilisation

* Smart Grid.
* Échange machine-to-machine sécurisé.
* Réseaux d’agents intelligents.

---

## 🔗 7. **Zigbee**

### 📌 Définition

Protocole sans fil basé sur **IEEE 802.15.4** pour la communication **maillée à faible consommation**.

### 🏗️ Architecture & Fonctionnement

* Topologie : **maillé, étoile, arborescence**.
* Rôles : **Coordinator**, **Router**, **End Device**.
* Fonctionne dans la bande **2.4 GHz** (ou autres).
* Pile complète OSI jusqu’à l’application.

### ✅ Avantages

* Maillage intelligent (auto-réparation).
* Très faible consommation.
* Norme éprouvée (utilisée dans la domotique).

### ❌ Inconvénients

* Débit limité (\~250 kbps).
* Portée réduite sans répéteurs.

### 📍 Utilisation

* Maison connectée (Philips Hue, IKEA TRÅDFRI).
* Éclairage intelligent.
* Capteurs de sécurité.

---

## 🔗 8. **LoRaWAN (Long Range Wide Area Network)**

### 📌 Définition

Protocole LPWAN (Low Power Wide Area Network) basé sur la modulation **LoRa**.

### 🏗️ Architecture & Fonctionnement

* Réseau **étoile** : capteurs → passerelle → serveur de réseau → serveur d’application.
* Communication asynchrone (uplink/downlink limité).
* Chiffrement de bout en bout (AES-128).
* Très faible consommation.

### ✅ Avantages

* Très longue portée (jusqu’à 10-15 km).
* Autonomie des capteurs > 5 ans.
* Licence radio gratuite (ISM).

### ❌ Inconvénients

* Faible bande passante (\~50 kbps).
* Limitations en messages downlink.
* Latence non garantie.

### 📍 Utilisation

* Agriculture (capteurs de sol, météo).
* Villes intelligentes (déchets, stationnement).
* Suivi logistique.

---

## 🔗 9. **Bluetooth Low Energy (BLE)**

### 📌 Définition

Extension du Bluetooth classique pour les appareils à faible consommation.

### 🏗️ Architecture & Fonctionnement

* Communication **point-à-point** ou **broadcast**.
* Profils standardisés (GATT, GAP).
* Pile complète OSI intégrée.

### ✅ Avantages

* Très faible consommation.
* Intégré aux smartphones/tablettes.
* Sécurité (pairing, chiffrement AES-CCM).

### ❌ Inconvénients

* Portée limitée (10–100 m).
* Connexion à un seul central en général.

### 📍 Utilisation

* Wearables (montres, capteurs santé).
* Balises de localisation (iBeacon).
* Accès sans clé.

---

## 📌 Synthèse Comparative (Résumé)

| Protocole | Modèle         | Transport | Cas d’usage typique   | Avantage principal   | Inconvénient principal     |
| --------- | -------------- | --------- | --------------------- | -------------------- | -------------------------- |
| MQTT      | Pub/Sub        | TCP       | Domotique, capteurs   | Léger, fiable        | Dépendance au broker       |
| CoAP      | REST           | UDP       | Capteurs simples      | Léger, RESTful       | Fiabilité limitée          |
| HTTP      | REST           | TCP       | APIs IoT, dashboards  | Universel            | Trop verbeux               |
| AMQP      | Pub/Sub        | TCP       | IIoT, backends        | Fiabilité, sécurité  | Trop lourd                 |
| DDS       | Pub/Sub        | UDP       | Robotique, avionique  | Temps réel           | Complexe à mettre en place |
| XMPP      | Client/Serveur | TCP       | Smart Grid            | Extensible, sécurisé | Trop lourd (XML)           |
| Zigbee    | Mesh           | RF        | Maison connectée      | Maillage efficace    | Débit faible               |
| LoRaWAN   | Étoile         | RF        | Réseaux longue portée | Autonomie, portée    | Débit très faible          |
| BLE       | P2P            | RF        | Wearables, BLE tags   | Énergie réduite      | Connexion limitée          |


