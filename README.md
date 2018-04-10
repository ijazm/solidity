#### The crowd sale contracts have two main contract which are 
1. Crowdsale.sol
  + CappedCrowdSale.sol
  + TimedCrowdSale.sol
2. ERC20.sol


#### 1. Crowdsale.sol
##### function crowdsale(uint256 _rate,address _wallet,ERC20_token)
   a>uint256 _rate is the wei value of each token.
   b>address _wallet is the address at which all funds will be stored .
   c>ERC20 _token is the address at which token contract is deployed.
  At first we need to transfer tokens to asset based crowdsale contracts deployed address.From there participants will buy tokens. 
  Function crowdsale is the constructor of crowdsale contract which is used to set initial parameters like value of each token,address of owners wallet.

##### function buyTokens(address_beneficiary) public payable
   a>address _beneficiary is the address of participants who are participating in asset based crowdsale contact.
  Function buyToken is used by participants to buy tokens.It is also used to update total wei amount raised .

##### function _deliverTokens(address_beneficiary,uint256_tokenAmount)
   a>address _beneficiary is the address of participants.
   b>uint256 _tokenAmount is the total wei paid by participant to buy tokens.
  Function _deliveryTokens is used to emmit tokens from owners account to participants account.

##### function _processPurchase(address _beneficiary,uint256 _tokenAmount)
  This function is executed when a purchase has been validated and is ready to be executed. Not necessarily emits/sends tokens.

##### function _preValidatePurchase(address _beneficiary, uint256 _weiAmount) internal
  This function does validation of an incoming purchase. Uses require statements to revert state when conditions are not met

##### function _getTokenAmount(uint256 _weiAmount)
  a>uint256 _weiAmount is value in wei to be converted into tokens.
  This function is used find number of tokens that can be purchased with the specified _weiAmount.

##### function _forwardFunds()
  This function is used to determines how ETH is stored/forwarded on purchases.


