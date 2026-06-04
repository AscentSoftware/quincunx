# Are you sure?

This function asks you interactively for permission to continue or not.
You can specify a custom message before the question and also different
messages for a both a positive and negative answer.

## Usage

``` r
sure(
  before_question = NULL,
  after_saying_no = NULL,
  after_saying_yes = NULL,
  default_answer = NULL
)
```

## Arguments

- before_question:

  String with message to be printed before question.

- after_saying_no:

  String with message to be printed after answering `'no'`.

- after_saying_yes:

  String with message to be printed after answering `'yes'`.

- default_answer:

  String with answer to question, if run in non-interactive mode.

## Value

A logical indicating if answer was `'yes'`/`'y'` (`TRUE`) or otherwise
(`FALSE`).

## Details

If you run this function in non-interactive mode, you should pass an
automatic answer to `default_answer`: `'yes'` or `'no'`.
