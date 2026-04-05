# Moment Trading Strategy Project 
# Momentum Strategy Backtest

This project builds a simple momentum strategy using S&P 500 stocks.

The idea I wanted to test is whether stocks that have performed well over the past year continue to outperform those that haven’t.

I pulled monthly price data, built a momentum signal, formed portfolios, and then evaluated how those portfolios performed over time.

## Approach

I used the current S&P 500 constituents as the universe and pulled monthly data from Yahoo Finance.

The signal is based on a standard 12-1 momentum definition. I look back 12 months, skip the most recent month, and calculate cumulative returns over the remaining period.

Each month, stocks are ranked into deciles based on that signal. From there I form three portfolios:

Winner portfolio holding the top decile  
Loser portfolio holding the bottom decile  
Winners minus losers portfolio going long winners and short losers  

All portfolios are equal weighted.

Returns are calculated using next month’s performance after forming the portfolios to avoid look ahead bias.

## Results

The results line up with what you would expect from a momentum strategy.

The winner portfolio generally outperforms the loser portfolio. The spread between the two is captured in the winners minus losers portfolio, which shows the clearest signal.

On a risk adjusted basis, the long short portfolio performs better than the individual long only portfolios.

From the regressions, the strategy shows positive alpha relative to the market, and some of that remains even after controlling for size and value factors.

## What I looked at

I evaluated performance using:

Annualized return  
Volatility  
Sharpe ratio  
Information ratio  
Turnover and holding period  

I also ran CAPM and Fama French 3 factor regressions to understand where the returns are coming from.

## Limitations

This uses the current S&P 500 constituents applied to historical data, so there is survivorship bias.

I also did not include transaction costs and used equal weighting for simplicity.

## Takeaway

This was a straightforward way to test momentum in a structured way. The results support the idea that recent winners tend to keep outperforming, although in a real setting you would need to adjust for costs and use cleaner data.



Results & Interpretation

Results & Interpretation

A few things stood out from the results:

- The **winner portfolio consistently outperformed the loser portfolio**, which is what we would expect from a momentum-based strategy.
- The **WML (winners minus losers) portfolio showed the clearest signal**, capturing the spread between strong and weak performers.
- In most periods, the WML strategy delivered **higher returns than the market**, although it also came with higher volatility.

From a risk-adjusted perspective:

- The **Sharpe ratio for the WML portfolio was generally stronger than the individual winner and loser portfolios**, suggesting the long-short structure improves efficiency.
- The **information ratio vs the market was positive**, indicating that the strategy adds value beyond just market exposure.

Looking at the regressions:

- The **CAPM results showed positive alpha**, meaning the strategy is not fully explained by market movements alone.
- Even after controlling for size and value in the **Fama-French 3-factor model**, a portion of the alpha remained, which supports the idea that momentum is a distinct factor.

From a practical standpoint:

- The strategy has **moderate turnover**, which suggests it would require regular rebalancing.
- The implied **holding period is relatively short**, which is typical for momentum strategies.

Overall, the results support the idea that **momentum is a persistent effect**, although in a real-world setting you would need to account for transaction costs and more realistic data assumptions.


