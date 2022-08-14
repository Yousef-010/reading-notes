# Reading 28 : API Deployment 


> Managing Django Settings : Issues
- Different environments.
  - Usually, you have several environments: local, dev, ci, qa, staging, production, etc
  - Each environment can have its own specific settings
  - You need an approach that allows you to keep all these Django setting configurations.
- Sensitive data.
  - You have SECRET_KEY in each Django project
  - This data cannot be stored in VCS
- Sharing settings between team members
  - You need a general approach to eliminate human error when working with the settings
- Django settings are a Python code
  - This is a curse and a blessing at the same time.
  - It gives you a lot of flexibility, but can also be a problem –
  - instead of key-value pairs, settings.py can have a very tricky logic.


> Setting Configuration: Different Approaches 
- the most popular ones to examine their weaknesses and strengths.
- settings_local.py
  - This is the oldest method. I used it when I was configuring a Django project on a production server for the first time
  - The basic idea of this method is to extend all environment-specific settings in the settings_local.py file, which is ignored by VCS.
  - Pros:
    - Secrets not in VCS.
  - Cons:
    - settings_local.py is not in VCS, so you can lose some of your Django environment settings.
    - The Django settings file is a Python code, so settings_local.py can have some non-obvious logic
    - You need to have settings_local.example (in VCS) to share the default configurations for developers



> 12 Factors 
- 12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale in the Cloud
- Codebase
- Dependencies
- Config
- Backing services
- Build, release, run
- Processes
- Port binding
- Concurrency
- Disposability
- Dev/prod parity
- Logs
- Admin processes


> Setting Structure
- Instead of splitting settings by environments, you can split them by the source: Django, third- party apps (Celery, DRF, etc.), and your custom settings.


> Naming Conventions
- Naming of variables is one of the most complex parts of development.
  - Give meaningful names to your settings.
  - Always use the prefix with the project name for your custom (project) settings.
  - Write descriptions for your settings in comments.


> Django Settings: Best practices
- Keep settings in environment variables.
- Write default values for production configuration (excluding secret keys and tokens).
- Don’t hardcode sensitive settings, and don’t put them in VCS.
- Split settings into groups: Django, third-party, project.
- Follow naming conventions for custom (project) settings.



> What Is SSH or Secure Shell Protocol 
- is a remote administration protocol that allows users to access, control, and modify their remote servers over the internet.


> How Does SSH Work 
- Windows, you will need to utilize an SSH client to open SSH connections. 
- Mac and Linux users, head over to your terminal program


> Different Encryption Techniques
- Symmetrical encryption (shared key or shared secret)
  - is a form of encryption where a secret key is used for both encryption and decryption of a message by both the client and the host 
  - Symmetric keys are used to encrypt the entire communication during an SSH session.


![image](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/symmetric-encryption-ssh-tutorial.webp)


- Asymmetrical encryption
  - Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. 
  - These two keys are known as the public key and the private key.


![image](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/asymmetric-encryption.webp)


- Hashing
  - One-way hashing is another form of cryptography used in Secure Shell Connections.
  - One-way-hash functions differ from the above two forms of encryption in the sense that they are never meant to be decrypted
  - They generate a unique value of a fixed length for each input that shows no clear trend which can be exploited


![image](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/ssh-tutorial-hash.webp)


> Session Encryption Negotiation
- algorithm works at a very basic level
    - Both the client and the server agree on a very large prime number, which of course does not have any factor in common.This prime number value is also known as the seed value.
    - Next, the two parties agree on a common encryption mechanism to generate another set of values by manipulating the seed values in a specific algorithmic manne
    - Both the parties independently generate another prime number. This is used as a secret private key for the interaction.
    - This newly generated private key, with the shared number, is used to compute a public key which is distributed to the other computer.
  

> WhiteNoise 
- WhiteNoise allows your web app to serve its own static files
- Installation
  - `pip install whitenoise`
```
MIDDLEWARE = [
    # ...
    "django.middleware.security.SecurityMiddleware",
    "whitenoise.middleware.WhiteNoiseMiddleware",
    # ...
]
```


> Resources
- https://djangostars.com/blog/configuring-django-settings-best-practices/#header6
- https://12factor.net/
- https://django-environ.readthedocs.io/en/latest/
- Two Scopes of Django
- https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work#What_Is_SSH
- http://whitenoise.evans.io/en/stable/