1 0 1
_______
1 0 0 | 1 0 1 0 0 0
      - 1 0 0
      -------
        1 0 0 0
      -   1 0 0
      ---------
            0

That is, 0b10100 ÷ 0b100 = 0b101.

Due to the tedium of computing binary multiplication and division by hand, it seems more reasonable to define algorithms that utilize repeated addition and subtraction. After all, this is essentially what computers do. In that regard, please refer to *Machine Approaches to Multiplication & Division* section below.

# 5.5 BOOLEAN LOGIC

Boolean logic is the conceptual basis for digital logic, which takes a binary input, such as 0 or 1 representing true or false, and outputs a binary result. Only a few rules of digital logic are needed for some complex decision making in general purpose computers.

In order of simplicity, the typical digital logic conditions are NOT, AND, OR, XOR, NAND, NOR and XNOR. These are described as follows using data x and output y.