# Deposit & Withdrawal Mechanics

The section below illustrates how deposits and withdrawals work in a single network world. We later show how these concepts are applied to the Valio omnichain architecture.

When a user allocates capital to a vault, they are issued vault shares, that hold a % claim to the assets in the vault. Upon redemption, these shares hold a claim to a proportion of each asset in the vault. Users can withdraw their assets any time.

    !!! info inline end "Capital Allocation"

        When a user allocates capital to a vault, they are issued vault shares, that hold a % claim to the assets in the vault. Upon redemption, these shares hold a claim to a proportion of each asset in the vault. Users can withdraw their assets any time.

## Deposit

When a user allocates funds to a vault, they are issued vault shares corresponding to the increase in Net Asset Value that they contribute to the vault. The following sequence of actions takes place:

1. User initiates a deposit. This is expressed in USDC
2. The vault calculates the Net Asset Value: $NAV = SUM(asset_i * price_i)$
3. Your vault share % is calculated: $Share = Deposit/(Deposit+NAV)$
4. New vault shares are issued to the depositor s.t.:

$$Share = NewlyIssued / (NewlyIssued + Outstanding)$$

so that the amount of newly issued shares:

$$NewlyIssued = Share * Outstanding/(1-Share)$$

## Withdrawal

When a user wishes to withdraw their funds from a vault, the following sequence of calculations takes place:

1. Withdrawal % is calculated: WithdrawalPercent = MyShares/Outstanding
2. The WithdrawalPercent is applied to each asset position in the vault, and the user is sent a proportion of each position in the vault
3. WIth a future update: The user is able to select between receiving the various vault assets or converting them into USDC. If the user selects USDC, their claimed assets are routed through the market and liquidated
4. When the withdrawal is processed, shares are burnt