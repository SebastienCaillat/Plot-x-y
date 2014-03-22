#!python3
""" Simple X/Y graphs drawing from csv files
 Last update S. Caillat 17/03/2014"""
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.ticker import MultipleLocator, FormatStrFormatter
# ----------------- Settings ------------------------------------
# Decimal separator must be "." not "," Warning: bad space encoding may cause disfunction 
filename = "Data.csv"         # Data csv file, UTF-8 encoding, use notetab++ or similar to convert
filefigurename = "Fig-01"     # Figure file name
Xlabel = "Temperature (°C)"
Ylabel = "Mass/initial mass (%)"
Labels = ["  5 K/min","10 K/min","15 K/min","20 K/min"]
ColorsSymbols = ["g-","k--","r-.","b:"] # Here example for 4 graphs
# Colors: b: blue, g: green, r: red, c: cyan, m: magenta, y: yellow, k: black, w: white color=''
# symbols: o, +, * marker=''
#{0: 'tickleft', 1: 'tickright', 2: 'tickup', 3: 'tickdown', 4: 'caretleft',
#'D': 'diamond', 6: 'caretup', 7: 'caretdown', 's': 'square', '|': 'vline',
# '': 'nothing', 'None': 'nothing', 'x': 'x', 5: 'caretright', '_': 'hline',
#'^': 'triangle_up', None: 'nothing', 'd': 'thin_diamond', 'h': 'hexagon1',
#'+': 'plus', '*': 'star', ',': 'pixel', 'o': 'circle', '.': 'point',
#'1': 'tri_down', 'p': 'pentagon', '3': 'tri_left', '2': 'tri_up', '4': 'tri_right',
#'H': 'hexagon2', 'v': 'triangle_down', '8': 'octagon', '<': 'triangle_left', '>': 'triangle_right'}
majorticksAuto = True        # True/False major ticks are automaticaly set 
minorticks = True            # True/False for minor ticks in the figure
#majorFormatter = FormatStrFormatter('%d') # Optional define format
# ----------------- Set minor / major ticks (optional) --------------------------
if majorticksAuto is False :            
    majorLocatorX = MultipleLocator(100)# Major X interval
    majorLocatorY = MultipleLocator(10) # Major Y interval
    Ymax = 100                          # Y & X range
    Ymin = 0             # Manualy adapt values if majortickAuto is False                  
    Xmin = 30
    Xmax = 950
if minorticks is True :  # Manualy adapt values if minorticks is True   
    minorLocatorX = MultipleLocator(20) # Minor X interval
    minorLocatorY = MultipleLocator(2)  # Minor Y interval
# ------------------ Reading data file -----------------------------------------
try:                        # Try to read data file
    data = np.genfromtxt(filename,          
        names = True,       # If True, field names read from first valid line
        comments = '#',     # Skip characters after #
        delimiter=';',      # Change if needed according to csv file used
        dtype = None)       # Guess the dtype of each column (float)
except:
    print ('Error reading file: '+ filename +', see message below')
    print ('Could be wrong file name, error in number of columns,')
    print ('decimal separator (use . not ,), bad space encoding...')
# ------------------- Reading Data -----------------------------------
a = [row[0] for row in data] # Reading rows
b = [row[1] for row in data]
c = [row[2] for row in data]
d = [row[3] for row in data]
e = [row[4] for row in data]

fig=plt.figure()
ax=fig.add_subplot(111, axisbg='w')
# ------------------- Define the graph to plot ------------------------
ax.plot(a,b,ColorsSymbols[0], label = Labels[0]) # x/y pairs
ax.plot(a,c,ColorsSymbols[1], label = Labels[1])
ax.plot(a,d,ColorsSymbols[2], label = Labels[2])
ax.plot(a,e,ColorsSymbols[3], label = Labels[3])
# --------------------- Ticks -----------------------------------------
if majorticksAuto is False :    # Set major tick if auto mode is off
    ax.xaxis.set_major_locator(majorLocatorX)
    ax.yaxis.set_major_locator(majorLocatorY)
    plt.axis(ymax=Ymax, ymin=Ymin, xmin=Xmin, xmax=Xmax)
if minorticks is True :         # Minor tricks if needed
    ax.xaxis.set_minor_locator(minorLocatorX)
    ax.yaxis.set_minor_locator(minorLocatorY)
# -------------------- Additional text ------------------------------
# plt.grid()                    # Grid on the graph (optional)
# plt.title("Title here")       # Title on the graph (optional)
plt.xlabel(Xlabel)              # X & Y axis label
plt.ylabel(Ylabel)
# Position of the legend box see http://matplotlib.org/users/legend_guide.html#legend-location
legend=plt.legend(loc='upper right',handlelength=3,fontsize=11)
for label in legend.get_lines(): label.set_linewidth(1.5)  # to increase the legend line width (optional)
# ------------- Saving figure ---------------------------------------------
plt.savefig(filefigurename+'.png', dpi = 300, frameon=False)    # png format
#plt.savefig(filefigurename+'.pdf', dpi = 300, frameon=False)   # if pdf needed
plt.show()

