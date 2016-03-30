# ActionScript Virtual Goods

## *Introduction*

Once you have created [Virtual Goods](..\Creating A Virtual Good.html) on the Portal, you can now incorporate them in your game. This tutorial will show you how to buy and consume goods using a shop interface.

*Creating a 'Grant Currency' Event*

  * To help test the Virtual Goods, create an Event on the portal which takes an attribute of type NUMBER.
  * Using Cloud code, accredit the player an amount of currency passed in through the NUMBER attribute.

*Creating the Buy and Consume functions*

  * Create a function to log the BuyVirtualGoods request and one for the ConsumeVirtualGoods request.
  * Create a function to handle the BuyVirtualGoods request.
  * Create a function to handle the ConsumeVirtualGoods request which logs an Event to accredit the authenticated player with extra currency.

*Keeping track of player details*

  * Create a function that updates the player's currency and amount of Virtual Goods owned by using the AccountDetails request.

*Testing Virtual Goods*

  * Launch your game, buy and consume Virtual Goods to see your details being updated accordingly.
[wpdm_file id=38 title="true" ]

## *Creating the 'Grant Currency' Event*

Create an Event that credits the authenticated player with extra *currency*. Add an *attribute* that will be used to indicate the amount to credit. You will log this Event whenever the authenticated player *consumes* a Gold Coin (Virtual Good).


![l](img\AS\1.png)

In the Event *Cloud Code* create a variable that holds the amount being passed in the Event through the 'CASH' attribute, and name it 'money'. Next get the Player object using *Spark.getPlayer()* and credit their *currency1* with the 'money' value.

![l](img\AS\2.png)
 

## *Creating the Buy and Consume functions*

Create a function which will log a *buy Request* when called by using *BuyVirtualGoods* request. The *BuyVirtualGoods* request needs a *currency* type, a *quantity* and the *Short code* for the item to be purchased.


```
    			private function PurchaseItem():void
    			{
    				logger("Buying Virtual Good...");
    				requestBuilder.createBuyVirtualGoodsRequest().setCurrencyType(1).setQuantity(Number(BuyQnt.text)).setShortCode("Gold_Coin").send(BuyResponse);
    			}
```

Create a function for the consumption of *Virtual Goods*, this will use the *ConsumeVirtualGoodRequest.* The *ConsumeVirtualGoodRequest* needs a *quantity* and *Short code* of the item to be consumed.

```
    	private function ConsumeItem():void
    			{
    				logger("Consuming Virtual Good...");
    				requestBuilder.createConsumeVirtualGoodRequest().setQuantity(Number(ConsumeQnt.text)).setShortCode("Gold_Coin").send(ConsumeResponse);
    			}
```

Now you can make the *response* *handler* functions for your *consume* and *buy* requests. Both *response handlers* will be similar. For our tutorial we won't need them to do much. Have the functions check the response for errors. If the response has no errors then send a *string* to the *logger*. For the *consume* *response*, if there are no errors*,* call the Event which accredits the player with extra *currency.  *When either *response* *handler* reaches the end of their sequence, the shop data will be updated.

```
    	private function BuyResponse(response:BuyVirtualGoodResponse):void
    			{

    				if (response.HasErrors())
    				{
    					logger("Problem occurred");
    				}
    				else
    				{
    					logger("Item bought");
    				}

    				requestBuilder.createAccountDetailsRequest().send(UpdateDetailsForShop);
    			}

    	private function ConsumeResponse(response:ConsumeVirtualGoodResponse):void
    			{
    				if (response.HasErrors())
    				{
    					logger("Problem occurred");
    				}
    				else
    				{
    					requestBuilder.createLogEventRequest().setEventKey("Grant_Currency").setNumberEventAttribute("CASH", Number(ConsumeQnt.text)).send(GeneralLogResponse);
    					logger("Item consumed");
    				}

    				requestBuilder.createAccountDetailsRequest().send(UpdateDetailsForShop);
    			}
```

## *Keeping track of player details*

To update the shop details, request the *account* *details* for the currently authenticated player. For the *currency* it's a simple text display. For the *Virtual* *Goods,* retrieve the *Virtual Goods* through *getVirtualGoods()* method, followed by the *Short code* of your *Virtual Good* which retrieves a *Number* of the *Virtual Good* of that type.

```
    	private function UpdateDetailsForShop(response:AccountDetailsResponse):void
    			{
    				ShopCurrency.text = response.getCurrency1().toString();
    				NOwned.text = response.getVirtualGoods().Gold_Coin.toString();
    			}
```

## *Testing Virtual Goods*

Create a way for the player to *buy* and *consume* Virtual Goods in your project. Test your shop to make sure that when you click *buy*, the *currency* depletes in exchange for an increased amount of Virtual Goods. When you *consume* items the *currency* should go up but the amount of Virtual Goods owned should decrease.

![l](img\AS\3.jpg)
