## Interpolation

![interpolation](https://github.com/voxel51/fiftyone-plugins/assets/12500356/602e1049-75d7-4b54-bc5d-9e651d39b9c3)

This plugin allows you to "interpolate" between two text prompts and see the
results in the UI.

Given a `left_prompt`, a `right_prompt`, and an interpolation strength `alpha`,
the plugin will embed the left and right prompts into $v_l$ and $v_r$ and then
sort by similarity on similarity index with selected brain key, with the query

$$v = \alpha v_l + (1 - \alpha) v_r$$

**Note:** This plugin requires a similarity index that supports prompts (i.e.
embeds text and images) to be present on the dataset. You can create one with:

```py
import fiftyone as fo
import fiftyone.brain as fob

dataset = fo.load_dataset("my_dataset")
fob.compute_similarity(
    dataset,
    brain_key="my_brain_key",
    model_name="clip-vit-base32-torch",
    metric="cosine",
    )
```

## Watch On Youtube
[![Video Thumbnail](https://img.youtube.com/vi/EQGYxPwM0pM/0.jpg)](https://www.youtube.com/watch?v=EQGYxPwM0pM&list=PLuREAXoPgT0RZrUaT0UpX_HzwKkoB-S9j&index=1)

## Installation

```shell
fiftyone plugins download https://github.com/jacobmarks/concept-interpolation
```

Refer to the [main README](https://github.com/voxel51/fiftyone-plugins) for
more information about managing downloaded plugins and developing plugins
locally.

## Operators

### `open_interpolation_panel`

-   Opens the interpolation panel on click
-   Only activated when the dataset has a similarity index

### `interpolator`

-   Runs the interpolation
