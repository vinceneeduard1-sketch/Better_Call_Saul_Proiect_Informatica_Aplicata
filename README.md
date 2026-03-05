# Better Call Saul API using Bluetooth Classic

Acest proiect a fost realizat de către **Vincene Eduard** și **Enciu Andrei Eduard** din grupa **ETTI-CTI-413A**.

##  Descriere Generală
Proiectul presupune conectarea unui telefon mobil prin intermediul **Bluetooth Classic** la o aplicație denumită „Proiect IA”. Prin această conexiune, se realizează configurarea plăcuței **ESP32** pentru acces la internet (WIFI), urmată de obținerea unor date de la un API web extern despre personajele din serialul *"Better Call Saul"*.

Comunicarea dintre aplicația mobilă și plăcuța ESP32 se realizează exclusiv prin schimb de date în format **JSON**, asigurând o structură flexibilă și ușor de extins.

##  Funcționalități Principale
* **Scanare rețele WIFI:** Plăcuța scanează rețelele disponibile și trimite către aplicație detalii precum SSID, puterea semnalului și tipul de criptare.
* **Conectare de la distanță:** Permite introducerea credențialelor WIFI în aplicație și transmiterea lor către ESP32 pentru autentificare.
* **Interogare API:** Plăcuța face cereri HTTP GET pentru a prelua lista de personaje și detaliile acestora.
* **Transmitere date prin Bluetooth:** Toate informațiile procesate (liste de rețele, confirmări de conexiune, date API) sunt transmise înapoi la telefon prin Bluetooth.

##  Structura Codului (Funcții Cheie)

### 1. Procesarea Comenzilor (`receivedData`)
Funcția principală de control care primește date prin Bluetooth și, în funcție de acțiunea specificată în JSON (`getNetworks`, `connect`, `getData`, `getDetails`), apelează logica corespunzătoare.

### 2. Gestionarea WIFI (`Lista_Retele` & `conecteaza`)
* **`Lista_Retele`**: Scanează mediul local și construiește un obiect JSON pentru fiecare rețea găsită.
* **`conecteaza`**: Primește SSID-ul și parola, încearcă stabilirea conexiunii și raportează succesul sau eșecul prin Bluetooth.

### 3. Integrarea cu API-ul (`get_data` & `detalii_extra`)
* **`get_data`**: Realizează o cerere GET către server pentru a obține lista generală de personaje (nume, ID, imagine).
* **`detalii_extra`**: Folosește un ID specific pentru a aduce informații amănunțite precum: data nașterii, ocupația, statusul, pseudonimul și sezoanele în care apare personajul.

##  Date Preluate (Exemple)
Aplicația afișează o listă interactivă cu personaje cunoscute:
* **Howard Hamlin** (ID: 113)
* **Gustavo Fring** (ID: 9)
* **Kimberly Wexler** (ID: 112)
* **Mike Ehrmantraut** (ID: 7)

---
**Tehnologii utilizate:** ESP32, Bluetooth Classic, JSON (ArduinoJson), HTTPClient.
