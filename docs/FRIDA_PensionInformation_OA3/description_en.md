# Overview
<p>The Frida PensionService allows customers to perform a calculation of his pension for a specific contract. For this, the user has to configure his visible contracts which can be
accessed by the DRI platform to perform the calcution using the contract data afterwards. After this configuration the contracts are visible in the pension cockpit. Upon choosing a 
specfic contract from the fetched list a calculation can be performed. All these steps require a token which has to be requested by the user beforehand from the identity providers of 
the insurance companies. </p>

<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/User_en.png">     
<p>This UML diagram describes the relationship between the client and the two platforms. He interacts with the DRI portal to calculate his pension.
The DRI platform then queries the contracts via the customer platform. In addition to that, the customer is able to configure the visible contracts via the customer platform.</p>

## Query Contracts
<img style="width:100%; height: auto;" src="FRIDA_PensionInformation_OA3/resources/Query_contracts.png">  
<p>Before starting any calculation the user has to decide which contracts he wants to make accessible to the DRI on the customer portal.
He can also access the pension cockpit of the DRI which then sends a request with a token to the customer portal. 
If this process succeed the visible contracts get returned to the customer. </p> <br>
<p>The customer also has the option to calculate a selected contract which he can send to the DRI. The DRI then asks for the master data of the 
selected contract from the customer portal with the method ```ContractDetails(contract_id, token)``` the request contains the selected
contract and a token, if this process succeeds the DRI recieves the master data and uses that data to calculate the pension amout, which then
gets returned to the customer.</p>
  





