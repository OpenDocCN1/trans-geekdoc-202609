# Table 3.2 List of examples of building slicing and striding configurations using Python `slice` or NumPy's `np.s_`.

| Operations | Python `slice` | NumPy `np.s_` |
| :--- | :--- | :--- |
| Slicing between two indices | `slice(start, stop)` | `np.s_[start:stop]` |
| Slicing using negative indices (translated to start+n and stop+n) | `slice(start, stop)` | `np.s_[start:stop]` |
| Slicing from a start index to the last element | `slice(start, None)` | `np.s_[start:]` |
| Slicing from the first element to a stop index | `slice(None, stop)` | `np.s_[:stop]` |
| Striding | `slice(start, stop, step)` | `np.s_[start:stop:step]` |
| Selecting all elements | `slice(None)` | `np.s_[:]` |
| Selecting all elements except the last element | `slice(None, -1)` | `np.s_[:-1]` |
| Selecting all elements except the last N element(s) | `slice(None, -N)` | `np.s_[:-N]` |
| Reversing array | `slice(None, None, -1)` | `np.s_[::-1]` |
| Striding from the first element to a stop index | `slice(None, stop, step)` | `np.s_[:stop:step]` |
| Striding from a start index to the last element | `slice(start, None, step)` | `np.s_[start::step]` |
| Striding from first to last element | `slice(None, None, step)` | `np.s_[: :step]` |
| Striding from last to first element | `slice(None, None, -step)` | `np.s_[::-step]` |

Note `np.s_` also supports convenient construction of slicing configurations of multiple dimensions, with the syntax `np.s_[start_0:stop_0:step_0, start_1:stop_1:step_1, ..., start_n:stop_n:step_n]`. This will return a tuple of `slice` objects, e.g. `(slice(start_0, stop_0, step_0), slice(start_1, stop_1, step_1), ..., slice(start_n, stop_n, step_n))`. To clarify, I have overloaded the ellipsis ... symbol here and it carries two meanings here:

+   • I intend the ellipsis “...” here as a notation to indicate there may be a variable number of dimensions when constructing the slices.