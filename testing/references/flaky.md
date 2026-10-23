# Flaky tests

A flaky test is a bug, in the test or in the code. Fix it in the change where you saw it, even if it is outside your scope. Never retry a CI job only to get green.

## Where the fix goes

- The default branch is red for everyone: a small separate branch off it with only the fix.
- It only failed on your branch or locally: a separate commit, first in your MR. No second MR.

## Common causes

| Symptom | Usual cause | Fix |
|---|---|---|
| Passes alone, fails in the suite | shared state, test order | isolate data, reset globals, unique names |
| Fails under load or in CI only | fixed sleep, race on a background task | wait on the condition, not on time |
| Fails at midnight or month end | wall clock | inject the clock |
| Fails with a different seed | unseeded randomness, unbounded property inputs | seed it, or fix the bug the input found |
| Coverage differs from local | CI skips tests that need services | add a unit test for the branch, mocking the earlier check |

## Wait on conditions

Never `sleep(n)` and hope. Poll for the condition with a timeout and a clear failure message:

```python
def wait_for(cond, timeout=5.0, interval=0.05, what="condition"):
    deadline = time.monotonic() + timeout
    while time.monotonic() < deadline:
        if cond():
            return
        time.sleep(interval)
    raise AssertionError(f"timed out after {timeout}s waiting for {what}")
```

Better still: make the code under test signal completion (an event, a returned future) and wait on that.

## Proving the fix

Run the test many times in a loop (for example 50 runs, or `pytest --count` / `-p no:randomly` variations) before and after the fix. Report both numbers.
