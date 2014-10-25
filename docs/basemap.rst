.. _basemap:

Basemap
-------

Any map created with the Basemap library must start with the creation of a Basemap instance

`mpl_toolkits.basemap.Basemap(llcrnrlon=None, llcrnrlat=None, urcrnrlon=None, urcrnrlat=None, llcrnrx=None, llcrnry=None, urcrnrx=None, urcrnry=None, width=None, height=None, projection='cyl', resolution='c', area_thresh=None, rsphere=6370997.0, ellps=None, lat_ts=None, lat_1=None, lat_2=None, lat_0=None, lon_0=None, lon_1=None, lon_2=None, o_lon_p=None, o_lat_p=None, k_0=None, no_rot=False, suppress_ticks=True, satellite_height=35786000, boundinglat=None, fix_aspect=True, anchor='C', celestial=False, round=False, epsg=None, ax=None) <http://matplotlib.org/basemap/api/basemap_api.html#mpl_toolkits.basemap.Basemap>`_

The class constructor has many possible arguments, and all of them are optional

Passing the bounding box
^^^^^^^^^^^^^^^^^^^^^^^^

The following arguments are used to set the extent of the map.

To see some examples and explanations about setting the bounding box, take a look at the :ref:`extension` section.

The first way to set the extent is by defining the map bounding box in geographical coordinates:

========= ===========
Argument  Description
========= ===========
llcrnrlon The lower left corner geographical longitude
llcrnrlat The lower left corner geographical latitude
urcrnrlon The upper right corner geographical longitude
urcrnrlat The upper right corner geographical latitude
========= ===========

An other option is setting the bounding box, but using the projected units:

========= ===========
Argument  Description
========= ===========
llcrnrx   The lower left corner x coordinate, in the projectino units
llcrnry   The lower left corner y coordinate, in the projectino units
urcrnrx   The upper right corner x coordinate, in the projectino units
urcrnry   The upper right corner y coordinate, in the projectino units
========= ===========

Finally, the last option is to set the bounding box giving the center point in geographical coordinates, and the width and height of the domain in the projection units

========= ===========
Argument  Description
========= ===========
width     The width of the map in the projection units
height    The heoght of the map in the projection units
lon_0     The longitude of the center of the map
lat_0     The latitude  of the center of the map
========= ===========

Using the Basemap instance to convert units
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The basemap instance can be used to calculate positions on the map and the inverse operation, converting positions on the map to geographical coordinates.

.. code-block:: python

	from mpl_toolkits.basemap import Basemap
	import matplotlib.pyplot as plt
	
	map = Basemap(projection='aeqd', lon_0 = 10, lat_0 = 50)
	
	print map(10, 50)
	print map(20015077.3712, 20015077.3712, inverse=True)

The output will be:
	
	(20015077.3712, 20015077.3712)
	(10.000000000000002, 50.000000000000014)

When inverse is False, which is its default value, the input values are a longitude and a latitude, and the output, the position of this point in the map coordinates. When *inverse* is set to true, the behaviour is the opposite, the arguments are an x and y positions in the map coordinates, and the output is the position of this point in geographical coordinates.

