

### 构建网络模型

```python
seq = Sequential()
seq.add(ConvLSTM2D(filters=40, kernel_size=(3, 3),
                   input_shape=(None, 40, 40, 1),
                   padding='same', return_sequences=True))
seq.add(BatchNormalization())

seq.add(ConvLSTM2D(filters=40, kernel_size=(3, 3),
                   padding='same', return_sequences=True))
seq.add(BatchNormalization())

seq.add(ConvLSTM2D(filters=40, kernel_size=(3, 3),
                   padding='same', return_sequences=True))
seq.add(BatchNormalization())

seq.add(ConvLSTM2D(filters=40, kernel_size=(3, 3),
                   padding='same', return_sequences=True))
seq.add(BatchNormalization())

seq.add(Conv3D(filters=1, kernel_size=(3, 3, 3),
               activation='sigmoid',
               padding='same', data_format='channels_last'))
seq.compile(loss='binary_crossentropy', optimizer='adadelta')
```

### 训练网络

#### 注意：这需要花费一些时间（在我的硬件上每个 epoch 大约需要 3 分钟）

```python
# Train the network
noisy_movies, shifted_movies = generate_movies(n_samples=1200)
seq.fit(noisy_movies[:1000], shifted_movies[:1000], batch_size=10,
        epochs=20, validation_split=0.05)
```

