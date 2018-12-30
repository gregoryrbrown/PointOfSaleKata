# Point Of Sale Kata

This is a sample solution for a point-of-sale kata. The point of the kata is to use TDD to develop the components for the business logic involved in keeping track of unit prices for items (per unit or per unit of weight) and to calculate a running total of the pre-tax checkout price as items are added or removed from an order at checkout.

Assumption: There is no database; each time this software component is used, it will have to be configured with unit/"eaches" prices and current markdowns/specials.

Assumption: The solution to this kata will be the business logic, not a particular implementation of a scenario of usage of the business logic. However, that might be written as part of the tests for the business logic.

Assumption: There is no pre-set list of items. For the tests, various things will probably be used such as "can of soup", "bananas", "bag of onions".

Assumption: If there is a multiple configuration of the unit price or the markdown/special of the same thing, the last one takes precedent. 

Assumption: Anything set up with a special/markdown will have a unit/eaches price.

Assumption: For things sold as a unit, such as "can of soup", there is no need to specify the number scanned, and that doesn't actually model the way a POS scanner works. However, for "bananas", there would be a weight associated when it is scanned.

Assumption: When a deletion of a certain thing is made that is sold in units, it doesn't matter which thing is deleted because everything with the same label string is the same. When something with a weight is deleted, it will be the last thing of that kind. For instance, if there are "bananas" scanned for half a pound, then "bananas" scanned for one pound, then "bananas" deleted, the one for one pound will be deleted.

Assumption: "It should repeatedly accept a scanned item or item and weight through an API call. It must keep an accurate current total through the process." and "The display system or receipt may query your code for the total" seem to be contradictory. We are not responsible for anything but calculating the pre-tax total. Thus, going to do the calculation on demand as mentioned in the second quote there.

Assumption: For "Support 'Buy N, get M of equal of lesser value for %X off' on weighted items", this is only for weighted items and also the M should be of the cheapest other type possible. There will be no checking for cycles or price optimization if we have multiple possible ways to apply these. The item type of N will be specified, but the item type of M will not. It could be the same item type. 

Assumption: There will be only one type of special/markdown per item type and there will only be one applied to each item type. If an item type has a special/markdown for it, it won't be eligible for "Support 'Buy N, get M of equal of lesser value for %X off' on weighted items".

