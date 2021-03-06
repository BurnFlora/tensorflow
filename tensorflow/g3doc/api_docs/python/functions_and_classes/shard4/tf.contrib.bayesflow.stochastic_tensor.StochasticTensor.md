StochasticTensor is a BaseStochasticTensor backed by a distribution.
- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.__init__(dist_cls, name=None, dist_value_type=None, loss_fn=score_function, **dist_args)` {#StochasticTensor.__init__}

Construct a `StochasticTensor`.

`StochasticTensor` will instantiate a distribution from `dist_cls` and
`dist_args` and its `value` method will return the same value each time
it is called. What `value` is returned is controlled by the
`dist_value_type` (defaults to `SampleAndReshapeValue`).

Some distributions' sample functions are not differentiable (e.g. a sample
from a discrete distribution like a Bernoulli) and so to differentiate
wrt parameters upstream of the sample requires a gradient estimator like
the score function estimator. This is accomplished by passing a
differentiable `loss_fn` to the `StochasticTensor`, which
defaults to a function whose derivative is the score function estimator.
Calling `stochastic_graph.surrogate_loss(final_losses)` will call
`loss()` on every `StochasticTensor` upstream of final losses.

`loss()` will return None for `StochasticTensor`s backed by
reparameterized distributions; it will also return None if the value type is
`MeanValueType` or if `loss_fn=None`.

##### Args:


*  <b>`dist_cls`</b>: a `Distribution` class.
*  <b>`name`</b>: a name for this `StochasticTensor` and its ops.
*  <b>`dist_value_type`</b>: a `_StochasticValueType`, which will determine what the
      `value` of this `StochasticTensor` will be. If not provided, the
      value type set with the `value_type` context manager will be used.
*  <b>`loss_fn`</b>: callable that takes `(dt, dt.value(), influenced_loss)`, where
      `dt` is this `StochasticTensor`, and returns a `Tensor` loss. By
      default, `loss_fn` is the `score_function`, or more precisely, the
      integral of the score function, such that when the gradient is taken,
      the score function results. See the `stochastic_gradient_estimators`
      module for additional loss functions and baselines.
*  <b>`**dist_args`</b>: keyword arguments to be passed through to `dist_cls` on
      construction.

##### Raises:


*  <b>`TypeError`</b>: if `dist_cls` is not a `Distribution`.
*  <b>`TypeError`</b>: if `loss_fn` is not `callable`.


- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.clone(name=None, **dist_args)` {#StochasticTensor.clone}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.distribution` {#StochasticTensor.distribution}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.dtype` {#StochasticTensor.dtype}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.entropy(name='entropy')` {#StochasticTensor.entropy}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.graph` {#StochasticTensor.graph}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.input_dict` {#StochasticTensor.input_dict}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.loss(final_loss, name='Loss')` {#StochasticTensor.loss}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.mean(name='mean')` {#StochasticTensor.mean}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.name` {#StochasticTensor.name}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.value(name='value')` {#StochasticTensor.value}




- - -

#### `tf.contrib.bayesflow.stochastic_tensor.StochasticTensor.value_type` {#StochasticTensor.value_type}




