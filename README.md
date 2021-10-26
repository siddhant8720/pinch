import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import interpolate
import math
input_table=pd.read_excel('Input Sheet.xlsx')
input_table["Stream Type"]=np.where(input_table["Supply Temperture (°C)"]>input_table["Target Temperature (°C)"],"HOT","COLD")
input_table["Heat Capacity Flowrate (kW/K)"]=round(input_table["Heat Load (kW)"]/(input_table["Target Temperature (°C)"]-input_table["Supply Temperture (°C)"]),2)
#Heat Capacity Flowrate values of all hot streams have been made negative. This convention will be used later to simplify calculations for problem table algorithm.
index=[]
for n in range(1,len(input_table)+1):
    index.append(n)
input_table["Stream Number"]=index
input_table=input_table.set_index('Stream Number')
input_table
