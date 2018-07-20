---
title: Bbali API Reference



toc_footers:
  - <a href='https://www.bbali.io'>Documentation by bbali</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Bbali API! This documentation powers the Bbali mobile application for shared scooter rentals. Users can find scooters nearby them, rent them on-demand, and then drop them off wherever they would like. Users can signup as chargers and receive/pick-up scooters at their location for charging at a fee. Some users can sign up as delivery people and deliver scooters to people who want to use the "deliver to me" option instead of the pickup option.
Admins of the application can send free credits to users, and toggle features such as the ability for users to send share codes to friends to get free rides (as well as adjust how much they want to send in free rides). Admins can also make other users admins, block users, check users ride status/history, and edit credits. 
One of the most awesome features is that the Bbali app is also a crypto wallet for Bitcoin and Ether. Users can get paid as mechanics, delivery people and chargers in crypto. Riders can optionally pay for rides in crypto. Ride credits are also transferable and can be converted into crypto and sent off-platform.

This API will be written in Node.js with Mongo database.


# User Stories

Bbali is a super-easy-to-use application for renting electric scooters.

You can either

A) walk up to a scooter, scan it’s QR code to unlock it, and ride it as long as you would like

B) Order a scooter to be delivered to you

C) see a map of nearby scooters and rent the one nearest to you before you reach it

———

Unique aspects of the mobile application:

During promotional periods, new users get $5 (or equivalent in local currency) in rental credits

Every user gets a unique promotional link. When friends they refer sign up with their special link or promo code, the referrer gets $5 in free ride credits and so does their friend, after the friends first ride.

Users signup in the app and become chargers, mechanics and/or delivery people. All payments are in cryptocurrency. Users can pay for rides with cryptocurrency (bitcoin or ether) or send crypto outside the app to crypto exchanges (for conversion to cash), cold storage (For saving off the platform) or other users.

Here are some typical user scenarios:

## The new college student male user
Happy during first-time use because the signup process automatically picks up his phone number and all he has to do is create a password. There is also the option to signup with email, but he prefers to easier process, but likes the option. After signing up he can optionally add a name. He accepts the terms of service which highlight Bbali is not liable for any accidents or scooter defects.

He immediately sees scoooters nearby. Selects one, sees its specs including max speed of 30km per hour. He reserves the scooter for 2 hours since paying as you go is a bit more expensive. The app tells him just one more step before confirming his pickup.

Fortunately he already has Android Pay on his phone and just accepts apps permission to use that option instead of scanning a credit card or using crypto, such as bitcoin or ethereal.

There are instructions that his scooter is near a bike rack he knows near a nearby parking lot. He is informed that he has 30 mins to get to the scooter and unlock it or his reservation will be cancelled.

He heads to the scooter and upon reaching it, he simple clicks the QR code button at the upper right on each screen. He scans the QR on top of the scooter. The app gives him the temporary passcode for that scooter that has a 30 second timer before new code is generated. He punches the code into the scooter and it’s unlocked. When he scanned the QR code, he gets a push notification that his ride has started. The default screen once he finishes reservation is the how to use screen.

He is surprised how easy it is to use. He rides for 10mins to his girlfriend’s dorm. When he reaches her dorm he parks it in her hallway because it’s so easy to fold and bring up stairs. He clicks the lock button. After talking for a bit they head to a nearby parking lot and ride it around switching use after unlocking it with the timed unlock code in the app.

After 1 hour, he is finished and clicks end ride. He is notified that he can get 1 dollar off if he returns it to a nearby Bbali shop. He prefers not to, parks it where he is, and clicks checkout in the app. That’s the default screen whenever he opens the app when he is riding. Also while riding, the checkout button has replaced the QRcode button that used to be on each screen

After checking it out, he receives a push notification with a link to a receipt as well as the option to rate his ride. He gives it 5 stars. The app also reminds him that he gets a 5 dollar credit when he refers the app to his friend. He asks his girlfriend to signup. She does and she uses his promo code when signing up. She automatically gets 5 credits. She add bitcoin as her payment option, loads 25 bucks which is the minimum deposit amount and starts her ride to her friends apt. When she does, her boyfriend gets a push notification that he has received 5 bucks in credits. The next time he rides, it lets him know the credits will be used as default payment method and remainder will be applied to his Android Pay account.

The next time he rides, he books a scooter for a whole day. However at the end, he his card can’t process the payment. He ends his ride and he is sent a push notification. After that he tries to reserve again but it asks him to confirm payment for his last trip or add a new payment option. The only thing originally charged came from the 10 dollar authorization that’s made each time a user checks in to a vehicle.



