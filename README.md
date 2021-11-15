# GrowPy

## Project Description

For questions and comments contact the developer directly at: <seilis@unbc.ca>.


## Installation
GrowPy is available through [PyPi](https://pypi.org/project/growpy/), and can be installed via `pip` using
```
pip install growpy
```
or 
```
pip3 install growpy
```

## Example Usage

```python
import tensorflow as tf
import matplotlib.pyplot as plt

# Constuct/Import data
x = tf.abs(tf.random.uniform((100000,1), 0, 10))
y = 500 / (1 + (500-50)/50 * tf.exp(-0.5 * x))

# Construct model
model = MaasHoffman()
optimizer = tf.keras.optimizers.Nadam()
loss = tf.keras.losses.MeanSquaredError()
model.compile(optimizer=optimizer, loss=loss)


# Train model
history = model.fit(x, y, epochs=100, batch_size=1000)

# Inspect results
print(model.weights)

fig, axes = plt.subplots(2, 1)
axes[0].scatter(x,y, alpha=0.5, s=1)
axes[0].scatter(x, model(x), alpha=0.5, s=1)
axes[0].set_ylabel('y')
axes[0].set_xlabel('x')

axes[1].plot(history.history['loss'])
axes[1].set_ylabel('MSE')
axes[1].set_xlabel('Epoch')
plt.show()
```

## License

