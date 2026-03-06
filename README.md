<h2>Visual Studio Project Template for SkyLite Framework v 2.0.8.8</h2>

03/03/2026

This template, designed for Microsoft Visual Studio, provides the standard file and folder structure to get you started quickly.


<h3>Introduction</h3>

SkyLite is a .NET framework for rapidly building modern, data-driven web applications. It uses a server-centric model where your UI is controlled by server-side C# or VB.NET, and client-server communication is handled by a lightweight, built-in AJAX engine. This allows you to leverage your .NET skills to create responsive, interactive web pages with minimal custom JavaScript, all within the familiar Visual Studio environment.
<br>

- SKYLITE framework<br>
Platform: IIS / .Net framework 4.5 +<br>

- SKYNET framework<br>
Platform: ASP.NET Core / .NET 10<br>
Architecture: Middleware-based <br>

- Technical Documents : https://www.theskylite.com/document<br>
- Showcase Demo. Site: https://www.theskylite.com/SkyLiteProject<br>
- Download GitHub: https://github.com/hkim6000/SkyNetDemo-AspNetCore<br>

support: hkim6000@gmail.com<br><br>

<h3>Project Structure</h3>

This template has created the official SkyLite folder structure. The framework relies on these specific folders to automatically locate and link your files.

- <b>/App_Code/</b> or <b>/codes/</b>
  Place all your server-side page logic files here (e.g., MyPage.cs, MyPage.vb). Every page class MUST inherit from `skylite.WebPage`.

- <b>/appConfig/</b>
  Contains application configuration files, such as `application.cfg` for database connection strings and other global settings.

- <b>/bin/</b>
  Contains the required `skylite.dll`/'skynet.dll'. 

- <b>/data/</b>
  A general-purpose folder for data files like SQLite databases, CSVs, etc.

- <b>/htmls/</b>
  Place your optional, pure HTML files here. If a file named `MyPage.html` exists in this folder, its content will be automatically loaded as the initial body for the `MyPage` class.

- <b>/images/</b>
  Store all your image assets here.

- <b>/logs/</b>
  The framework will automatically write error logs to this directory.

- <b>/scripts/</b>
  Place all your client-side JavaScript files here. A file named `MyPage.js` will be automatically linked to the `MyPage` page.

- <b>/styles/</b>
  Place all your CSS stylesheets here. A file named `MyPage.css` will be automatically linked to the `MyPage` page.

- <b>/temp/</b>
  A directory for temporary file generation, such as reports or uploads.


<h3>Getting Started</h3>

To create your first page using this Visual Studio template:

1.  **Create the Server-Side Class:**
    - Right-click the `App_Code` folder in the Solution Explorer and select "Add" -> "Class".
    - Name it `HomePage.cs` (for C#) or `HomePage.vb` (for VB.NET).
    - Ensure the class inherits from `skylite.WebPage`.

    **C# Example (`HomePage.cs`)**
    ```csharp
    using skylite;
    using skylite.ToolKit;

    public class HomePage : WebPage
    {
        public override void OnInitialized()
        {
            // Your UI controls will be created here.
            var welcomeLabel = new Label("Welcome to SkyLite!");
            HtmlDoc.HtmlBodyText = welcomeLabel.HtmlText();
        }
    }
    ```

    **VB.NET Example (`HomePage.vb`)**
    ```vb.net
    Imports skylite
    Imports skylite.ToolKit

    Public Class HomePage
        Inherits WebPage

        Public Overrides Sub OnInitialized()
            ' Your UI controls will be created here.
            Dim welcomeLabel As New Label("Welcome to SkyLite!")
            HtmlDoc.HtmlBodyText = welcomeLabel.HtmlText()
        End Sub

    End Class
    ```

2.  **Run the Application:**
    - Set up your project in IIS as an application.
    - In Visual Studio, you can set the "Start Action" in your project properties to your page URL to debug directly.
    - Open your browser and navigate to: http://localhost/[YourAppName]/HomePage or http://localhost/HomePage

3.  **Add Interaction (Optional):**
    - Create a `HomePage.js` file in the `/scripts` folder.
    - Add a `Button` control in your `OnInitialized` method with an `onclick` event.
    - Create the corresponding public function in your `HomePage` class to handle the button click.


<h3>Key Concepts</h3>

- **Page Lifecycle (GET):** When a page is requested, the framework runs `OnLoad` (loads .html if it exists) and then `OnInitialized` (where you build your UI).
- **API Calls (POST):** Client-side JavaScript uses the built-in `$ApiRequest()` function to call public functions in your page class.
- **ApiResponse:** Server-side functions return an `ApiResponse` object, which contains commands to manipulate the page in real-time (e.g., `_ApiResponse.SetElementContents(...)`, `_ApiResponse.Navigate(...)`).

For complete documentation on all UI controls and framework features, please visit the official documentation site.

Happy Coding!
