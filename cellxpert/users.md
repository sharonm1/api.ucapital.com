## Users

Get all **changed** users between specified dates

[Try it online](http://api.UCapital.com/nunit/page/online.html)


#### Request

GET http://api.UCapital.com/online/integration/cellxpert/users?data=JSON_DATA

where `JSON_DATA` is like

```C#
enum EOrderBy
{
    UserId, UpdateDate
}

{
    DateTime From;              // starting from this date
    DateTime To;                // until this date
    int PagingIndex;            // user index to start with in case there are more results
    EOrderBy OrderBy;			// optional (default is UserId)
}
```

##### A valid request example

```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 0
}

{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 0,
  "OrderBy": "UpdateDate"
}
```



#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string TrackingId;          // tracking id of this request (for troubleshooting...)
    UserInfo[] Users;           // an array of retrieved users
    int PagingIndex;            // should be used in a consequent request
    int HasMoreData;            //     if there is more data
}

UserInfo
{
    int UserId;
    string Email;
    int UserGroupId;
    int BusinessUnitId;
    string UserGroupName;
    UserStatus Status;
    string CreatedAt;
    string UpdatedAt;
    int AffProgramId;
    string UserName;
    string UserPhone;
    int AffiliateId;
    string ActivationDate;
    string AdServer;            // A free parameter affiliate passes with registration
    string CountryCode;         // ISO two letters country code
    int Eligible;               // 1 - eligible
    string SalesStatus;         // see statuses below
}
```

Sales statuse |
-------------
New |
NoAnswer |
CallInAWhile |
PaymentSuccessful |
SelfActivation |
NoInterest |
VoiceMail |
Unreachable |
CcClearanceFailed |
PotentialSpy |
ForexTrader |
NotConverted |
SecondChance |



##### Successful response example

```json
{
  "Users": [
    {
      "UserId": 271250,
      "Email": "vicentecolombini@gmail.com",
      "UserGroupId": 10914,
      "BusinessUnitId": 10293,
      "UserGroupName": "micro (UCapital)",
      "Status": "Active",
      "CreatedAt": "2014-01-05 13:20:15",
      "UpdatedAt": "2014-04-21 21:52:49",
      "AffProgramId": 1,
      "UserName": "Vicente M Colombini",
      "UserPhone": "+31-65-1700812",
      "AffiliateId": 4866
    }
  ],
  "PagingIndex": 1,
  "HasMoreData": 0
}
```

##### Successful response example with consequent request for remaining data

```json
{
  "PagingIndex": 101,
  "HasMoreData": 1,
  "Users": [
    ...
}
```


```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 101,
  "Token": ""
}
```


#### Access restrictions

- Each request may retrieve up to one hundred items
- White IP list


#### Expectations

None
