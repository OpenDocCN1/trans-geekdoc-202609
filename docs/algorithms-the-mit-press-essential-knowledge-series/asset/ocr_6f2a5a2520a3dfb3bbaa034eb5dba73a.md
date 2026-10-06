We make sure that all the integers have the same number of digits. So we pad the numbers with zeros on the left if necessary, turning 5 to 005, 97 to 097, and 53 to 053. We go through all our numbers and triage them by their rightmost digit. We use that digit to place them in ten piles:

| 742 | | 165 | 417 |
| | 612 | | |
| 760 | 151 | 162 | 855 | 317 |
| 970 | 961 | 272 | 245 | 926 | 787 |
| 590 | 261 | 412 | 364 | 005 | 496 | 097 | 639 |
| 840 | 981 | 812 | 053 | 274 | 845 | 686 | 577 | 568 | 709 |

We lightened up the numbers’ fill color to indicate that they are partially sorted; each pile contains the numbers with the same rightmost digit. All the numbers in the first pile end in zero, and in the second pile they end in one, up to the last pile, where they end in nine. We collect the ten piles, starting from the first on the left and adding piles at the bottom (taking care not to shuffle the numbers in any way). Then we redistribute them into ten piles using the second digit from the right and get: