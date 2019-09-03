# Data for plotting 20m topography in Basemap (Python)
Contains data for plotting the topo file

```
def plot_topo(map,cmap=plt.cm.jet):
    #20 minute bathymetry/topography data
    etopo = np.loadtxt('topo/etopo20data.gz')
    lons  = np.loadtxt('topo/etopo20lons.gz')
    lats  = np.loadtxt('topo/etopo20lats.gz')
    # shift data so lons go from -180 to 180 instead of 20 to 380.
    etopo,lons = shiftgrid(180.,etopo,lons,start=False)
    lons, lats = np.meshgrid(lons, lats)
    # cs = map.contourf(lons,lats,etopo,30,cmap=plt.cm.jet,shading='interp')
    cs = map.pcolormesh(lons,lats,etopo,cmap=cmap,latlon=True,shading='gouraud')
```
<img src="https://github.com/utpalrai/topo_python/blob/master/events_map.png">
