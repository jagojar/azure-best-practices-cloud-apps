# Retry strategies

### Exponential

```csharp
var random = new Random();

var delta = (int)((Math.Pow(2.0, currentRetryCount) - 1.0) *
            random.Next((int)(this.deltaBackoff.TotalMilliseconds * 0.8),
            (int)(this.deltaBackoff.TotalMilliseconds * 1.2)));
var interval = (int)Math.Min(checked(this.minBackoff.TotalMilliseconds + delta),
                this.maxBackoff.TotalMilliseconds);
retryInterval = TimeSpan.FromMilliseconds(interval);
```

### Incremental

```csharp
retryInterval = TimeSpan.FromMilliseconds(this.initialInterval.TotalMilliseconds +
                (this.increment.TotalMilliseconds * currentRetryCount));
```

### LinearRetry

```csharp
retryInterval = this.deltaBackoff;
```
