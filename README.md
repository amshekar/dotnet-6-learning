# dotnet-6-learning

1.	.NET MAUI (Multi-platform App UI)

2.	.NET CLI and SDK workloads (Earlier SDK is monolith now we can install only required sdk)
   ex : command dotnet workload search

3.	Language Updates
     C# 10
     Removed startup.cs and usings(i.e. implicitusings enables in csproj) and static main method

     Sample
        .net 6
         var builder = WebApplication.CreateBuilder(args);

          Net Core 3.1

        var host = new WebHostBuilder()
        .UseKestrel()
        .UseUrls("http://*:5000")
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

4. C# enhancements
	File Scoped namespace
    i.e name space level curly braces not required just use semicolon at end of name space.
     ex:
    namespace Microsoft.eShopWeb.PublicApi; //curlybracket optional just ;
    public static class ImageValidators
     {

    Global Using directives
      ex: global using system.string

    Performance updates for string interpolation by using DefaultInterpolatedStringHandler
5. WebApplication
    Microsoft dropped name core from .net 5 now in .NET 6 its called as ASP.NET 6

    Updates in ASP.NET6
      Improved performance Reduced memory for idle TLS Connectiona, Reduced memory allocation on HttpRequest.Cookies, Socket Connection overhead reduced to 30%, 50% faster Get access(HttpRequestFeature, IHttpRequestFeature, etc..)
      Blazor WebAssembly ahead-of-time (AOT) compile
    Hot Reload on web projects
    Async stream Json : Performance earlier version asp,net run time used to store or buffer the chunks  in inmemory and used to return the payload\data to client once but in .NET 6 by using IAsyncEnumerable<T>

    Async stream Json : Memory it wont buffer the chunks of data so will use less memory

    Log output with HttpLogging using UseHttpLogging() middleware for debugging in outputwindow
     var app=builder.Build();
     app.UseHttpLogging();

    MinimalAPI using MapGet, MapPost, MapPut, MapDelete
     MapGet: app.MapGet(pattern:"api/hello",handler:sayHello)
             static string sayHello()
             {
                 return "Hello";
             }
    MapGet or MapPost from Repository:
        builder.Services.AddSingleton<ToDORepository>();
        var app=builder.Build();
        app.MapGet(pattern:"todo-list/{id}", handler:([FromService] ToDORepository repo, long id)=>{
            var todoItems=repo.GetById(id);
            return todoItem is not null? Results.Ok(todoItem):Results.NotFound();
        });

6.	.NET Libraries
     Single file application:
     DateTime, TimeOnly,DateOnly
     ArgumentNullException.ThrowIfNull(lineParam) //no need of if to check is null
     Linq Updates
       *OrDefault ex FirstOrDefault() FirstOrDeefault(defaultValue:20)
        Chunk
        Zip
     Collection Updates
       PriorityQueue
       EnsureCapacity
     Threading
       Parallel.ForEachAsync


7.	Review our current project authentication, configure and configure service and swagger implementation
	JWT Or OAuth Authentication

8.	Deployment With Containers(Linux)
9.	Life Cycle
10.	Dependency Injection
11.	API Vs Micro Services
