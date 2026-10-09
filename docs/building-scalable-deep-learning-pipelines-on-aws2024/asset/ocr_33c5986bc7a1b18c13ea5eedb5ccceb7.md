```
```
                outputs = model(inputs)
                loss = criterion(outputs, labels.
unsqueeze(1))
                loss.backward()
                optimizer.step()
            logger.info(
                f"Epoch [{epoch + 1}/{num_epochs}],"
                f"Loss: {loss.item():.4f}"
            )
```


```

```
```
[In]: def evaluate_model(
            model,
            test_loader,
            criterion
    ) -> Tuple[float, float]:
        """
        Evaluate the trained model on the test data to assess
        its performance.
        Calculate the test loss and additional evaluation
        metrics such as the R-squared score.
        """
        with torch.no_grad():
            model.eval()
            predictions = []
            targets = []
            test_loss = 0.0
            for inputs, labels in test_loader:
                outputs = model(inputs)
                loss = criterion(outputs, labels.unsqueeze(1))
                test_loss += loss.item() * inputs.size(0)
                predictions.extend(outputs.squeeze().tolist())
```


```