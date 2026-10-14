First 200 words of each movie review

Top 20K most frequent words

```
max_words = 20000
seq_len = 200
(x_train, y_train), (x_val, y_val) = keras.datasets.imdb.load_data(
    num_words=max_words)

x_train = keras.utils.pad_sequences(x_train, maxlen=seq_len)
x_val = keras.utils.pad_sequences(x_val, maxlen=seq_len)

batch_size = 256
num_epochs = 8

hidden_size = 64
embed_dim = 128
lstm_dropout = 0.2
dense_dropout = 0.5
weight_decay = 1e-3

#LSTM architecture
model = Sequential()
model.add(Embedding(max_words, embed_dim, input_length=seq_len))
model.add(Bidirectional(LSTM(hidden_size, dropout=lstm_dropout,
    recurrent_dropout=lstm_dropout)))
model.add(Dense(hidden_size,
    kernel_regularizer=regularizers.l2(weight_decay),
    activation='relu'))
model.add(Dropout(dense_dropout))
model.add(Dense(hidden_size/4,
    kernel_regularizer=regularizers.l2(weight_decay), activation='relu'))
model.add(Dense(1, activation='sigmoid'))

model.compile(
    loss=keras.losses.BinaryCrossentropy(),
    optimizer=tf.keras.optimizers.Adam(),
    metrics=["accuracy"]
)

model.summary()

#define callbacks
file_name = SAVE_PATH + 'lstm-weights-checkpoint.h5'
checkpoint = ModelCheckpoint(file_name, monitor='val_loss', verbose=1,
    save_best_only=True, mode='min')
reduce_lr = LearningRateScheduler(scheduler, verbose=1)
early_stopping = EarlyStopping(monitor='val_loss', min_delta=0.01,
    patience=16, verbose=1)
#tensor_board = TensorBoard(log_dir='./logs', write_graph=True)
callbacks_list = [checkpoint, reduce_lr, early_stopping]

hist = model.fit(x_train, y_train, batch_size=
    batch_size, epochs=num_epochs, callbacks=
    callbacks_list, validation_data=(x_val, y_val))

test_scores = model.evaluate(x_val, y_val,
    verbose=2)
```

Training paramaters

Model parameters

Model training

Model evaluation