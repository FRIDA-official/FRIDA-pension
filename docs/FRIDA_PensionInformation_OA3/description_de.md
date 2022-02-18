# Übersicht
<p>Der Frida PensionService ermöglicht es dem Kunden, eine Berechnung seiner Rente für einen bestimmten Vertrag durchzuführen. Dazu muss der Benutzer seine sichtbaren Verträge konfigurieren, auf die
auf die die DRI-Plattform zugreift, um anschließend die Berechnung anhand der Vertragsdaten durchzuführen. Nach dieser Konfiguration sind die Verträge im Rentencockpit sichtbar. Nach Auswahl eines 
bestimmten Vertrag aus der abgerufenen Liste kann eine Berechnung durchgeführt werden. Für all diese Schritte wird ein Token benötigt, das der Benutzer zuvor bei den Identitätsprovidern der Versicherungsgesellschaften anfordern muss. 
</p>

<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/User_en.png">     
<p>Dieses UML-Diagramm beschreibt die Beziehung zwischen dem Kunden und den beiden Plattformen. Er interagiert mit dem DRI-Portal, um seine Rente zu berechnen.
Die DRI-Plattform fragt dann die Verträge über die Kundenplattform ab. Darüber hinaus kann der Kunde über die Kundenplattform die sichtbaren Verträge konfigurieren.</p>

## Query Contracts
<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Query_contracts.png">  
<p>Vor dem Start einer Berechnung muss der Anwender entscheiden, welche Verträge er der BBS im Kundenportal zugänglich machen möchte.
Dazu kann er auf das Rentencockpit der BBS zugreifen, die dann eine Anfrage mit einem Token an das Kundenportal sendet. 
Ist dieser Vorgang erfolgreich, werden die sichtbaren Verträge an den Kunden zurückgegeben. </p> <br>
<p>Der Kunde hat auch die Möglichkeit, einen ausgewählten Vertrag zu berechnen, den er an die DRI senden kann. Die BBS fragt dann die Stammdaten des 
ausgewählten Vertrages aus dem Kundenportal mit der Methode ```ContractDetails(contract_id, token)``` die Anfrage enthält den ausgewählten
Die Anfrage enthält den ausgewählten Vertrag und ein Token, bei Erfolg erhält die DRI die Stammdaten und berechnet daraus die Rentenhöhe, die dann an den Kunden zurückgegeben wird.
an den Kunden zurückgegeben wird.</p>
  





