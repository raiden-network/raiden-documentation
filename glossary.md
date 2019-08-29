# Glossary

### Payments and Transfers

#### Available Balance \(!! Whats the difference between this and balance?\)

#### Balance

The balance determines how many tokens one specific channel participant holds. 

You can calculate the balance by taking the total amount of tokens deposited, adding the total amount of tokens received and subtracting the total amount of tokens sent for a participant.

$$
B_{participant} = P_{total\,token\,deposit} + P_{total\,tokens\,received} - P_{total\,tokens\,sent}
$$

#### Channel Capacity

The channel capacity determines how many tokens a channel holds. You can calculate the capacity by either:

* Taking the total amount of tokens deposited and subtracting the total amount of tokens withdrawn by both participants that have a channel open with each other.
* Taking the sum of both channel participants [balance](glossary.md#balance).

#### Payment

A payment in Raiden is the process of sending tokens from one account to another. Each payment has an initiator and a target.

#### Payment Channel

A payment channel allows for back and forth Raiden payments between participants without involving the actual blockchain.

A on-chain payment channel is opened whenever an initial deposit of tokens are made for a token network.

#### Transferred Amount

The

### Participants

#### Counterparty

#### Initiator

#### Payee

#### Payer

#### Target

#### Transfer

