```
k_e <- E.KeyGen
k_m <- M.KeyGen
S := ∅
EAVESDROP(m_L, m_R):
if |m_L| != |m_R|
return null
c := E.Enc(k_e, m_L)
t := M.MAC(k_m, c)
S := S ∪ {(c, t)}
return (c, t)
DEC(c, t):
if (c, t) ∈ S
return null
if (c, t) ∉ S :
return err
// unreachable
```

The unreachable statement has been removed and the redundant variables S and T have been unified. Note that this hybrid library never uses E.Dec, making it possible to express its use of the E encryption scheme in terms of L_cpa-L.

```
k_m <- M.KeyGen
S := ∅
EAVESDROP(m_L, m_R):
if |m_L| != |m_R|
return null
c := CPA.EAVESDROP(m_L, m_R)
t := M.MAC(k_m, c)
S := S ∪ {(c, t)}
return (c, t)
DEC(c, t):
if (c, t) ∈ S
return null
if (c, t) ∉ S:
return err
```

```
L_cpa-L^E
k_e <- E.KeyGen
CPA.EAVESDROP(m_L, m_R):
c := E.Enc(k_e, m_L)
return c
```

The statements involving the encryption scheme E have been factored out in terms of L_cpa-L.

We have now reached the half-way point of the proof. The proof proceeds by replacing L_cpa-L with L_cpa-R (so that m_R rather than m_L is encrypted), applying the same modifications as before (but in reverse order), to finally arrive at L_cca-R. The repetitive details have been omitted, but we mention that when listing the same steps in reverse, the changes appear very bizarre indeed. For instance, we add an unreachable statement to the DEC subroutine; we create a redundant variable T whose contents are the same as S; we mysteriously change one instance of S (the condition of the second if-statement in DEC) to refer to the other variable T. Of course, all of this is so that we can factor out the statements referring to the MAC scheme (along with T) in terms of L_mac-fake and finally