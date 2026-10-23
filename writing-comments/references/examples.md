# Comment examples

Bad (dev history):

```rust
//! The dead-man's switch depends on TWO clocks (split plan, review-2 F1).
```

Good:

```rust
//! Lease expiry uses two clocks: monotonic time drives the deadline, while
//! wall time detects suspension that may have frozen the monotonic clock.
```

Bad (restates the line):

```python
# Retry 3 times before failing.
retries = 3
```

Good (states the reason):

```python
# Bound retries so an unavailable upstream cannot hold a worker indefinitely.
retries = 3
```

Bad (figurative):

```rust
/// This is the load-bearing seam between the controller and executor.
```

Good:

```rust
/// All controller commands enter the executor through this interface.
```

Bad (incident story in code):

```python
# Added after a customer job looped for 6 hours last March.
MAX_TURNS = 50
```

Good:

```python
# Caps a runaway agent; a normal task finishes in under 20 turns.
MAX_TURNS = 50
```

Bad (field meaning far from the field):

```python
@dataclass
class Job:
    """... `deadline` is when the job is dropped, None for no limit;
    the scheduler turns it into `timeout` ..."""
    deadline: datetime | None = None
    timeout: float | None = None
```

Good:

```python
@dataclass
class Job:
    """One unit of work in the queue."""
    deadline: datetime | None = None  # drop after this; None means no limit
    timeout: float | None = None      # seconds, set from deadline by the scheduler
```

Unnecessary:

```rust
/// Represents a sort direction.
enum SortDirection { Ascending, Descending }
```
