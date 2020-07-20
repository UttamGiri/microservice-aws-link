
THIS IS MICROSERVICE PROJECT


1) CONFIG 
   PersonalAppApiConfigServer

2) CONFIG CONFIGURATION  (IT IS CALLED INSIDE CONFIG PROJECT THIS IS NOT DEPLOYED  CONFIGURATION IS KEPT IN GIT FOR BUS/REFRESH)
  PersonalAppConfiguration

3) 
   DISCOVERY SERVICE
  PersonalAppDiscoveryService

4).  ZUUL 

  PersonalAppZuulAPIGateway

5) User micro-service

   PersonalAppApiUsers

6) Account Microservice

   PersonalAppAccount




FLOW 

Register new user

a). 
POST
54.211.111.0:8011/users-ws/users

  {

 "firstName": "Uttam",
 "lastName": "Giri",
 "password": "12345678",
 "email": "abc32@gmail.com"

}

please change email if error. Has to be unique in database.

O/p random generated useriduserid. (Random generated User id is persisted to database)

B)POST

 54.211.111.0:8011/users-ws/users/login

{
   "email": "abc32@gmail.com",
   "password": "12345678"

}

0/P. Token

C)
   GET
   54.211.111.0:8011/users-ws/users/userid-generated

  Add Header Authorization   Bearer token generated



Output should be like this

<UserResponseModel>
    <userId>c6447073-98ca-487a-89ed-387430875d41</userId>
    <firstName>Uttam</firstName>
    <lastName>Giri</lastName>
    <email>abc32@gmail.com</email>
    <accounts>
        <accounts>
            <accountId>account1Id</accountId>
            <userId>c6447073-98ca-487a-89ed-387430875d41</userId>
            <name>account 1 name</name>
            <description>account 1 description</description>
        </accounts>
        <accounts>
            <accountId>accountId</accountId>
            <userId>c6447073-98ca-487a-89ed-387430875d41</userId>
            <name>account 2 name</name>
            <description>account 2 description</description>
        </accounts>
    </accounts>
</UserResponseModel>


Account section is received from account micro services .  Connection through feign client

EUREKA DASHBOARD
http://3.215.132.252:8010/

Check zipkin dashboard
http://ec2-100-25-111-0.compute-1.amazonaws.com:9411/zipkin/

ZUUL API health
GET
54.211.111.0:8011/actuator/health

USER API health
GET
54.211.111.0:8011/users-ws/actuator/health

H2 Database
http://ec2-54-146-94-206.compute-1.amazonaws.com:43685/h2-console
uttam/giri

DB testdb




Elastic search ELK. .  it is stopped cause I have use not free t2.small space

Elastic
http://52.1.191.122:9200/

Kinana

http://52.1.191.122:5601/










  
