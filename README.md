
# HotelBookingAPI

.NET Core 8 Web API to Demonstarte APIs Working with SQL Server [SQL Querries & Stored Procedures] as Backend & REST API on .NET Core Web API with ADO.NET with DTOs and Repositories with Dependency Injection.

## Project References
```
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
    <InvariantGlobalization>false</InvariantGlobalization>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.Data.SqlClient" Version="5.2.2" />
    <PackageReference Include="Serilog.AspNetCore" Version="8.0.3" />
    <PackageReference Include="Serilog.Settings.Configuration" Version="8.0.4" />
    <PackageReference Include="Serilog.Sinks.File" Version="6.0.0" />
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.6.2" />
  </ItemGroup>

</Project>

```

## APIs

Below is a list of API endpoints with their respective input and output. Please note that the application needs to be running.

### Users - Get All Users with Active Status

Endpoint

```
https://localhost:7145/User/AllUsers?isActive=true
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Retrieved all Users Successfully.",
  "Data": [
    {
      "UserID": 1,
      "Email": "Testedd@example.com",
      "IsActive": true,
      "LastLogin": "2024-12-07T09:18:39.893",
      "RoleID": 1
    },
    {
      "UserID": 2,
      "Email": "user@example.com",
      "IsActive": true,
      "LastLogin": null,
      "RoleID": 3
    }
  ],
  "Error": null
}
```

### Users - Get Specific Users with ID

Endpoint

```
https://localhost:7145/User/GetUser/2
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "User fetched successfully.",
  "Data": {
    "UserID": 2,
    "Email": "user@example.com",
    "IsActive": true,
    "LastLogin": null,
    "RoleID": 3
  },
  "Error": null
}
```

### Users - Add User

Endpoint

```
https://localhost:7145/User/AddUser
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "User Created Successfully",
  "Data": {
    "UserId": 3,
    "Message": "User Created Successfully",
    "IsCreated": true
  },
  "Error": null
}
```

### Users - Assign User Role

Endpoint

```
https://localhost:7145/User/AssignRole
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "User Role Assigned",
  "Data": {
    "Message": "User Role Assigned",
    "IsAssigned": true
  },
  "Error": null
}
```

### Users - User Login

Endpoint

```
https://localhost:7145/User/Login

{
  "Email": "Elivateduser@example.com",
  "Password": "Elivateduser"
}
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Login Successful",
  "Data": {
    "UserId": 3,
    "Message": "Login Successful",
    "IsLogin": true
  },
  "Error": null
}
```

### Users - Delete User

Endpoint

```
https://localhost:7145/User/Delete/1
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "User Deleted.",
  "Data": {
    "Message": "User Deleted.",
    "IsDeleted": true
  },
  "Error": null
}
```

### Users - Update User

Endpoint

```
https://localhost:7145/User/Update/3

{
  "UserID": 3,
  "Email": "Elivateduser@example.com",
  "Password": "Elivateduserupdated"
}
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "User Information Updated.",
  "Data": {
    "UserId": 3,
    "Message": "User Information Updated.",
    "IsUpdated": true
  },
  "Error": null
}
```

### Room - Get All Rooms

Endpoint

```
https://localhost:7145/api/Room/All
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Retrieved all Room Successfully.",
  "Data": [
    {
      "RoomID": 1,
      "RoomNumber": "101",
      "RoomTypeID": 1,
      "Price": 100,
      "BedType": "Queen",
      "ViewType": "Sea",
      "Status": "Occupied",
      "IsActive": true
    },
    {
      "RoomID": 2,
      "RoomNumber": "102",
      "RoomTypeID": 1,
      "Price": 100,
      "BedType": "Queen",
      "ViewType": "City",
      "Status": "Under Maintenance",
      "IsActive": true
    },
    {
      "RoomID": 3,
      "RoomNumber": "201",
      "RoomTypeID": 2,
      "Price": 150,
      "BedType": "King",
      "ViewType": "Garden",
      "Status": "Occupied",
      "IsActive": true
    },
    {
      "RoomID": 4,
      "RoomNumber": "301",
      "RoomTypeID": 3,
      "Price": 200,
      "BedType": "King",
      "ViewType": "Sea",
      "Status": "Occupied",
      "IsActive": true
    },
    {
      "RoomID": 5,
      "RoomNumber": "401",
      "RoomTypeID": 4,
      "Price": 250,
      "BedType": "Twin",
      "ViewType": "Pool",
      "Status": "Occupied",
      "IsActive": true
    }
  ],
  "Error": null
}
```

