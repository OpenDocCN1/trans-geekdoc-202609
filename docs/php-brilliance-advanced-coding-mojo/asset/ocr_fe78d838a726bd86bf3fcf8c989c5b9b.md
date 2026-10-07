Proding the polymorph.

```
interface RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm);
}

class FixedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on a fixed interest rate
        //
        return $paymentPlan;
    }
}
```

```
class CappedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on variable interest rates but subject
        // to a nominal cap to prevent repayments exceeding
        // a certain value
        //
        return $paymentPlan;
    }
}
```

As you can see here, I've provided an interface from the get-to-go. This is because we to ensure that when we inject a repayment calculator into a MortgagePlan instance, our mortgage plan needs to know that the calculator will provide the getPaymentPlan() method. Implementing the interface means that this is guaranteed since the PHP interpreter will emit a fatal error if this isn't the case.

And lastly, those two specialised classes that were in the first example have now been modified so that, instead of extending the original MortgagePlan abstract, they now implement the RepaymentCalc interface. Each calculator is now an injectable behaviour, allowing us to change the way that the consuming object behaves at run time. This is an important distinction and it's one that means our MortgagePlan