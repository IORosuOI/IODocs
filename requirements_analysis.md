# 📂 IODocs - Documentație Model Funcțional (Faza I)

## 1. Diagrama Cazurilor de Utilizare (Use Case Diagram)
![Diagrama UML Use Case](link_catre_imaginea_ta_aici.png)
*Notă: Diagrama ilustrează interacțiunile principale dintre Actori (User, Admin, Guest) și funcționalitățile sistemului, evidențiind relația de tip <<extend>> pentru funcția de Export.*

---

## 2. Descrierea Textuală a Cazurilor de Utilizare (Cockburn Template)

### **UC-1: Partajare Document (Share a Document)**
| Câmp | Detalii |
| :--- | :--- |
| **ID și nume** | UC-1: Share a Document |
| **Actor primar** | Utilizator (Proprietar) |
| **Actori secundari** | Sistem de Baze de Date |
| **Descriere** | Un proprietar acordă acces unui alt utilizator înregistrat prin introducerea adresei de email și selectarea nivelului de permisiune. |
| **Trigger** | Utilizatorul apasă butonul "Share" din meniul documentului. |
| **Precondiții** | PRE-1: Documentul există în sistem.<br>PRE-2: Utilizatorul are drepturi de scriere/administrare asupra documentului. |
| **Postcondiții** | POST-1: O nouă înregistrare de permisiune este salvată.<br>POST-2: Documentul apare în lista "Shared" a destinatarului. |
| **Flux Normal** | **1.0 Partajare Document**<br>1. Utilizatorul solicită partajarea unui document.<br>2. Sistemul solicită adresa de email a destinatarului.<br>3. Utilizatorul introduce email-ul. (vezi 1.0.E1)<br>4. Sistemul afișează opțiunile de permisiune (Read-Only, Can Edit).<br>5. Utilizatorul alege nivelul și confirmă.<br>6. Sistemul validează existența destinatarului în baza de date.<br>7. Sistemul acordă accesul și afișează confirmarea succesului. |
| **Fluxuri alternative** | **1.1 Actualizare permisiune existentă**<br>1. Dacă destinatarul are deja acces, sistemul afișează nivelul actual.<br>2. Utilizatorul alege un nou nivel și revine la pasul 7 din fluxul normal. |
| **Excepții** | **1.0.E1 Email negăsit**<br>1. Sistemul informează utilizatorul că adresa nu este înregistrată.<br>2. Utilizatorul poate reintroduce email-ul sau poate anula procesul. |
| **Method-level traces** | `ro.ubb.docsio.service.SharingService#validateRecipient`<br>`ro.ubb.docsio.repository.PermissionRepository#saveAccessLevel`<br>`ro.ubb.docsio.controller.DocumentController#handleShareRequest` |

---

### **UC-2: Organizare în Foldere (Organize Folders)**
| Câmp | Detalii |
| :--- | :--- |
| **ID și nume** | UC-2: Organize Folders |
| **Actor primar** | Utilizator |
| **Actori secundari** | Niciunul |
| **Descriere** | Utilizatorul creează foldere noi sau mută documente/foldere existente pentru a menține o structură ierarhică. |
| **Trigger** | Utilizatorul selectează "New Folder" sau acțiunea "Move To". |
| **Precondiții** | PRE-1: Utilizatorul vizualizează Dashboard-ul.<br>PRE-2: Locația țintă permite drepturi de scriere. |
| **Postcondiții** | POST-1: Structura folderelor este actualizată în baza de date.<br>POST-2: Interfața se reîmprospătează pentru a reflecta ierarhia. |
| **Flux Normal** | **2.0 Creare și Mutare în Folder**<br>1. Utilizatorul solicită crearea unui folder nou.<br>2. Sistemul solicită numele folderului.<br>3. Utilizatorul introduce numele și confirmă. (vezi 2.0.E1)<br>4. Sistemul creează folderul în directorul curent.<br>5. Utilizatorul selectează un document și cere mutarea lui.<br>6. Sistemul afișează lista de foldere destinație disponibile.<br>7. Utilizatorul selectează folderul nou creat.<br>8. Sistemul mută documentul și actualizează ID-ul părintelui. (vezi 2.0.E2) |
| **Fluxuri alternative** | Niciunul |
| **Excepții** | **2.0.E1 Nume duplicat**<br>1. Sistemul anunță că există deja un folder cu acest nume.<br>2. Utilizatorul introduce un nume diferit.<br>**2.0.E2 Referință circulară**<br>1. Utilizatorul încearcă să mute un folder părinte într-unul din sub-folderele sale.<br>2. Sistemul blochează acțiunea și afișează o eroare. |
| **Method-level traces** | `ro.ubb.docsio.model.Folder#setParentId`<br>`ro.ubb.docsio.service.FolderService#createFolder`<br>`ro.ubb.docsio.validator.HierarchyValidator#checkCircularReference` |

---

## 3. Cerințe Nefuncționale (NFRs)

* **NFR-1 (Performanță):** Salvarea automată a documentului trebuie să se finalizeze în maxim 2 secunde de la încetarea tastării.
* **NFR-2 (Usabilitate):** Interfața trebuie să fie de tip "Clean UX", necesitând maxim 3 click-uri pentru a ajunge la funcția de "Export" din Dashboard.
* **NFR-3 (Disponibilitate):** Sistemul trebuie să permită vizualizarea documentelor deschise anterior în mod "Offline" prin cache-ul browserului.
* **NFR-4 (Scalabilitate):** Ierarhia de foldere trebuie să suporte minim 10 niveluri de adâncime fără degradarea vizibilă a performanței.