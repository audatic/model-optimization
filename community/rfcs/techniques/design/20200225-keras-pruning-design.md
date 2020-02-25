# Keras Pruning API Design

| Status        | (Proposed / Accepted / Implemented / Obsolete)       |
:-------------- |:---------------------------------------------------- |
| **RFC #**     | [NNN](https://github.com/tensorflow/model-optimization/pull/NNN) (update when you have the PR #)|
| **Author(s)** | Sample Name (me@email.com)                           |
| **Sponsor**   | Sample Sponsor (whomever@email.com)                  |
| **Updated**   | 2020-02-25                                           |

<!-- This should be replaced with a link to the technique's overview page after launch. -->
See the initial proposal [here](https://github.com/tensorflow/model-optimization/pull/NNN) for
background and motivation for the technique.

<!-- See the technique overview page documentation template for what to consider
here. Includes potential support matrix section. -->
### API compatibility at launch
Users can apply pruning with the following APIs:

*   Model building: `tf.keras` with only Sequential and Functional models
*   TensorFlow versions: TF 1.x for versions 1.14+ and 2.x.
    *   `tf.compat.v1` with a TF 2.X package and `tf.compat.v2` with a TF 1.X
        package are not supported.
*   TensorFlow execution mode: both graph and eager
*   Distributed training: `tf.distribute` with only graph execution

### API compatibility roadmap

It is on our roadmap to add support in the following areas:
*  Minimal Subclassed model support, meaning that we automatically prune
any weights that are created inside a Keras layer (whether builtin or custom
PrunableLayer).

This is important because several critical use cases (e.g. Object Detection, BERT)
use Subclassed models today


### Public API Summary
<figure>
  <table>
    <tr>
      <th>Model</th>
      <th>Baseline {Accuracy Metric}</th>
      <th>{Accuracy Metric} with {technique} </th>
      <th>Baseline {Optimization Metric} </th>
      <th>{Optimization Metric} with {technique} </th>
      <th>{Critical Hyperparameter} </th>
    </tr>
    <tr>
      <td>{MobilenetV2 224}</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
 </table>
</figure>

## Public API Design
There are three parts of the API, pruning the model, training the model,
and exporting the model.

### Pruning the model

`
 model = tf.keras.Sequential([...])

#### Prune all layers


#### Prune some layers
##### Prune Keras functional model
#### Prune custom Keras layer

### Training the model

#### Training with custom training loop.


## Comparisons with existing TFMOT tools

1. In contrast to the Keras quantization API, pruning only acts on a single Keras
layer at a time, meaning there does not have to be a two-phase API for applying
pruning (e.g. `prune_annotate` and `prune_apply`).

2. In contrast to weight clustering, pruning has be successfully used when
training a model from scratch, as opposed to only finetuning.






