#### The crowd sale contracts have two main contract which are 
### 1. Crowdsale.sol
  #### 1.1 CappedCrowdSale.sol - Crowdsale with a limit for total contributions
  #### 1.2 TimedCrowdSale.sol - Crowdsale accepting contributions only within a time frame
### 2. ERC20.sol


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
  
  
### 1.1 CappedCrowdSale.sol
#### contract CappedCrowdsale is Crowdsale:contract CapppedCrowdsale is inheriting all functions from Crowdsale contract.
#### function CappedCrowdsale(uint256 _cap) public
  This function is constructor which set smaximum amount of wei accepted in the crowdsale.
    + uint256 _cap - is the maximum amount of wei to be contributed.
  

#### function capReached() public view returns (bool).
  This function Checks whether the cap has been reached and returns the cap was reached.

#### function _preValidatePurchase(address _beneficiary, uint256 _weiAmount) internal. 
  + address_beneficiary - is token purchaser.
  + uint256 _weiAmount - is the amount of wei contributed.
 
### 1.2 TimedCrowdSale.sol
#### contract TimedCrowdsale is Crowdsale:contract TimedCrowdsale inherits functions from Crowdsale contract.
#### modifier onlyWhileOpen:this modifier is used to set starting and ending time of crowdsale contract.

#### function TimedCrowdsale(uint256 _openingTime, uint256 _closingTime) public
  This constructor sets crowdsale opening and closing times.
  + uint256 _openingTime - is Crowdsale opening time.
  + uint256 _closingTime - is Crowdsale closing time.
  

#### function hasClosed() public view returns (bool) 
  This function checks whether the crowdsale period has elapsed.

#### function _preValidatePurchase(address _beneficiary, uint256 _weiAmount) internal onlyWhileOpen.
  This function validates the purchase using criteria set by onlyWhileOpen modifier.
  + address_beneficiary - is token purchaser.
  + uint256 _weiAmount - is the amount of wei contributed.
  
 ### 2. ERC20.sol
 #### contract ERC20Basic: 
 #### function totalSupply() public view returns (uint256)
  This function is used to check total tokens that are available or created.

#### function balanceOf(address who) public view returns (uint256)
  This function takes address of participants as argument and returns total token balance .
  + address who - is the address of the person whose token balance we need to check.
  
#### function transfer(address _to, uint256 _value) public check(_value)
  This function is used to transfer tokens between accounts while checking the condition set by modifier check.
    + address to - is the account of participant to whose account tokens need to be transfered.
    + uint256 value -  is the number of tokens which needs to be transferred.
    
#### contract ERC20 is ERC20Basic :Here we are inheriting functions of contract ERC20Basic to contract ERC20.
  This function transfer tokens from one address to another.
#### function transferFrom(address _from, address _to, uint256 _value)
  + address _from - is the address of the participant from whose account token is being transferred.
  + address _to is - the account of participant to whose account tokens are transferred.
  + uint256 _value is - the number of tokens which are transferred.
  
#### function approve(address _spender, uint256 _value)
  This function approves the passed address to spend the specified amount of tokens on behalf of msg.sender.
  + address _spender - the address which will spend the funds.
  + uint256 _value - the amount of tokens to be spent.
    
#### function ERC20()
  This function is constructor of ERC20 contract which is used to set total tokens and address of owner or deployer of contract.

#### function allowance(address _owner, address _spender) public view returns (uint256)
  This function checks the amount of tokens that an owner has allowed to a spender and returns the amount of tokens still available for   the spender.
  + address _owner - which owns the funds.
  + address _spender - which will spend the funds.  

#### modifier check(uint256 value)
  This function is used to check the required criteria to allow transaction between accounts.
  + uint256 value - is the number of token to be transferred between CRwallet or the amount of tokens to be redeemed.
  

#### function redeem(uint256 Value)public check(Value)
  This function is used to redeem tokens by purchasing real world assets from owner by checking criteria set by modifier.
  + uin256 Value -  is the number of token which will be used for redeeming.
  

#### function reserveUpdate(uint val)
  This function is used to update reserve by external auditor with the permission of owner.
  + uint val - Reserve value

#### function TTcirculation() constant returns(uint256)
  This function returns the total number of tokens in circulation.


