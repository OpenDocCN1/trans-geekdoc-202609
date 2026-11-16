![](bbox=[0.153, 0.108, 0.725, 0.276])

Figure 4.2 Distributed CNOT by Eisert et al.

Consider the state of the system at slice 1 above, where we let |c⟩ = α|0⟩ + β|1⟩:

at slice 1 : (α|0⟩ + β|1⟩) ⊗ (1/√2|00⟩ + 1/√2|11⟩) ⊗ |t⟩
= (α/√2|000⟩ + α/√2|011⟩ + β/√2|100⟩ + β/√2|111⟩) ⊗ |t⟩

then, applying the CNOT between the top two qubits we have, at slice 2:

at slice 2 : ( (α/√2|000⟩ + α/√2|011⟩ + β/√2|110⟩ + β/√2|101⟩ ) ⊗ |t⟩ )

Then, the second qubit (from the top) is measured, and

+   1) if we get a 0, and this is sent from A to B, and since it is 0, the X gate is not applied, then, at slice 3, we have:

at slice 3 : √2 · ( (α/√2|000⟩ + β/√2|101⟩ ) ⊗ |t⟩ )
= (α|000⟩ + β|101⟩) ⊗ |t⟩

since 1/√(prob(0) in second qubit) = 1/√(|α/√2|² + |β/√2|²) = 1/√(1/2) = √2, and then applying the CNOT between the two qubits at B locally:

at slice 4 : α|000⟩|t⟩ + β|101⟩(X|t⟩)

and then applying gate H in the third line (from the top):

at slice 5 : α|00⟩(H|0⟩)|t⟩ + β|10⟩(H|1⟩)(X|t⟩)
= α/√2 |000⟩|t⟩ + α/√2 |001⟩|t⟩ + β/√2 |100⟩(X|t⟩)
- β/√2 |101⟩(X|t⟩)