# optimal_one_sided_supply
 
Solidity code implements a contract called `OptimalOneSidedSupply` that demonstrates an optimal one-sided supply strategy for liquidity provision in a Uniswap V2 pair. Here's an explanation of the code:

- The contract starts with the SPDX-License-Identifier to specify the license under which the code is released.

- The contract defines several private constant addresses:
  - `FACTORY`: Represents the address of the Uniswap V2 Factory contract.
  - `ROUTER`: Represents the address of the Uniswap V2 Router contract.
  - `WETH`: Represents the address of the Wrapped Ether (WETH) token.

- The `sqrt` function is a helper function that calculates the square root of a given number using the Babylonian method. It is used later in the code.

- The `getSwapAmount` function calculates the optimal swap amount from token A to token B based on the reserve amounts of the pair and the current user's token A balance. It uses a formula to determine the optimal swap amount that maximizes liquidity provision. The formula includes the swap fee percent and a mathematical expression to find the optimal amount.

- The `zap` function implements the optimal one-sided supply strategy. It takes the addresses of two tokens (`_tokenA` and `_tokenB`) and the amount of token A to be supplied (`_amountA`). The function requires either `_tokenA` or `_tokenB` to be WETH. The function transfers the specified amount of token A from the user to the contract. It retrieves the pair address using the Factory contract and obtains the reserve amounts of the pair. Depending on the token order in the pair, it calculates the optimal swap amount using the `getSwapAmount` function. Then, it performs the swap from token A to token B using the Router contract's `swapExactTokensForTokens` function. Finally, it adds liquidity to the pair using the Router contract's `addLiquidity` function.

- The contract includes two internal helper functions: `_swap` and `_addLiquidity`. These functions handle the swapping of tokens and adding liquidity, respectively. They use the appropriate Router contract functions and approve the necessary token transfers.

- The contract includes several interface declarations for the Uniswap V2 Router, Factory, and Pair contracts. These interfaces define the required functions and their signatures to interact with the respective contracts.

This contract serves as a demonstration of an optimal one-sided supply strategy for Uniswap V2 liquidity provision. By following this strategy, users can maximize their liquidity provision while minimizing the impact of swap fees.