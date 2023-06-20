```csharp
using var httpClient = new HttpClient(handler);
httpClient.BaseAddress = new Uri(baseUrl);
httpClient.DefaultRequestHeaders.Remove(AuthorizationName);

//httpClient.DefaultRequestHeaders.Add("content-type", "multipart/form-data");

string requestUri = $"";

//var requestContent = new StringContent(content, Encoding.UTF8, "application/json");
//var requestContent = new StringContent(content, Encoding.UTF8, "multipart/form-data");

var requestContent = new MultipartFormDataContent();
requestContent.Add(new StringContent(encryptStr, Encoding.UTF8), "param");

var response = await httpClient.PostAsync(requestUri, requestContent);

response.EnsureSuccessStatusCode();

var json = await response.Content.ReadAsStringAsync();

```