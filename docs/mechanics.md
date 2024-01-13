# Deposit & Withdrawal Mechanics

The section below illustrates how deposits and withdrawals work.

When a user allocates capital to a vault, they are issued vault shares, that hold a % claim to the assets in the vault. Upon redemption, these shares hold a claim to a proportion of each asset in the vault. Users can withdraw their assets any time.

## Deposit

> 📌 Current beta version of the vault uses a *Direct NAV Approach* to calculate the amount of newly issued shares. While this approach provides more simplicity and clarity, future versions of the vaults will use a *Proportional Contribution Approach* which offers a fairer distribution of shares.

When a user allocates funds to a vault, they are issued vault shares corresponding to the increase in Net Asset Value (NAV) that they contribute to the vault. The following sequence of actions takes place:

1. User initiates a deposit in FUSD.

2. The vault calculates the NAV:
$$
NAV = \sum _ { i = 1} ^ { m } asset_i * price_i
$$

3. Your vault share % is calculated:
$$
DepositRatio = \frac{Deposit}{NAV}
$$

4. New vault shares are issued to the depositor:
$$
NewlyIssued = DepositRatio * TotalShares
$$

### Future advancements

* Allow the user to deposit into a vault with a wider range of assets besides FUSD.
* Implement *Proportional Contribution Approach* for fairer distibution of shares.

<!-- Proportional Contribution Approach -->

<!-- 1. User initiates a deposit. This is expressed in FUSD.

2. The vault calculates the NAV:
$$
NAV = \sum _ { i = 1} ^ { m } asset_i * price_i
$$

3. Your vault share % is calculated:
$$
Share = \frac{Deposit}{(Deposit+NAV)}
$$

4. New vault shares are issued to the depositor s.t.:

$$
Share = \frac{NewlyIssued}{(NewlyIssued + TotalShares)}
$$

so that the amount of newly issued shares:

$$
NewlyIssued = Share * \frac{TotalShares}{(1-Share)}
$$ -->

## Withdrawal

When a user wishes to withdraw their funds from a vault, the following sequence of calculations takes place:

1. Withdrawal % is calculated:
$$WithdrawalRatio = \frac{MyShares}{TotalShares}$$

2. The WithdrawalRatio is applied to each asset position in the vault, and the user is sent a proportion of each position in the vault.

3. When the withdrawal is processed, shares are burnt.

### Future advancements

* Allow the user to decide in which asset he wants to withdraw his share of the vault. The vault will perform the swap before sending the assets to the user.