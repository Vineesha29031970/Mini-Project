# Mini-Project
# Description :
Airport traffic encompasses the dynamic movement and activity of aircraft, passengers, and cargo within an airport. It involves the arrivals and departures of planes, taxiing on runways and taxiways, and parking at gates. Passenger traffic includes processes like check-in, security screening, boarding, and arrivals. Cargo traffic involves the transportation of goods. Ground services such as fueling, catering, baggage handling, and maintenance contribute to airport traffic. Air traffic control plays a crucial role in managing the safe movement of aircraft. Airport infrastructure, including runways, terminals, and gates, impacts traffic flow. Peak hours and seasons may lead to increased demand. Regulatory compliance, technological advancements, and environmental considerations also influence airport traffic dynamics. Overall, efficient traffic management is essential for the safety and satisfaction of all stakeholders in air travel.
# KEY FEATURES :
 Some key features include analyzing flight movements, passenger flow, cargo handling, ground services performance, traffic flow on runways and taxiways, infrastructure utilization, weather impact, predictive analysis for demand, and environmental impact.Additionally, examining customer satisfaction metrics provides insights into the overall passenger experience. 
# CODE :
DEVELOPED BY : VINEESHA S

REGISTER NO : 212221040180

from datetime import date
import os

import geopandas as gpd
import geoplot as gplt
import folium
import mapclassify
import matplotlib.pyplot as plt
from mpl_toolkits.axes_grid1 import make_axes_locatable
import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)
import plotly.express as px
import re
import seaborn as sns
from shapely.geometry import Point, Polygon
from shapely.geometry import MultiPolygon
