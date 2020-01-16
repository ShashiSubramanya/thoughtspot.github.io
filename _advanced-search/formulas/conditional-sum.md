---
title: [Formula operators]


last_updated: tbd
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
Formula operators allow you to apply `if`/`then`/`else` conditions in your
formulas. You can leverage operators in your formulas to have them return true,
false, or a predetermined value.

## Formula operators

The operators include:

{% include content/operators.md %}

## Calculate the conditional sum

Calculating the conditional sum is useful when you want to see, for example, the
total revenue for a product by region.

Conditional sum formulas follow this syntax: if (some condition) then (measure)
else 0. You can use this syntax to limit your search in cases when you don't
want to add a column filter. For example: `if ( product = shoes ) then revenue
else 0`

The following example shows you how to figure out the number of customers who
bought both products, in this case an ipad and galaxy tablet. You can then find
out the revenue generated by both products.

1. Create the following formula in the Formula Builder:

    `ipadcount = sum ( if ( product = 'ipad' ) then 1 else 0 ) > 0`

     This formula will provide you with the number of ipads that were bought.

2. You can then create another formula that looks like this:

    `galaxycount = sum ( if ( product = 'galaxy' then 1 else 0 ) > 0`

    And this formula will provide you with the number of galaxys that were bought.

3. Using [nested formulas]({{ site.baseurl }}/complex-search/about-nested-formulas.html#), you can combine these two formulas.

    For example: `f1 = ipadcount + galaxycount`

4. Now, you can search using the `f1` formula to find out the revenue generated by both products.

## Related information

* [Operators]({{ site.baseurl }}/reference/formula-reference.html#operators) in the [Formula function reference]({{ site.baseurl }}/reference/formula-reference.html#)