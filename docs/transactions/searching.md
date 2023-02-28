# Searching Transactions

The search bar at the top of the page can be used to search for transactions.

## Hidden transactions
The hidden eye 👁️ button next to the search bar allows you to view "hidden" transactions, i.e. transactions that I don't think are interesting.
An example to that is a bank transaction for your credit card bill, for a credit card you're already getting the transactions from.
Such a transaction is already displayed in better detail in your credit card transactions, so it's a sort of a duplicate and is not interesting.

## Simple queries
A string value will look for that string in the description, memo category and account fields.
A numeric value will look for the absolute value (`X` or `-X`) in the amount field

Multiple queries are chained with "AND", so looking for `computer nam` will find "namaste computers" but not "blob computers".

Spaces separate queries from each other. To look for an expression with a space in it, like `Electric Company`, use quotes (`"Electric Company"`).

## Complex queries
For people that want be more specific, you can use these:

* Strings and numbers work as in "Simple Queries"
* Use `&&` for "and" and `||` for "or"
* You can use brackets (`(` and `)`) to affect order of operations
* Using `@` indicates a specific field, like `@description`
* When using `@`, you can use the following operators:
    * `=`: Contains (substring)
    * `==`: Equals (not a substring, whole string has to match)
    * `~=`: Regex match
    * `<`, `>`, `<=`, `>=` for numeric fields and values

An example query for finding big expenses on Wolt can be:
```
wolt @charged_amount<-500
```
