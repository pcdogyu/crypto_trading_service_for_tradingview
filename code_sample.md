**代码模板**  
  
修改策略/指标为方便与本软件对接的代码，需要添加和修改以下代码


```
condition1 = false
condition2 = false
condition3 = false

//开多代码信号
plotshape(condition1, text='▲', style=shape.labeldown, textcolor=color.white, color = color.green,   location = location.abovebar, title = "开多")
alertcondition(condition1 , title="CrossOver Double EMA Buy", message="CrossOver Double EMA Buy")
//开空代码信号模板  
plotshape(condition2, text='▼', style=shape.labeldown, textcolor=color.white, color = color.red,   location = location.abovebar, title = "开空")
alertcondition(condition2  , title="CrossUnder Double EMA Sell", message="CrossUnder Double EMA Sell")
//平仓代码模板   
plotshape(condition3, text='Cancel', style=shape.labeldown, textcolor=color.white, color = color.red,   location = location.abovebar, title = "开空")
alertcondition(condition3  , title="CrossUnder Double EMA Sell", message="CrossUnder Double EMA Sell")
```  

以上的 `condition1 = false`  `condition2 = false`  `condition3 = false` 就是需要操作判断的代码。也是我们需要修改的片段，根据视频教程修改即可。  
  

**TradingView通知参数模板**  

```
{
	"symbol": "SHIB-USDT-SWAP",
	"price": {close},
	"amount": "1000000",
	"side": "sell",
	"ordType": "limit",
	"apiSec": "5BFJYtNg7hwkgCzYQMwwQNctqan9CmqOzmtldJc"
}
```  
symbol是交易对，可以从OKEX的官网地址栏或者，详见视频说明。  
price是挂单的价格，一般用{close}就是收盘价  
amount就是挂单的数量，统一用币的单位计算，比如0.1个比特币就填0.1，1000000个shib就用1000000  
side就是挂单方向。sell -> 开空（如果有仓位会先平掉），buy -> 开多（如果有仓位会先平掉），close -> 取消挂单并平仓  
ordType挂单类型，可以是limit限价单，或者是market市价单，使用市价market的话price会失效  
apiSec是我们再软件服务配置页面中设置的通信密钥参数。  