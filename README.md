## Installation

```bash
pip install httpie
```

## Data examples

* Request latest 311 reports, with extended data:

```bash
http GET http://311api.cityofchicago.org/open311/v2/requests.json extensions=true
```

*N.B.*, even though a POST will get you the same data, the POST requires an API key, while the GET does not.

```json
[
  {
    "address": "30th & Spaulding",
    "agency_responsible": "Bureau of Street Operations - Graffiti",
    "extended_attributes": {
      "channel": "open311",
      "police_district": "10",
      "ward": "22"
    },
    "lat": 41.836922,
    "long": -87.725703,
    "media_url": "http://311request.cityofchicago.org/media/chicago/report/photos/51e95391016370e2c133b98c/pic_8304_693.png",
    "notes": [
      {
        "datetime": "2013-07-19T09:56:17-05:00",
        "summary": "Request submitted via Open311",
        "type": "submitted"
      },
      {
        "datetime": "2013-07-19T09:56:48-05:00",
        "summary": "Request opened",
        "type": "opened"
      }
    ],
    "requested_datetime": "2013-07-19T09:56:48-05:00",
    "service_code": "4fd3b167e750846744000005",
    "service_name": "Graffiti Removal",
    "service_request_id": "13-00983453",
    "status": "open",
    "updated_datetime": "2013-07-19T09:59:35-05:00"
  },
  ...
```

* Using a `service_request_id` from the previous query, get a single 311 report (again, with extended data):

```bash
http GET http://311api.cityofchicago.org/open311/v2/requests/13-00776762.json extensions=true
```

```json
[
  {
    "address": "1425 North Ashland Avenue, Chicago, IL 60642, USA",
    "agency_responsible": "Bureau of Forestry - S/S",
    "extended_attributes": {
      "channel": "open311",
      "police_district": "14",
      "ward": "1"
    },
    "lat": 41.9078441229322,
    "long": -87.6673774413278,
    "media_url": "http://311request.cityofchicago.org/media/chicago/report/photos/51c095030163a1392d6b1096/1371575056640.jpg",
    "notes": [
      {
        "datetime": "2013-06-18T12:12:35-05:00",
        "summary": "Request submitted via Open311",
        "type": "submitted"
      },
      {
        "datetime": "2013-06-18T12:14:18-05:00",
        "summary": "Request opened",
        "type": "opened"
      },
      {
        "datetime": "2013-06-20T15:54:00-05:00",
        "description": "*Complete the Service Request",
        "summary": "Dispatch Clam",
        "type": "activity"
      },
      {
        "datetime": "2013-06-20T15:55:01-05:00",
        "summary": "Request closed",
        "type": "closed"
      }
    ],
    "requested_datetime": "2013-06-18T12:14:18-05:00",
    "service_code": "4fd3bbf8e750846c53000069",
    "service_name": "Tree Debris",
    "service_request_id": "13-00776762",
    "status": "closed",
    "status_notes": "*Complete the Service Request",
    "updated_datetime": "2013-06-20T15:55:01-05:00"
  }
]
```

### Other API parameters:

* `callback=?` -- for JSONP embedding.
