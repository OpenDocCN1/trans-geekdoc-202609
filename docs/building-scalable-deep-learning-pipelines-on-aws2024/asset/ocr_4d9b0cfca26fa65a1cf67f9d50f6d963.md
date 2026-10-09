```
.collect()
		)
y_train = np.array(
			train_diabetes_df.select("Outcome")
			.rdd.flatMap(lambda x: x)
			.collect()
		)

model = Sequential()
model.add(Dense(
		64,
		input_dim=X_train.shape[1],
		activation='relu'
))
model.add(Dense(32, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

optimizer = SGD(learning_rate=0.01)
model.compile(
		loss='binary_crossentropy',
		optimizer=optimizer,
		metrics=['accuracy']
)

custom_callback = CustomCallback()
model.fit(
		X_train,
		y_train,
		epochs=100,
		verbose=0,
		callbacks=[custom_callback]
	)
```