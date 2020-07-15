### Python

```python
def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
    total_tank = 0
    cur_tank = 0
    index = 0
    for i in range(len(gas)):
        total_tank += gas[i] - cost[i]
        cur_tank += gas[i] - cost[i]
        if cur_tank < 0:
            cur_tank = 0
            index = i + 1
    return index if total_tank >= 0 else -1
```
