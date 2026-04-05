# Momentum Strategy Backtest

<img width="1448" height="756" alt="image" src="https://github.com/user-attachments/assets/e5348723-bc92-4420-83f2-f255d9fb0cf9" />

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

The winner portfolio generally outperforms the loser portfolio, and the spread between the two is captured in the winners minus losers portfolio, which shows the clearest signal.

The long short portfolio tends to perform better on a risk adjusted basis than the individual long only portfolios.

From the regressions, the strategy shows positive alpha relative to the market, and some of that remains even after controlling for size and value factors.

## What I looked at

I evaluated performance using:

Annualized return  
Volatility  
Sharpe ratio  
Information ratio  
Turnover and holding period  

I also ran CAPM and Fama French 3 factor regressions to understand where the returns are coming from.

## Interpretation

A few things stood out to me:

The winner portfolio consistently outperformed the loser portfolio, which supports the momentum effect.

The WML portfolio captured this most clearly and showed the strongest overall performance.

Sharpe ratios were generally higher for the WML strategy, which suggests the long short structure improves efficiency.

Even after adjusting for market, size, and value, the strategy still showed some alpha, which is consistent with momentum being a separate factor.

Turnover was moderate, which means the strategy would require regular rebalancing, and the holding period is relatively short.

## Limitations

This uses the current S&P 500 constituents applied to historical data, so there is survivorship bias.

Transaction costs are not included and all portfolios are equal weighted for simplicity.

## Takeaway

This was a straightforward way to test momentum in a structured way.

The results support the idea that recent winners tend to keep outperforming, although in a real setting you would need to adjust for costs and use cleaner data.
