# go-xrate

go-xrate is a small lib for getting cryptocurrency rates from several Exchanges around the world.

## Install

To install, just run 

`go get github.com/SwipeCoin/go-xrate`

It doesn't rely on any external lib :D
  
## Supported Exchanges

As of now, only exchanges from Brazil are supported. But the code is prepared to work with multiple countries, fiat currencies and cryptocurrencies. 

Here's the supported list (We are constantly adding more and more):
- [FoxBit](https://foxbit.exchange)
- [Mercado Bitcoin](https://wwww.mercadobitcoin.com.br) 
- [BitcoinTrade](https://bitcointrade.com.br)

## Supported Cryptocurrencies

- BTC: Bitcoin
- LTC: Litecoin
- BCH: Bitcoin Cash

## Usage
It's really simple to get started.

##### First, you import the package:
```go
// Here we are importing from the brazilian package of exchanges
import (
    xrbr "go-xrate/exchanges/br"
)
```

##### Then, instantiate a new ExchangeCrawler and call the specific method for the cryptocurrency you want:
```go
// FoxBit - BTC
xrbr.NewFoxBitCrawler().BTC()
  
// OR 
// Mercado Bitcoin - BCH
xrbr.NewMercadoBitcoinCrawler().BCH()
 
// OR 
// BitcoinTrade - BTC
xrbr.NewBitcoinTradeCrawler().BTC()
```

## API
#### NewFoxBitCrawler() FoxBitCrawler
Creates and returns a new FoxBitCrawler

###### Methods:
- BTC() CryptoCurrencyTicker

#### NewMercadoBitcoinCrawler() MercadoBitcoinCrawler
Creates and returns a new MercadoBitcoinCrawler

###### Methods:
- BTC() CryptoCurrencyTicker
- LTC() CryptoCurrencyTicker
- BCH() CryptoCurrencyTicker

#### NewBitcoinTradeCrawler() BitcoinTradeCrawler
Creates and returns a new BitcoinTradeCrawler

###### Methods:
- BTC() CryptoCurrencyTicker

#### Methods response
All methods return a CryptoCurrencyTicker, with fields:
- **Acronym**: Cryptocurrency acronym. (BTC, BCH or LTC)
- **FiatCurrencyAcronym**: Fiat currency acronym. (BRL, USD)
- **Last**: Value of the last price
- **High24h**: Price of the highest order in the last 24 hours
- **Low24h**: Price of the lowest order in the last 24 hours
- **Volume24h**: Trading volume in the last 24 hours
- **VolumeFiat24h**: Fiat trading volume in the last 24 hours (Not supported by all)
- **RecentBuyOrder**: Price of the most recent buy order
- **RecentSellOrder**: Price of the most recent sell order

In the case of a exchange not supporting a specific field, we fill it with a 'falsy' value. (E.g. float32 -> 0.0)

## TODO
- [ ] More Exchanges (From both Brazil and other countries)
- [ ] Tests
- [ ] Other useful statistics from a specific cryptocurrency and/or exchange

## Support
Please feel free to contribute with both suggestions and new code :D