## Affiliates

Update affiliate details - **DEPRECATED**

#### Request

POST http://api.UCapital.com/online/integration/cellxpert/update/affiliates


where `JSON_DATA` is like

```C#
{
    AffiliateDetails[] Affiliates;      // array of affiliate details
}

AffiliateDetails
{
    int AffProgramId;
    int AffiliateId;
    string UserName;
    string Email;
    string FirstName;
    string LastName;
    string CountryCode;
    string WebSite;
    AffiliateStatusId StatusId;
}

enum AffiliateStatusId
{
    Active = 1
}
```

##### A valid request example

```json
{
    ...
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    int CreatedCount;
    int UpdatedCount;
    int FailedCount;
}
```

##### Response example

```json
{
    ...
}
```


#### Access restrictions

- White IP list


#### Expectations

None
