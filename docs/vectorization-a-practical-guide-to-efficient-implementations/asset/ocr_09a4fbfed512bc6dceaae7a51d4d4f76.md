```
"eval_loss": [],
"eval_acc": [],
}
for epoch in range(num_epochs):
    train_loss, train_acc=train_epoch(model, device, train_data, optimizer)
    eval_loss, eval_acc = eval_epoch(model, device, eval_data)
    print (
        f"Epoch ({epoch+1})/{num_epochs}:",
        f"train_loss - {train_loss:.2f}",",
        f"train_acc - {train_acc:.2f}",",
        f"eval_loss - {eval_loss:.2f}",",
        f"eval_acc - {eval_acc:.2f}",
    )
    history["train_loss"].append(float(train_loss))
    history["eval_loss"].append(float(eval_loss))
    history["train_acc"].append(float(train_acc))
    history["eval_acc"].append(float(eval_acc))
    # saving checkpoint
    if (epoch + 1) % 20 == 0:
        torch.save({
        'epoch': epoch + 1,
        'model_state_dict': model.state_dict(),
        'optimizer_state_dict': optimizer.state_dict(),
        'loss': eval_loss,
        }, f"./checkpoints/tiny_llm_checkpoint_{epoch+1:03d}.pt")
    # Saving metrics
    with open("./training_history.json", "w") as fid:
        json.dump(history, fid)
    # Saving the final model
    torch.save(model.state_dict(), "./final_model_weights.pt")
```

Over 10 epochs, we reached the best evaluation accuracy at 0.27.

```
Epoch 1/10: train_loss - 6.96, train_acc - 0.16 eval_loss - 5.85, eval_acc - 0.25
Epoch 2/10: train_loss - 6.46, train_acc - 0.20 eval_loss - 5.83, eval_acc - 0.22
Epoch 3/10: train_loss - 6.27, train_acc - 0.21 eval_loss - 5.65, eval_acc - 0.26
Epoch 4/10: train_loss - 6.23, train_acc - 0.21 eval_loss - 5.67, eval_acc - 0.25
Epoch 5/10: train_loss - 6.18, train_acc - 0.21 eval_loss - 5.73, eval_acc - 0.26
Epoch 6/10: train_loss - 6.14, train_acc - 0.21 eval_loss - 5.67, eval_acc - 0.25
Epoch 7/10: train_loss - 6.13, train_acc - 0.21 eval_loss - 5.73, eval_acc - 0.24
Epoch 8/10: train_loss - 6.03, train_acc - 0.21 eval_loss - 5.40, eval_acc - 0.27
Epoch 9/10: train_loss - 6.10, train_acc - 0.21 eval_loss - 5.56, eval_acc - 0.26
Epoch 10/10: train_loss - 6.00, train_acc - 0.21 eval_loss - 5.54, eval_acc - 0.26
```

However, if we train for more epochs, we can obtain even better results. Figure 11.10 plots the training and evaluation loss as well as prediction accuracy for this model trained over 300 epochs.