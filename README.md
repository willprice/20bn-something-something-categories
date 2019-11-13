# 20BN Something-Something category counts

This repository contains CSVs that list classes of varying levels of granularity
and the mappings between these levels for the [Something-something](https://20bn.com/datasets/something-something) dataset.


## Class levels

- **Fine-grained classes** (mid-level): the original 174 classes released with the dataset as
  specified in [`something-something-v2-labels.json`](https://20bn.com/dataset-release/something-something/v2/labels).
- **Coarse-grained classes** (high-level): A remapping of the *fine-grained classes* into 40 classes.
- **Captions** (low level): The *fine-grained classes* are actually templates.  Templates contain 
  0 or more placeholders (surrounded by square brackets) for which the
  corresponding values are available for each instance.

---

## Fine-grained labels (mid-level)

These are the original 174 classes first described in the [dataset paper](https://20bn.com/datasets/something-something).

These are stored in the `template` field in the JSON files provided by 20BN.

## Coarse-grained labels (high-level)

There are 50 high level classes derived from all the fine-grained labels. 
`fine_to_coarse.csv` contains the correspondence between the 174 fine-grained
classes to the 50 coarse-grained classes.

These have to be mapped from the `template` field in the JSON files provided by
20BN in combination with `fine_to_coarse.csv`.

## Captions (low-level)

The fine-grained labels are actually templates parameterised with noun phrases,
for example, here is the metadata for video id 207125:

- Template: *Putting [something] onto [something else that cannot support it] so it falls down*
- Place-holders: 
  - *ice cream container*
  - *water bottle*
- Caption: *"putting ice cream container onto water bottle so it falls down"*

The template corresponds to the *fine-grained label*, and the placeholders
combined with this produce the *caption*.

In total there are 123,858 unique captions in the combined training and testing
split (9/10th of the dataset). Presumably the test set contains a reasonable
proportion more unique captions.

These are stored in the `label` field in the JSON files provided by 20BN. The
original template is stored in the `template` field and the values that have been
substituted in are stored in the `placeholders` field.

## Dataset Paper Table Reference

- Table 5: `10_class_subset.csv`
- Table 6: `40_class_subset.csv`
- Table 7: `fine_to_10_classes.csv`
- Table 8: `fine_to_coarse.csv`

## Warnings

The coarse-grained classes in `10_class_subset.csv`, `40_class_subset.csv`, and
`fine_to_10_classes.csv` are *DIFFERENT* to the coarse-grained classes in
`fine_to_coarse.csv` and `coarse_grained_classes.csv`. The paper defined two
sets of coarse-grained classes for the 10/40 class subsets and the full dataset.

---

## Attribution & References

The data contained in this repository is entirely derived from either the papers
below, or from the dataset itself.

- The original dataset paper: [The "something something" video database for
  learning and evaluating visual common sense](https://arxiv.org/pdf/1706.04261.pdf).
- A follow up paper using v2 of the dataset and the varying levels of labels:
  ["On The Effectiveness of Task Granularity for Transfer Learning"](https://arxiv.org/pdf/1804.09235.pdf)

Many thanks to 20BN for providing such an interesting dataset to work on.
