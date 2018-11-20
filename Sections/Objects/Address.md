## Address
There are two Address objects that represent the shipping or billing address of a customer, AddressPost and AddressResponse. These objects may be included as a child attribute of other JSON objects (such as [Customer](Customer.md) or [Payment Method](PaymentMethod.md)).


## AddressPost
This object is used when creating an address on the PayFabric Receivables website.

| Attribute | Data Type | Definition | Max Length |
| :----------- | :--------- | :--------- | :--------- |
| Address1\* | String | The first line of a street address | nvarchar(100) |
| Address2 | String | The second line of a street address | nvarchar(100) |
| Address3 | String | The third line of a street address | nvarchar(100) |
| AddressID\* | String | The address identifier | nvarchar(50) |
| City | String | City name | nvarchar(50) |
| Country\* | String | Country name | nvarchar(50) |
| EMailAddress\* | String | Email address | nvarchar(255) |
| Fax\* | String | Fax number | nvarchar(50) |
| Name\* | String | Customer name | nvarchar(50) |
| Phone1 | String | Phone number line 1 | nvarchar(50) |
| Phone2 | String | Phone number line 2 | nvarchar(21) |
| Phone3 | String | Phone number line 3 | nvarchar(21) |
| State | String | State name | nvarchar(50) |
| UserDefine1 | String | User-defined field 1. Developer can store additional data in this field. | nvarchar(255) |
| UserDefine2 | String | User-defined field 2. Developer can store additional data in this field. | nvarchar(255) |
| Zip | String | Zip code | nvarchar(50) |
\*Required


## AddressResponse
This object is used when getting an address from the PayFabric Receivables website.

| Attribute | Data Type | Definition | Max Length |
| :----------- | :--------- | :--------- | :--------- |
| Address1 | String | The first line of a street address | nvarchar(100) |
| Address2 | String | The second line of a street address | nvarchar(100) |
| Address3 | String | The third line of a street address | nvarchar(100) |
| City | String | City name | nvarchar(50) |
| Country | String | Country name | nvarchar(50) |
| EMailAddress | String | Email address | nvarchar(255) |
| Fax | String | Fax number | nvarchar(50) |
| Name | String | Customer name | nvarchar(50) |
| Phone1 | String | Phone number line 1 | nvarchar(50) |
| Phone2 | String | Phone number line 2 | nvarchar(21) |
| Phone3 | String | Phone number line 3 | nvarchar(21) |
| State | String | State name | nvarchar(50) |
| UserDefine1 | String | User-defined field 1. Developer can store additional data in this field. | nvarchar(255) |
| UserDefine2 | String | User-defined field 2. Developer can store additional data in this field. | nvarchar(255) |
| Zip | String | Zip code | nvarchar(50) |
