# Reading 27 : JSON Web Tokens JWT 

> What is JSON Web Token?
- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. 
- This information can be verified and trusted because it is digitally signed.
- JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.


> When should you use JSON Web Tokens? 
- Authorization: This is the most common scenario for using JWT.
- Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties.

> What is the JSON Web Token structure? 
- JSON Web Tokens consist of three parts separated by dots (.), which are:
  - Header
    - The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
  - Payload
    - Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.
      - Registered claims
        - These are a set of predefined claims which are not mandatory but recommended
        - Public claims:
          - These can be defined at will by those using JWTs
        - Private claims:
          - These are the custom claims created to share information between parties that agree on using them and are neither registered public claims.

  - Signature
    - To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.


> Header Example 
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```


> payload Example
```
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```


> signature Example
```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```


![image](https://cdn.auth0.com/blog/legacy-app-auth/legacy-app-auth-5.png)


> Installation & Setup 
- `pip install djangorestframework_simplejwt`
- configuration
```
  REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
}
```
- paths
```
    path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
```


> Nginx and Gunicorn work together 
- Nginx
  - is where requests from the internet arrive first. It can handle them very quickly, 
  - and is usually configured to only let those requests through, which really need to arrive at your web application.
- Gunicorn
  - translates requests which it gets from Nginx into a format which your web application can handle, 
  - and makes sure that your code is executed when needed.


> Nginx
- Nginx is a web server and reverse proxy.
- Here are a few things it’s great at:
  - Take care of domain name routing (decides where requests should go, or if an error response is in order)
  - Serve static files
  - Handle lots of requests coming in at once
  - Handle slow clients
  - Forwards requests which need to be dynamic to Gunicorn
  - Terminate SSL (https happens here)
  - Save computing resources (CPU and memory) compared to your Python code
  - And a lot more, if you configure it to do so (load balancing, caching, …)

- Things Nginx can’t do for you
  - Running Python web applications for you
  - Translate requests to WSGI



> Gunicorn 
- Gunicorn is really great at what it does! It’s highly optimized and has a lot of convenient features
- its jobs consist of:
  - Running a pool of worker processes/threads (executing your code!)
  - Translates requests coming in from Nginx to be WSGI compatible
  - Translate the WSGI responses of your app into proper http responses
  - Actually calls your Python code when a request comes in
  - Gunicorn can talk to many different web servers
- What Gunicorn can’t do for you
  - Not prepared to be front-facing: easy to DOS and overwhelm
  - Can’t terminate SSL (no https handling)
  - Do the job of a webserver like Nginx, they are better at it


> Resources 
- https://vsupalov.com/gunicorn-and-nginx/
- https://jwt.io/introduction/
- https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html
- https://vsupalov.com/django-runserver-in-production/