Protocol
********

Client / Server
===============

While there is an "official" client, in reality data can be sent to the server
by whatever mechanism you wish, as long as it adheres to the protocol below.
Each module sends its data as JSON, through a TCP socket.

**scanner**

.. code-block:: json

    {
        "lat": float,
        "lng": float,
        "freq": int,
        "pwr": float,
        "rand": str,
        "protocol": 1,
        "stationid": str,
        "module": 1,
        "sign": [md5(station_pass + rand)]
    }

**freqwatch**

.. code-block:: json

    {
        "lat": float,
        "lng": float,
        "freq": int,
        "pwr": float,
        "rand": str,
        "ts": str,
        "protocol": 1,
        "stationid": str,
        "module": 6,
        "sign": [md5(station_pass + rand)]
    }

**p25rx**

.. code-block:: json

    {
        "talkgroup": str,
        "lat": float,
        "lng": float,
        "rand": str,
        "protocol": 1,
        "stationid": str,
        "module": 4,
        "sign": [md5(station_pass + rand)]
    }

**snapshot**

.. code-block:: json

    {
        "lat": float,
        "lng": float,
        "snapshotid": str,
        "rawdata": str,
        "type": str,
        "rand": str,
        "protocol": 1,
        "stationid": str,
        "module": 5,
        "sign": [md5(station_pass + rand)]
    }

**spectrum**

.. code-block:: json

    {
        "lat": float,
        "lng": float,
        "freq": int,
        "mean": str,
        "stdev": str,
        "range": str,
        "protocol": 1,
        "stationid": str,
        "module": 2,
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
