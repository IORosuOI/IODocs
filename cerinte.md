# docsIO_ISS2026

Proiect realizat pentru disciplina **Ingineria Sistemelor Software (ISS)**, anul universitar 2025-2026.

## 📝 Descrierea Proiectului
Aplicație pentru gestionarea și editarea documentelor (Document Management System), dezvoltată pe o arhitectură stratificată (Presentation, Business Logic, Data Access). Proiectul parcurge toate etapele procesului ingineresc: colectare cerințe, analiză, proiectare, implementare și testare.

---

## ⚙️ Cerințe Generale
- **Arhitectură:** Stratificată (Presentation, Business Logic, Data Access).
- **Complexitate:** Medie (6-10 funcționalități majore).
- **Tehnologii:** Limbaj orientat obiect (Java/Spring Boot), Bază de date relațională, bibliotecă ORM.
- **Modelare:** Diagrame UML realizate într-un instrument CASE.
- **CRUD:** Implementat pentru cel puțin o entitate principală.

---

## 🛠️ Structura Laboratoarelor și Artefacte

### FAZA I (Colectarea și analiza cerințelor)
**Laboratorul 1**
- Stabilirea temei și definirea funcționalităților majore (6–10).
>Tema: Aplicatie de management a documentelor (docsIO)
        -Editor minimalist de text cu functii de auto-salvare
        -Sistem de organizare ierarhica (Foldere si Sub-foldere)
        -Partajarea documentelor cu permisiuni specifice (Citire/Editare)
        -Sistem de versionare si recuperare (Undo/Redo) la nivel de continut
        -Cos de gunoi (Trash) pentru stergere logica si recuperare
        -Cautare globala si filtrare dupa tag-uri sau data modificarii
        -Sistem de roluri pentru utilizatori (Admin, Editor, Viewer)
        -Exportarea documentelor in formate multiple (PDF, TXT)
>

**Laboratorul 2**
- Modelul funcțional (Diagrama UML a cazurilor de utilizare + descrierea textuală/tabelară).
>
Analiza fluxurilor de utilizare pentru crearea si partajarea documentelor.
>
- Specificarea cerințelor nefuncționale.
>
    -Interfata intuitiva si minimalista (Clean UX)
    -Sincronizarea schimbarilor in timp real (sub 2 secunde)
    -Securitate prin criptare si autentificare multi-factor (2FA)
    -Disponibilitatea vizualizarii documentelor in mod offline
>

- Planificarea pe 3 iterații.
>
Iterația 1: CRUD
    Gestiune Documente (CRUD): Creare, vizualizare, editare și ștergere a notelor (Titlu, Continut, Data Crearii).

        -Vizualizare tip Grid: 
        Afisarea documentelor sub forma de carduri intuitive.

        -Autentificare de baza:
        Creare cont si Login (Sistem de sesiuni).

        -Filtrare simpla:
        Sortarea documentelor dupa titlu sau data.

Iterația 2: Business Logic
    Funcționalități de organizare si acces:

        -Sistem de Foldere:
        Logica de organizare a documentelor in directoare.

        -Partajare (Sharing):
        Permisiunea de a invita alti utilizatori in documente specifice (RBAC).

        -Cos de gunoi (Recycle Bin):
        Gestionarea documentelor sterse temporar.

        -Undo/Redo:
        Implementarea istoricului de actiuni pentru editor.

Iterația 3: Quality of Life++
    Finisări și funcții complexe:

        -Setari Avansate:
        Configurarea temelor (Dark/Light), limbii si preferintelor de securitate.

        -Sistem de Versionare:
        Salvarea starilor documentului pentru revenire la versiuni anterioare.

        -Export PDF/TXT:
        Generarea de fisiere descarcabile din continutul documentului.

        -Analytics:
        Statisici despre timpul de editare si frecventa accesarii.

**Laboratorul 3**
- Modelul conceptual (Diagramă UML de clase pentru entitățile domeniului).
- Prototipul interfeței grafice cu utilizatorul (GUI).

### FAZA II (Proiectare/implementare/testare iterația 1)
**Laboratorul 4**
- Diagrame de interacțiune (secvență/comunicare) pentru Iterația 1.
- Rafinarea diagramei de clase cu entitățile domeniului soluției.

**Laboratorul 5**
- Prima versiune funcțională: Implementare și testare Iterația 1.

### FAZA III (Proiectare/implementare/testare iterații 2, 3)
**Laboratorul 6**
- Design și rafinare diagramă de clase pentru Iterația 2.
- Implementare și testare Iterația 2.

**Laboratorul 7**
- Diagrame de interacțiune și rafinare finală pentru Iterația 3.
- Implementare și testare versiune finală.

---

## 📅 Termene de Predare
| Faza | Laboratoare | Termen Limită |
| :--- | :--- | :--- |
| **Faza 1** | Lab 1, 2, 3 | Săptămâna 5/6 |
| **Faza 2** | Lab 4, 5 | Săptămâna 9/10 |
| **Faza 3** | Lab 6, 7 | Săptămâna 13/14 |

*Notă: Predarea după termen se penalizează cu 1 punct / săptămână de întârziere.*