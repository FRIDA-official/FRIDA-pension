# Overview
<p>The Frida PensionService allows customers to perform a calculation of his pension for a specific contract. For this, the user has to configure his visible contracts which can be
accessed by the DRI platform to perform the calcution using the contract data afterwards. After this configuration the contracts are visible in the pension cockpit. Upon choosing a 
specfic contract from the fetched list a calculation can be performed. All these steps require a token which has to be requested by the user beforehand from the identity providers of 
the insurance companies. </p>

<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/User_en.png">     
<p>This UML diagram describes the relationship between the client and the two platforms. He interacts with the DRI portal to calculate his pension.
The DRI platform then queries the contracts via the customer platform. In addition to that, the customer is able to configure the visible contracts via the customer platform.</p>

## Security
### Data in Transit
When information is transmitted via communications networks, there is a risk of unauthorized interception or unauthorized manipulation of information. To ensure the confidentiality and integrity of the information, appropriate measures must be taken to secure the transmission.
FRIDA uses the recommendations and the minimum standard according to the German Federal Office for Information Security (BSI), as defined here: <br>
* https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/CloudComputing/SecurityRecommendationsCloudComputingProviders.pdf <br>
* https://www.bsi.bund.de/DE/Themen/Oeffentliche-Verwaltung/Mindeststandards/TLS-Protokoll/TLS-Protokoll_node.html

Accordingly, the following minimum standards apply to communication: 
* TLS > 1.2 in combination with Perfect Forward Secrecy (PFS). 
 * Older TLS or SSL versions must not be used
 * Use of HTTP Strict Transport Security (HSTS) is recommended
* Authentication using OpenID Connect 1.0 (OIDC) and authorization using OAuth 2.0
 * For single page applications or native mobile applications: Authorization Code Grant with PKCE
 * Web applications with the ability to securely store passwords (client secret): Authorization Code Grant and optional PKCE
 * The Implicit Grant is not recommended
 * The Password Grant must not be used

### Data at Rest
At Data at Rest, data must be securely stored and processed according to the following criteria: 
* Encryption
* Data protection 
* Data backup
* Deletion and destruction

Here the guidelines of the BSI can be used: <br>
* https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/IT-Grundschutz-Kompendium/IT-Grundschutz-Bausteine/Bausteine_Download_Edition_node.html

In order to be able to guarantee complete end-to-end encryption, measures to secure the data must also be ensured at the provider of the data (e.g. insurance) and the service. This includes both secure storage of the data, as well as the use of encryption within the internal network. Ensuring these guidelines is not part of the FRIDA specification. 
## Query Contracts
<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Query_contracts.png">  
<p>Before starting any calculation the user has to decide which contracts he wants to make accessible to the DRI on the customer portal.
He can also access the pension cockpit of the DRI which then sends a request with a token to the customer portal. 
If this process succeed the visible contracts get returned to the customer. </p> <br>
<p>The customer also has the option to calculate a selected contract which he can send to the DRI. The DRI then asks for the master data of the 
selected contract from the customer portal with the method <code>ContractDetails(contract_id, token)</code> the request contains the selected
contract and a token, if this process succeeds the DRI recieves the master data and uses that data to calculate the pension amout, which then
gets returned to the customer.</p>
  





