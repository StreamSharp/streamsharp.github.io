# StreamSharp Surface Types

The StreamSharp surface types are the means in which to connect to specific types of input on a Stream Deck device.

## Surface type categories

Please note that we only list the two categories for types on this page. For more information on individual surface types, please see the navigation.

### Individual Types

Individual types are focused on a single paradigm (such as dials, keys, etc).

??? note
    Individual types are the recommended option by the lib founder (for the most part), as they allow you to be more granular in your functionality, and allow you to have the mindset of adjusting your functionality based on the input surface you're working with.
    ??? tip
        If you are wanting to bring similar functionality to multiple input surfaces, consider using naming suffixes.
        
        Let's take an example:

        - You're building an action of `ControlInput` that will use both keys and dials
            1. Use `ControlInputKey` for the keypad
            2. Use `ControlInputEncoder` for the dials
        
        Please note that this is a guideline, and you are free to approach this how you feel is best.

??? info "Does this come in StreamSharp.Base?"
    StreamSharp.Base includes all individual types by default. You will not need to download any helper modules to access these.

### Combined Types

Combined types take more than one paradigm and include them together.

??? danger "Pitfalls of using combined types"
    While combined types seem useful, dependent on the way the SDK functionality is combined, this may end up merging functionality into a single method between input types. It is a trade off between centralising your code and allowing for more granular control.

    These are mostly available for compatibility purposes

??? warning "Does this come in StreamSharp.Base?"
    Unless otherwise stated in the individual surface type page, Combined Types are in separate helper modules and will need to be downloaded separately.