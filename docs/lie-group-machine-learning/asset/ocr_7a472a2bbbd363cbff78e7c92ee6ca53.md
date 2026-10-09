```
Algorithm 14.6: determines whether the two subdivision spaces can be homeomorphic.

Procedure Homeomorphism space {X1, X2}

//Input: subdivision space: X1, X2//
//Output:{0,1}//
If (X1 ∪ X2 are the spaces of a flat ring and Mobius zone) then {input the X1, X2}
Else
{Compute the dimension k of polyhedron;
For i=1 to k do
{Compute the homology group;
If (the homology group is isomorphic) continue;
Else
{return 0; exit}
End if}
End for;
Return 1;
End if
End Procedure Homeomorphism space
```

```
Algorithm 14.7: Determine whether the relationship between the two-dimensional chain is equivalent.

Procedure Chain of q dimension

//Input: n, k //
//Output: {0,1}//
Compute Z_q(K) = {z_q ∈ C_q(K); ∂z_q = 0} = Ker_q
Compute B_q(K) = {b_q ∈ C_q(K); ∃c_{q+1} ∈ C_{q+1}(k), S.T.∂c_{q+1} = b_q} = Im∂_{q+1}
Compute H_q(K) = Z_q(K)/B_q(K)
End Procedure Chain of q dimension
```

The element in quotient group H_q(K) is the mold of elements B_q(K) in Z_q(K). Hence, the equivalence classes determined by mold B_q(K) of complex K on the q-dimensional closed chain z_q is z_q + B_q(K), denoted by [z_q]. We say that z_q is a-dimensional homology class, and we have H_q(K) = {[z_q]; z_q ∈ Z_q(K)} for any [z_q] + [z_q'] = [z_q + z_q']. If z_q, z_q' ∈ Z_q(K), then [z_q] ↔ z_q - z_q' ∈ B_q(K). We call z_q, z_q' as the cohomology =dimensional closed chain, denoted by z_q - z_q' ~ 0 or z_q ~ z_q'.

For any q-dimensional chain c_q, c_q' ∈ C_q(K), if c_q - c_q' ∈ C_q(K), then we say that c_q, c_q' is a cohomology q-dimensional chain, denoted by c_q - c_q'. It is obvious that the homological relation between q-dimensional chains is an equivalant relation. The homological equivalence classes of c_q ∈ C_q(K) are [c_q] = c_q + B_q(K); we call it the q-dimensional homology class of c_q.

# 14.2.4 Cell homology edge algorithm

Many commonly used spaces can be cut into simple shapes. We can study the space created by standard bricks, which is the origin of the concept of complex. The first