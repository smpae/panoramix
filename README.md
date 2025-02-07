Panoramix
=========

Panoramix is a data exploration platform designed to be visual, intuitive
and interactive.


![img](http://i.imgur.com/aOaH0ty.png)

Panoramix
---------
Panoramix's main goal is to make it easy to slice, dice and visualize data. 
It empowers its user to perform **analytics at the speed of thought**.

Panoramix provides:
* A quick way to intuitively visualize datasets
* Create and share simple dashboards
* A rich set of visualizations to analyze your data, as well as a flexible
    way to extend the capabilities
* An extensible, high granularity security model allowing intricate rules
    on who can access which features, and integration with major
    authentication providers (database, OpenID, LDAP, OAuth & REMOTE_USER
    through Flask AppBuiler)
* A simple semantic layer, allowing to control how data sources are 
    displayed in the UI,
    by defining which fields should show up in which dropdown and which
    aggregation and function (metrics) are made available to the user
* Deep integration with Druid allows for Panoramix to stay blazing fast while
    slicing and dicing large, realtime datasets


Buzz Phrases
------------

* Analytics at the speed of thought!
* Instantaneous learning curve
* Realtime analytics when querying [Druid.io](http://druid.io)
* Extentsible to infinity

Database Support
----------------

Panoramix was originally designed on to of Druid.io, but quickly broadened
its scope to support other databases through the use of SqlAlchemy, a Python
ORM that is compatible with
[most common databases](http://docs.sqlalchemy.org/en/rel_1_0/core/engines.html). 


What is Druid?
-------------
From their website at http://druid.io

*Druid is an open-source analytics data store designed for 
business intelligence (OLAP) queries on event data. Druid provides low 
latency (real-time) data ingestion, flexible data exploration, 
and fast data aggregation. Existing Druid deployments have scaled to 
trillions of events and petabytes of data. Druid is best used to 
power analytic dashboards and applications.*


Installation
------------

Follow these few simple steps to install Panoramix

```
# Install panoramix
pip install panoramix

# Create an admin user
fabmanager create-admin --app panoramix

# Load some data to play with
panoramix load_examples

# Start the development web server
panoramix runserver -d
```

After installation, you should be able to point your browser to the right
hostname:port [http://localhost:8088](http://localhost:8088), login using
the credential you entered while creating the admin account, and navigate to
`Menu -> Admin -> Refresh Metadata`. This action should bring in all of 
your datasources for Panoramix to be aware of, and they should show up in
`Menu -> Datasources`, from where you can start playing with your data!

Configuration
-------------

To configure your application, you need to create a file (module) 
`panoramix_config.py` and make sure it is in your PYTHONPATH. Here are some
of the parameters you can copy / paste in that configuration module:

```
#---------------------------------------------------------
# Panoramix specifix config
#---------------------------------------------------------
ROW_LIMIT = 5000
WEBSERVER_THREADS = 8

PANORAMIX_WEBSERVER_PORT = 8088
#---------------------------------------------------------

#---------------------------------------------------------
# Flask App Builder configuration
#---------------------------------------------------------
# Your App secret key
SECRET_KEY = '\2\1thisismyscretkey\1\2\e\y\y\h'

# The SQLAlchemy connection string.
SQLALCHEMY_DATABASE_URI = 'sqlite:////tmp/panoramix.db'

# Flask-WTF flag for CSRF
CSRF_ENABLED = True

# Whether to run the web server in debug mode or not
DEBUG = True
```

This file also allows you to define configuration parameters used by
Flask App Builder, the web framework used by Panoramix. Please consult
the [Flask App Builder Documentation](http://flask-appbuilder.readthedocs.org/en/latest/config.html) for more information on how to configure Panoramix.


* From the UI, enter the information about your clusters in the 
``Admin->Clusters`` menu by hitting the + sign. 

* Once the Druid cluster connection information is entered, hit the 
``Admin->Refresh Metadata`` menu item to populate

* Navigate to your datasources

More screenshots
----------------

![img](http://i.imgur.com/Rt6gNQ9.png)
![img](http://i.imgur.com/t7VOtqQ.png)
![img](http://i.imgur.com/PaiFQnH.png)
