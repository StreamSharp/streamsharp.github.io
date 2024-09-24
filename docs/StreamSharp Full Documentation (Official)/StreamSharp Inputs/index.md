# StreamSharp Inputs

StreamSharp Inputs is a subset of StreamSharp that is focused on providing the class structure required to access certain types of input (for example keys, or keys & dials). Download as many of these as required for your plugin functionality.

## List of input types
### Individual Types
??? info
    Individual types are the recommended option by the lib founder (for the most part), as they allow you to be more granular in your functionality, and allow you to have the mindset of adjusting your functionality based on the input surface you're working with.
    ??? tip
        If you are wanting to bring similar functionality to multiple input surfaces, consider using naming suffixes. Let's say you're wanting an action of `ControlInput` on both keys and encoders, then you could name the action `ControlInputKey` for keys, and `ControlInputEncoder` for dials (but this is just a guideline)

#### StreamSharp.Keypad
Focused solely on using the keys found on most (if not all) Stream Deck devices.

#### StreamSharp.Encoder
Focused solely on using the dials (and corresponding touch screen above each dial), found on the Stream Deck Plus.

### Combined Types
??? danger "Pitfalls of using combined types"
    While combined types seem useful, dependent on the way the SDK functionality is combined, this may end up merging functionality into a single action between input types. It is a trade off between centralising your code and allowing for more granular control.

    These are mostly available for compatibility purposes

#### StreamSharp.KeyAndEncoder

This combines the keys and the dials into a single format (for a single action).
???+ success "No problems here"
    There are no merged functions in this device type. It is therefore possible to maintain fully granular control over functionality for functions between keys and dials.