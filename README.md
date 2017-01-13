<!-- This file was auto-generated by the 'readme' makefile target. -->

Prettyprinter à la Wadler/Leijen
================================

Master build: [![status](https://travis-ci.org/quchen/prettyprinter.svg?branch=master)](https://travis-ci.org/quchen/prettyprinter)

This module defines a prettyprinter to format text in a flexible and convenient
way. The idea is to combine a document out of many small components, then using
a layouter to convert it to an easily renderable simple document, which can then
be rendered to a variety of formats, for example plain `Text`, or Markdown.
*What you are reading right now was generated by this library (see
`GenerateReadme.hs`).*

The `wl-pprint` family consists of:

  - `wl-pprint` is the core package. It defines the language to generate nicely
    laid out documents, which can then be given to renderers to display them in
    various ways, e.g. HTML, or plain text.
  - `wl-pprint-ansi` provides a renderer suitable for ANSI terminal output
    including colors (at the cost of a dependency more).
  - `wl-pprint-compat-old` provides a drop-in compatibility layer forprevious
    users of the old `wl-pprint`. Use it for easy adaption of the new
    `wl-pprint`, but don't develop anything new with it.
  - `wl-pprint-compat-old-ansi` is the same, but for previous users of
    `ansi-wl-pprint`.

Differences to the old Wadler/Leijen prettyprinter
--------------------------------------------------

The library originally started as a fork of `ansi-wl-pprint` until every line
had been touched. The result is still in the same spirit as its predecessors,
but modernized to match the current ecosystem and needs.

The most significant changes are:

  1. `(<$>)` is removed as an operator, since it clashes with the common alias
     for `fmap`.
  2. All but the essential `<>` and `<+>` operators were removed or replaced by
     ordinary names.
  3. Everything extensively documented, with references to other functions and
     runnable code examples.
  4. Use of `Text` instead of `String`.
  5. A `fuse` function to optimize often-used documents before rendering for
     efficiency.
  6. Instead of providing an own colorization function for each
     color/intensity/layer combination, they have been combined in 'color'
     'colorDull', 'bgColor', and 'bgColorDull' functions.
