---
title: Basic Authentication
author: Adithya Vijay
date: 2022-05-24 14:00:00 +0550
categories: [Blogging, Programming]
tags: [development programming dotnet6]     # TAG names should always be lowercase
---

### Introduction
In this blog, we'll discuss about how we'll store passwords in a database, the basics of authentication and jwt tokens. Authentication is verifying that the user is who he says he is.

### How to Store passwords in a database
Password can be saved in different ways :
- Storing in clear text - Never save password in clear text
- Hashing the password - Apply a hashing algorithm to the password and storing the passwordhash in the database. You can't calculate what the password is from the hash. However, if there are 2 people with the same password then the hashes of both these passwords will be the same. If the db is compromised, the hacker can identify that both passwords are same and decrypt them via the dictionary of hashes that have already been decrypted.
- Hashing and salting the password - A salt applied to a hashing algorithm will scramble the hash. So even if 2 passwords are the same, the password hash created will be different. We also have to store the password salt in the database to decode the hash (unscramble the hash).
Simple basics authentication is implemented using password hash and salt. This is similar to the method followed in ASP.NET Identity however, it's not as battle hardened as Identity.

### JWT Token Authentication
An API is not something that we maintain a session state with. We make a request to an API, it returns the data we asked for and that ends the relationship with the API. Tokens are good to use with an API, they are small enough to send with each request.
JWT is an industry standard for tokens. They are self contained and can contain credentials, claims, and other information.
JWT has 3 parts each seperated by a '.' period
1. Header - It contains the algorithm and token type. The algorithm is used to encrypt the signature. The type of the token will be JWT
2. Payload - It contains information like claims, credentials etc. - (Roles, name identifies). It has 3 timestamps notbefore(nbf), expairy(exp), issued at(iat)
3. Signature - This signature is encrypted by the server using a private key. The only part of the token that is encrypted is the signature.

We cannot modify the token and expect the API to accept it. This will change the entire structure of the token and signature won't be verified.
The header and payload part of a JWT token can be decoded [here](https://jwt.io/)

#### Working:  

1. A user logs in and sends their username and password to the server
2. The server validates their credentials and returns a JWT token that the client will store locally on their machine. (We use browser storage to store the token)
3. JWT stored in the local machine (browser storage) is send along with all further requests.
4. Anytime we want to access something that is protected by authentiation on the server, we send the JWT token with the request. 
5. We add an authentication header to the request and then the server will verify that the token is valid. The server will have the private key that was used to encrypt the signature and can use this to verify that the token is valid (since it's stored in the server user secrets, no need for a database call)
6. Server verifies the JWT and sends back response.

#### Benifits of JWT:  

1. No sessions to manage - JWT's are self contained tokens.
2. Portable - A single token can be used with multiple backends. (Backends all share same private key)
3. No cookies required - mobile friendly (Mobile phones don't have cookies)
4. Performance - Once a token is issued, there is no need to make a database request to verify a users authentication

To add JWT to .NET Core project use the package : System.IdentityModel.Tokens.Jwt by Microsoft

Class to generate JWT Token

```
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using System.Text;
using API.Entities;
using API.Interfaces;
using Microsoft.IdentityModel.Tokens;

public class TokenService : ITokenService
{
    private readonly SymmetricSecurityKey _key;

    public TokenService(IConfiguration config)
    {
        _key = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(config["TokenKey"])); // PrivateKey
    }

    public string CreateToken(AppUser user)
    {
        var claims = new List<Claim>
        {
            new Claim(JwtRegisteredClaimNames.NameId, user.UserName)
        };

        var creds = new SigningCredentials(_key, SecurityAlgorithms.HmacSha512Signature);

        var tokenDescriptor = new SecurityTokenDescriptor
        {
            Subject = new ClaimsIdentity(claims),
            Expires = DateTime.Now.AddDays(7),
            SigningCredentials = creds
        };

        var tokenHandler = new JwtSecurityTokenHandler();

        var token = tokenHandler.CreateToken(tokenDescriptor);

        return tokenHandler.WriteToken(token);
    }
}
```

### Authentication middleware in .NET 6
To add the authentication middleware, we need to first add the package Microsoft.AspNetCore.Authentication.JwtBearer by Microsoft
Then we need to add the following in the configureservices() method in startup.cs

```
services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
                .AddJwtBearer(options =>
                {
                    options.TokenValidationParameters = new TokenValidationParameters
                    {
                        ValidateIssuerSigningKey = true,
                        IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(_config["TokenKey"])),
                        ValidateIssuer = false,
                        ValidateAudience = false
                    };
                });
```
After adding this, we need to add the useAuthorization() middleware after useAuthentication() in the configure method.
To allow only authorized users to access an endpoint, we use the Authorize attribute on the particular method.

Now to access the endpoint, we need to send the JWT token in the authorization header along with the request headers in the format ``` Bearer <jwtToken> ```.