### RoomAmenity - Get Amenities By RoomTypeId 

Endpoint

```
https://localhost:7145/api/RoomAmenity/FetchAmenitiesByRoomTypeId/1
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Fetch Amenities By Room Type Id Successfully.",
  "Data": [
    {
      "AmenityID": 1,
      "Name": "Wi-Fi",
      "Description": "High-speed wireless internet access",
      "IsActive": true
    },
    {
      "AmenityID": 4,
      "Name": "Fitness Center",
      "Description": "Gym with modern equipment",
      "IsActive": true
    }
  ],
  "Error": null
}
```

### RoomType - Get All Room Types

Endpoint

```
https://localhost:7145/api/RoomType/AllRoomTypes?IsActive=true
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Retrieved all Room Types Successfully.",
  "Data": [
    {
      "RoomTypeID": 1,
      "TypeName": "Standard",
      "AccessibilityFeatures": "Wheelchair ramps, Grab bars in bathroom",
      "Description": "Basic room with essential amenities",
      "IsActive": true
    },
    {
      "RoomTypeID": 2,
      "TypeName": "Deluxe",
      "AccessibilityFeatures": "Wheelchair accessible, Elevator access",
      "Description": "High-end room with luxurious amenities",
      "IsActive": true
    },
    {
      "RoomTypeID": 3,
      "TypeName": "Executive",
      "AccessibilityFeatures": "Wide door frames, Accessible bathroom",
      "Description": "Room for business travelers with a work area",
      "IsActive": true
    },
    {
      "RoomTypeID": 4,
      "TypeName": "Family",
      "AccessibilityFeatures": "Child-friendly facilities, Safety features",
      "Description": "Spacious room for families with children",
      "IsActive": true
    }
  ],
  "Error": null
}
```

### Amenity - Get All Amenties

Endpoint

```
https://localhost:7145/api/Amenity/Fetch?isActive=true
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Retrieved all Room Amenity Successfully.",
  "Data": {
    "Amenities": [
      {
        "AmenityID": 1,
        "Name": "Wi-Fi",
        "Description": "High-speed wireless internet access",
        "IsActive": true
      },
      {
        "AmenityID": 2,
        "Name": "Pool",
        "Description": "Outdoor swimming pool with lifeguard",
        "IsActive": true
      },
      {
        "AmenityID": 3,
        "Name": "SPA",
        "Description": "Full-service spa and wellness center",
        "IsActive": true
      },
      {
        "AmenityID": 4,
        "Name": "Fitness Center",
        "Description": "Gym with modern equipment",
        "IsActive": true
      }
    ],
    "Message": "Data retrieved successfully.",
    "IsSuccess": true
  },
  "Error": null
}
```

### HotelSearch - Get Hotel search via Price Range

Endpoint

