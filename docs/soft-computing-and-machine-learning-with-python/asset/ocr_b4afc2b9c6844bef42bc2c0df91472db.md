# Algorithm 4: Individual detector to recognize functions.

```
Function individual_detector(program)
  individuals <- []
  instruction <- program[0]
  repeat
    if is.function(instruction) then
      individuals <- individuals + label(instruction)
    end if
    instruction <- next(instruction)
  until not next(instruction)
  return individuals
```

After identifying the individuals, we must extract the binary patterns we are looking for. To this, the user should provide a Pattern Detector, which comprises a collection of predicate functions. These functions receive one instruction of the instrumented binary program. In case that instruction is not included in the expected pattern, null must be returned. If the pattern is identified, a pair containing the individual and the range of instructions in the pattern (other pair) is returned.

Algorithm 5 presents a Pattern Detector of our example. It recognizes the return pattern added by the Instrumentor. If the instruction label is RETURN, the Pattern Detector recognizes the pattern. The corresponding function is returned as the first element of the pair. The second one is the range of instructions comprising the pattern: the first one (the one labeled RETURN) and the next instruction after the following RET.

# Algorithm 5: Pattern detector to recognize RET patterns.

```
Function RET_pattern_detector(instruction)
  if instruction is not _RETURN_id_func then
    return null
  end if
  begin_instruction <- instruction
  while not instruction is RET do
    instruction <- next(instruction)
  end while
  return (id_func, begin_instruction, next(instruction)))
```