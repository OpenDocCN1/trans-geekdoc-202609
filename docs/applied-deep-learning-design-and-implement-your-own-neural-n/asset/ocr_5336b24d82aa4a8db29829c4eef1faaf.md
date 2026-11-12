```
// 0.0552

[9/10][1550/1583]Loss D: 0.3120 Loss G: 2.8712D(x): 0.8571 D(G(z)):
0.1281

// 0.0711
```

```
## Train with all-fake batch
    # Generate batch of latent vectors
    noise = torch.randn(b_size, latent_vec, 1, 1, device=d
evice)
    # Generate fake image batch with G
    fake = G_network(noise)
    label.fill_(fake_label)
    # Classify all fake batch with D
    output = D_network(fake.detach()).view(-1)
    # Calculate D's loss on the all-fake batch
    errD_fake = loss_function(output, label)
    # Calculate the gradients for this batch
    errD_fake.backward()
    D_G_z1 = output.mean().item()
    # Add the gradients from the all-real and all-
    fake batches
    errD = errD_real + errD_fake
    # Update D
    optimizerD.step()
```

# # Saving the model

In the following, the trained model is saved to the disk using torch.save so that it can be used later on.

```
torch.save(G_network,'dcgan_generator.pth')
```

# # Reload the model

The saved model can be reloaded back to the memory using torch.load function:

```
loaded_G_net= torch.load('dcgan_generator.pth')
```

# # Visualizing real versus fake images

After the training, the GAN model generated new celebrity faces. Here, we are having a look at real and fake images side by side.