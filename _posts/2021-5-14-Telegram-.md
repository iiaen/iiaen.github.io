---
layout: post
title: Receiving Automated Messages on Telegram
categories: [Projects, Python, Raspberry Pi]
excerpt: Using Python and Raspberry Pi to receive scheduled Telegram messages on stock portfolio 📈 
---

So I bought a Raspberry Pi on Pi day!! Here's a belated post about my first use for the Pi.  

Using `python` and `cron` to automate the collection and message delivery of the following info to myself on Telegram:
- Daily list of insider purchases (info from SEC Form 4 filings)
- Daily price and volume metrics for a list of tickers
- Candlestick chart for previous day MSFT price and volume data, in 5 minutes intervals  

<p>&nbsp;</p>
There are 5 scheduled Cron tasks, scripts can be found [here](https://github.com/iiaen/telegram_windrunner).  
  
```
0 6 * * * python3 /home/pi/telegram_windrunner/create_portfolio_png.py
5 6 * * * python3 /home/pi/telegram_windrunner/create_openinsider_png.py
10 6 * * * python3 /home/pi/telegram_windrunner/create_candlestick_png.py
15 6 * * * python3 /home/pi/telegram_windrunner/send_image.py
20 6 * * * python3 /home/pi/telegram_windrunner/cleanup.py
```  

<p>&nbsp;</p>
Notable Python packages that were used:  

- yfinance : to get ticker data from Yahoo Finance
- mplfinance : for making Candlestick charts
- pandas : your standard dataframe manipulation stuff
- bokeh : to save dataframes as png images
- telethon : to send and receive messages on Telegram
  
  
![Alt text](https://raw.githubusercontent.com/iiaen/iiaen.github.io/master/images/post_images/WindrunnerMockup65.png "Mockup")    
<p>&nbsp;</p>  
🏮 This is just for fun only! I don't really make any purchases based on these information since DCA (dollar-cost-averaging) suits my needs better. 
  
