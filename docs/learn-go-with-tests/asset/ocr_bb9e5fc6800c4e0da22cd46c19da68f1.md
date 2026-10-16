Table-based test works nicely here and clearly illustrate what our requirements are. We run through the table and check the SpyBlindAlerter to see if the alert has been scheduled with the correct values.

# Try to run the test

You should have a lot of failures looking like this

```
=== RUN   TestCLI
--- FAIL: TestCLI (0.00s)
=== RUN   TestCLI/it_schedules_printing_of_blind_values
    --- FAIL:  TestCLI/it_schedules_printing_of_blind_values
    (0.00s)
===                                 RUN
TestCLI/it_schedules_printing_of_blind_values/100_scheduled_for
_0s
    ---         FAIL:
TestCLI/it_schedules_printing_of_blind_values/100_scheduled_for
_0s (0.00s)
        CLI_test.go:71: got scheduled time of 5s, want 0s
===                                 RUN
TestCLI/it_schedules_printing_of_blind_values/200_scheduled_for
_10m0s
    ---         FAIL:
TestCLI/it_schedules_printing_of_blind_values/200_scheduled_for
_10m0s (0.00s)
        CLI_test.go:59: alert 1 was not scheduled
[{5000000000 100}]
```

# Write enough code to make it pass

```
func (cli *CLI) PlayPoker() {

    blinds := []int{100, 200, 300, 400, 500, 600, 800, 1000, 20
```