# AUTHORIZATIONserver_JWT_Symmetric

This is stand alone AuthorizationServer.It does require Db Repo and userdetailservice.
It uses the private key and creates token and the creates signature.


#########Password Grant Flow######


Resource server/Client is running on 9091

and autherzationserver running on 9092

'http://localhost:9092/oauth/token' with postbody with grant_type as password is sent.

The password body contains urlencodedbody params of usename,password of the user,granttype,scope

Client recives the token and client extracts the user details and finally fetches the request,if his role permits.
The rolechecking happens in ResourceWebConfig only,but Authorizaton happens in AuthorizationServer.



Sample Request for getting Token

curl --location --request POST 'http://localhost:9092/oauth/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Basic Y291cG9uY2xpZW50YXBwOjk5OTk=' \
--header 'Cookie: JSESSIONID=CC2B758F85008DA9A5E3DE9807AC463F' \
--data-urlencode 'username=admin' \
--data-urlencode 'password=admin' \
--data-urlencode 'grant_type=password' \
--data-urlencode 'scope=read write'

