# Visa-nodered docker image environment variables

Here is some environment variables in docker-compose, that you should edit in ***[docker-compose.yml](https://raw.githubusercontent.com/Chatbots-Studio/visa-nodered-public-deploy/main/docker-compose.yml)*** : 

- **SHARED_SECRET** - shared secret for VisaAPI authorization. It can be retrieved in the personal account
- **API_KEY** - API key for VisaAPI authorization. It can be retrieved in the personal account
- **AUTH_TOKEN** - authorization key for Node-RED. Then use it in the Authorization request header. You should generate it by yourself
- **CARD_ACCEPTOR** - have 8 fields in json format  : 
  * *cardAcceptorCountry* - 3-digit alpha country code for money transfer operator.
  * *сardAcceptorZipCode* - postal code of the money transfer operator.
  * *сardAcceptorCity* - city of money transfer operator.
  * *cardAcceptorState* - state or province of the money transfer operator.
  * *cardAcceptorIdCode* - Visa Direct Originator ID
  * *cardAcceptorName* - name of the money transfer operator.
  * *cardAcceptorTerminalId* - identifier of the terminal at the place of card acceptance.
- **ACQUIRING_INFO** - have 2 fields in json format  : 
  * *acquirerCountryCode* - 3-digit numeric country code for the BIN country under which the Visa Direct solution is registered. This should correspond to the information provided during registration for the program.
  * *acquiringBin* - bank identification number (BIN) under which Visa Direct is registered. This should correspond to the information provided during registration. 
- **BUSINESS_APP_ID** - Determines the type of business applications for VisaNet transaction processing applications. For example, for money transfers : AA applies to transactions where the sender and recipient are one person, and PP applies to transactions where the sender and recipient are not one person.

# Deploy

To deploy Visa-nodered you can clone this repo or copy ***[docker-compose.yml](https://raw.githubusercontent.com/Chatbots-Studio/visa-nodered-public-deploy/main/docker-compose.yml)*** and than run 

```
docker-compose up -d
```

Or if you use docker swarm
```
docker stack deploy --compose-file docker-compose.yml visa-nodered
```

By default your application will run on port *1880*, so you shoud make requests to *http://localhost:1880*

If you want to change the port you should edit *published* in **ports** section ***docker-compose.yml***

![](https://i.imgur.com/Yh6bzKX.png)
