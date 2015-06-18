# inselect-templates

Templates for [Inselect](https://github.com/NaturalHistoryMuseum/inselect).
Templates are written in [YAML](https://en.wikipedia.org/wiki/YAML).

* `Name`
Required

* `Object label`
    A string that defines how Inselect will assemble the file names of cropped
    object images and of the names shown on Object view grid.
    Text between curly braces (`{` and `}`) will be substituted with the value
    of that field for that crop.
    For example, if a template contains the fields `Specimen number` and
    `Family`, the `Object label` could be `{Specimen number}-{Genus}`.
    For an Inselect document with three crops with a `Specimen number` of `1`,
    `2` and `3` and each with a `Family` of `Coleoptera`, the saved crops would
    be called `1-Coleoptera.jpg`, `2-Coleoptera.jpg` and `3-Coleoptera.jpg`.
    * The special label `{ItemNumber}` will be substituted with the numerical
    index of that crop.
    * For fields with a `Choices with data`, the hidden data value can be
    accessed by appending `-value` to the field name.

* `Thumbnail width pixels`
    A number between 1024 and 16384 inclusive.
    **Not currently used by Inselect**

* `Cropped file suffix`
    One of `.bmp`, `.jpeg`, `.jpg`, `.png`, `.tif`, `.tiff`
    **Not currently used by Inselect**

* `Fields`
    A list of mappings for which the following can be used.
    * `Name` Required

    * `Label`
        Optional. Will be displayed in the UI instead of `Name`

    * `URI`
        Optional. Should be a valid URL.

    * `Mandatory`
        Optional. Should be either `true` or `false`. If `true` the user must
        enter a value for this field.

    * `Choices`
        A list of unique strings from which the user can choose.

    * `Choices with data`
        A list of unique strings from which the user can choose, together with
        hidden data values. 
        `Choices` and `Choices with data` are mutually exclusive.

    * `Parser`
        One of the following
        * `date`
        A string in the form `YYYY-M[M]-D[D]`.

        * `float`
        A floating point number.

        * `float_ge0`
        A floating point number is greater than or equal to zero.

        * `float_gt0`
        A floating point number that is greater than zero.

        * `four_digit_int`
        A positive  integer with exactly four digits.

        * `int`
        An integer.

        * `int_ge0`
        An integer that is greater than or equal to zero.

        * `int_gt0`
        An integer that is greater than zero.

        * `latitude`
        A latitude in one of a number of formats:
            * -41.38
            * -41.38°
            * 41.38° S
            * 41 22.8 S
            * 41 22 48 S
            * 41:22:00 S
            * 41:22:48.03
            * 41 22' 48" S
            * 41 22' 48'' S
            * 41°22'48"S
            * 41°22′48″S

        * `longitude`
        A longitude - see `latitude` for a list of acceptable formats.

        * `one_or_two_digit_int`
        A positive integer with either one or two digits.

        * `sparse_date`
        A string in one of the forms:
            * `YYYY`
            * `YYYY-M[M]`
            * `YYYY-M[M]-D[D]`

    * `Regex parser`
        A regular expression. Values that do not match the regular expression
        are considered to be invalid. `Regex parser` and `Parser` are mutually
        exclusive.
