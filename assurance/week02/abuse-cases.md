# Abuse cases

Threat Model v1.0 — CPS 5981 01, Week 02

**Mission:** This system succeeds when every order is recorded at the price the shop set, not the price sent from the browser and every order is one the customer meant to place.

Each case names an actor, what they can already do, what they do with it, what stops being
true for the mission, and what that costs.

## Case 1

- **Actor:** a customer with an ordinary account
- **Capability:** an place orders, and can change what their browser sends before it leaves their machine
- **Action sequence:** change the price on an order before it reaches the server
- **Mission effect:** the price recorded on the order stops matching the price the shop set
- **Impact:** money the shop cannot get back, and no record showing what the price should have been

Because a customer with an ordinary account can change the price on an order before it reaches the server, the price recorded on the order stops matching the price the shop set occurs, costing money the shop cannot get back, and no record showing what the price should have been.

## Case 2

- **Actor:** someone with no account at all
- **Capability:** can open the sign-in page as many times as they want
- **Action sequence:** guess passwords against email addresses until one works
- **Mission effect:** orders start appearing against people who did not place them
- **Impact:** refunds the shop has to issue, and no way to tell real customers from impostors

Because someone with no account at all can guess passwords against email addresses until one works, orders start appearing against people who did not place them occurs, costing refunds the shop has to issue, and no way to tell real customers from impostors.

## Case 3

- **Actor:** a customer who has already signed in
- **Capability:** can post review text that other customers' browsers will display
- **Action sequence:** leave text on a product page that runs as script when another signed-in customer opens it
- **Mission effect:** an order gets placed under one customer's account by someone else, and the account holder cannot show it was not them
- **Impact:** orders the shop cannot prove were genuine, and no way to say how many customers were affected

Because a customer who has already signed in can leave text on a product page that runs as script when another signed-in customer opens it, an order gets placed under one customer's account by someone else, and the account holder cannot show it was not them occurs, costing orders the shop cannot prove were genuine, and no way to say how many customers were affected.

## Case 4

- **Actor:** a member of staff with routine access
- **Capability:** can read customer order records as part of their job
- **Action sequence:** read and copy customer contact details far beyond what any task required
- **Mission effect:** the shop loses the ability to say who has seen a customer's details
- **Impact:** a notification duty the shop cannot scope, and customer trust it does not get back

Because a member of staff with routine access can read and copy customer contact details far beyond what any task required, the shop loses the ability to say who has seen a customer's details occurs, costing a notification duty the shop cannot scope, and customer trust it does not get back.

## Case 5

- **Actor:** an automated client run by anyone
- **Capability:** can request the search page repeatedly at no cost
- **Action sequence:** send far more requests than a person would, continuously
- **Mission effect:** customers cannot place orders for as long as it lasts
- **Impact:** orders that go to a competitor, and staff time spent on something that was never a customer

Because an automated client run by anyone can send far more requests than a person would, continuously, customers cannot place orders for as long as it lasts occurs, costing orders that go to a competitor, and staff time spent on something that was never a customer.

## Case 6

- **Actor:** a customer who wants a refund
- **Capability:** can place a genuine order and later deny placing it
- **Action sequence:** place an order, receive it, then claim someone else used their account
- **Mission effect:** the shop cannot show which sign-in placed the order
- **Impact:** refunds the shop cannot contest, with no evidence either way

Because a customer who wants a refund can place an order, receive it, then claim someone else used their account, the shop cannot show which sign-in placed the order occurs, costing refunds the shop cannot contest, with no evidence either way.
