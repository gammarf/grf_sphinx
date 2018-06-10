Distributed Radio Signal Collection and Analysis
================================================
ΓRF is a radio signal collection, storage, and analysis system based on inexpensive
distributed nodes and a central server.

Nodes run modules which provide various types of functionality, such as monitoring
the power on a set of frequencies, watching for 'hits' on frequencies, monitoring
aircraft activity (through their ADS-B traffic), and more.  Nodes can be distributed
geographically and their data combined for hybrid analysis.

Nodes are based on inexpensive hardware such as Intel NUCs, Raspberry Pis, RTL-SDR
USB radios, and the HackRF, so ΓRF is accessible to both professional and hobby users.

Data collected by nodes is stored on a server and used to form visualizations and other
analysis products.

.. figure:: _static/images/srv_landing.jpg
    :align: center

    Web interface, landing page

Applications
============
Some examples of what has been implemented, or may be easily implemented,
using the system include:

    * Monitoring ham radio activity on repeaters in a city
    * Creating timelines of emergency services activity in an area
    * Distributed tracking of satellites
    * Building direction finding networks (e.g. for fox hunts)
    * Spectrum enumeration (finding channels and guessing modulation) [under development]

Client
======
There is an open-source client available `here <https://github.com/gammarf/gammarf>`_.
We cover installation and usage of this client later in this documentation.

.. figure:: _static/images/client.jpg
    :align: center
    :width: 70%

    ΓRF client software

Server
======
The server collects and stores data from clients, and provides an elegant web interface for analysis of this data.

.. figure:: _static/images/srv_snapshot.jpg
    :align: center
    :width: 70%

    A 'snapshot' view of a spectrum slice as seen by a client

.. figure:: _static/images/srv_adsb_detail.jpg
    :align: center
    :width: 70%

    Timeline of hits (activity) for a frequency of interest

ΓRF documentation
=====================

Contents:

.. toctree::
   :maxdepth: 2

   client
   server
   protocol
   contact
