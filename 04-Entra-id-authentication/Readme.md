
# Internal Support Application — Microsoft Entra ID Authentication

## Project Overview

This project demonstrates how to secure an **ASP.NET Core Razor Pages application** using **Microsoft Entra ID** and **OpenID Connect**.

The application authenticates users through Microsoft Entra ID, displays the authenticated user's information, and protects an Admin page using the `[Authorize]` attribute.

## Table of content

-[Authentication Flow](#Authentication-Flow)

-[Project Objective](#Project-Objective)
##  Architecture

```text
User
  │
  │ Access Application
  ▼
ASP.NET Core Razor Pages
  │
  │ Redirect for Sign-in
  ▼
Microsoft Entra ID
  │
  │ OpenID Connect Authentication
  │
  │ ID Token
  ▼
ASP.NET Core Application
  │
  │ User Claims
  ▼
Authenticated User

        │
        ▼
   [Authorize]
        │
        ▼
   /Admin Page
(Authenticated Users Only)
```

##  Authentication Flow

1. User accesses the ASP.NET Core application.
2. The application redirects the user to Microsoft Entra ID.
3. The user signs in using their Microsoft Entra account.
4. Microsoft Entra ID authenticates the user.
5. An ID token is returned to the application.
6. ASP.NET Core creates an authenticated user session.
7. User information is retrieved from the authentication claims.
8. The `/Admin` page is protected using `[Authorize]`.

## Key Features

* Microsoft Entra ID authentication
* OpenID Connect integration
* ID token-based authentication
* Authenticated user information
* Protected Razor Page using `[Authorize]`
* Microsoft Entra ID consent flow
* Local HTTPS development
* Sign-in and sign-out functionality

## Technologies Used

* ASP.NET Core Razor Pages
* C#
* Microsoft Entra ID
* OpenID Connect
* .NET
* Visual Studio Code
* GitHub

## Project Structure

```text
InternalSupportApp/
│
├── Pages/
│   ├── Index.cshtml
│   ├── Index.cshtml.cs
│   ├── Admin.cshtml
│   ├── Admin.cshtml.cs
│   └── Shared/
│
├── wwwroot/
│
├── appsettings.json
├── Program.cs
└── InternalSupportApp.csproj
```

##  Authorization

The Admin page is protected using:

```csharp
[Authorize]
public class AdminModel : PageModel
{
    public void OnGet()
    {
    }
}
```

This ensures that only authenticated users can access:

```text
/Admin
```

## Testing Performed

### Test 1 — Microsoft Entra ID Login

Successfully redirected to Microsoft Entra ID and completed authentication.

### Test 2 — User Information

The application successfully displayed the authenticated user:

```text
Signed-in User:
app-user01@sarapreethygmail.onmicrosoft.com
```

### Test 3 — Protected Page

Successfully accessed:

```text
https://localhost:7198/Admin
```

The page displayed:

> You are authenticated with Microsoft Entra ID.

### Test 4 — Authorization

The `/Admin` page is protected with the `[Authorize]` attribute and requires authentication.

##  Screenshots

### 1. Microsoft Entra ID Consent

Shows the Microsoft Entra ID permission/consent screen for the application.

Save the screenshot in your repository as:

```text
screenshots/entra-consent.png
```

### 2. Authenticated Home Page

Shows successful authentication and the signed-in user's information.

Save as:

```text
screenshots/home-authenticated.png
```

### 3. Protected Admin Page

Shows the authenticated user accessing the protected `/Admin` page.

Save as:

```text
screenshots/admin-protected.png
```

##  How to Run

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/InternalSupportApp.git
```

Navigate to the project:

```bash
cd InternalSupportApp
```

Run the application:

```bash
dotnet run
```

Open the application using the HTTPS localhost URL shown in the terminal.

For example:

```text
https://localhost:7198
```

The protected page is available at:

```text
https://localhost:7198/Admin
```

## Skills Demonstrated

* Microsoft Entra ID
* Identity and access management
* Authentication
* Authorization
* OpenID Connect
* ID tokens and claims
* ASP.NET Core
* Razor Pages
* `[Authorize]`
* Application troubleshooting
* Azure cloud security concepts


