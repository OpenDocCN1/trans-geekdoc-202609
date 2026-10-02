In this example, we use date and time functions to work with order dates. We extract the year and month from the order date, add 7 days to calculate the delivery date, and calculate the duration between the order date and delivery date using the DATE_ADD and DATE_DIFF functions.

# Section 5: User-Defined Functions (UDFs)

Apart from the built-in functions, SQL also allows you to create your own functions known as User-Defined Functions (UDFs). UDFs provide flexibility and reusability by encapsulating custom logic. You can create scalar functions that return a single value or table functions that return a result set.

Example:

```
```sql
CREATE FUNCTION calculate_discount(price DECIMAL, discount_rate DECIMAL)
RETURNS DECIMAL
BEGIN
  DECLARE discounted_price DECIMAL;
  SET discounted_price = price - (price * discount_rate);
  RETURN discounted_price;
END;
```
```