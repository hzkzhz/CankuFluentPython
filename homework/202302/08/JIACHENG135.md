- Decorator syntax sugar
    ```python
    @alpha 
    @beta
    def my_fn():
        pass
    ```

    equals

    ```python
    my_fn = alpha(beta(my_fn))
    ```