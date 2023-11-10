# crypto-alarm-service

```
IMPORTANT:
	- allow for anonymous users? only need them to register when they pay for the app or they need email notification




Backend:
	- Java
	- Microservices:
		- API server
		- price Watcher - check current price against active alerts
		- notification sender
	- API Endpoints:
		- createUser
		- createAlert
		- getCoinsList
		- getCurrentPrice
	- Accept webhooks from TradingView alerts

	- Deverá ter restriçoes nos alarmes: maximo que um user pode criar, e deverá ter um prazo


Database Structure:
	- Firebase? (pq é mais facil enviar notifs às apps, sem que estas estejam constantemente a checkar?)
	{
		users: [{
			uid (PK): 		1
			email: 		dsafrew@mail.com
			password: 	123
		}],
		coins: [
			"btc": [
			{
				id (PK): 		1
				coinSymbol: 	btc
				targetPrice: 	100000000
				vsCurrency: 	usd
				alarm:			true
				notification:	false		//notificaçao no telemovel
				email:			true
				expiryDate: 	xxxx-xx-xx
				priceSource:	CoinGecko/Binance/Bybit/...
			},
			{
				id: 2
				...
			}],
			"eth": [{...}, {...}]
		}],
		sourceList: [{
			name (PK): 			CoinGecko
			priceUrl: 		"https://api.coingecko.com/api/v3/simple/price?ids= %coinSymbol% &vs_currencies= %vsCurrency%"
			coinsListUrl: 	"https://api.coingecko.com/api/v3/simple/..."
			coinsList: 		[btc, eth, bnb, ...]
			authToken: 		(...)
		}]
	}




Frontend Mobile:
	- Flutter ?
	- Paginas:
		- Home:
			- Lista de alarmes ativos
			- Botao + para criar novos alarmes
		- NewAlert:
			1 - escolher a source do price data
			2 - app vai buscar à API da source a lista de coins que suporta (incluindo dos derivativos)
			3 - indicar o preço atual
			4 - indicar target price
			5 - indicar Vs_Currency
			6 - escolher o tipo de notificaçoes (check list)
		- Creditos
			- me
			- you
			- donation options (if app does not have ads neither a paid version)

	- Sistema deverá enviar notificaçao e email quando um alarme expira





Monetizar:
	- Free:
		- Anuncios. O UI deverá ser desenhado de forma a que seja fácil distinguir entre anuncios e os alarmes, mesmo que fique "menos bonito"
		- Numero minimo de alertas ativos, por exemplo 10
		- Alarmes expiram em menos tempo, por exemplo maximo de 6 meses
	- Paid:
		- remove anuncios; extende numero max de alertas; permite prazo mais longo
		- Pode custar por exemplo 0.5€ por mes, ou lifetime por 10€
```
