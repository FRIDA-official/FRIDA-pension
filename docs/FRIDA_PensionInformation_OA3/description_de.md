# Overview
<p>Der Frida PensionService ermöglicht es dem Kunden, eine Berechnung seiner Rente für einen bestimmten Vertrag durchzuführen. Dazu muss der Benutzer seine sichtbaren Verträge konfigurieren, auf die
auf die die DRI-Plattform zugreift, um anschließend die Berechnung anhand der Vertragsdaten durchzuführen. Nach dieser Konfiguration sind die Verträge im Rentencockpit sichtbar. Nach Auswahl eines 
bestimmten Vertrag aus der abgerufenen Liste kann eine Berechnung durchgeführt werden. Für all diese Schritte wird ein Token benötigt, das der Benutzer zuvor bei den Identitätsprovidern der Versicherungsgesellschaften anfordern muss. 
</p>

<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/User_en.png">     
<p>Dieses UML-Diagramm beschreibt die Beziehung zwischen dem Kunden und den beiden Plattformen. Er interagiert mit dem DRI-Portal, um seine Rente zu berechnen.
Die DRI-Plattform fragt dann die Verträge über die Kundenplattform ab. Darüber hinaus kann der Kunde über die Kundenplattform die sichtbaren Verträge konfigurieren.</p>

## Security
### Data in Transit
Bei der Übertragung von Informationen über Kommunikationsnetze besteht die Gefahr, dass Informationen unbefugt abgehört oder unbefugt manipuliert werden. Um die Vertraulichkeit und die Integrität der Informationen sicherzustellen, müssen entsprechende Maßnahmen zur Absicherung der Übertragung ergriffen werden.
FRIDA nutzt hierbei die Empfehlungen und den Mindeststandard gemäß dem Bundesamt für Informationssicherheit (BSI), wie hier definiert: <br>
* https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/CloudComputing/SecurityRecommendationsCloudComputingProviders.pdf <br>
* https://www.bsi.bund.de/DE/Themen/Oeffentliche-Verwaltung/Mindeststandards/TLS-Protokoll/TLS-Protokoll_node.html

Entsprechend gelten folgende Mindeststandards für die Kommunikation: 
* TLS > 1.2 in Kombination mit Perfect Forward Secrecy (PFS) 
 * Ältere TLS oder SSL Versionen dürfen nicht eingesetzt werden
 * Die Nutzung von HTTP Strict Transport Security (HSTS) wird empfohlen
* Authentifizierung mittels OpenID Connect 1.0 (OIDC) und Autorisierung mittels OAuth 2.0
 * Für Single-Page-Applikationen oder native mobile Applikationen: Authorization Code Grant mit PKCE
 * Webanwendungen mit der Möglichkeit Kennwörter (client secret) sicher speichern zu können: Authorization Code Grant und optional PKCE
 * Der Implicit Grant wird nicht empfohlen
 * Der Password Grant darf nicht eingesetzt werden

### Data at Rest und Data inside Network
Bei Data at Rest müssen Daten nach folgenden Kriterien sicher gespeichert und verarbeitet werden: 
* Verschlüsselung
* Datenschutz 
* Datensicherung
* Löschen und Vernichten

Hierbei können die Richtlinien vom BSI eingsetzt werden: <br>
* https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/IT-Grundschutz-Kompendium/IT-Grundschutz-Bausteine/Bausteine_Download_Edition_node.html

Um eine vollständige End-to-End Verschlüsselung gewährleisten zu können, müssen Maßnahmen zur Sicherung der Daten auch beim Anbieter der Daten (z.B. Versicherung) und des Dienstes sichergestellt werden. Dazu gehört sowohl eine sichere Speicherung der Daten, als auch die Nutzung von Verschlüsselung innerhalb des internen Netzwerks. Die Sicherstellung dieser Richtlinien ist nicht Teil der Spezifikation von FRIDA. 


## Query Contracts
<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Query_contracts.png">  
<p>Vor dem Start einer Berechnung muss der Anwender entscheiden, welche Verträge er der BBS im Kundenportal zugänglich machen möchte.
Dazu kann er auf das Rentencockpit der BBS zugreifen, die dann eine Anfrage mit einem Token an das Kundenportal sendet. 
Ist dieser Vorgang erfolgreich, werden die sichtbaren Verträge an den Kunden zurückgegeben. </p> <br>
<p>Der Kunde hat auch die Möglichkeit, einen ausgewählten Vertrag zu berechnen, den er an die DRI senden kann. Die BBS fragt dann die Stammdaten des 
ausgewählten Vertrages aus dem Kundenportal mit der Methode <code>ContractDetails(contract_id, token)</code> die Anfrage enthält den ausgewählten
Die Anfrage enthält den ausgewählten Vertrag und ein Token, bei Erfolg erhält die DRI die Stammdaten und berechnet daraus die Rentenhöhe, die dann an den Kunden zurückgegeben wird.
an den Kunden zurückgegeben wird.</p>
  



