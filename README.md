#### The crowd sale contracts have two main contract which are 
1. Crowdsale.sol
  + CappedCrowdSale.sol
  + TimedCrowdSale.sol
2. ERC20.sol


### 1. Crowdsale.sol
#### function crowdsale(uint256 _rate,address _wallet,ERC20_token)
  At first we need to transfer tokens to asset based crowdsale contracts deployed address.From there participants will buy tokens. 
  Function crowdsale is the constructor of crowdsale contract which is used to set initial parameters like value of each token,address     of owners wallet.
  + uint256 _rate - is the wei value of each token.
  + address _wallet - is the address at which all funds will be stored .
  + ERC20 _token - is the address at which token contract is deployed.
  

#### function buyTokens(address_beneficiary) public payable
  Function buyToken is used by participants to buy tokens.It is also used to update total wei amount raised .
  + address _beneficiary - is the address of participants who are participating in asset based crowdsale contact.
  

#### function _deliverTokens(address_beneficiary,uint256_tokenAmount)
  Function _deliveryTokens is used to emmit tokens from owners account to participants account.
  + address _beneficiary - is the address of participants.
  + uint256 _tokenAmount - is the total wei paid by participant to buy tokens.
 

#### function _processPurchase(address _beneficiary,uint256 _tokenAmount)
  This function is executed when a purchase has been validated and is ready to be executed. Not necessarily emits/sends tokens.
  + address _beneficiary - is the address of participants.
  + uint256 _tokenAmount - is the total wei paid by participant to buy tokens.

#### function _preValidatePurchase(address _beneficiary, uint256 _weiAmount) internal
  This function does validation of an incoming purchase. Uses require statements to revert state when conditions are not met
  + address _beneficiary - is the address of participants.
  + uint256 _tokenAmount - is the total wei paid by participant to buy tokens.

#### function _getTokenAmount(uint256 _weiAmount)
  This function is used find number of tokens that can be purchased with the specified _weiAmount.
  + uint256 _weiAmount - is value in wei to be converted into tokens.
  

#### function _forwardFunds()
  This function is used to determines how ETH is stored/forwarded on purchases.


