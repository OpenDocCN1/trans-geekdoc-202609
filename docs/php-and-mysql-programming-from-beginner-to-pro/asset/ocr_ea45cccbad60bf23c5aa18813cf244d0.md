In this instance, `UserFactory` abstracts the creation of different `User` types, simplifying object creation and promoting flexibility in user management.

# Strategy Pattern for Flexible Payment Processing

The Strategy pattern enables the selection and interchange of algorithms, such as payment methods, at runtime, based on the application's requirements.

```
interface PaymentMethod
{
    public function processPayment($amount);
}

class CreditCard implements PaymentMethod
{
    public function processPayment($amount)
    {
        // Process payment through credit card
    }
}

class PayPal implements PaymentMethod
{
    public function processPayment($amount)
    {
        // Process payment via PayPal
    }
}

class PaymentProcessor
{
    private $paymentMethod;

    public function setPaymentMethod(PaymentMethod $method)
    {
        $this->paymentMethod = $method;
    }

    public function executePayment($amount)
    {
        $this->paymentMethod->processPayment($amount);
    }
}

$paymentProcessor = new PaymentProcessor();
$paymentProcessor->setPaymentMethod(new PayPal());
$paymentProcessor->executePayment(100);
```