# In practice, if you want to annotate numeric arguments for static type checking, you have a few options:
1. Use one of the concrete types int, float, or complex—as recommended by PEP 488.
2. Declare a union type like Union[float, Decimal, Fraction].
3. If you want to avoid hardcoding concrete types, use numeric protocols like SupportsFloat, covered in “Runtime Checkable Static Protocols” on page 468.

<img width="644" alt="Screen Shot 2023-02-05 at 11 41 28 AM" src="https://user-images.githubusercontent.com/73077953/216841041-4075dffe-337b-4dfd-9223-1f9ba721598b.png">
