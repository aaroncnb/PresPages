
# Onaka Lab Meeting
## Discussion of Perrott et al. (accepted):
> ##### AMI-CL J0300+2613: a Galactic anomalous-microwave-emission ring masquerading as a galaxy cluster


Thursday, October 4th, 2017  
Aaron Bell

# Outline:  
  * What is the AMI?
  * What is Sunyaev Zeldovich?
  * What did this paper find?
  * Open questions?
  

# What is the Sunyaev-Zel'dovich effect?
> "when CMB photons inverse-Compton scattered by hot plasma in a galaxy cluster's potential well"  
> -Shimwell et al. (2013)

  * Galaxy clusters can be traced by CMB fluctuations!
  * SZ causes a drop in flux at freq. < 217 GHz

# What is AMI?
  * Arcminute Microkelvin Imager:
> "blind galaxy cluster survey [...] aiming to detect via the Sunyaev-Zel'dovich effect"  
> -page 1  
  * New digital correlator
  * Large-array: Sensitivity and resolution - foreground/background isolation
  * Small array: High surface brightness sensitivity - SZ imaging
#### Small Array:
![](http://www.mrao.cam.ac.uk/wp-content/uploads/2012/11/SA_110128_02.jpg)
#### Large array
![](http://www.mrao.cam.ac.uk/wp-content/uploads/2012/11/amila_nieuwburg2.jpg)

  * __1972__: Sunyaev & Zel'dovich claim CMB deviations can identify galaxy clusters
  * __2008-2011__: AMI observes "blindly" at 15.7 GHz - detects several clusters
  * __2013__: Schiwell+ report detection of "extended and unusual cluster" `J0300+2613` via SZ
  * __2011-present__: Anomalous microwave emission/spinning dust annoys cosmologists
  * __2015__: AKARI Far IR data relased
  * __2017__: Perrott+ claim `J0300+2613` is just galactic dust! (not SZ, but AME)
    


# What was their strategy?
  1. Repeat observation with new correlator
  2. Compare with newly available IR and MW data (i.e. AKARI!)
  3. Rule-out synchrotron with `GLEAM` 200 MHz data
  4. Rule-out free-free with `GB6` 5 GHz data
  5. Rule-out thermal dust emission via blackbody fit

### Repeat J003+2613 observation with new correlator
##### Left: Analog Correlator
##### Right: Digital Correlator
<img src="paper_2017/figs/AMI_SA.png" alt="Drawing" style="float: left; width: 40%; margin-right: 1%; margin-bottom: 0.5em;"/><img src="paper_2017/figs/AMIDC_SA.png" alt="Drawing" style="float: left; width: 40%; margin-right: 1%; margin-bottom: 0.5em;"/>

### Compare to IR data:
##### Left: AKARI 140 micron
##### Center: AKARI 90 micron
##### Right: WISE 12 micron 
<img src="paper_2017/figs/sim_WideL.png" alt="Drawing" style="float: left; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"/><img src="paper_2017/figs/sim_WideS.png" alt="Drawing" style="float: left; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"/><img src="paper_2017/figs/sim_WISE12.png" alt="Drawing" style="float: left; width: 30%; margin-right: 1%; margin-bottom: 0.5em;"/>  


 

### Rule out synchrotron with GLEAM 200 MHz:
![](paper_2017/figs/GLEAM.png)

### Rule out free-free with GB6 5 GHz:
![](paper_2017/figs/GB6_pred.png)

# What did this paper find?
  * `J0300+2613` correlates with IR emission
  * Obsvervation with upgraded instrument shows much weaker SZ-effect 
  * Unlikely to be synchrotron or free-free emission

# Open Questions

  1. __What does `J0300+2613` look like in MIR data?__
  2. __Could other SZ "clusters" be mislabled?__
  3. __Even if  `J0300+2613` is really Galactic emission-__Is it necessarily AME?
      * What about free-free?
      * Synchrotron?
      * Thermal dust?

## What does J0300+2613 look like in MIR data?
  * We can find out:
      




```python
#Load `J0300+2613` coordinates into python:
from astropy.coordinates import SkyCoord # Low-level frames
import astropy.units as u
coord = SkyCoord('3:00:08.9','+26:16:29.1',frame='icrs', unit=(u.hourangle, u.deg))
#Convert to degrees RA DEC:
coord
```




    <SkyCoord (ICRS): (ra, dec) in deg
        ( 45.03708333,  26.27475)>




```python
#So the kernel doesn't crash when we plot stuff in a notebook
%matplotlib inline 

# Convenient package for plotting FITS images
import aplpy 

def fits_display(image_file):
   
    # Create a new figure
    fig = aplpy.FITSFigure(image_file)

    # Show the colorscale
    fig.show_colorscale()

    # Make ticks white
    fig.ticks.set_color('white')

    # Make labels smaller
    fig.tick_labels.set_font(size=15)
    
    # Round out those tick labels:
    fig.tick_labels.set_xformat('ddd.dd')
    fig.tick_labels.set_yformat('ddd.dd')
    
    # Overlay a grid
    fig.add_grid()
    fig.grid.set_alpha(0.9)
    
    # Add a colorbar
    fig.add_colorbar()
    fig.colorbar.set_axis_label_text('Intensity (MJy/sr)')
    
    return fig

```

# How the region looks if we make an exact cutout from raw IRC data:
Zodi is not subtracted!


```python
# 9 micron data
fits_display('/home/aaronb/J003+2613/image/J003+2613_S.fits')
# 18 micron data
fits_display('/home/aaronb/J003+2613/image/J003+2613_L.fits')
```

    WARNING: Cannot determine equinox. Assuming J2000. [aplpy.wcs_util]
    WARNING:astropy:Cannot determine equinox. Assuming J2000.
    WARNING: Cannot determine equinox. Assuming J2000. [aplpy.wcs_util]
    WARNING:astropy:Cannot determine equinox. Assuming J2000.
    INFO:astropy:Auto-setting vmin to  1.360e+01
    INFO:astropy:Auto-setting vmax to  1.790e+01


    INFO: Auto-setting vmin to  1.360e+01 [aplpy.core]
    INFO: Auto-setting vmax to  1.790e+01 [aplpy.core]





    <aplpy.core.FITSFigure at 0x2ba51749ef50>




![png](output_16_3.png)



```python

```

    WARNING: Cannot determine equinox. Assuming J2000. [aplpy.wcs_util]
    WARNING:astropy:Cannot determine equinox. Assuming J2000.
    WARNING: Cannot determine equinox. Assuming J2000. [aplpy.wcs_util]
    WARNING:astropy:Cannot determine equinox. Assuming J2000.
    INFO:astropy:Auto-setting vmin to  1.360e+01
    INFO:astropy:Auto-setting vmax to  1.790e+01


    INFO: Auto-setting vmin to  1.360e+01 [aplpy.core]
    INFO: Auto-setting vmax to  1.790e+01 [aplpy.core]





    <aplpy.core.FITSFigure at 0x2ba517d01a50>




![png](output_17_3.png)



```python
# How the region looks in Zodi-subtracted All-sky Tiles
```


```python
# 9 micron data:
fits_display('/work2/users/onaka/AKARI/IRC_AllSkyMap_2016/G156m27/G156m27_S_intensity.fits')
# 18 micron data:
fits_display('/work2/users/onaka/AKARI/IRC_AllSkyMap_2016/G156m27/G156m27_L_intensity.fits')
```

    INFO:astropy:Auto-setting vmin to -5.674e+00
    INFO:astropy:Auto-setting vmax to  7.043e+00


    INFO: Auto-setting vmin to -5.674e+00 [aplpy.core]
    INFO: Auto-setting vmax to  7.043e+00 [aplpy.core]
    INFO

    INFO:astropy:Auto-setting vmin to -9.226e+00
    INFO:astropy:Auto-setting vmax to  9.921e+00


    : Auto-setting vmin to -9.226e+00 [aplpy.core]
    INFO: Auto-setting vmax to  9.921e+00 [aplpy.core]





    <aplpy.core.FITSFigure at 0x2b5323ee9750>




![png](output_19_5.png)



![png](output_19_6.png)



```python
# 9 micron data:
fits_display('/work2/users/onaka/AKARI/IRC_AllSkyMap_2016/G157m30/G157m30_S_intensity.fits')
# 18 micron data:
fits_display('/work2/users/onaka/AKARI/IRC_AllSkyMap_2016/G157m30/G157m30_L_intensity.fits')
```

    INFO:astropy:Auto-setting vmin to -3.828e+00
    INFO:astropy:Auto-setting vmax to  4.931e+00


    INFO: Auto-setting vmin to -3.828e+00 [aplpy.core]
    INFO: Auto-setting vmax to  4.931e+00 [aplpy.core]
    INFO

    INFO:astropy:Auto-setting vmin to -6.854e+00
    INFO:astropy:Auto-setting vmax to  7.413e+00


    : Auto-setting vmin to -6.854e+00 [aplpy.core]
    INFO: Auto-setting vmax to  7.413e+00 [aplpy.core]





    <aplpy.core.FITSFigure at 0x2b53207cc6d0>




![png](output_20_5.png)



![png](output_20_6.png)



```python

```
