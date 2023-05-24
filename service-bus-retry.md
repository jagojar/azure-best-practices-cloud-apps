```csharp
// using Azure.Messaging.ServiceBus;

using Azure.Messaging.ServiceBus;

string connectionString = "<connection_string>";
string queueName = "queue1";

// Because ServiceBusClient implements IAsyncDisposable, we'll create it 
// with "await using" so that it is automatically disposed for us.
var options = new ServiceBusClientOptions();
options.RetryOptions = new ServiceBusRetryOptions
{
    Delay = TimeSpan.FromSeconds(10),
    MaxDelay = TimeSpan.FromSeconds(30),
    Mode = ServiceBusRetryMode.Exponential,
    MaxRetries = 3,
};
await using var client = new ServiceBusClient(connectionString, options);

// The sender is responsible for publishing messages to the queue.
ServiceBusSender sender = client.CreateSender(queueName);
ServiceBusMessage message = new ServiceBusMessage("Hello world!");

await sender.SendMessageAsync(message);

// The receiver is responsible for reading messages from the queue.
ServiceBusReceiver receiver = client.CreateReceiver(queueName);
ServiceBusReceivedMessage receivedMessage = await receiver.ReceiveMessageAsync();

string body = receivedMessage.Body.ToString();
Console.WriteLine(body);
```

