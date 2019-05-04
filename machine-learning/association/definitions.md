# Association rules

* **support**: number of transactions that contains all elements
* **trust**: proportion from the transactions with A that also contain B
* **strength**: support + trust

## Example

Transactions:
* A B C
* B C
* A B
* A B C
* A B
* B

Who buys C also buys B
* transactions: 6
* support: 3/6 = 0.5 = 50%
* trust: 
    * transactions with C: 3
    * transactions with C and B: 3
    * trust: 3/3 = 1 = 100%

Who buys B also buys C
* transactions: 6
* support: 3/6 = 0.5 = 50%
* trust: 
    * transactions with B: 6
    * transactions with B and C: 3
    * trust: 3/6 = 0.5 = 50%

Who buys A also buys B
* transactinos: 6
* support: 4/6 = 0.66 = 66%
* trust:
    * with A: 4
    * with A and B: 4
    * trust: 4/4 = 1 = 100%
