可以使用Microsoft.AspNetCore.SignalR.Client库来实现WebSocket的重连功能。你可以在连接丢失时捕获异常并在异常处理程序中重新连接。

```csharp
using Microsoft.AspNetCore.SignalR.Client;
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        var connection = new HubConnectionBuilder()
            .WithUrl("http://localhost:5000/chatHub")
            .Build();

        connection.Closed += async (exception) =>
        {
            Console.WriteLine($"Connection closed: {exception}");
            await Task.Delay(new Random().Next(0, 5) * 1000); // 添加随机延迟，避免频繁重连
            await connection.StartAsync();
        };

        connection.On<string>("ReceiveMessage", message =>
        {
            Console.WriteLine($"Received message: {message}");
        });

        await connection.StartAsync();

        Console.ReadLine();
    }
}
```
首先创建了一个HubConnection连接对象，并且在连接断开时注册了一个Closed事件处理程序。在Closed事件处理程序中，我们输出了连接关闭的异常信息，并且重新连接了服务器。

另外，我们还可以添加一个随机延迟，避免频繁重连造成服务器负担过重。

通过以上方法，你可以实现WebSocket连接在异常情况下的自动重连功能。