## The couple that rents at the park at a Bbali popup shop

A couple is walking through a park seeing a bunch of people having fun riding around on scooters. They see a Bbali popup stand where people wearing Bbali T-shirts are standing around.

It says 5 bucks an hour. They show their ids to the staff and pay 5 bucks. They download the app and quickly signup. The staff sends 5 bucks to their accounts. Because credits are sent from an admin, their ride does not require them authorize a payment method.

The staff scans the scooters with their phones and they are off to ride. They ride a bit longer than expected and pay when they return for the extra time and the amount is credited in credits to their account which immediately are used to cover cost of their ride.

They are also informed they can do anytime and don’t need to return to shop if they authorize a payment method in the app and pickup a scooter from another location.

They are also advised to share with friends so they can get more credits for rides




## The babysitter turned charger/delivery person

When passing by a Bbali scooter rental shop, she sees a sign saying “earn cryptocurrency charging and riding scooters”

She walks into a shop and a staff member gets her email, sending her an e-brochure about signing up to be a charger and delivery person.

She downloads the app, signs up and sees the option in the menu called become a charger. She can optionally apply with a message and enters a code she got from the staff member. She does same for “become a delivery person”
When applying to be a charger it prompts her to enter the address and confirm on a map her home address where people can charge their scooters.
A few hours later she gets an email requesting info such as her license photo. After sending she gets an email and push notification that she has been both approved as delivery person and charger.

1 hour later, she gets a ping that there is a drop off opportunity. She clicks the accept button immediately, beating the other potential candidates. She sees its 5 bucks when it’s delivered. She walks 200 kilometers to where the scooter is. She scans the qr and gets the unlock code.

She drives the scooter. The person requesting the scooter gets a notification both when the scooter is picked up as well as when they are driving to them, receiving estimated times based on the persons distance from their location and scooter speed.

When she arrives, the person requesting its phone or email pops up and calls to let them know it’s delivered. She also marks it delivered in the app with a description of where exactly it is. The app also gets her geolocation for where the drop off is.

The ordering user goes to pickup the scooter and enters the pickup code from the app on the scooter to unlock and start their ride. The user also rates the delivery which affects which delivery people get a notification first.

Later, the pickup person, because their charger status is flipped on, gets a notication that a scooter needs to charged. She goes to pick it up, charges at her home and then returns it where she got it from or a shop. She gets 2 bucks for every vehicle she recharges. That she picks up, and 50 cents for ones that are delivered to her by riders to charge. Riders get a 1 buck discount when they drop off scooters that need a recharge (Under 15 percent battery life or less)




## The crypto enthusiast

Though he doesn’t care about riding scooters he is part of the crypto movement and supports anything that accepts crypto.

After signing up he loads bitcoin and ether to his account.

He goes around referring friends to use his promo code. Each time after they complete their first ride worth 5 bucks or more, he gets credits, he converts them to ether and sometimes transfers ether from the app to other friends for them to use the app. Sometimes he sends to an external crypto exchange to convert to cash.

 When he converts credits to crypto his conversion spread is 10 percent below market price because risk bbali takes due to possible refunds by friends and price volatility considerations.


## The techie turned Bbali mechanic

A techie walks by a Bbali store and sees he can become a mechanic.
He applies through the menu option in the app

He gets email with trading video and takes an online quiz
Upon completion, whenever his status is set to available, he gets push notifications. When he accepts a fix request, he goes to location, performs fixes on spot or takes to shop

After he fixes he marks scooter as repaired in the app or brings to Bbali shop. Fix materials are provided by Bbali. When starting repair he selected estimated fix time.

Once he returns it to Bbali shop and admin confirms as fixed, he gets 10 usd in the app in form of ether which he can convert to ride credits or transfer off the platform.




## The regular business man user who goes to and from work to lunch

A man who works for national tax service likes to do fun activities with his employees. He has the Bbali app and occasionally uses scooters to go to and from lunch or home.

He clicks the deliver to me option and selects that he wants 6 scooters delivered.

A delivery person who has car is notified and picks up the 6 scooters after the mans payment is authorized for all scooters.

The man gets a notification when the scooters are delivered. 
Each person downloads the app and scans the vehicles to ride after adding payment and agreeing to liability terms. One scooter is not charged and delivery person charges it at location... he had already been doing so in car.

One person backs out and the scooter is then available on the map for people at rent that are not in group after 30 mins.








# Vehicles

## Get Nearby Vehicles

