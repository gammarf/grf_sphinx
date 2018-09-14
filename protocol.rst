Protocol
********

Client / Server
===============

While there is an "official" client, in reality data can be sent to the server by whatever mechanism you wish, as long as it adheres to the protocol below.  Each module sends its data as JSON, through a ZMQ socket.  See the client source for details.

**adsb**

.. code-block:: json

    {
        "icao": string,
        "callsign": string,
        "aircraft_lat": string,
        "aircraft_lng": string,
        "altitude": string,
        "heading": string,
        "updownrate": string,
        "speedtype": string,
        "speed": string,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**channels**

.. code-block:: json

    {
        "center": int,
        "bw": int,
        "pwr": string,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**freqwatch**

.. code-block:: json

    {
        "freq": int,
        "pwr": float,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**ism433**

.. code-block:: json

    {
        "model": string,
        "type": string,
        "id": int,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**p25rx**

.. code-block:: json

    {
        "talkgroup": string,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**scanner**

.. code-block:: json

    {
        "freq": int,
        "pwr": float,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }

**single**

.. code-block:: json

    {
        "freq": int,
        "thresh": float,
        "pwr": float,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }




**snapshot**

.. code-block:: json

    {
        "snapshotid": string,
        "freq": int,
        "pwr": string,
        "stationid": string,
        "dt": int,
        "lat": string,
        "lng": string,
        "protocol": int,
        "module": int,
        "rand": string,
        "sign": [md5(station_pass + rand)]
    }


Utility API
===========

**locations**

URL: http://[server]:[port]/util/locations

Returns a list of logged in stations, with a list of modules each is running.  Append a stationid to the URL to just retrieve one station.

**loggedin**

URL: http://[server]:[port]/util/loggedin/[stationid]

Returns 'true' or 'false', depending on whether [stationid] is logged in

**modrates**

URL: http://[server]:[port]/util/modrates/[stationid]

Transmit information for a station's running modules

**refxmtrs**

URL: http://[server]:[port]/util/refxmtrs

Returns a list of reference transmitters for the cluster, with a list for each
that includes callsign, location, power, and frequency.

**numalerts**

URL: http://[server]:[port]/util/numalerts/[stationid]

Returns the total number of alerts (active triggers) for the specified station.