```text
Train on 950 samples, validate on 50 samples
Epoch 1/50
950/950 [==============================] - 180s - loss: 0.3293 - val_loss: 0.6113
Epoch 2/50
950/950 [==============================] - 181s - loss: 0.0629 - val_loss: 0.4206
Epoch 3/50
950/950 [==============================] - 180s - loss: 0.0187 - val_loss: 0.2585
Epoch 4/50
950/950 [==============================] - 180s - loss: 0.0062 - val_loss: 0.2087
Epoch 5/50
950/950 [==============================] - 179s - loss: 0.0134 - val_loss: 0.1884
Epoch 6/50
950/950 [==============================] - 180s - loss: 0.0024 - val_loss: 0.1025
Epoch 7/50
950/950 [==============================] - 179s - loss: 0.0013 - val_loss: 0.0079
Epoch 8/50
950/950 [==============================] - 180s - loss: 8.1664e-04 - val_loss: 7.7649e-04
Epoch 9/50
950/950 [==============================] - 180s - loss: 5.9629e-04 - val_loss: 4.9810e-04
Epoch 10/50
950/950 [==============================] - 180s - loss: 4.8772e-04 - val_loss: 4.5704e-04
Epoch 11/50
950/950 [==============================] - 179s - loss: 4.1252e-04 - val_loss: 3.7326e-04
Epoch 12/50
950/950 [==============================] - 180s - loss: 3.6413e-04 - val_loss: 3.3256e-04
Epoch 13/50
950/950 [==============================] - 179s - loss: 3.2918e-04 - val_loss: 2.8421e-04
Epoch 14/50
950/950 [==============================] - 179s - loss: 2.9520e-04 - val_loss: 2.8827e-04
Epoch 15/50
950/950 [==============================] - 179s - loss: 2.7647e-04 - val_loss: 2.5144e-04
Epoch 16/50
950/950 [==============================] - 181s - loss: 2.5863e-04 - val_loss: 2.5015e-04
Epoch 17/50
950/950 [==============================] - 180s - loss: 2.4067e-04 - val_loss: 2.2645e-04
Epoch 18/50
950/950 [==============================] - 180s - loss: 2.2378e-04 - val_loss: 2.1206e-04
Epoch 19/50
950/950 [==============================] - 179s - loss: 2.1416e-04 - val_loss: 2.0406e-04
Epoch 20/50
950/950 [==============================] - 179s - loss: 2.0244e-04 - val_loss: 1.9820e-04
Epoch 21/50
 20/950 [..............................] - ETA: 170s - loss: 1.8054e-04


---------------------------------------------------------------------------

KeyboardInterrupt                         Traceback (most recent call last)

<ipython-input-4-5547645715ec> in <module>()
      2 noisy_movies, shifted_movies = generate_movies(n_samples=1200)
      3 seq.fit(noisy_movies[:1000], shifted_movies[:1000], batch_size=10,
----> 4         epochs=50, validation_split=0.05)


/home/valerio/anaconda3/lib/python3.5/site-packages/keras/models.py in fit(self, x, y, batch_size, epochs, verbose, callbacks, validation_split, validation_data, shuffle, class_weight, sample_weight, initial_epoch, **kwargs)
    854                               class_weight=class_weight,
    855                               sample_weight=sample_weight,
--> 856                               initial_epoch=initial_epoch)
    857 
    858     def evaluate(self, x, y, batch_size=32, verbose=1,


/home/valerio/anaconda3/lib/python3.5/site-packages/keras/engine/training.py in fit(self, x, y, batch_size, epochs, verbose, callbacks, validation_split, validation_data, shuffle, class_weight, sample_weight, initial_epoch, **kwargs)
   1496                               val_f=val_f, val_ins=val_ins, shuffle=shuffle,
   1497                               callback_metrics=callback_metrics,
-> 1498                               initial_epoch=initial_epoch)
   1499 
   1500     def evaluate(self, x, y, batch_size=32, verbose=1, sample_weight=None):


/home/valerio/anaconda3/lib/python3.5/site-packages/keras/engine/training.py in _fit_loop(self, f, ins, out_labels, batch_size, epochs, verbose, callbacks, val_f, val_ins, shuffle, callback_metrics, initial_epoch)
   1150                 batch_logs['size'] = len(batch_ids)
   1151                 callbacks.on_batch_begin(batch_index, batch_logs)
-> 1152                 outs = f(ins_batch)
   1153                 if not isinstance(outs, list):
   1154                     outs = [outs]


/home/valerio/anaconda3/lib/python3.5/site-packages/keras/backend/tensorflow_backend.py in __call__(self, inputs)
   2227         session = get_session()
   2228         updated = session.run(self.outputs + [self.updates_op],
-> 2229                               feed_dict=feed_dict)
   2230         return updated[:len(self.outputs)]


/home/valerio/anaconda3/lib/python3.5/site-packages/tensorflow/python/client/session.py in run(self, fetches, feed_dict, options, run_metadata)
    776     try:
    777       result = self._run(None, fetches, feed_dict, options_ptr,
--> 778                          run_metadata_ptr)
    779       if run_metadata:
    780         proto_data = tf_session.TF_GetBuffer(run_metadata_ptr)


/home/valerio/anaconda3/lib/python3.5/site-packages/tensorflow/python/client/session.py in _run(self, handle, fetches, feed_dict, options, run_metadata)
    980     if final_fetches or final_targets:
    981       results = self._do_run(handle, final_targets, final_fetches,
--> 982                              feed_dict_string, options, run_metadata)
    983     else:
    984       results = []


/home/valerio/anaconda3/lib/python3.5/site-packages/tensorflow/python/client/session.py in _do_run(self, handle, target_list, fetch_list, feed_dict, options, run_metadata)
   1030     if handle is None:
   1031       return self._do_call(_run_fn, self._session, feed_dict, fetch_list,
-> 1032                            target_list, options, run_metadata)
   1033     else:
   1034       return self._do_call(_prun_fn, self._session, handle, feed_dict,


/home/valerio/anaconda3/lib/python3.5/site-packages/tensorflow/python/client/session.py in _do_call(self, fn, *args)
   1037   def _do_call(self, fn, *args):
   1038     try:
-> 1039       return fn(*args)
   1040     except errors.OpError as e:
   1041       message = compat.as_text(e.message)


/home/valerio/anaconda3/lib/python3.5/site-packages/tensorflow/python/client/session.py in _run_fn(session, feed_dict, fetch_list, target_list, options, run_metadata)
   1019         return tf_session.TF_Run(session, options,
   1020                                  feed_dict, fetch_list, target_list,
-> 1021                                  status, run_metadata)
   1022 
   1023     def _prun_fn(session, handle, feed_dict, fetch_list):


KeyboardInterrupt: 
```

### 测试网络

```python
# Testing the network on one movie
# feed it with the first 7 positions and then
# predict the new positions
which = 1004
track = noisy_movies[which][:7, ::, ::, ::]

for j in range(16):
    new_pos = seq.predict(track[np.newaxis, ::, ::, ::, ::])
    new = new_pos[::, -1, ::, ::, ::]
    track = np.concatenate((track, new), axis=0)
```

