# Lab6-microservices

we have to run registration, this service must be run before the other services. 

```bash
./gradlew :registration:bootRun
```
![registration log](images/registration1111)

 
Then have to run accounts and web services in two other teminals

```bash
./gradlew :accounts:bootRun
```
![acoounts log](images/accounts2222)

```bash
./gradlew :web:bootRun
```

![web log](images/web3333)


Now we can check that all services are running in `https://localhost:1111`, `https://localhost:2222` `https://localhost:3333`

![web eureca](images/registerBrowser1111)
![web service](images/accountBrowser2222)
![account service](images/webBrowser3333)

After that, we are going to register a new account service using the port 4444. To do it have to change in `accounts/src/main/resources/application.yml` the the server port,write 4444 instead of 2222. 

At this moment, we can run the following command again in other terminal:

```bash
./gradlew :accounts:bootRun
```

And we have another accounts service running:

![accouts log 4444 port](images/accounts4444)

We can check that in `https://localhost:1111`:

Now in Euroka dashboard there are 2 account service up: 

![account service 4444](images/eureka1111up2222)

But after kill the accounts service of port 2222, it dessapears from the Euroka dashboard:

![web eureka](images/eureka1111down2222)

Instead of that, the second accounts service and the web service keep running.

We can check that the second account service are running in `https://localhost:4444` that they keep working in the following screenshot:

![account service](images/accountBrowser4444)

It keep running because Eureka acts as a mediator between the web service and the accounts service, Eureka detects that the first service is dead and don't make any problem with that. 