
# Internal Support Application — Microsoft Entra ID Authentication

## Project Overview

This project demonstrates how to secure an **ASP.NET Core Razor Pages application** using **Microsoft Entra ID** and **OpenID Connect**.

The application authenticates users through Microsoft Entra ID, displays the authenticated user's information, and protects an Admin page using the `[Authorize]` attribute.

## Table of content

-[Authentication Flow](#Authentication-Flow)

-[Project Structure](#Project-Structure)

-[Testing Performed](#Testing-Performed)

-[Screenshots](#Screenshots)


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

<img width="734" height="458" alt="13-change index" src="https://github.com/user-attachments/assets/e0347ecb-0fdf-48a2-a1c1-1ecd3cb1b5e0" />







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

##  Screenshots


### 1. Azure App Registration

The Azure Web App was integrated with Microsoft Entra ID using OpenID Connect.

<img width="668" height="367" alt="03-app-registration" src="https://github.com/user-attachments/assets/0a34bb3b-d8ef-4d7d-9704-dddcbf0406f8" />


<img width="888" height="356" alt="04-app-overview" src="https://github.com/user-attachments/assets/af759393-2cf7-4545-9360-3d3e60ea5cf8" />



### 2. Authentication – Redirect URI 

The redirect URI was configured in the Microsoft Entra ID App Registration:

<img width="377" height="383" alt="04-redirect URL" src="https://github.com/user-attachments/assets/58e4f4ef-f530-44ca-8853-3670d51be26d" />




### 3. Microsoft Entra ID Consent

Shows the Microsoft Entra ID permission/consent screen for the application.


<img width="353" height="420" alt="05-test success" src="https://github.com/user-attachments/assets/8ddcca6f-a2d6-415c-ad2a-aa9e1d2f2197" />




### 4. Authenticated Home Page



<img width="926" height="418" alt="12-page-after" src="https://github.com/user-attachments/assets/7e78b6a6-dbc9-421c-8ed6-a332f41e7b47" />

Shows successful authentication and the signed-in user's information.


### 5. Protected Admin Page



<img width="849" height="458" alt="14-protected page" src="https://github.com/user-attachments/assets/7c4c74dc-8cee-408f-8b7b-af2e74b5da00" />


Shows the authenticated user accessing the protected `/Admin` page.


##  How to Run

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/InternalSupportApp.git
```

Navigate to the project:

```bash
cd InternalSupportApp
```


<img width="960" height="504" alt="08-powershell" src="https://github.com/user-attachments/assets/503b6c8b-322d-422a-8ff5-c5b0da5069e0" />





Run the application:

```bash
dotnet run
```

Open the application using the HTTPS localhost URL shown in the terminal.

For example:

```text
https://localhost:7198
```

<img width="960" height="324" alt="09-powershell liste" src="https://github.com/user-attachments/assets/93703c74-b2d0-4c0e-9201-d2e668a77b18" />




The protected page is available at:

```text
https://localhost:7198/Admin
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


