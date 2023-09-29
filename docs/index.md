# Welcome to Rocket Bot

This series of documents will explain what Rocket bot is, which markets it will trade, and how you can set it up on your own account.


## What is Rocket Bot
Rocket bot is an algorithmic trading Robot, that uses technical analysis to decide when to buy to sell an underlying financial instrument or asset.
In essence, it tries to predict where the market will go next, and accordingly take a position to either buy or sell that asset.

## What are Futures
Before the bot starts trading, it needs to know which financial instrument to trade. Here is a non exhaustive list of such assets:

1. Futures
2. Commodities
3. Forex
4. Stocks
5. ETF's
6. Crypto
7. CFD
8. Options
9. Warrants
10. Bonds

Each asset is traded on different marketplaces, have different fees associated to them based on the broker used, and have different volatility and return profile.
For example, Futures are often centralized, have high liquidity and volatility, have built in high leverage, and are preferred by short term traders.
Stocks are not necessarily centralized, have a liquidity that varies between stocks, can be volatile (penny stocks) or not (blue chips), can be highly leveraged, some do give out dividends, and are preferred by long term investors.

Futures have 2 major use cases:

+ Real world hedging
+ Speculation

### Hedging
Let's say you are a farmer who owns a Coffee plantation, or a German company that sells car in the US. In both cases, months can pass by between the time you product your good, and the time you sell it.
Because the price of Coffee fluctuates, and because you sell your cars in USD while it costs you EUR to produce, you would very much love to have a way to hedge yourself. That is to say, to protect yourself from a sudden drop in price of Coffee, or appreciation of the EUR (which would lead you to earn less).

To do so, you can sell a futures contract on the day of production. This would effectively *lock* your price.
On the other side of that trade is an actual real world trade who wants to purchase that good from you in 3 months for example, and would like the same kind of protection.

Thus, a futures contract is a promise to deliver a good at a predefined time in the future. That is why futures contracts have expiry dates which tend to be every 3 months.
(Crypto futures are called perpetuals because they never expire. They also are swaps instead of typical futures.)

### Speculation
Given the nature of Futures contracts, they tend to attract speculators, or scalpers. These types of trades do not want to have the product delivered, instead prefer to be on the direction of the asset.
Rocket Bot can be classified as such a speculator

## Why Trade Futures
Futures have many properties that make them attractive to short term trades, be it day traders or scalpers.

+ They are very liquid
+ They have low margin requirements
+ They have built in leverage
+ They tend to be volatile especially on market open
+ Back in the days, being a `ES-mini` scalper who could take a point of two from the market, used to be a sign of professionalisme

## What's the CME
Futures are almost always traded on centralized exchanges. The only exception is crypto DeFi futures.
The reason is that a Future contract is a derivative on top of the actual underying.
For example, the $NQ is the future that tracks the NASDAQ100.
The CME, or Chicago Mercantile Exchange, is one of the few US based futures exchanges. Some of the popular contracts traded on it are the $ES (S&P500 future), $6E (EURUSD future) and the $NQ (NASDAQ100 future)
There are other exchanges such as COMEX. 

## How to access futures markets
Given the centralized nature of futures markets, a retail trader such as yourself, needs to have access via a third party called brokers. There are usually multiple parties involved in every transaction, but essentially, the broker you take abstracts it away from you.
The only difference for you as a trader, is that these other parties charge fees per transaction. These fees are fixed regardless of the broker. However broker fees vary from one platform to another.

In order to choose broker, multiple factors are taken into account:

+ What are the fees? Do they have volume discounts?
+ Which platforms are supported?
+ How safe are they?



## Is trading Futures safe?
Trading always involves risks, however trading on a centralized exchange reduces risks that are more common in non centralized ones such as spot forex or crypto.
Wash trading, book manipulation, and other malign operations are not very possible without damaging the exchange's reputation.
Exchanges also have circuit breakers in place that automatically halt any trading when an asset reaches a certain negative drawdown. This helps prevent flash crashes, some of which have occured in the past.

The trader's money is usually held by a third party custodian. This party is responsible for updating your balance.
This servers as a safety net.
In comparision to crypto for example, while binance is both the broker, the marketplace and the custodian, this is not the case in trading CME futures where the broker can be NinjaTrader, the custody of the money is with Dorman, and the exchange is the CME.
This is why fees get added up, however it adds security.

Ironically, on standard contracts, the fees remain low enough that even crypto futures are not that competitive!

The other kind of risks one need to be careful of are related to the strategy itself, as well as its execution:

+ The strategy used by Rocket Bot might fail to survive strong downturns such as the 2008 crash. But, this is only the case when the strategy's backtest is not robust enough
+ The bot itself could fail for many reasons. For example, server failure, lost connection with broker, etc...
These are technical risks related to our product, and we go over them in another part of the FAQ 

## Understanding the different Future contracts
Usually, every contract has 2 variants: The mini, and the micro.

+ The mini is the big contract
+ The micro is a fraction of the mini, usuall 1/10th

They have everything else in common. Essentially:

+ Tick size: The minimum $ amount the instrument must move. It is $0.25 on the $NQ and $1 on the $YM
+ Tick Value: The value of a single tick. For the $NQ, for every 0.25 point movement of the underlying, your PnL moves by $5. So, for every $NQ point move, the PnL moved by $20.
  Note that, for the $MNQ, every point is worth $2 instead of $20

## How much money do I need to get started?
Trading CME futures can require as low as 200$ to get started.
However, a single point of the $MNQ is worth 2$.
Given that the MNQ can move 300 points on a single day, that would be a +- PnL of 600$
In other words, a capital of 200$ implies a very high risk.
Also, this margin requirement only applies to day trades. If the trader wishes to hold the trade overnight, then the maintenance margin is applied.
This margin is 1,680$ on the MNQ and as high as 16,800$ on the NQ (As of this writing)
A full list of margins can be found [here](https://www.ampfutures.com/trading-info/margins)

Accordingly the safest initial capital is around $5,000 -- $10,000 if possible.

It is important to note that when the account has over $100,000 it becomes safer to trade Mini contracts instead of Micro contracts.
This safest is a measure of the expected Drawdown, in relation to the expected return. Let us illustrate with an example.

+ It is not possible to trade fractions of a contract. So, one can either buy 1, 2, or more contracts of $NQ.
+ For each contract, the point is worth $20
+ If we make a 100 point profit, the PnL would be +$2,000

Now, on a $5,000 account, this is a wopping 40% return.
However, it's enough for the $NQ to drop 250 points for the account to wipe out!.
On a $100,000 account, this is 2%. Still a good number, but now, if the $NQ drops 250 points, we would be losing 5% instead of blowing the account.

Rocket Bot works in threshold steps adjusted by the risk of the strategy.
We aim to have a certain Drawdown objective per strategy, and accordingly manage the contract sizing based on available capital.
