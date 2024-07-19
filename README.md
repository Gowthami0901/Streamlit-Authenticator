# Streamlit-Authentication

Streamlit authentication refers to the process of adding user authentication to a Streamlit application. This ensures that only authorized users can access the application or specific features within it. Authentication can be achieved through various methods, such as:

1. **Username and Password**: Basic authentication where users log in with a username and password.

2. **OAuth**: Using third-party services like Google, GitHub, or Facebook to authenticate users.

3. **Single Sign-On (SSO)**: For enterprise applications, integrating with corporate SSO systems.


Streamlit itself does not have built-in support for authentication, but developers can integrate authentication using third-party libraries and services. Some common approaches include:


- **Streamlit-Authenticator**: A third-party library that provides a simple way to add authentication to Streamlit apps using hashed passwords.

- **Auth0**: A flexible authentication and authorization platform that can be integrated with Streamlit.

- **Custom Solutions**: Using Flask, FastAPI, or other web frameworks to handle authentication and then embedding the Streamlit app within the authenticated environment.



Example using `streamlit-authenticator` library:

```python
import streamlit as st
import streamlit_authenticator as stauth

# Set up the authenticator
names = ['Haritha Gowda', 'Abhitha Miller']
usernames = ['Harith', 'Abhitha']
passwords = ['XXX', 'XXX']

hashed_passwords = stauth.hasher(passwords).generate()

authenticator = stauth.Authenticate(names, usernames, hashed_passwords,
    'some_cookie_name', 'some_signature_key', cookie_expiry_days=30)

name, authentication_status = authenticator.login('Login', 'main')

if authentication_status:
    st.write(f'Welcome {name}')
elif authentication_status == False:
    st.error('Username/password is incorrect')
elif authentication_status == None:
    st.warning('Please enter your username and password')
```

This example demonstrates a simple authentication setup where users log in with predefined usernames and passwords. The `streamlit-authenticator` library handles hashing and verification of passwords.