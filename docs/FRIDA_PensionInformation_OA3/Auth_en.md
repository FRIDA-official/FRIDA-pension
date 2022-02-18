<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Auth_en.png"> 
<p> The authentication also is carried out by the incurance company identity provider. The DRI redirects to the relevant login portal. After a successful login the customer
is redirected to the DRI and the token is saved for later use.<br>
It is recommended to pay attention to a simple user experience. For example, registration should be possible if a user account does not yet exist with the insurance provider.  
</p>

## Security
### Data in Transit
When information is transmitted via communications networks, there is a risk of unauthorized interception or unauthorized manipulation of information. To ensure the confidentiality and integrity of the information, appropriate measures must be taken to secure the transmission.
FRIDA uses the recommendations and the minimum standard according to the German Federal Office for Information Security (BSI), as defined here: https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/CloudComputing/SecurityRecommendationsCloudComputingProviders.pdf and https://www.bsi.bund.de/DE/Themen/Oeffentliche-Verwaltung/Mindeststandards/TLS-Protokoll/TLS-Protokoll_node.html

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

Here the guidelines of the BSI can be used: https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/IT-Grundschutz/IT-Grundschutz-Kompendium/IT-Grundschutz-Bausteine/Bausteine_Download_Edition_node.html

In order to be able to guarantee complete end-to-end encryption, measures to secure the data must also be ensured at the provider of the data (e.g. insurance) and the service. This includes both secure storage of the data, as well as the use of encryption within the internal network. Ensuring these guidelines is not part of the FRIDA specification. 
