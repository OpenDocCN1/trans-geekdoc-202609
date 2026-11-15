```
```
\mathcal{L}^{\Sigma_{\text{hyb}}}_{\text{pk-cpa-L}}
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \Sigma_{\text{pub}}.\text{Enc}(pk, tk)
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
```
```

The starting point is $\mathcal{L}_{\text{pk-cpa-L}}$, shown here with the details of $\Sigma_{\text{hyb}}$ filled in.

Our only goal is to somehow replace $m_L$ with $m_R$. Since $m_L$ is only used as a plaintext for $\Sigma_{\text{sym}}$, it is tempting to simply apply the one-time-secrecy property of $\Sigma_{\text{sym}}$ to argue that $m_L$ can be replaced with $m_R$. Unfortunately, this cannot work because the key used for that ciphertext is $tk$, which is used elsewhere. In particular, it is used as an argument to $\Sigma_{\text{pub}}.\text{Enc}$.

However, using $tk$ as the plaintext argument to $\Sigma_{\text{pub}}.\text{Enc}$ should $hide tk$ to the calling program, if $\Sigma_{\text{pub}}$ is CPA-secure. That is, the $\Sigma_{\text{pub}}$-encryption of $tk$ should look like a $\Sigma_{\text{pub}}$-encryption of some unrelated dummy value. More formally, we can factor out the call to $\Sigma_{\text{pub}}.\text{Enc}$ in terms of the $\mathcal{L}_{\text{pk-cpa-L}}$ library, as follows:

```
```
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
tk' \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \text{CHALLENGE}'(tk, tk')
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
```
```

```
```
\mathcal{L}^{\Sigma_{\text{pub}}}_{\text{pk-cpa-L}}
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}'(tk_L, tk_R):
return } \Sigma_{\text{pub}}.\text{Enc}(pk, tk_L)
```
```

Here we have changed the variable names of the arguments of CHALLENGE' to avoid unnecessary confusion. Note also that CHALLENGE now chooses two temporary keys — one which is actually used to encrypt $m_L$ and one which is not used anywhere. This is because syntactically we must have two arguments to pass into CHALLENGE'.

Now imagine replacing $\mathcal{L}_{\text{pk-cpa-L}}$ with $\mathcal{L}_{\text{pk-cpa-R}}$ and then inlining subroutine calls. The result is:

```
```
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
tk' \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \Sigma_{\text{pub}}.\text{Enc}(pk, tk')
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
```
```

At this point, it does now work to factor out the call to $\Sigma_{\text{sym}}.\text{Enc}$ in terms of the $\mathcal{L}_{\text{ots-L}}$ library. This is because the key $tk$ is not used anywhere else in the library. The result of