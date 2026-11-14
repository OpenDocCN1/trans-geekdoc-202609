

## 1. Assets

The following is the schema for the asset data stored in the system.

```
{
 "$class": "org.driveloop.vehicle.Vehicle",
 "vin": "4242",
 "vehicleDetails": {
 "$class": "org.driveloop.vehicle.VehicleDetails",
 "make": "fvefvsd",
 "modeType": "svsds",
 "variant": "csdcsdc",
 "chasisNumber": "sdscdsd",
 "engineNumber": "csdcsd",
 "colour": "sdcsdc",
 "manufacturingYear": "csdcsdc",
 "bodyWeight": "cdcsd"
 },
 "vehicleStatus": "UNDER_MANUFACTURER"
}
```

Fig. (14). Schema for Assets.

## 2. Manufacturer

The following is the schema for the manufacturer data stored in the system.

```
{
  "$class" : "org.driveloop.participant.Manufacturer",
  "make": {
    "$class": "org.driveloop.participant.Make",
    "name": "BMW",
    "registrationId": "asj5w67dw87wgx87x8vw"
  },
  "participantId": "9192"
}
```

Fig. (15). Schema for Manufacturer.

## 3. RTO

The following is the schema for the RTO data stored in the system.

```
{
  "$class":
  "officerName": "Mr. Joe",
  "signatureToken": "43546756545",
}
```

Fig. (16). Schema for RTO.

## 4. Dealer

The following is the schema for the dealer data stored in the system.

```
{
"$class": "org.driveloop.participant.Dealer",
"dealerName": "Man Sales",
"contact": {
"$class": "org.driveloop.participant.Contact",
"email": "mansales@gmail.com",
"address": "south district"
},
"participantId": "3888"
}
```

Fig. (17). Schema for Dealer.

## 5. Police

The following is the schema for the police data stored in the system.

```
{
"$class": "org.driveloop.participant.Police",
"officerName": "Mr. Joe",
"signatureToken": "43546756545",
"participantId": "8753"
}
```

Fig. (18). Schema for Police.

## Customer

The following is the schema for the customer data stored in the system.

```
{
"$class": "org.driveloop.participant.Customer",
"FName": "Anuranjan",
"lname": "Singh",
"contact": {
"$class": "org.driveloop.participant.Contact",
"email": "anuranjansingh@gmail.com",
"address": "ballia"
},
"participantId": "9317"
}
```

Fig. (19). Schema for Customer.

## 5 Software and Hardware Requirements

### Software Requirements

### Ubuntu 20.04

Team has chosen Linux operating system for its best support and user friendliness for this project.

### Hyperledger Fabric v0.20

It is used as a modular blockchain structure, which serves as the basis for the development of blockchain-based products, solutions and applications using plug-and-play components intended for use in private companies.

### Node JS v12.16.0-x64

It is been used to write down the backend logic _i.e_. Chain code for the automation of the transactions.

### Docker 19.03.8

It is used as a service product that uses OS-level virtualization to deliver software in packages called containers.

### Postman 7.24.0

It is used to create, share, test and document APIs. This is achieved because users can create and save simple and complex HTTP/s requests and their responses. This results in more effective and less tiring work.

### Hardware Requirements

### Processor

Intel i5-6200U / Intel Core or better.

### GPU

2.30Ghz

### Ram

8GB or more.

### Hard Disk

20GB or more.

### Input Device

Standard Keyboard, Mouse and USB.

## IMPLEMENTATION DETAILS

## Snapshots of Interfaces (shown in Figs. 20 to 27)

![](img/acd73a27093a44d669c4d9968aa1626b_150_0.png)

Fig. (20). Front Page.

There are few snapshots from our project.

The above Fig. (20) demonstrates the front page where the user can easily go to the platform and using the drive loop and different blockchain techniques, it facilitates the user for automobile registration using authentic and transparent manner.

Fig. (21) depicts the main page on which user can upload the documents of automobile and can see the all parties which were involved earlier in whole transaction before the registration of this particular vehicle. It will be able to show the whole history of automobile.

![](img/acd73a27093a44d669c4d9968aa1626b_151_0.png)

Fig. (21). Main Page.

Asset can be created by above Fig. (22) where the blocks will contain the records for automobile and whole details of all possible transactions will be stored for future purposes. This Asset will be base information and will be authenticated by all parties for transparency.

