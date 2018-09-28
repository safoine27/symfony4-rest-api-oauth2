Simple Symfony4.1 Rest API using oauth2 secure authentification

INSTALLATION: 

1- git clone https://github.com/safoine27/symfony4-rest-api-oauth2.git

2- cd symfony4-rest-api-oauth2

3- composer install  

4- change db credentials in .env

5- run php bin/console doctrine:schema:update --force

6- run php bin/console oauth:create --redirect-uri=http://www.redirecturi.com --grant-type=password --grant-type=refresh_token
 response would be something like this:
 
 Client Credentials
==================

 ------------------------------------------------------ --------------------------------------------------
  Client ID                                              Client Secret
 ------------------------------------------------------ --------------------------------------------------
  1_5gsz0lx68wowc404g44ww40gockc8oo44sgg80g4808wsg8w8s   m37g7yxy2og8w8swcoowgw40og4w084og444g0g0g40ko40o
 ------------------------------------------------------ --------------------------------------------------

7- make a post request to the address http://127.0.0.1:8000/oauth/v2/token

   body: 
   
   {
    "grant_type": "password",
    "client_id": "1_5gsz0lx68wowc404g44ww40gockc8oo44sgg80g4808wsg8w8s",
    "client_secret": "m37g7yxy2og8w8swcoowgw40og4w084og444g0g0g40ko40o",
    "username": "the_fos_username",
    "password": "the_fosuser_password"
    }
    
    response would be something like this 
    {
    "access_token": "ZmVkNDgyMDQzYTI2MTViNDY5YzAyMWFlZTQyZjRhM2ZiNTkzNzhlMGJkZmZmMWU1YzA0NjEzZjk2YWQxYjQ0ZQ",
    "expires_in": 86400,
    "token_type": "bearer",
    "scope": null,
    "refresh_token": "MzQyNDZmNzc1NjhjNTNiNjM0NWZlZDcxZWRlNzUxZWE5ZmU5Y2UxMDZiNjUxNWZiM2Y1NTI2NzYwOGFmYTQ2Mg"
}

8- use the access token in all requests by setting it up in the header

DONE!