This endpoint retrieves all vehicles nearby.

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "2 vehicles nearby",
  "data"
    [
      {
        "id": 1,
        "name": "463D3",
        "type": "adult-scooter",
        "charge": .5,
        "status": "available"
      },
      {
        "id": 2,
        "name": "463D3",
        "type": "adult-scooter",
        "charge": .6,
        "status": "being-repaired"
      }
  ]
}
```



### HTTP Request

`GET https://api.bbali.io/vehicles/nearby`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
lon | required | Longitude of user
lat | required | latitude of user
range | optional | Set to 5 by default (5 kilometers)







## Rent Vehicle

This endpoint allows a user to rent a vehicle

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "vehicle 57635JS rented",
  "data":
    
      {
        "id": 1,
        "name": "463D3",
        "type": "adult-scooter",
        "charge": .5,
        "status": "available",
        "unlockCode":"2387"
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/vehicles/rent`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | User authenication token
paymentMethod | required | ID of users payment method
vehicleName | required | Unique Identifier name of the vehicle
pickupLat | optional | Latitude of user at pickup location
pickupLon | optional | Longitude of user at pickup location
deductCredits | optional | Set by user, defaults to true, and if true the rental credits will be used towards this ride
type | required | minutely-on-demand, hourly, daily, weekly, monthy
duration | optional | if not minutely-on-demand, user sets the amount of time they are booking rental for
fromShop | required | if true then they are renting from a shop and must return to the shop






## Report Vehicle

This endpoint allows a user send information about an issue with a vehicle, such as no battery charge, not running, scratches, or other infomration

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "vehicle report posted",
  "data":
    
      {
        "users message": "x is the problem or whatever user sent",
        "vehicleId": "463D3",
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/vehicles/report`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | User authenication token
userEmail | required | email of user
msg | required | message from user describing problem
type | optional | damage, emptybattery, doesntcharge, lost, stolen, cantcheckin, cantcheckout, gotinaccident, confiscatedbyauthorities
userLat | optional | Latitude of user at pickup location
usersLon| optional | Longitude of the user whre they sent the message
vehicleName | optional | Unique identifier of the vehicle being written about



## Checkout of Vehicle

This endpoint allows a a user to complete their ride by that vehicles unique name, locking it

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "vehicle successfully checked out. Ride completed",
  "data":
    
      {
        "totalCharge": "5500",
        "currency": "KRW",
        "estimatedBatteryLife":.56,
        "methodUsedType": "ether",
        "paymentIdentifier": "xxxx hf749",
        "duration": "1.2 hours"
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/vehicles/checkout`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | User authenication token
vehicleName | required | unique identifier of vehicle
userLat| required | lat of user finishing their ride
userLon | required | long of user finishing their ride
userLat | optional | Latitude of user at pickup location



## Lock Vehicle

This endpoint allows a a user to lock the vehicle and the vehicle is still not rentable by other users. Status is changed to locked, but no available as it is when there is a checkout

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "vehicle successfully locked",
  "data":
    
      {
        "currentCharge": "5500",
        "currency": "KRW",
        "estimatedBatteryLife":.56,
        "duration": "1.2 hours"
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/vehicles/lock`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | User authenication token
vehicleName | required | unique identifier of vehicle
userLat| required | lat of user finishing their ride
userLon | required | long of user locking their vehicle
userLat | optional | Latitude of user at pickup vehicle















# Users



## Register User

This endpoint creates a user and returns their unique identifier for future calls authenticating user. Users can load funds optionally through bitcoin or Ether, and if they become a charger, delivery person or mechanic and this is where they will recieve crypto

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "user account successfully created",
  "data":
    
      {
        "userEmail": "mike@bbali.io",
        "userPhone": "+82 10278532534",
        "userAuth":"HDKJHD32328HDHD455DS",
        "bitcoinAddress":"HZTpqdYkRDahk95ZqBjUR82kBdFVPET3n",
        "etherAddress":"0xed7dBeb7998Ec79D99379dA81c4b54f74abc69d4"
        
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/users/create`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | optional (if phone is register) | User email
phone | optional (if email) | User phone (includes + area code then space and then phone number eg +82 1027853254)
fullName | required | first and last name of user
password | required | user password
userLat | optional | Latitude of user signing up
userLon | optional | Longitude of user signing up
selectedLanguage | optional | Defaults to English





## Login User

This endpoint logs in a user

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "user account successfully created",
  "data":
    
      {
        "currentStatus": "riding",
        "status": "notsuspended",
        "userAuth":"HDKJHD32328HDHD455DS",
        "language":"English"
        
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/users/session`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | optional  | User email
phone | optional (if email, user only has email registered) | User phone (includes + area code then space and then phone number eg +82 1027853254)
password | required | user password
userLat | optional | Latitude of user logging in
userLon | optional | Longitude of user logging in






## Edit User

This endpoint allows user to edit their information in the settings screen

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "user account successfully updated",
  "data":
    
      {
        "email": "mike@bbali.io",
        "passwordHash": "27732JHDJHA23272372232322dsadsd2d",
        "phone":"+82 1027853256",
        "language":"English",
        "allOtherPrefs": {}
        
       
      }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/users/edit`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token in otder to make change
email | optional  | User email
name | optional  | User name if not blank
language| optional  | If user wants to change language
phone | optional  | User phone update if not blank
password | optional | user password if not blank
userLat | optional | Latitude of user editting
userLon | optional | Longitude of user editting
isCharger | optional | toggles off charger or on user as charger if they were approved
isMechanic | optional | toggles of mechanic mode or on user as mechanic if they were approved
isDelivery | optional | toggles of "I'm a delivery person" or on user as delivery person if they were approved




## Forgot User Password

This endpoint accepts an email address and sends a reset link to the user if the user account exists

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "E-mail sent with reset instructions",
  "data":
    
      {
        "email": "mike@bbali.io",
        
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/users/forgotPassword`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | required | User email 



## Reset User Password

This endpoint receives a new user password and the token created by the forgot password enpoint that is only shared to a user's email and stored server-side

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Password successfully changed",
  "data":
    
      {
        "email": "mike@bbali.io",
        
       
      }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/users/resetPassword`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
resetToken | required | Forgot password reset token that was sent in the link URL of a user's inbox message
newPassword | required | User's new password




## Deactivate User Account

This endpoint allows user to deactivate account. They can still login and change this later. If they are a charger, mechanic, or delivery person then they can't be reached about events associated with those special accounts

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "user account successfully deactivated",
  "data":
    
      {
        "userAuth": "sjhfsdhjsd3443",
       
        
       
      }
   
}
```



### HTTP Request

`POST https://api.bbali.io/users/deactivate`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token in otder to make change













# Rides





## Start Ride

After a vehicle is rented, immediately a create ride is called

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Ride successfuly started",
  "data":
    
     {
      "rideId":"34778438743",
      "timstamp": "2017-03-12 07:15:20 GMT",
      "vehicleName":"55423JU",
      "unlockCode":"1375"
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/rides/start`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token 
vehicleName | required  | unique identifier of the vehicle being rented,
userLat | optional | Latitude of user creating ride
userLon | optional | Longitude of user creating ride



## End Ride

After a vehicle is checkedout, immediately a end ride is called, as a double confirm, because the checkout vehicle endpoint should do mostly what this does to the database

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Ride successfuly ended",
  "data":
    
     {
      "rideId":"34778438743"
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/rides/end`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token 
vehicleName | required  | unique identifier of the vehicle being checked out,
userLat | optional | Latitude of user creating ride
userLon | optional | Longitude of user creating ride






## Get Rides History

This endpoint allows user to view

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "85 rides in your history",
  "data":
    
      [
        {
          "rideId":2818128,
          "duration":"5.4 hours",
          "paymentMethod":"Android Pay",
          "paymentIdentifier":"3473474dfsdf3443",
          "costOfRide":25500,
          "currency":"KRW",
          "paymentStatus":"pending",
          "vehicleName":"KDG37D",
          "vehicleType":"adultscooter",
          "timstamp": "2017-02-12 05:15:20 GMT",
          "status":"in transit",
          "dropOfAddress":"",
          "pickupLat":37.2233232,
          "pickupLon":102.3223322,
          "dropOffLat":0,
          "dropoffLon":0,

        },
        {
          "rideId":3818125,
          "duration":"5.4 hours",
          "paymentMethod":"Android Pay",
          "paymentIdentifier":"5473474dfsdf3443",
          "costOfRide":25500,
          "currency":"KRW",
          "paymentStatus":"completed (approved)",
          "vehicleName":"7DG374",
          "vehicleType":"adultscooter",
          "timstamp": "2017-03-12 07:15:20 GMT",
          "status":"complete",
          "dropOfAddress":"74 Samobon-ro Seoul, KR",
          "pickupLat":37.2233232,
          "pickupLon":102.3223322,
          "dropOffLat":37.2233232,
          "dropoffLon":102.3223322,
        }

      ]
   
}
```



### HTTP Request

`GET https://api.bbali.io/rides/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token to get their ride history




## Rate Ride

This endpoint allows user to view

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Ride successfuly reviewed",
  "data":
    
     {
      "rating":4.3,
      "review":"I liked my ride",
      "reviewId":236237,
      "timstamp": "2017-03-12 07:15:20 GMT"
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/rides/review`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required  | user's authentication token 
rideId | required  | ID of ride
vehicleName | required  | unique identifier of the vehicle being rated,
starRating | optional| 1-5 float rating
textRating | optional| text about the ride or story about ride
userLat | optional | Latitude of user leaving review
userLon | optional | Longitude of user leaving review











#Notifications


## Send All User Notification Within GeoFence

Only can be created by development/operations team and not admins, either automated or manual, for both Apple and Android

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Notification Sent",
  "data":
    
     {
      "notifcationId":"34778438743",
      "timstamp": "2017-03-12 07:15:20 GMT",
      "numberOfUsersReached":8374
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/notification/send`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
notificationAuth | required  | special, secret auth code for sending these kinds of notifications
msg | required | message that's going to users
title | required | title of message that's going to users
centerLat | required | latitude center point of the notification geofence
centerlongitude | required | longitude center point of the notification geofence
radius |optional| defaults to global or 20,000 kilometers
type |optional| defaults to all user types, but can be set to be only users that are "mechanic", "admin", "riders" (all users), "currentRiders" (people on a trip at the moment), "charger" etc  
emailAsWell|optional|set by default to false but if true also send the message as an email
androidAuthCredentials|required| Android credentials tied to app in order to send notification
appleAuthCredntials | required| Apple credentials tied to app in order to send notification



# Chargers




## Apply To Become Charger

API call allows a user to apply to become a charger at their location. 

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Application Sent",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT",
     
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/chargers/apply`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
email | required | user's email
userLat | required | location of user's charger location
userLon | required | longitude location of user's charger location
address | required | longitude location of user's charger location
description | optional| description of the charging facility







## Change Charger Status

If user is approved by admin as a charger, then they can set their status to on or off (meaning they are available at the moment or not available regarding accepting vehicles to charge)

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Status updated",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT",
      "status":"available",
      "numberVehiclesCurrentlyCharging":2,
      "capacityLeft":3
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/chargers/status`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
status | required | available, unavailable, permanently closed, full, notfullanymore
capacity |optional | if not blank then the change in capcity for how may they can charge at one time at the current location
vehicleName |optional| if they are updating status with a particular vehicle they are charging
newLat | optional| if the charger address changes
newLon| optional | if charger address changes
newaddress | optional| if charger address changes
newdescription | optional| description of the charging facility if the facility has changed or location has changed








# Mechanics

## Apply To Become Mechanic

API call allows a user to apply to become a charger at their location. Users dont have static locations but when broken vehicles are near them a notification might be sent with opportunity to fix a vehicle if user reports a vehicle as broken or in accident

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Application Sent",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT"
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/chargers/apply`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
email | required | user's email
userLat | required | location of user
userLon | required | longitude location of user
address | required | longitude location of user
description | optional| description of the users capabilities







## Change Mechanic Status

If user is approved by admin as a charger, then they can set their status to on or off (meaning they are available at the moment or not available regarding accepting vehicles to charge)

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Status updated",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT",
      "status":"available",
      "numberVehiclesCurrentlyCharging":2,
      "capacityLeft":3
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/chargers/status`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
status | required | available, unavailable, permanently quiting, oncall, workingOnVehicle
vehicleName |optional| if they picking up a particular vehicle to fix
lat | optional| user's lat during update
lon| optional | user's lon during update






# Delivery

When someone create a ride, they can request "deliver to me" as an option. Notifications go out to these delivery people within a 10 kilimoter radius, who can then use the app to find a vehicle, unlock it without charge, and take it to a user's location. These endpoints define how that should be handled.


## Apply To Become Delivery Person

API call allows a user to apply to become a delivery person for review by admins

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Application Sent",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT"
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/delivery/apply`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
email | required | user's email
userLat | required | location of user
userLon | required | longitude location of user
address | required | longitude location of user
description | optional| description of the users availability







## Change Delivery Person Status

If user is approved by admin as a delivery person, then they can set their status to on or off (meaning they are available at the moment or not available regarding picking up and delivering vehicles to users). This endpoint is also used if they accept a request to pickup for somone

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Status updated",
  "data":
    
     {
    
      "timstamp": "2017-03-12 07:15:20 GMT",
      "status":"available",
      
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/delivery/status`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
status | required | available, unavailable, permanently quiting, headingToVehicle, deliveringVehicle
vehicleName |optional| if they picking up a particular vehicle to deliver
lat | optional| user's lat during update
lon| optional | user's lon during update







## See pending delivery requests

If user is approved by admin as a delivery person,they can see pending requests for people wanting a vehicle delivered to them

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Status updated",
  "data":
    
     [
        {
         
           "timstampRequested": "2017-03-12 07:15:20 GMT",
           "lon":47.233223,
           "lat":-100.332
           "address":"82 Sambong-ro, Seoul, KR",
           "type": "adultscooter",
           "descriptionOfWherabouts":"Information provided by user of where to drop of scooter",
           "userContactInfo":"email or phone of user who is getting vehicle for delivery person to call"
           
        },
        {
         
           "timstampRequested": "2017-03-12 08:15:40 GMT",
           "lon":46.233223,
           "lat":-110.332
           "address":"82 Sambong-ro, Seoul, KR",
           "type": "moped",
           "descriptionOfWherabouts":"Information provided by user of where to drop of scooter",
           "userContactInfo":"email or phone of user who is getting vehicle for delivery person to call"
           
        }
      ]
   
}
```



### HTTP Request

`GET https://api.bbali.io/delivery/opportunities`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
status | required | available, unavailable, permanently quiting, headingToVehicle, deliveringVehicle
lat | required| delivery person lat
lon| required| delivery person lon
radius |optional | in kilometers the radius the user is open to going from their current location to deliver




# Credits

User's automatically get 5,000 KRW (or $5 depending if they are outside of Korea), when they sign up if that feature is on (controlled by admins). If a user recieved credit from admin, these credits are transferrable. If they received credits from signing up or from referral, these credits are not transferrable. If user uses a promo code when signing up, then they do not get the default signup credits if that feature is activated.


## See available credits

API call allows a user to see how much in curency they have available in free ride credits

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have 5,000 KRW in credits",
  "data":
    
     {
    
      "creditsAmount": "5000",
      "currency":"KRW",
      "conversionToUSD": 4.45
      
    }
   
}
```



### HTTP Request

`GET https://api.bbali.io/credits/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
lat | optional| user's lat when making request
lon| optional | user's lon when making request


User's automatically get 5,000 KRW (or $5 depending if they are outside of Korea), when they sign up if that feature is on (controlled by admins). If a user recieved credit from admin, these credits are transferrable. If they received credits from signing up or from referral, these credits are not transferrable. If user uses a promo code when signing up, then they do not get the default signup credits if that feature is activated.



## Send Credits

API call allows a user to send credits that they received from an admin. Also sends a push notification and email to recieving user. If email is not a user, it still sends email with a promo code the user can unlock the credits with when they sign up

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Credits sent",
  "data":
    
     {
    
      "creditsAmount": "5000",
      "currency":"KRW",
      "conversionToUSD": 4.45,
      "recievingUserHasAccount": false
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/credits/send`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
toUserEmail | required (if not sending phone number) | the receiving user's email
toUserPhone | required (if not sending email) | the receiving user's email
lat | optional| user's lat when making request
lon| optional | user's lon when making request





# Referral Codes



## Create Referral Code

Code is created for each user when they first click the refer your friends button in the application

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Referral code successfully created",
  "data":
    
     {
    
      "code": "4K49U",
      "createdWhileReferFriendOn":true,
      "amountAssociatedWithCode":5000,
      "currency":"KRW"
    }
   
}
```



### HTTP Request

`GET https://api.bbali.io/referral/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
lat | optional| user's lat when making request
lon| optional | user's lon when making request





## Use Promo Code

API call allows a user, after signing up, to add a referral code to their account

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Promo successfully code applied to your account",
  "data":
    
     {
    
      "creditsAmount": "5000",
      "currency":"KRW",
      "conversionToUSD": 4.45
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/referral/usecode`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
code | required | the 6-character referral code being used
lat | optional| user's lat when making request
lon| optional | user's lon when making request





# Payments



## Add Payment Method

API call that creates a payment method for a user

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Payment Method successfully added",
  "data":
    
     {
    
      "encryptypedNumbers": "4K49USHD3282388232",
      "identifier":438834
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/paymentMethod/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
type | required | CreditCard, ApplePay, AndroidPay
credentials1 | required | Credit card number, Apple Pay Token, Android Pay token
credentials2 |optional if not credit card | If credit card, expiration date (e.g. 12/22)
credentials3 |optional if not credit card | CCV
credentials4 |optional if not credit card | billing country
credentials5 |optional if not credit card | billing address
credentials6 |optional if not credit card | billing city
credentials7 |optional if not credit card | billing name
credentials8 |optional | billing postal (post people dont know their zip and its not required in Korea)
lat | optional| user's lat when making request
lon| optional | user's lon when making request






## Update Payment Method

API call allows user to update credit card information ,remove payment method, or set as default

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Payment Method information successfully updated",
  "data":
    
     {
    
    
      "identifier":438834
      
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/paymentMethod/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
paymentMethodIdentifier | required | user's payment method identifier
credentials1 | optional if its not thing being updated | Credit card number, Apple Pay Token, Android Pay token
status | optional if its not thing being updated | default, notdefault, remove
credentials2 |optional if not credit card | If credit card, expiration date (e.g. 12/22)
credentials3 |optional if not credit card | CCV
credentials4 |optional if not credit card | billing country
credentials5 |optional if not credit card | billing address
credentials6 |optional if not credit card | billing city
credentials7 |optional if not credit card | billing name
credentials8 |optional | billing postal (post people dont know their zip and its not required in Korea)
lat | optional| user's lat when making request
lon| optional | user's lon when making request




## Authorize Payment Method

API call is made when user is booking a ride and authorizes the default or selected payment method for  10,000KRW (or $9 if outside Korea). If this fails, user is asked to try another payment method.

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Payment Method successfully authorized for your trip",
  "data":
    
     {
    
    
      "identifier":438834
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/paymentMethod/authorize`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
paymentMethodIdentifier | required | user's payment method identifier
lat | optional| user's lat when making request
lon| optional | user's lon when making request




## Send Cryptocurrency

API call allows a user to send bicoin or ether from their account to another user or cryptocurrency address

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Ether successfully sent",
  "data":
    
     {
    
    
      "transactionID":"0x3453455342dfgfgddgf55445",
      "confUrl":"https://etherscan.com/tx/345534453sfssdf344et435534",
      "transactionFee":".0001 BTC"
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/payments/sendCrypto`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
toAddress | required if user email not set | the address the payment is being sent to
toEmail | required if toAddress not set | the email of another bbali user the payment is being sent to
amount | required  | amount of crypto the user is sending. Must have this amount plus the miner network transaction fee to send
type | required  | either bitcoin or ether





## Convert Credits/Crypto

API call allows a user to convert bitcoin/ether into ride credits or ride credits into bitcoin or ether

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Conversion successful",
  "data":
    
     {
    
    
      "transactionID":"0x3453455342dfgfgddgf55445",
      "confUrl":"https://etherscan.com/tx/345534453sfssdf344et435534",
      "transactionFee":".0001 BTC",
      "conversionRateAtExecution":"520 USD/ether"
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/payments/convertCrypto`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
startCurrency | required  | KRW, USD, BTC or ETH
endCurrency | required | KRW, USD, BTC or ETH
amount | required | how much of the base currency they are converting






# Admin



## Make Admin
When first user creates an account on the application that user is set as admin and can give admin permissions to future users

API call allows one user to make another user an admin if they are an admin

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully updated user #48348 to an admin account",
  "data":
    
     {
    
      "usersId": "4K49USHD3282388232",
      
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/admin/makeAdmin`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
toUsersEmail | required, if no phone | email of user being made admin if no phone is provided
toUsersPhone | required, if no email | phone of user being made admin if no phone is provided






## Send Credit

API call allows admins to send credits to users. Admins do not need credits in their accounts to send credits. Max credit a admin can send to one user is equivalent to $100 USD.

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully sent credits to User ID 4845845",
  "data":
    
     {
    
      "usersId": "4K49USHD3282388232"
      
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/admin/sendCredits`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
toUsersEmail | required, if no phone | email of user being made admin if no phone is provided
toUsersPhone | required, if no email | phone of user being made admin if no phone is provided
amount | required| amount of currency to send to user
currency| required| defaults to KRW





## Search nearby users

API call allows admins to see all users nearby within a certain radius

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully sent credits to User ID 4845845",
  "data":
    
    [
      {
      
        "usersId": "4K49USHD3282388232",
        "userEmail": "user@email.com",
        "name":"Yoon Jenny",
        "userPhone": "+82 3456548383",
        "userLon": 20.30000,
        "userLat": 190.02020,
        "userAddress": "82 Samonbong-ro, Seouk, KR",
        "isAdmin":false,
        "isMechanic":true,
        "isCharger":false,
        "isDeliveryPerson": true,
        "currentLat":100.3232,
        "currentLon":93.02020,
        "lastUse": "2018-04-31 12:30:21 GMT",
        "status":"notSuspended"
        
        
      },
      {
      
        "usersId": "5K49USHD3282388232",
        "userEmail": "name@email.com",
        "userPhone": "+82 3456548383",
        "name":"Dave Thomas",
        "userLon": 20.30000,
        "userLat": 190.02020,
        "userAddress": "82 Samonbong-ro, Seouk, KR",
        "applicationTextSubmitted":"I want to me a mechanic and here ar emy crednetials",
        "isAdmin":false,
        "isMechanic":true,
        "isCharger":false,
        "isDeliveryPerson": true,
        "currentLat":100.3232,
        "currentLon":93.02020,
        "lastUse": "2018-04-31 12:30:21 GMT",
        "status":"notSuspended"
        
        
      }
    ]
   
}
```



## HTTP Request

`GET https://api.bbali.io/admin/searchNearby`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
lon | optional| admin's current longitude
lat | optional| admin's current latitude
email | optional| if admin is searching by email
name | optional| if admin is searching by name
radius | optional| if admin is setting a radius for geofence for their query, defaults to 20 kilometers







## Update User

API call allows admins to see update user using their email or phone as the query. Admin can also take away another admin's privelges if their user account became an admin before the editted query.

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully updated User ID 4845845",
  "data":
    
     {
    
      "usersId": "4K49USHD3282388232"
      
      
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/admin/updateUser`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | user authenication token
usersEmail | required, if no phone | email of user being updated
userPhone | required, if no email | phone of user being updated
isMechanic | optional | If admin is making user a mechanic, sets to true or false to permit or deny user particular status/type
isCharger | optional | If admin is making user a charger, sets to true or false to permit or deny user particular status/type
isDeliveryPerson | optional | If admin is making user a deliveryPerson, sets to true or false to permit or deny user particular status/type
status| optional | If admin is making user a active or suspended








## Create Vehicle

API call allows an admin to create a vehicle

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully created a vehicle",
  "data":
    
     {
    
      "vehicleName": "4K49UG5"
      
      
    }
   
}
```



### HTTP Request

`POST https://api.bbali.io/admin/createVehicle`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | user authenication token
vehiclePhoto | optional | photo of vehicle
originalLat | required | original latitude of the vehicle
originalLon | required | original longitude of the vehicle
type | required | adultscooter, kidscooter, moped, car.
unlockSeed | optional | The unlock seed of the vehicle so the server can stay synced in order to unlock and have the right timed unlock code
description| optional | Description of the vehicle
make| optional | manufacturer
model| optional | model of vehicle
year| optional | year vehicle was released
serialNum| optional | serial num/license plate of vehicle if applicable








## Update Vehicle

API call allows an admin to edit a vehicle's information

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "You have successully editted vehicle",
  "data":
    
     {
    
      "vehicleName": "4K49UG5"
      
      
    }
   
}
```



### HTTP Request

`PUT https://api.bbali.io/admin/editVehicle`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | user authenication token
vehicleName | required | unique identifier of the vehicle
vehiclePhoto | optional | photo of vehicle
originalLat | optional |  latitude of the vehicle if editing this
originalLon | optional|  longitude of the vehicle if editing this
type | optional| adultscooter, kidscooter, moped, car.
unlockSeed | optional | If changing: The unlock seed of the vehicle so the server can stay synced in order to unlock and have the right timed unlock code
description| optional | Description of the vehicle
batteryPower| optional | float of the battery power
status| optional | available, riding, charging, locked, unavailable, broken










## View Special User Applications

API call allows admins to see applications for chargers, mechanics and delivery people

> This API call returns JSON structured like this:

```json
{ "error": false, 
  "msg": "Special User Applications loaded (500 total)",
  "data":
    [
      {
      
        "usersId": "4K49USHD3282388232",
        "userEmail": "user@email.com",
        "name":"Yoon Jenny",
        "userPhone": "+82 3456548383",
        "userLon": 20.30000,
        "userLat": 190.02020,
        "userAddress": "82 Samonbong-ro, Seouk, KR",
        "applicationTextSubmitted":"I want to me a mechanic and here ar emy crednetials"
        
        
      },
      {
      
        "usersId": "5K49USHD3282388232",
        "userEmail": "name@email.com",
        "userPhone": "+82 3456548383",
        "name":"Dave Thomas",
        "userLon": 20.30000,
        "userLat": 190.02020,
        "userAddress": "82 Samonbong-ro, Seouk, KR",
        "applicationTextSubmitted":"I want to me a mechanic and here ar emy crednetials"
        
        
      }
    ]
}
```



### HTTP Request


`POST https://api.bbali.io/admin/viewApplications`


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userAuth | required | users Authentication token
lon | required | admin's current longitude
lat| required | admin's current latitude
radius | optional| defaults to 20000 kilometers to see applications globally