![](img/acd73a27093a44d669c4d9968aa1626b_151_1.png)

Fig. (22). Asset creation.

Above form in Fig. (23) is to show the model for manufacturer and displays the process of entering the unique and basic details of automobile by the manufacturer which will help to maintain the transparency and ease in smart contract and future transactions.

![](img/acd73a27093a44d669c4d9968aa1626b_152_0.png)

Fig. (23). Model Testing for Manufacturer.

The Fig. (24) code in Hyperledger shows the transaction history along with all necessary details for a automobile.

![](img/acd73a27093a44d669c4d9968aa1626b_152_1.png)

Fig. (24). Transaction History.

Fig. (25) runs the possible test cases and checks the right functioning of the software.

![](img/acd73a27093a44d669c4d9968aa1626b_153_0.png)

Fig. (25). Process History.

## Test Cases

To run the tests locally, we use a Docker file that builds our environment. The Docker file is shown in Fig. (26).

![](img/acd73a27093a44d669c4d9968aa1626b_153_1.png)

Fig. (26). Docker File.

We'll get a response like this if everything went nicely in Fig. (27) after running all the test cases. The sample snippets are presented for the understanding of the readers.

![](img/acd73a27093a44d669c4d9968aa1626b_154_0.png)

Fig. (27). Test cases.

## RESULTS AND DISCUSSION

DriveLoop enables all information to be accumulated into one place so that it can be easily accessed and managed. Vehicle Registration, Citations, Insurance Details and everything else accruing to the vehicle in question is integrated on this platform. So, when you log in to find out something about one particular vehicle, what you will find is everything there is to know about it. A comprehensive, all-encompassing history. Anybody who is even remotely aware of the Blockchain technology will tell you how authentic it is.

DriveLoop enables all information to be accumulated into one place so that it can be easily accessed and managed. Vehicle Registration, Citations, Insurance Details and everything else accruing to the vehicle in question is integrated on this platform. So, that when you log in to find out something about one particular vehicle, what you will find is everything there is to know about it. A comprehensive, all encompassing history. Anybody who is even remotely aware of the Blockchain technology will tell you how authentic it is. It is structured in such a way that only authorized personnel can make entries or change records. Hence, there is no need to worry about any kind of tampering with the data or falsification of information.

From our research, we implement the blockchain technology to maintain trust, security, and clarity in the system. We use many technologies and one of the technologies is IoT, Ethereum. On the basis of latency of blockchain, the throughput of blockchain, the accuracy of transactions, we test our proposed idea (Table 1).

Table 1. Comparison with existing State-of-the-Art Technologies.

| Carchain | DriveLoop (Our Application) |
|---|---|
| 1. It is used to maintain the data for rental cars. | 1. It is an automated process for buying and selling of cars. |
| 2. It uses the Ethereum platform. | 2. It uses Hyperledger Fabric platform. |
| 3. It is a public blockchain. | 3. It is a private blockchain. |

## NOVELTY AND RECOMMENDATIONS

If you have ever bought your own vehicle or have sold one, or have been a part of an automobile manufacturing or dealing at any stage of the cycle, you would be familiar with the complication that is Vehicle Registration. Given the fact that all vehicles in the market have been sold and resold as they passed through multiple hands, it becomes a cumbersome task to maintain a legitimate record of the history of each vehicle and make it available when needed.

But before we go on to talk about the problems of the process of Vehicle Registration, we first need to understand why Vehicle Registration is such an important aspect of automobile dealing. Car ownership of changes as many times as you can imagine. Whether you look at it in the terms of dealing in spare parts or in assembled vehicles, dealings by the middlemen or by the retailer who makes the final sale to a consumer, or in terms of the resale of a second-hand vehicle, there are a number of stakeholders who would very much want to know about all the history of the vehicle they are buying. Not to mention the insurance agencies, the police and other authorities and well, the government too need to keep tabs on the automobiles for various reasons.

The fact of the matter is that all these stakeholders need information about the vehicles, starting from its manufacturing story, covering its first sale, the accidents, if any, that it has been in, and any and all repairs and maintenance. This is crucial not just to maintain a track record of the vehicle in question to determine its market value, but also for legal and insurance purposes [14].

Vehicle Registration is a way to facilitate this record keeping by maintaining a link between the vehicle and its owner. It might be or not be compulsory, depending on the law of the land. This helps the authorities with regard to
