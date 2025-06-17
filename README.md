**Instructions:**  
Implement a function `flag_suspicious_batches(input_queue, output_queue)` that processeses transactions and produces batched reports.

The `input_queue` is a queue containing 1000 transactions, where each transaction is an object (map) with attributes `account_id` (string), `month` (integer), and `amount` (integer).

The function should deqeue transactions one by one and process them until the queue is empty. 

For every 100 transactions dequeued, the function should write a report to the `output_queue`.
The report should be a `list` of `tuples` of the form `(account_id, reason_of_suspicion)`, where `account_id` is a string and `reason_of_suspicion` is an integer 1 to 3, where:
- 1: The account has had a `cumulative amount of more than 1000 in the same month`.
- 2: The account has had `more than 10 transactions in the same month`.
- 3: The account has had both a `cumulative amount of more than 1000 in the same month` and `more than 10 transactions in the same month`.

**Sample Input:**
```python
transaction_queue = [
    {'account_id': 'A1', 'month': '6', 'amount': 2000},
    {'account_id': 'A2', 'month': '10', 'amount': 3000},
    {'account_id': 'A3', 'month': '7', 'amount': 11000},
    # ... 
]
```

**Sample Output:**
```python
output_queue = [
    [('A1', 3), ('A2', 1), ('A3', 2)],
    [('A4', 3), ('A6', 1)],
    # ...
]
```
