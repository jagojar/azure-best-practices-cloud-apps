# Retry Guidance

![Retry Guidance Table](RetryFeatures4AzureServices.jpeg)



# Transient fault handling with [Polly](https://github.com/App-vNext/Polly)
Polly is a library to programmatically handle retries and circuit breaker strategies. The Polly project is a member of the .NET Foundation. For services where the client doesn't natively support retries, Polly is a valid alternative and avoids the need to write custom retry code, which can be hard to implement correctly. Polly also provides a way to trace errors when they occur, so that you can log retries.


| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
