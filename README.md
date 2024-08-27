https://github.com/chen4903/Liquidation-Comparisons

# Brief
We use Foundry to conduct practical demonstrations of liquidate various lending protocols, with the goal of achieving higher profits and explaining the liquidation strategies as clearly as possible.

# Effect factors
How to maximize profits? The influencing factors 
generally include the following:

* healthFactor: It's not true that the closer it gets to 1, the greater the profit is.

* gas: If the profit you earn after liquidation can not cover gas, you would lose money.

* The amount of Liquidation: The max ratio of liquidation that can be made for each protocol varies. E.g. AAVEV2 is 50%. How much should we liquidation is an issue?

* Liquidation reward: Do you want underlying token or aToken?

* Slippage:
    * To swap the token that we get after liquidation to the token we want.
    * The best path to swap, making the slippage the lowest.
    
* User's debt specifications:
    * Price: The price of the token that user borrows and collaterals.
    * Amount: The amount you can get after liquidation and the depth of the pool will influence the output of swap directly.

* Flashloan(If you liquidate by flashloan):
    * Flashloan fee.
    * The pool's depth limits the number you can flashloan.

# Math
Assuming that all swaps are priced in WETH, all swaps will ultimately be converted to WETH

We define:

*  The amount of flashloan.
*  The fee of flashloan.
*  gas.
*  The amount of WETH after liquidation and swap we can get.
*  The profit we earn ultimately.

We can infer: $$ P = d - b -c \qquad [f(a) = d] $$ a will indirectly affect d, and a represents your liquidation ability under the flashloan. Your liquidation strategy directly affect profits, and are influenced by a mixture of the seven effect factors mentioned above, so the logic behind this will not be simple and clear. 