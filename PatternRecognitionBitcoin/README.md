## Aim
The aim of this program is to recognise patterns across multiple financial indicators. The program starts by choosing a sub-series of prices with a set length, starting at a randomly chosen point in time (e.g. 30 price points recorded every 5 minuts starting at 12:00:00 01/01/2015). I'll refer to this as the 'Chosen Pattern'. For this time period it then also finds the correspoinding sequence of Volume and MACD (other indicators easily added) data points.

The program then iterates through the entire history of prices and other indicators and calculates the average difference between the Chosen Pattern and the sequence of current data points. If this difference satisfies some upper bound (e.g. aveDiff < 0.5), then the current price series is saved with all other instances of recognised patterns. nb. this bound is different for each indicator.

Intuitively, if there are a larger number of recognised patterns that are similar to the Chosen Pattern, then it's more likely that the pattern is a recurring phenomena. As this process is done for each indicator and each time step in Bitcoin's history however, the selection of the afore mentioned 'upper bounds' is key. If they're too high then there will be too many recognised patterns, too small there won't be enough. This forms a nice optimisation problem, as we want to find the optimal parameters to find the most patterns with the most significance - this will be a future post. If the pattern is recognised enough times, then it is saved to a recognisedPatterns array, alongside other relevant information. Below are some examples of recognised patterns.

<p align="center">
  <img src="plot2.png" width="350"/>
  <img src="plot3.png" width="350"/>
  <img src="plot4.png" width="350"/>
</p>

This only returned patterns in volume and close price, as the parameter (upper bound) for MACD was too low so no patterns were recognised. This is an avenue I'll explore, to find optimal parameters.
