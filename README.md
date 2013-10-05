Abhörsicherer E-Mail Service
============================

To-Do's und Fragen
------------------

* Wie soll das Projekt heißen?
* dieses Dokument ergänzen
* interessante andere Links? / Projekte?
* erstes Treffen im neuen Semester organisieren

Interessante Links
------------------

* http://prism-break.org/
* https://github.com/sebsauvage/ZeroBin

Begrifflichkeiten
-----------------

* Alice: der Besucher, der die Nachricht schreiben will
* Bob: der Empfänger der Nachricht, der keine Verschlüsselung alla PGP anbietet
* Web-App: unsere App, die im Browser des Besuchers über JavaScript ausgeführt wird (vertrauenswürdig)
* Client: Browser des Besuchers (vertrauenswürdig)
* Server: unserer Server (vertrauenswürdig)
* E-Mail Provider: Gmail und Co (nicht vertrauenswürdig)

Wie es funktionieren könnte
---------------------------

### Möglichkeit 1: Schlüssel auf Server speichern und nach einer Benutzung löschen

1. Alice schreibt Nachricht in der Web-App und drückt dann auf "verschlüsseln"
2. Server erzeugt Schlüssel, schickt ihn an Web-App und speichert diesen.
3. Nachricht wird in Web-App mit Schlüssel des Servers verschlüsselt und es wird ein Link der Form http://<unser-service>.org/<Schlüssel-ID>/<verschlüsselte Nachricht in base64> erzeugt.
4. Link wird via E-Mail an Bob verschickt
5. Bob besucht den Link; Server sendet gespeicherten Link an Bob und löscht diesen

### Möglichkeit 2: verschlüsselte Nachricht wird auf dem Server gespeichert

1. Alice schreibt Nachricht in der Web-App und drückt dann auf "verschlüsseln"
2. Web-App erzeugt Schlüssel und verschlüsselt die Mail
3. verschlüsselte Nachricht wird auf dem Server gespeichert
4. Link alla http://<server>/<message-id>#<schluessel> wird per Mail an Bob geschickt
    * alles hinter der Raute wird nicht an Server geschickt
5. eine Nachricht kann nur auf einem Client gelesen werden

Probleme / Lücken im System
---------------------------

* E-Mail Provider liest Nachricht und erzeugt eine neue mit unserem Service
    * Gegenmaßnahme: Captcha beim Versand
    * Gegenmaßnahme: Benutzer müssen sich anmelden (Absender wird auch angezeigt)
    * Gegenmaßnahme: System wird von Bots auf Konsistenz geprüft
* E-Mail Provider liest Nachricht und zeigt sie dem Kunden in Klarform oder unter ihrem Server an
    * Gegenmaßnahme: System wird von Bots auf Konsistenz geprüft
    * URL oder Form der E-Mail ändert sich -> überprüfbar

Brainstorming
-------------

* zusätzliches Passwort über zusätzlichen Kanal ausgetauscht wird
* verschiedene Kanäle benutzen
* zusätzliches Feld wie: "Bei welchem Festival waren wir zusammen dieses Jahr?"