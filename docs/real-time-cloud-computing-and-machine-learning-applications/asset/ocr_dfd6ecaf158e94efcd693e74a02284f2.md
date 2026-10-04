724 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondonon

```
float[][] normalized = new float[row][col];
//normalize every column in the array
for (int i = 0; i < row; i++) {
  for (int j = 0; j < col; j++) {
    normalized[i][j] = (data_o[i][j] - min[j]) / (max[j] - min[j]);
  }
}
//returns the normalized value
return normalized;
/**
 * Denormalizes an array of values
 * @param norm array of the normalized value
 * @return float array @code denormalized] of denormalized value.
 */
public float[] denormalize(float[] norm) {
  int col = norm.length;
  //create an array to store denormalized
float[] denormalized = new float[col];
//denormalizes each value
for (int i = 0; i < col; i++) {
  denormalized[i] = (norm[i] * (max[i] - min[i])) + min[i];
}
//returns denormalized value
return denormalized;
n/**
 * Denormalizes a single value given the variable index
 * @param norm normalized value
 * @param var index of min & max value
 * @return denormalized value
 */
public float denormalize(float norm, int var) {
//returns denormalized value
  return (norm * (max[var] - min[var])) + min[var];
}
```

# 7.1.12.2. Reshape The Data into the Appropriate Format

a) The Data format for MLP Network, for example, the observed temperature over the last seven days is given in Table 7.14.