```
https://localhost:7145/HotelSearch/PriceRange?MinPrice=10&MaxPrice=300
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Fetch rooms by price range Successful",
  "Data": [
    {
      "RoomID": 1,
      "RoomNumber": "101",
      "Price": 100,
      "BedType": "Queen",
      "ViewType": "Sea",
      "Status": "Occupied",
      "RoomType": {
        "RoomTypeID": 1,
        "TypeName": "Standard",
        "AccessibilityFeatures": "Wheelchair ramps, Grab bars in bathroom",
        "Description": "Basic room with essential amenities"
      }
    },
    {
      "RoomID": 2,
      "RoomNumber": "102",
      "Price": 100,
      "BedType": "Queen",
      "ViewType": "City",
      "Status": "Under Maintenance",
      "RoomType": {
        "RoomTypeID": 1,
        "TypeName": "Standard",
        "AccessibilityFeatures": "Wheelchair ramps, Grab bars in bathroom",
        "Description": "Basic room with essential amenities"
      }
    },
    {
      "RoomID": 3,
      "RoomNumber": "201",
      "Price": 150,
      "BedType": "King",
      "ViewType": "Garden",
      "Status": "Occupied",
      "RoomType": {
        "RoomTypeID": 2,
        "TypeName": "Deluxe",
        "AccessibilityFeatures": "Wheelchair accessible, Elevator access",
        "Description": "High-end room with luxurious amenities"
      }
    },
    {
      "RoomID": 4,
      "RoomNumber": "301",
      "Price": 200,
      "BedType": "King",
      "ViewType": "Sea",
      "Status": "Occupied",
      "RoomType": {
        "RoomTypeID": 3,
        "TypeName": "Executive",
        "AccessibilityFeatures": "Wide door frames, Accessible bathroom",
        "Description": "Room for business travelers with a work area"
      }
    },
    {
      "RoomID": 5,
      "RoomNumber": "401",
      "Price": 250,
      "BedType": "Twin",
      "ViewType": "Pool",
      "Status": "Occupied",
      "RoomType": {
        "RoomTypeID": 4,
        "TypeName": "Family",
        "AccessibilityFeatures": "Child-friendly facilities, Safety features",
        "Description": "Spacious room for families with children"
      }
    }
  ],
  "Error": null
}
```

### Reservation - Get Reservation Calculation

Endpoint

```
https://localhost:7145/api/Reservation/CalculateRoomCosts

{
  "RoomIDs": [
    2
  ],
  "CheckInDate": "2024-12-18",
  "CheckOutDate": "2024-12-19"
}
```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Success",
  "Data": {
    "RoomDetails": [
      {
        "RoomID": 2,
        "RoomNumber": "102",
        "RoomPrice": 100,
        "NumberOfNights": 1,
        "TotalPrice": 100
      }
    ],
    "Amount": 100,
    "GST": 18,
    "TotalAmount": 118,
    "Status": true,
    "Message": "Sucess"
  },
  "Error": null
}
```

### Cancellation - Get All Cancellation Policies

Endpoint

```
https://localhost:7145/Cancellation/GetCancellationPolicies

```

Response body

```json
{
  "Success": true,
  "StatusCode": 200,
  "Message": "Cancellation policies retrieved successfully.",
  "Data": {
    "Status": true,
    "Message": "Policies retrieved successfully.",
    "Policies": [
      {
        "PolicyID": 1,
        "Description": "No charge if cancelled more than 30 days before check-in",
        "CancellationChargePercentage": 0,
        "MinimumCharge": 0,
        "EffectiveFromDate": "2024-01-01T00:00:00",
        "EffectiveToDate": "2024-12-31T00:00:00"
      },
      {
        "PolicyID": 2,
        "Description": "10% charge if cancelled between 15 and 30 days before check-in",
        "CancellationChargePercentage": 10,
        "MinimumCharge": 0,
        "EffectiveFromDate": "2024-01-01T00:00:00",
        "EffectiveToDate": "2024-12-31T00:00:00"
      },
      {
        "PolicyID": 3,
        "Description": "25% charge if cancelled between 7 and 14 days before check-in",
        "CancellationChargePercentage": 25,
        "MinimumCharge": 0,
        "EffectiveFromDate": "2024-01-01T00:00:00",
        "EffectiveToDate": "2024-12-31T00:00:00"
      },
      {
        "PolicyID": 4,
        "Description": "50% charge if cancelled less than 7 days before check-in",
        "CancellationChargePercentage": 50,
        "MinimumCharge": 0,
        "EffectiveFromDate": "2024-01-01T00:00:00",
        "EffectiveToDate": "2024-12-31T00:00:00"
      }
    ]
  },
  "Error": null
}
```

## Run the Solution - HotelBookingAPI

From the terminal/shell/command line tool, use the following commands to build, test and run the API.

### Start the SQL Server instance

```console
$ SQL Server Configuration Manager - Start
```

### Build the project

```console
$ dotnet clean
$ dotnet build
```


### Run the application

Run the application which will be listening on port `7145`.

```console
$ dotnet run --project HotelBookingAPI
```

