useEffect - works on every render

PS: it's still better if you used a library that handles it for you or at least a fetching library that supports cancellation signals like axios.



```
useEffect(() => {
    let overridden = false

    const callApi = async() => {
        const response = await ApiService.get()
        if(!overridden && response.success){
            setApiValues(response.value)
        }
    }

    callApi()

    return () => {
        overridden = true
    }
}, [setApiValues])
```

