---
nav_sort: 7
src: Documentation/Configurator/Virtual Goods.md
---

# Virtual Goods

In the context of the GameSparks platform, a Virtual Good is any in-game asset that can be awarded, accumulated or bought. This would cover XP points and in-game currencies as well as specific goods that deliver benefits in-game (convenience, customisation, competitive advantage etc).  These can be used and consumed cross-platform. You can set up Virtual Goods to be bought as IAPs - you associate the Virtual Goods with the Product IDs of the corresponding items on the stores and when a good is purchased we can reconcile the store receipts with the items.  You can also establish relationships between them so they can be traded or converted.

## Managing Virtual Goods configurations

The Configurator Virtual Goods page displays the list of Virtual Goods and allows you to create new Virtual Goods and edit or delete existing ones.

![](img/VGoods/1.jpg)

The icons (highlighted above) give you the following capabilities:

  * __ Add a new Virtual Good.
  * __ Edit this Virtual Good.
  * __ Delete this Virtual Good.

## Creating a new Virtual Good configuration

Press the __ icon to create a new Virtual Good.

![](img/VGoods/2.jpg)

  * *Short Code* \- The Short Code is a mandatory field used to give the Virtual Good a unique identifier for use elsewhere in the Portal and in Cloud Code.
  * *Name* \- The Name field is a mandatory field used as an identifier to help the user find the Virtual Good in the Portal.
  * *Description* \- The Description is a mandatory field which should be used to describe the Virtual Good.
  * *Currencies* \- The amount of each of the currency needed to buy the Virtual Good.
  * *Product IDs* \- The ID of the item that has been created in the appropriate store.
  * *Max Quantity* \- The maximum quantity of this good that the player can own at any one time. Only enforced on BuyVirtualGoodsRequests using virtual currency. Purchases from external stores will still be awarded even if they result in this maximum being exceeded.
  * *Tags* \- Tags associated with the Virtual Good.
  * *Type* \- Is this a Virtual Good or a Currency Pack.
