NOTE: the `synonym` crate is a better implementation of this idea using a proc macro. Use that!

Utility macros for newtype trait implementations.
For a type A defined via the newtype pattern by wrapping type B
(i.e. struct A(B)), if B satisfies some trait, we often want A to
satisfy the same trait for the same types by calling type B's implementation.
Rust provides no standard mechanism for doing this, so we provide these
macros for some common cases.

For every macro, the underlying type of the newtype must implement
the trait already for the appropriate types, or else an error will occur.

Note that these macros implement for `self` rather than `&self`. This is
how std::ops traits are defined. To implement an op for references to a type,
you'd need to implement the trait on the reference type itself i.e. &MyType.
That's really true for any implementation for std::ops, though, rather
than something unique to these macros.

`TODO` This is pretty well tested, but I'd clean it up a bit and ensure it's good before publishing to crates.io.
