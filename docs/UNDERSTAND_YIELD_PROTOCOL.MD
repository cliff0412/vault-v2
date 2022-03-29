## overview
To borrow, you deposit collateral in the protocol and draw new fyTokens against the collateral.
You may proceed to sell the fyTokens for the underlying token, locking in your borrowing rate. 
Yield Protocol v2 has a built-in automated market maker(AMM) called YieldSpace to enable efficient selling of fyTokens. 
At maturity, you must repay the debt to reclaim your collateral.
After maturity, there is no requirement to close a borrowing position, however, interest is charged to keep the position open. 

Debt in Yield is tokenized in the form of fyTokens (“fixed yield tokens”).
fyTokens are ERC-20 tokens that are redeemable one-for-one upon reaching a maturity date. Thus fyUSDC0625 tokens are redeemable for USDC after June 25th, 2021. Each fyToken maturity has an associated FyToken ERC-20 smart contract. 


Lending in Yield Protocol is as simple as purchasing fyTokens from our YieldSpace AMMs at a discount.  After maturity, lenders may redeem their fyTokens for the underlying token one-to-one. 



## contracts
### cauldron
At the core of Yield Protocol is the Cauldron, a smart contract that records the collateral and debt for users. Collateral and debt are kept in vaults which may be owned by a particular address. Cauldron permits management of the full lifecycle of a vault, from creating a vault, adding and removing collateral, adding and removing debt, checking collateralization, permitting liquidation of undercollateralized vaults, and rolling collateral and debt to a new series

### join
Join contracts receive assets from users and store it until it is removed from the system. Join does not record any vault state. Join permits users to flash borrow all assets it holds. 

### ladle
User activity in Yield is orchestrated by the Ladle contract.

### witch
If users fail to maintain the appropriate level of collateral, they may be liquidated via Witch, Yield’s liquidation engine. Liquidation is performed via an increasing price auction that increases the amount of collateral the system is willing to pay to cover the debt. 

### wand
Bundling of discrete governance actions into useful governance features.
- add asset
- Make base
- Make ilk
- Add series


### Pool
Yield includes an internal AMM to provide liqudity for fyTokens. The AMM is called YieldSpace. 
YieldSpace is implemented in the Pool contract. YieldSpace pools are designed to trade in interest rates space. That means that the pool will quote trades at the same marginal interest rate over time, absent any trading activity (that would change the interest rate). 


base: DAI
ilk: ETH
series: fyDAI

## references
[yield v2 syllabus](https://docs.google.com/document/d/1WBrJx_5wxK1a4N_9b6IQV70d2TyyyFxpiTfjA6PuZaQ/edit?urp=gmail_link#heading=h.ab6mqo1xaks0)