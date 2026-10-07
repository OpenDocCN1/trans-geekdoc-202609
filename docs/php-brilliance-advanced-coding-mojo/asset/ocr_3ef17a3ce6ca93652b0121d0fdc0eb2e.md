# Don't Talk To Strangers

```
class User
{
    public function payForOrder(Chargeable $order)
    {
        try {
            $this->getAccount()->payOrder($order);
        } catch (InsufficientFundsException $e) {
            // throw new OrderPaymentException();
        }
    }
}
```

> For the sake of the One Dot Principle, we are safe to exclude the arrow that comes after any references to $this. I'll come to that bit shortly.

A proxy method is a pretty simple construct. In this instance it just two things. Firstly, it makes sure that it's receiving a parameter that conforms to our Chargeable interface, whatever that may be. Secondly, it passes that Chargeable item on to this user's UserAccount instance.

> Remember that I mentioned the User Account instance would be lazily loaded? If this is the case, then acquiring it via a getAccount() method is a sensible way to achieve this. The alternative would be to inject a pre-fabricated UserAccount instance via the constructor, in which case we would probably access it as $this->account instead.

This is the point where we start encountering the downsides of achieving loose coupling by following the Law of Demeter; a proliferation of proxy methods.

In this rather simple scenario, it isn't really a problem. The addition of the payForOrder() method to the public interface of our User model is both short and to the point. Any other developer on our team ought to be able to look at that code as