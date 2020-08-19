# Add Razor Pages support to a .Net Core MVC Project
I wanted to take a default asp.net core MVC project in Visual Studio and then see if I could added razor pages support and use them both. 

I created an MVC project and compared it to a new razor project. Using insight from a  stack overflow article "[How to extend an ASP.NET Core MVC project by Razor Pages?](https://stackoverflow.com/questions/62863196/how-to-extend-an-asp-net-core-mvc-project-by-razor-pages)", I was able to successfully do just that. 

## Here is how

Using `Visual Studio`
- [x] Create a new Project
![Create a new Project](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/1.png)

- [x] Choose ASP.NET Core Web App
![Choose ASP.NET Core Web App](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/2.png)

- [x] Name the project and solution
![Name the project and solution](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/3.png)

- [x] Choose the MVC option
![Choose the MVC option](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/4.png)

The folder structure of the result:

![MVC folder structure](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/5.png)
 
Do F5 (or CTRL+F5) and you get the standard MVC rendered web pages and web app. 
![Default MVC webapp](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/6.mvcAppHomePage.png)

Add a new folder to the project and name it `Pages`
This is a razor convention. Other helpful razor information at the [MS Docs site](https://docs.microsoft.com/en-us/aspnet/core/razor-pages/?view=aspnetcore-3.1&tabs=visual-studio).

Add the line `services.AddRazorPages();` in 
```csharp
public void ConfigureServices(IServiceCollection services)
```


Add the line `endpoints.MapRazorPages();` to 
```csharp
app.UseEndpoints(endpoints => 
``` 
in  
```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
```
At this point, a razor page can be added and can be navigated to:
