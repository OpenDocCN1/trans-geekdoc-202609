```
// Placeholder data
let train_data = Tensor::randn(&[100, 784], (tch::Kind::Float, device));
let train_labels = Tensor::randint(10, &[100], (tch::Kind::Int64, device));

let loss_fn = nn::cross_entropy_for_logits;
let mut opt = nn::Adam::default().build(&vs, 1e-3)?;

// Training loop
for epoch in 1..=10 {
    let logits = net.forward(&train_data);
    let loss = loss_fn(&logits, &train_labels);

    opt.backward_step(&loss);

    if epoch % 2 == 0 {
        println!("Epoch: {} | Loss: {:.4}", epoch, loss.double_value(&[]));
    }
}
```

```
// Calculate feature importance
let mut feature_importance = Tensor::zeros(&[784], (tch::Kind::Float, device));
for i in 0..784 {
    let original = train_data.copy();
    let perturbed = original.index_put_(&[Tensor::of_slice(&[i]),
    Tensor::arange(100, (tch::Kind::Int64, device))], &Tensor::zeros(&[100],
    (tch::Kind::Float, device)));

    let original_logits = net.forward(&original);
    let perturbed_logits = net.forward(&perturbed);
    let diff = (original_logits - perturbed_logits).abs().sum(tch::Kind::Float);
    feature_importance += &diff;
}

println!("Feature importance: {:?}", feature_importance);

Ok(())
}
```

# **4. Using LIME for Local Interpretability**