+   1. The duration of pronunciation is predicted to be short so we rounded to 0 durations at inference time.

+   2. We are dealing with paddings at the end of the sequence. In this case, the values of the embedding vectors for the padding token should be all zeros. Even if we leave the zero paddings around, the model should be able to learn not to generate any audio on top of it. Toward the end of the call function, we will do extra cleaning to remove these paddings.

+   - Lines 49–52 store some shapes which we will leverage later on to reshape our inputs. This also includes pre-computing the expected duration of the audio (max_durations).

+   - Lines 54–56 reshape the batch of token sequence embeddings into shape [batch_size x seq_len, num_channels]. This turns the 3D tensor into a stack of embedding vectors, which we will then use the tf.repeat operation to repeat/upsample the vectors.

+   - Line 57 reshapes the batch of durations into a 1D array of [batch_size x seq_len]. This new array will indicate how many times each piece of embedding vectors from hidden_states (Lines 54–56) needs to be repeated.

+   - Line 60 performs the tiling/repetition operation. We now should have a stack of embedding vectors of shape [batch_size x time_len, num_channels].

+   - Lines 63–73 implement a scattering logic to reshape the stack of repeated embedding vectors back into the shape of [batch_size, time_len, num_channels]. Because our repeated embedding vectors are organized in the shape of [batch_size x time_len, num_channels], we need to reshape the first dimension and split them into two separate dimensions, i.e. [batch_size, time_len]. Since this is a 2D matrix, we use the terminology row to indicate the batch dimension and col to indicate time_len here:

+   * row_indices: This is the index of the batch dimension. It is constructed with two steps of tf.repeat operations. We first construct the batch index [0, 1, ..., batch_size]. We then repeat each batch index by the sequence length. That way, we are assigning a batch index to each token embedding, which becomes [0, 0, ..., 1, 1, ..., batch_size, batch_size, ...]. Finally, since each token embedding vector is repeated duration times (Line 60), we also repeat the batch index by that many times corresponding to each token. This should give us an array whose length is identical to the second dimension (axis=1) of hidden_states that we obtained from Line 60.

+   * col_indices: This is the index of the time dimension, which is constructed by our helper function tf_ragged_range. For each