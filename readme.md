# Add Razor Pages support to a .Net Core MVC Project
I wanted to take a default asp.net core MVC project in Visual Studio and then see if I could added Razor pages support and use them both. 

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

- [x] Add a new folder to the project and name it `Pages`
This is a Razor convention. Other helpful Razor information at the [MS Docs site](https://docs.microsoft.com/en-us/aspnet/core/razor-pages/?view=aspnetcore-3.1&tabs=visual-studio).
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/7.addPagesFolder.png)

- [x] Add the line `services.AddRazorPages();` in 
```csharp
public void ConfigureServices(IServiceCollection services)
```
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/8.addService.png)


- [x] Add the line `endpoints.MapRazorPages();` to 
```csharp
app.UseEndpoints(endpoints => 
``` 
in  
```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
```
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/9.addEndpoint.png)

At this point, a Razor page can be added and can be navigated to:
- [x] Add a new Razor page
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/10.addRazorPage.png)
results in:
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/11.pageadded.png)
basic page code:
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/12.newpagecode.png)
rendered view:
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/13.razorPageRendered.png)

## Layout

So now one may wish to use the existing layout options with the new razor pages. 
- [x] Copy the `_ViewStart.cshtml` file from the `>Views` folder to the `>Pages` folder. 
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/14.copyViewStart.png)

That will result in the following rendered html:
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/15.razorRendered.png)

IF you do not copy the `_ViewStart.cshtml` file to the `>Pages` folder, you CAN selectively apply the layout to a individual Razor files by adding the tag to page:
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/16.layoutforpageonly.png)

## Navigation

MVC
```html
<a class="nav-link text-dark" asp-area="" asp-controller="Home" asp-action="Privacy">Privacy</a>
```
vs
Razor
```html
<a class="nav-link text-dark" asp-area="" asp-page="/HelloWorld">Hello Razor</a>
```
![enter image description here](https://raw.githubusercontent.com/IvanRainbolt/AddRazorPagesToMVC/master/images/17.navrendering.png)

I create this for my own reference and hopefully others will also find it helpful.
