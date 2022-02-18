### Data in Transit
Bei der Übertragung von Informationen über Kommunikationsnetze besteht die Gefahr, dass Informationen unbefugt abgehört oder unbefugt manipuliert werden. Um die Vertraulichkeit und die Integrität der Informationen sicherzustellen, müssen entsprechende Maßnahmen zur Absicherung der Übertragung ergriffen werden.
FRIDA nutzt hierbei die Empfehlungen und den Mindeststandard gemäß dem Bundesamt für Informationssicherheit (BSI), wie hier definiert: https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/CloudComputing/SecurityRecommendationsCloudComputingProviders.pdf und https://www.bsi.bund.de/DE/Themen/Oeffentliche-Verwaltung/Mindeststandards/TLS-Protokoll/TLS-Protokoll_node.html

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

Hierbei können die Richtlinien vom BSI eingsetzt werden: https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/IT-Grundschutz-Kompendium/IT-Grundschutz-Bausteine/Bausteine_Download_Edition_node.html

Um eine vollständige End-to-End Verschlüsselung gewährleisten zu können, müssen Maßnahmen zur Sicherung der Daten auch beim Anbieter der Daten (z.B. Versicherung) und des Dienstes sichergestellt werden. Dazu gehört sowohl eine sichere Speicherung der Daten, als auch die Nutzung von Verschlüsselung innerhalb des internen Netzwerks. Die Sicherstellung dieser Richtlinien ist nicht Teil der Spezifikation von FRIDA. 

<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Auth_en.png"> 
<p>Die Authentifizierung erfolgt ebenfalls über den Identity Provider des Versicherers. Das DRI leitet auf das entsprechende Login-Portal weiter. Nach einem erfolgreichen Login wird der Kunde wird der Kunde zum DRI weitergeleitet und das Token wird für die spätere Verwendung gespeichert.<br>
Es wird empfohlen eine einfache Nutzererfahrung zu achten. So sollte beispielsweise eine Registrierung möglich sein, sofern noch kein Benutzerkonto beim Versicherungsanbieter vorhanden ist. 
</p>