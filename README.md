# GrabAIforSEA (Traffic Mangement)

**Numpy, pandas, matplotlib.pyplot, pmdarima, statsmodels NEEDED.**<br/>
*Training.csv us too big to upload here in GitHub, so it is not included.*

Since the traffic demand for the following time will be affected by the previous traffic demand and traffic is seasonal for every day (24 hours, 96 data in 15 min time interval), instead of judging by the position of the location, we forecast based on the historical data by using SARIMA model with 96 data lag. 

This is a time series problem and this challenge is done by using Seasonal Auto Regressive Integrated Moving Average (SARIMA) model.
There are more explanations and guides in the document.  I did some testing and the results will be in the document as well for viewing purpose.

### To run the program 

1.Change the “training.csv” to the correct path of the “test.csv”. Run every row in Jupyter Notebook and it will automatically tidy up the data format to match with my program.

**Note: For testing in "training.csv", after pointing to the correct file, simply run all the code and this program will show all the related results.**

**By default it is grabData(separated_data[geohash6[3]],100,4), which location = geohash6[3], start from time_order 100 and continuous fir 4 days, meaning 100+(4*96) = 484, it predicts the demand of 485 - 489 time_order.**


2.There are some parts that to uncomment and comment out to focus, so that the testing can be done accordingly. (more explanation in the Jupyter notebook for the code)

A)<br />
\# comment out this when doing testing<br />
final_test = grabData(separated_data[geohash6[3]],100,4)<br />
stationarity = stationarity(final_test)<br />

\# uncomment it when doing testing<br />
\# final_test = grabDataTesting(separated_data["geohash6--Name"])<br />
\# stationarity = stationarity(final_test)<br />

B)<br />
\# comment out this for testing<br />
final_test = grabData(separated_data[geohash6[3]],100,4)

\# ---------------------------uncomment this for testing-------------------<br />
\# second parameter is suggested to be 4 continuos day to predict the next 5 interval<br />
\# final_test = grabDataTesting(separated_data[geohash6[3]],4)<br />

C)<br />
\# comment out this for testing<br />
plt.plot(grabData(separated_data[geohash6[3]],100,5)[:-91])<br />

\# uncomment this for testing<br />
\# plt.plot(grabDataTesting(separated_data[geohash6[3]],4))

D)<br />
\# comment out this for testing<br />
RMSE = np.sum((final_demand.as_matrix() - grabData(separated_data[geohash6[3]],100,5)[-96:-91].values.reshape(-1))**2)/len(final_demand)

\# uncomment this for testing<br />
\# RMSE = np.sum((final_demand.as_matrix() - grabDataTesting(separated_data[geohash6[3]],4)[-96:-91].values.reshape(-1))**2)/len(final_demand)*
